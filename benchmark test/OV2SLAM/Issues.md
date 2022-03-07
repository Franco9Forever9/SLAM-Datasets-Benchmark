#### **M2DGR Street_02 测试**
问题1：程序中断退出！
终端输出：
```shell
OpenCV Error: Assertion failed (isIdentity(expr)) in _InputArray, file /home/jgl/Dependencies/opencv-3.4.15/modules/core/src/matrix_expressions.cpp, line 1843
OpenCV Error: Assertion failed (isIdentity(expr)) in _InputArray, file /home/jgl/Dependencies/opencv-3.4.15/modules/core/src/matrix_expressions.cpp, line 1843
OpenCV Error: Assertion failed (isIdentity(expr)) in _InputArray, file /home/jgl/Dependencies/opencv-3.4.15/modules/core/src/matrix_expressions.cpp, line 1843
OpenCV Error: Assertion failed (isIdentity(expr)) in _InputArray, file /home/jgl/Dependencies/opencv-3.4.15/modules/core/src/matrix_expressions.cpp, line 1843
OpenCV Error: Assertion failed (isIdentity(expr)) in _InputArray, file /home/jgl/Dependencies/opencv-3.4.15/modules/core/src/matrix_expressions.cpp, line 1843
OpenCV Error: Assertion failed (isIdentity(expr)) in _InputArray, file /home/jgl/Dependencies/opencv-3.4.15/modules/core/src/matrix_expressions.cpp, line 1843
terminate called after throwing an instance of 'cv::Exception'
  what():  /home/jgl/Dependencies/opencv-3.4.15/modules/core/src/matrix_expressions.cpp:1843: error: (-215) isIdentity(expr) in function _InputArray

Stack trace (most recent call last) in thread 26569:
#18   Object "", at 0xffffffffffffffff, in 
#17   Source "../sysdeps/unix/sysv/linux/x86_64/clone.S", line 95, in __clone [0x7fdca0e9461e]
#16   Source "/build/glibc-uZu3wS/glibc-2.27/nptl/pthread_create.c", line 463, in start_thread [0x7fdca170c6da]
#15   Object "/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.25", at 0x7fdca14396de, in 
#14   Source "/home/jgl/Documents/Projects/OV2SLAM/src/ov2slam/src/ov2slam.cpp", line 156, in run [0x7fdca29cea7a]
        153:             if( pslamstate_->debug_ )
        154:                 std::cout << "\n \t >>> [SLAM Node] New image send to Front-End\n";
        155: 
      > 156:             bool is_kf_req = pvisualfrontend_->visualTracking(img_left, time);
        157: 
        158:             // Save current pose
        159:             Logger::addSE3Pose(time, pcurframe_->getTwc(), is_kf_req);
#13   Source "/home/jgl/Documents/Projects/OV2SLAM/src/ov2slam/src/visual_front_end.cpp", line 50, in visualTracking [0x7fdca29e964c]
         47:     bool iskfreq = trackMono(iml, time);
         48: 
         49:     if( iskfreq ) {
      >  50:         pmap_->createKeyframe(cur_img_, iml);
         51: 
         52:         if( pslamstate_->btrack_keyframetoframe_ ) {
         53:             cv::buildOpticalFlowPyramid(cur_img_, kf_pyr_, pslamstate_->klt_win_size_, pslamstate_->nklt_pyr_lvl_);
#12   Source "/home/jgl/Documents/Projects/OV2SLAM/src/ov2slam/src/map_manager.cpp", line 54, in createKeyframe [0x7fdca2a1259a]
         51:     prepareFrame();
         52: 
         53:     // Detect in im and describe in imraw
      >  54:     extractKeypoints(im, imraw);
         55: 
         56:     // Add KF to the map
         57:     addKeyframe();
#11   Source "/home/jgl/Documents/Projects/OV2SLAM/src/ov2slam/src/map_manager.cpp", line 319, in extractKeypoints [0x7fdca2a1202f]
        316:             vnewpts = pfeatextract_->detectGridFAST(im, pslamstate_->nmaxdist_, vpts, pcurframe_->pcalib_leftcam_->roi_rect_);
        317:         } 
        318:         else if ( pslamstate_->use_singlescale_detector_ ) {
      > 319:             vnewpts = pfeatextract_->detectSingleScale(im, pslamstate_->nmaxdist_, vpts, pcurframe_->pcalib_leftcam_->roi_rect_);
        320:         } else {
        321:             std::cerr << "\n Choose a detector between : gftt / FAST / SingleScale detector!";
        322:             exit(-1);
#10 | Source "/home/jgl/Documents/Projects/OV2SLAM/src/ov2slam/src/feature_extractor.cpp", line 334, in parallel_for_
    |   332:     auto cvrange = cv::Range(0, nbcells);
    |   333: 
    | > 334:     parallel_for_(cvrange, [&](const cv::Range& range) {
    |   335:         for( int i = range.start ; i < range.end ; i++ ) {
      Source "/home/jgl/Dependencies/opencv-3.4.15/install/include/opencv2/core/utility.hpp", line 601, in detectSingleScale [0x7fdca2a06fc3]
        599: inline void parallel_for_(const Range& range, std::function<void(const Range&)> functor, double nstripes=-1.)
        600: {
      > 601:     parallel_for_(range, ParallelLoopBodyLambdaWrapper(functor), nstripes);
        602: }
        603: #endif
#9    Object "/usr/lib/x86_64-linux-gnu/libopencv_core.so.3.2.0", at 0x7fdca2471fff, in cv::parallel_for_(cv::Range const&, cv::ParallelLoopBody const&, double)
#8    Object "/usr/lib/x86_64-linux-gnu/libtbb.so.2", at 0x7fdc9c14878f, in 
#7    Object "/usr/lib/x86_64-linux-gnu/libtbb.so.2", at 0x7fdc9c14be9a, in 
#6    Object "/usr/lib/x86_64-linux-gnu/libtbb.so.2", at 0x7fdc9c146d0b, in 
#5    Object "/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.25", at 0x7fdca140ead9, in std::rethrow_exception(std::__exception_ptr::exception_ptr)
#4    Object "/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.25", at 0x7fdca140eb20, in std::terminate()
#3    Object "/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.25", at 0x7fdca140eae5, in 
#2    Object "/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.25", at 0x7fdca1408956, in 
#1    Source "/build/glibc-uZu3wS/glibc-2.27/stdlib/abort.c", line 79, in abort [0x7fdca0db37f0]
#0    Source "../sysdeps/unix/sysv/linux/raise.c", line 51, in raise [0x7fdca0db1e87]
Aborted (Signal sent by tkill() 26546 1000)
./run.sh：行 4: 26546 已放弃               （核心已转储） rosrun ov2slam ov2slam_node /home/jgl/Documents/Projects/OV2SLAM/src/ov2slam/parameters_files/accurate/m2dgr/m2dgr_mono.yaml
```