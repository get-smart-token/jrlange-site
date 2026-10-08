THE AITHORITY - Chapter 1 audiobook video kit (full quality)

What this makes: a 1920x1080 MP4 of the Chapter 1 audio with a neon cyan/magenta
waveform over chapter1-background.png. About 18.5 minutes, roughly 250-600 MB.

Easiest: open Claude Code in this folder and say:
  "Install ffmpeg if needed, then run the command in README.txt using my
   Chapter 1 MP3 at <path to 00_Chapter_1.mp3>."

The command (replace CHAPTER1.mp3 with the path to your MP3):

ffmpeg -loop 1 -framerate 24 -i chapter1-background.png -i CHAPTER1.mp3 -filter_complex "[1:a]asplit=2[a1][a2];[a1]showwaves=s=1700x380:mode=cline:scale=sqrt:colors=0x00E5FF:r=24,format=rgba[w1];[a2]adelay=60|60,showwaves=s=1700x380:mode=line:scale=sqrt:colors=0xFF2BD6:r=24,format=rgba,colorchannelmixer=aa=0.65[w2];[w2][w1]overlay=format=auto[w];[w]split[ws][wg];[wg]gblur=sigma=14[glow];[0:v][glow]overlay=110:340:shortest=1[b1];[b1][ws]overlay=110:340:shortest=1,format=yuv420p[v]" -map "[v]" -map 1:a -c:v libx264 -preset veryfast -b:v 1700k -maxrate 2600k -bufsize 5200k -c:a aac -b:a 192k -shortest -movflags +faststart THE_AITHORITY_Chapter_1.mp4

For other chapters: make a copy of the background with the chapter number changed
(ask Claude), and swap in that chapter's MP3.
