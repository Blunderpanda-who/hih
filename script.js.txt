const song1 = document.getElementById("song1");
const song2 = document.getElementById("song2");
const song3 = document.getElementById("song3");

[song1, song2, song3].forEach(s => s.volume = 0);

function fadeIn(song) {
  song.play();
  let v = 0;
  const i = setInterval(() => {
    if (v < 0.3) {
      v += 0.02;
      song.volume = v;
    } else clearInterval(i);
  }, 200);
}

function fadeOut(song) {
  let v = song.volume;
  const i = setInterval(() => {
    if (v > 0.02) {
      v -= 0.02;
      song.volume = v;
    } else {
      song.pause();
      song.currentTime = 0;
      clearInterval(i);
    }
  }, 200);
}

/* FLOW */

function startLove() {
  fadeIn(song1); // chaandni
  document.querySelector(".landing").style.display = "none";
  document.getElementById("sorry").classList.remove("hidden");
}

function goToMemories() {
  fadeOut(song1);
  fadeIn(song2); // rtc
  document.getElementById("sorry").style.display = "none";
  document.getElementById("memories").classList.remove("hidden");
}

function goToChristmas() {
  document.getElementById("memories").style.display = "none";
  document.getElementById("christmas").classList.remove("hidden");
}

function goToNewYear() {
  fadeOut(song2);
  fadeIn(song3); // high on you
  document.getElementById("christmas").style.display = "none";
  document.getElementById("newyear").classList.remove("hidden");
}
