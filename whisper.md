
# Extraire l'audio d'une vidéo
ffmpeg -i AFC_part2.mp4 -vn -acodec pcm_s16le -ar 44100 -ac 2 AFC_part2_audio.wav

# Extraire la transcription texte de l'audio
whisper AFC_part2_audio.wav --model medium --language fr --device cpu
