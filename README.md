# ez-sporting-event-capture

Automated capture and processing of sporting events.

This project was started Dec 2020.  Interested?  Welcoming help planning & developing it.

Expected components:

1. capture
2. processing
3. viewing (basic viewing, annotating, analysis)

For now, success means to me being able to:
 - capture a soccer game without any human intervention (stationary camera, whole-field-capture, at high resolution, from good height above the field, possibly with fish-eye lens)
 - the processing step figures out what subregion of the video to show over time and handles correcting any lens distorition
 - watching the processed video is like watching a professionally broadcast game

# Roadmap

1. one camera
 - how will camera be positioned to capture at least half the field?  (e.g., [N-foot tripod](https://www.amazon.com/Glide-Gear-Camera-Sports-Tripod/dp/B07S9VNR73) w/ [gopro]() mount)
 - how will wide-field-of-view lens distortion be unwarped? (e.g., [GoPro wide angle correction](https://www.rcgroups.com/forums/showthread.php?1711535-Gimp-2-8-and-GoPro-wide-angle-correction) or [ffmpeg & lens correction](http://ffmpeg.org/ffmpeg-filters.html#lenscorrection))
 - how will region-of-interest over time be determined? (e.g., [Multi-target tracking from football player tracking](https://www.researchgate.net/publication/251415375_Multi-target_Tracking_on_a_Large_Scale_Experiences_from_Football_Player_Tracking))
 - how will processing be done, given region-of-interest over time? ([]())
 - should fisheye correction happen before identifying region of interest or vice versa?

2. multiple cameras
 - how will cameras be synched?
 - how will multiple streams be merged or selected?

3. sharing
 - .. 

Other resources / examples:
 - [moving video crop](https://video.stackexchange.com/questions/15417/moving-crop-in-video)
   - [trf files and ffmpeg](https://video.stackexchange.com/a/15465)
   - [trf may be slow, instead try trim filter to gen N frames and rebuild video](https://video.stackexchange.com/questions/15417/moving-crop-in-video#comment28207_19403)
 - [fisheye correct with gimp](https://www.rcgroups.com/forums/showthread.php?1711535-Gimp-2-8-and-GoPro-wide-angle-correction)
 - [remove gopro fisheye using ffmpeg](https://stackoverflow.com/questions/30832248/is-there-a-way-to-remove-gopro-fisheye-using-ffmpeg)
 - [Correcting lens distortion using ffmpeg](https://www.danielplayfaircal.com/blogging/ffmpeg/lensfun/v360/lenscorrection/fisheye/dodgeball/2020/03/24/correcting-lens-distortion-with-ffmpeg.html)
 - [OpenCV calibrate camera](https://docs.opencv.org/master/d9/d0c/group__calib3d.html#ga3207604e4b1a1758aa66acb6ed5aa65d)
 - [Camera calibration with OpenCV](https://docs.opencv.org/2.4/doc/tutorials/calib3d/camera_calibration/camera_calibration.html)
 - [OpenCV fisheye camera model](https://docs.opencv.org/master/db/d58/group__calib3d__fisheye.html#gsc.tab=0)
 - Example from [here](https://stackoverflow.com/a/55229835)
 
 ```
 ffmpeg -i input.mp4 \
    -vf 'lenscorrection=k2=0.006:k1=-0.18' \
    output.mp4
```

or [here](https://stackoverflow.com/a/55695738)

```
ffmpeg -i input.mp4 -vf "lenscorrection=0.5:0.5:-0.335:0.097" output.mp4
```

 - [Crop video with ffmpeg](https://video.stackexchange.com/questions/4563/how-can-i-crop-a-video-with-ffmpeg)
 - [cutting videos with ffmpeg](http://www.markbuckler.com/post/cutting-ffmpeg/)
 - [stabilize video with ffmpeg](http://public.hronopik.de/vid.stab/)
 - [vid.stab](http://public.hronopik.de/vid.stab/features.php?lang=en)
   - [example youtube video stablizing](https://youtu.be/HYE3KAl8RAQ)
