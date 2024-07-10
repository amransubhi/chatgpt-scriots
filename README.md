# chatgpt-scripts
async function getChatGPTResponse(prompt) {
  const apiKey = 'sk-proj-3Yn8fbHm4ugXHHiElcjBT3BlbkFJhqufldH2lxg1SCZlkxlu';
  const url = 'https://api.openai.com/v1/engines/davinci-codex/completions';
  
  const response = await fetch(url, {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': Bearer ${apiKey}
    },
    body: JSON.stringify({
      prompt: prompt,
      max_tokens: 150
    })
  });
  
  const data = await response.json();
  return data.choices[0].text;
}

document.getElementById('chat-form').addEventListener('submit', async function(event) {
  event.preventDefault();
  const prompt = document.getElementById('chat-input').value;
  const response = await getChatGPTResponse(prompt);
  document.getElementById('chat-output').innerText = response;
});
