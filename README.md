ScholarAudioProcessor
=====================


Emulador del raspberry: 

http://sourceforge.net/projects/rpiqemuwindows/postdownload?source=dlp

http://www.linux-mitterteich.de/fileadmin/datafile/papers/2013/qemu_raspiemu_lug_18_sep_2013.pdf

======================


![alt tag](https://raw.github.com/AudioProcessor/ScholarAudioProcessor/master/Diagrama-Base-controlador-Raspberry.jpg)


Sobre el diagrama: 

El audio (pre amplificado) "entrará" al raspberry por medio de una tarjeta de sonido.

Las tarjetas propuestas que al parecer funcionan sin problemas son las siguientes: 

*Logitech USB To 3.5mm Jack Audio Adapter ASIN: B0058P0I2C w/ dwc_otg.speed=1

*Beringher UCA222 w/ dwc_otg.speed=1

*Griffin iMic. Cheap, 3.5mm jacks, mic/line in, USB powered w/ dwc_otg.speed=1

*ESI UDJ 6, 6 24bit outputs @ 48kHz : 4 line output on RCA, 2 headphone out on jack 6,3mm, USB powered, works out of box on Raspbian (i.e. without USB speed down), tested with kernel 3.6.11+ and active ethernet connection and with Pd Vanilla 0.44-2, can't manage to make it work with only 2 outputs @ 96kHz.

*ESI UGM6 ouput works with alsa driver without USB slowdown, input doesn't work with output and ethernet(got crackles). Input and output seems to work after disabling ethernet (see the linuxaudio wiki for more info (link on top of this page)). Interface not seen correctly with USB slowdown.

*ESI GIGAPort AG (old version), only the last 6 outputs works. Out 1&2 does work either on headphone or on RCA plug. Don't know why...

*ESI GIGAPort HD+. Works fine with alsa driver and without USB slowdown. Note this is HD+ (HD plus) version, the HD is reported to not work.

*HY544 USB 3D Sound Adapter. You just need to type 'amixer -c 1 set Mic 80% cap' in a term window to enable to Mic. In Pd, under preferences, choose 'Alsa' as output and under 'audio configuration', select 'input Generic AudioUSB Device (hardware) Channels 1' and 'output Generic USB Audio Device (plug-in) Channels 2'.

el raspberry recibirá la señal de audio y lo procesará segun el efecto que defina el control (delay, reverv, chorus...) 


-la Interfáz que controlará los efectos será posible por medio de OSC 
http://es.wikipedia.org/wiki/OpenSound_Control


-El procesamiento del sonido será a través de Pure Data
http://es.wikipedia.org/wiki/Pure_Data
http://puredata.info/

