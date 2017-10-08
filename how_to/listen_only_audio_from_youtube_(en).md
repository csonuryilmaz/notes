I will use [mpv](https://mpv.io/) for the purpose. It's a media player which is opensource and cross platform. It has also a command line interface that I will use for my purpose. As I want to listen only audio, I don't need a GUI

Example from run-time:
```
onurs-mbp:~ onuryilmaz$ mpv --no-video https://www.youtube.com/watch?v=zfXBNQMj2SE
Playing: https://www.youtube.com/watch?v=zfXBNQMj2SE
 (+) Audio --aid=1 --alang=eng (*) (opus)
AO: [coreaudio] 48000Hz stereo 2ch floatp
A: 00:03:45 / 00:03:45 (99%) Cache:  0s+0KB


Exiting... (End of file)
```
[mpv](https://mpv.io/) installation for mac os was very easy but on Debian 8 it take some time for me to listen youtube audio from console. So here is my notes:
#### Installing Mpv on Debian 8

I have found it and installed by Synaptic.
![Mpv package @Synaptic](/how_to/images/mpv-debian-8/mpv-debian-8-1.png?raw=true "Mpv package @Synaptic")

But when I tried to play youtube video, it gave me an error about **youtube-dl** and **ffmpeg**.
![Mpv package @Synaptic](/how_to/images/mpv-debian-8/mpv-debian-8-2.png?raw=true "Mpv package @Synaptic")

Youtube-dl was in recommended packages. So it wasn't installed. I found it in Synaptic.
![Mpv package @Synaptic](/how_to/images/mpv-debian-8/mpv-debian-8-3.png?raw=true "Mpv package @Synaptic")

It also installed **ffmpeg**. After installation, I tried again. This time it complained about version of **youtube-dl**.
![Mpv package @Synaptic](/how_to/images/mpv-debian-8/mpv-debian-8-4.png?raw=true "Mpv package @Synaptic")

So I removed it by package manager. I went to [its site](https://rg3.github.io/youtube-dl/download.html). Followed these installation instructions:
```bash
sudo wget https://yt-dl.org/downloads/latest/youtube-dl -O /usr/local/bin/youtube-dl
sudo chmod a+rx /usr/local/bin/youtube-dl
```
Finally, **mpv** played youtube link successfully.
![Mpv package @Synaptic](/how_to/images/mpv-debian-8/mpv-debian-8-5.png?raw=true "Mpv package @Synaptic")

#### Installing Mpv on Debian 9
It's very easy and no surprise while installing with package manager. All packages and its dependencies are suitable.
```bash
sudo apt install mpv/stable
```
or
```bash
sudo apt-get install mpv
```
will be enough to install mpv.
