---
layout: post
title: "Audio tag does not work in Safari"
date: 2017-03-08 16:20:55 +0800
comments: true
categories: html5 safari audio 
---
<p>Test - 再见二丁目</p>
<audio id="music" autoplay preload loop controls></audio>
<head>
<script>
    (function() {
        function log(info) {
            console.log(info);
        }
		function safariPlay() {
            audioEl.load(); // iOS 9   load before play
            audioEl.play(); // iOS 7,8 play
        }
        var audioEl = document.getElementById('music');
        // play enabled event order: loadstart -> loadedmetadata -> loadeddata -> canplay -> play -> playing
        // play disabled event order:
        // iPhone5  iOS 7.0.6 loadstart
        // iPhone6s iOS 9.1   loadstart -> loadedmetadata -> loadeddata -> canplay
        audioEl.addEventListener('loadstart', function() {
            log('loadstart');
        }, false);
   		audioEl.addEventListener('loadeddata', function() {
            log('loadeddata');
        }, false);
   		audioEl.addEventListener('loadedmetadata', function() {
            log('loadedmetadata');
        }, false);
   		audioEl.addEventListener('canplay', function() {
            log('canplay');
        }, false);
  		audioEl.addEventListener('play', function() {
            log('play');
            // remove this event after audio can play
            window.removeEventListener('clickstart', safariPlay, false);
        }, false);
        audioEl.addEventListener('playing', function() {
            log('playing');
        }, false);
  		audioEl.addEventListener('pause', function() {
            log('pause');
        }, false);
		// iOS Safari disabled audio autoplay
        window.addEventListener('clickstart', safariPlay, false);
		audioEl.src = '/assets/mp3/zaijianerdingmu.mp3';
    })();
</script>
</head> 

    <script>
    (function() {
        function log(info) {
            console.log(info);
        }
		function safariPlay() {
            audioEl.load(); // iOS 9   load before play
            audioEl.play(); // iOS 7,8 play
        }
        var audioEl = document.getElementById('music');
        // play enabled event order: loadstart -> loadedmetadata -> loadeddata -> canplay -> play -> playing
        // play disabled event order:
        // iPhone5  iOS 7.0.6 loadstart
        // iPhone6s iOS 9.1   loadstart -> loadedmetadata -> loadeddata -> canplay
        audioEl.addEventListener('loadstart', function() {
            log('loadstart');
        }, false);
   		audioEl.addEventListener('loadeddata', function() {
            log('loadeddata');
        }, false);
   		audioEl.addEventListener('loadedmetadata', function() {
            log('loadedmetadata');
        }, false);
   		audioEl.addEventListener('canplay', function() {
            log('canplay');
        }, false);
  		audioEl.addEventListener('play', function() {
            log('play');
            // remove this event after audio can play
            window.removeEventListener('clickstart', safariPlay, false);
        }, false);
        audioEl.addEventListener('playing', function() {
            log('playing');
        }, false);
  		audioEl.addEventListener('pause', function() {
            log('pause');
        }, false);
		// iOS Safari disabled audio autoplay
        window.addEventListener('clickstart', safariPlay, false);
		audioEl.src = '/assets/mp3/zaijianerdingmu.mp3';
    })();
	</script>
