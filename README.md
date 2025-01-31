const MeetingTranscriptApp = () => {
  let meetingDetails = {
    title: "",
    date: "",
    time: "",
    location: "",
    participants: "",
  };
  let transcript = [];
  let currentSpeaker = "";
  let currentText = "";

  function handleAddEntry() {
    if (currentSpeaker && currentText) {
      const newEntry = {
        timestamp: new Date().toLocaleTimeString(),
        speaker: currentSpeaker,
        text: currentText,
      };
      transcript.push(newEntry);
      currentText = "";
    }
  }

  return `
    <div class='p-6 max-w-3xl mx-auto bg-white shadow-md rounded-xl'>
      <h1 class='text-xl font-bold mb-4'>Meeting Transcript App</h1>
      
      <div class='mb-4'>
        <label class='block text-sm font-medium'>Meeting Title</label>
        <input type='text' class='w-full p-2 border rounded-md' />
      </div>
      
      <div class='grid grid-cols-2 gap-4 mb-4'>
        <div>
          <label class='block text-sm font-medium'>Date</label>
          <input type='date' class='w-full p-2 border rounded-md' />
        </div>
        <div>
          <label class='block text-sm font-medium'>Time</label>
          <input type='time' class='w-full p-2 border rounded-md' />
        </div>
      </div>
      
      <div class='mb-4'>
        <label class='block text-sm font-medium'>Location</label>
        <input type='text' class='w-full p-2 border rounded-md' />
      </div>

      <div class='mb-4'>
        <label class='block text-sm font-medium'>Participants</label>
        <textarea class='w-full p-2 border rounded-md' rows='2'></textarea>
      </div>
      
      <hr class='my-4' />
      <h2 class='text-lg font-semibold'>Transcript</h2>
      <div class='mb-4'>
        <label class='block text-sm font-medium'>Speaker</label>
        <input type='text' class='w-full p-2 border rounded-md' />
      </div>
      
      <div class='mb-4'>
        <label class='block text-sm font-medium'>Text</label>
        <textarea class='w-full p-2 border rounded-md' rows='2'></textarea>
      </div>
      
      <button class='px-4 py-2 bg-blue-500 text-white rounded-md' onclick='handleAddEntry()'>
        Add Entry
      </button>
      
      <div class='mt-6'>
        <h3 class='text-lg font-semibold'>Transcript Entries</h3>
        <ul class='mt-2'>
          ${transcript.map((entry, index) => `
            <li key='${index}' class='p-2 border-b'>
              <span class='text-sm text-gray-500'>[${entry.timestamp}]</span>
              <strong class='ml-2'>${entry.speaker}:</strong>
              <span class='ml-2'>${entry.text}</span>
            </li>
          `).join('')}
        </ul>
      </div>
    </div>
  `;
};

export default MeetingTranscriptApp;
