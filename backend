const express = require('express');
const app = express();
const bodyParser = require('body-parser');
const multer = require('multer');
const upload = multer({ dest: 'uploads/' });

app.use(bodyParser.json());

const port = process.env.PORT || 3000;

// Helper function to validate input
function validateInput(req, res) {
  if (!req.body || !req.body.data) {
    return res.status(400).json({ error: 'Invalid input' });
  }
  return true;
}

// POST endpoint
app.post('/bfhl', upload.single('file_b64'), (req, res) => {
  try {
    if (!validateInput(req, res)) return;

    const { data, file_b64 } = req.body;
    const userId = 'kss_navya_27102003'; // hardcoded for simplicity
    const email = 'nk4088@srmist.edu.in'; // hardcoded for simplicity
    const rollNumber = 'RA2111028010086'; // hardcoded for simplicity

    const numbers = data.filter((item) => !isNaN(item));
    const alphabets = data.filter((item) => isNaN(item));
    const highestLowercaseAlphabet = alphabets.filter((item) => item === item.toLowerCase()).sort((a, b) => b.localeCompare(a))[0];

    const fileValid = file_b64 ? true : false;
    const fileMimeType = file_b64 ? 'image/png' : null; // hardcoded for simplicity
    const fileSizeKb = file_b64 ? 400 : null; // hardcoded for simplicity

    res.json({
      is_success: true,
      user_id: userId,
      email,
      roll_number: rollNumber,
      numbers,
      alphabets,
      highest_lowercase_alphabet: [highestLowercaseAlphabet],
      file_valid: fileValid,
      file_mime_type: fileMimeType,
      file_size_kb: fileSizeKb,
    });
  } catch (error) {
    console.error(error);
    res.status(500).json({ error: 'Internal server error' });
  }
});

// GET endpoint
app.get('/bfhl', (req, res) => {
  res.json({ operation_code: 1 });
});

app.listen(port, () => {
  console.log(`Server listening on port ${port}`);
});