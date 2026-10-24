# Using the Google Cloud Speech API: Challenge Lab

## ID: ARC131

## Task 2: Transcribe Speech to English Text

Create request.json

```bash
cat <<EOF >request.json
{
"config": {
"encoding": "LINEAR16",
"languageCode": "en-US",
"audioChannelCount": 2
},
"audio": {
"uri": "gs://spls/arc131/question_en.wav"
}
}
EOF
```

## Task 3. Transcribe speech to Spanish text

Create speech_request_sp.json:

```bash
cat <<EOF >speech_request_sp.json
{
"config": {
"encoding": "FLAC",
"languageCode": "es-ES"
},
"audio": {
"uri": "gs://spls/arc131/multi_es.flac"
}
}
EOF
```

# Explore Generative AI with the Gemini API in Agent Platform: Challenge Lab

## ID: GSP515

## Commend 1:

```bash
curl -X POST \
-H "Authorization: Bearer $(gcloud auth print-access-token)" \
-H "Content-Type: application/json" \
"https://${API_ENDPOINT}/v1/projects/${PROJECT_ID}/locations/${LOCATION}/publishers/google/models/${MODEL_ID}:generateContent" \
-d '{
"contents": [{
"role": "user",
"parts": [{"text": "Why is the sky blue?"}]
```
}]

}'

## Commend 2:

**FunctionDeclaration**

**Tool**

weather_tool

**Part**

gs://github-repo/img/gemini/multimodality_usecases_overview/mediterraneansea.mp4

gene	rate_content_stream

# Store, Process, and Manage Data on Google Cloud: Challenge Lab

## ID: ARC100

## Commend 1:

```bash
export BUCKET=
export REGION=
export TOPIC=
export FUNCTION=
```

## Commend 2:

```bash
curl -LO https://raw.githubusercontent.com/chayandeokar/Cloud-Skills-2025/refs/heads/master/Store%2C%20Process%2C%20and%20Manage%20Data%20on%20Google%20Cloud%20Challenge%20Lab/ARC100.sh
sudo chmod +x ARC100.sh
./ARC100.sh
```

# Build a Website on Google Cloud: Challenge Lab

## ID: GSP319

## Commend 1:

```bash
curl -LO raw.githubusercontent.com/prateekrajput08/Arcade-Google-Cloud-Labs/refs/heads/main/Build%20a%20Website%20on%20Google%20Cloud%3A%20Challenge%20Lab/TechCode.sh
sudo chmod +x TechCode.sh
./TechCode.sh
```

# Develop AI-Powered Prototypes in Google AI Studio: Challenge Lab

## ID: GSP529

## Commend 1:

Create a simple interactive web application called Fantasy Character Creator.

The application should have a clean, simple interface with a prominent "Generate Character" button.

When the user clicks "Generate Character", generate and display a random fantasy character.

Each generated character must have:

- A unique Name

- A Class

The Class should be one of fantasy classes such as Mage, Rogue, Warrior, Ranger, Paladin, or Cleric.

Every time the Generate Character button is clicked, generate a new random character with a different name and class combination.

Display the character's Name and Class clearly on the page.

Keep the initial version simple. Do not add portraits, backstories, player-card stats, or deck functionality yet.

## Commend 2:

Modify the existing Fantasy Character Creator application.

Add a character portrait feature for the currently displayed character.

Requirements:

## 1. Add a "Generate Portrait" button.

## 2. Add a "Regenerate Portrait" button.

## 3. When "Generate Portrait" is clicked, generate a cartoon/video game style portrait representing the currently displayed fantasy character.

## 4. The portrait should be based on the character's current Name and Class.

## 5. Display the generated portrait in the application.

## 6. When "Regenerate Portrait" is clicked, generate a new portrait for the same currently displayed character.

## 7. Regenerating the portrait must not change the character's Name or Class.

8. If no character has been generated yet, the portrait buttons should not attempt to generate a portrait.

9. Keep the existing Generate Character functionality working.

Do not remove the existing character generation feature.

## Commend 3:

Refine the existing Fantasy Character Creator UI without removing any existing functionality.

Transform the visual design into an "ancient alchemist's workbench" fantasy theme.

Required design changes:

## 1. Use a dark, textured background that feels like an ancient alchemist's workbench.

## 2. Give the application an immersive fantasy/alchemical appearance.

## 3. Use a stylized fantasy-style font for the character's Name.

## 4. Make the character Name visually prominent.

## 5. Use colors, borders, panels, shadows, and decorative elements that fit an ancient fantasy alchemy theme.

## 6. Keep the interface readable and usable.

## 7. Keep all existing functionality working:

- Generate Character

- Generate Portrait

- Regenerate Portrait

8. Do not remove or replace existing character data or functionality.

Only improve the UI and visual presentation while preserving the existing application features.

## Commend 4:

Modify the existing Fantasy Character Creator application.

Add a new "Generate Backstory" button.

Requirements:

## 1. Add a clearly visible "Generate Backstory" button.

## 2. The button should work for the currently displayed fantasy character.

## 3. When clicked, generate a unique origin story for the current character.

## 4. The backstory must be one to two sentences long.

## 5. The generated backstory must be inspired by the character's current Name and Class.

## 6. Display the generated backstory clearly in the application.

## 7. Generating a backstory must not change the character's Name, Class, or portrait.

8. If no character exists yet, handle the situation gracefully.

9. Preserve all existing functionality:

- Generate Character

- Generate Portrait

- Regenerate Portrait

10. Keep the existing ancient alchemist's workbench visual theme.

Do not remove existing features.

## Commend 5:

Transform the existing Fantasy Character Creator into a complete fantasy player-card application while preserving all existing functionality.

Reformat the entire UI into a bordered fantasy player card.

The player card must clearly display:

- Character Name

- Character Class

- Character Portrait

- Character Backstory

- Health

- Mana

- Strength

Generate random values for Health, Mana, and Strength whenever a new character is generated.

Requirements for stats:

## 1. Health must be randomly generated.

## 2. Mana must be randomly generated.

## 3. Strength must be randomly generated.

## 4. Display all three stats clearly on the player card.

## 5. Stats should belong to the currently displayed character.

## 6. Generating a new character should generate a new set of random stats.

## 7. Regenerating a portrait must not change the stats.

8. Generating a backstory must not change the stats.

Add a "Save to Deck" button.

When the user clicks "Save to Deck":

- Save the currently displayed character to a "My Deck" list within the application.

- The saved character should retain its Name, Class, Portrait, Backstory, Health, Mana, and Strength.

- The character should appear in the My Deck list.

- The user should be able to save multiple different characters.

- Saving a character should not replace previously saved characters.

- Prevent accidental loss of previously saved characters.

Add a clearly labeled "My Deck" section to the application.

Preserve all existing functionality:

- Generate Character

- Generate Portrait

- Regenerate Portrait

- Generate Backstory

- Save to Deck

Keep the ancient alchemist's workbench visual theme.

Make the player card visually polished, bordered, and fantasy-themed while keeping the interface usable.

# Implement Speech and Language Solutions with Pre-trained APIs: Challenge Lab

## ID: ARC132

## COMMENT 1:

```bash
export API_KEY="YOUR_API_KEY"
#!/usr/bin/env bash
set -e
if [ -z "${API_KEY}" ]; then
API_KEY=$(gcloud services api-keys list --filter="displayName:*API key*" --format="value(keyString)" 2>/dev/null | head -n 1)
if [ -z "${API_KEY}" ]; then
API_KEY=$(gcloud alpha services api-keys list --format="value(keyString)" 2>/dev/null | head -n 1)
```
fi

fi

```bash
if [ -z "${API_KEY}" ]; then
echo "Error: API_KEY is not set and could not be detected. Run 'export API_KEY=\"...\"' and retry."
```
exit 1

fi

```bash
export API_KEY
gcloud services enable speech.googleapis.com texttospeech.googleapis.com translate.googleapis.com >/dev/null 2>&1 || true
cat << 'EOF' > synthesize-text.json
{
"input":{
"text":"Cloud Text-to-Speech API allows developers to include natural-sounding, synthetic human speech as playable audio in their applications. The Text-to-Speech API converts text or Speech Synthesis Markup Language (SSML) input into audio data like MP3 or LINEAR16 (the encoding used in WAV files)."
},
"voice":{
"languageCode":"en-GB",
"name":"en-GB-Standard-A",
"ssmlGender":"FEMALE"
},
"audioConfig":{
"audioEncoding":"MP3"
}
}
EOF
curl -s -H "Content-Type: application/json; charset=utf-8" --data @synthesize-text.json "https://texttospeech.googleapis.com/v1/text:synthesize?key=${API_KEY}" -o synthesize-text.txt
cat << 'EOF' > tts_decode.py
import argparse
from base64 import decodebytes
import json
```
def decode_tts_output(input_file, output_file):

```bash
with open(input_file) as input_stream:
response = json.load(input_stream)
audio_data = response['audioContent']
with open(output_file, "wb") as new_file:
new_file.write(decodebytes(audio_data.encode('utf-8')))
if __name__ == '__main__':
```
parser = argparse.ArgumentParser()

```bash
parser.add_argument('--input', required=True)
parser.add_argument('--output', required=True)
args = parser.parse_args()
```
decode_tts_output(args.input, args.output)

EOF

```bash
python3 tts_decode.py --input "synthesize-text.txt" --output "synthesize-text-audio.mp3"
cat << 'EOF' > speech_request_fr.json
{
"config":{
"encoding":"FLAC",
"languageCode":"fr-FR",
"audioChannelCount":1
},
"audio":{
"uri":"gs://cloud-samples-data/speech/corbeau_renard.flac"
}
}
EOF
cp speech_request_fr.json speech_request.json
cp speech_request_fr.json request.json
curl -s -X POST -H "Content-Type: application/json; charset=utf-8" --data @speech_request_fr.json "https://speech.googleapis.com/v1/speech:recognize?key=${API_KEY}" -o response.json
cp response.json speech_response.json
curl -s -X POST -H "Content-Type: application/json; charset=utf-8" -d '{"q":"これは日本語です。","target":"en"}' "https://translation.googleapis.com/language/translate/v2?key=${API_KEY}" -o translation_response.txt
cp translation_response.txt translated_response.txt
curl -s -X POST -H "Content-Type: application/json; charset=utf-8" -d '{"q":"Este%é%japonês."}' "https://translation.googleapis.com/language/translate/v2/detect?key=${API_KEY}" -o detection_response.txt
cp detection_response.txt detected_response.txt
```

## COMMENT 2:

```bash
ls -la synthesize-text-audio.mp3 speech_response.json translated_response.txt detected_response.txt
```
