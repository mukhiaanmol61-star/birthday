
(function () {
  function startBirthdayWebsite() {
    const intro = document.getElementById("intro");
    const birthday = document.getElementById("birthday");
    const revealBtn = document.getElementById("revealBtn");

    const chapterModal = document.getElementById("chapterModal");
    const chapterWindow = document.querySelector(".chapter-window");
    const closeChapter = document.getElementById("closeChapter");
    const prevChapter = document.getElementById("prevChapter");
    const nextChapter = document.getElementById("nextChapter");
    const chapterCounter = document.getElementById("chapterCounter");

    const chapterIds = [
      "birthday-wishes",
      "memories",
      "reasons",
      "hard-days",
      "wishes",
      "letter",
      "promises",
      "forever",
      "last-surprise"
    ];

    let currentChapter = 0;

    // Make sure the website starts on the opening screen
    if (intro) intro.classList.remove("hidden");
    if (birthday) birthday.classList.add("hidden");
    if (chapterModal) chapterModal.classList.add("hidden");

    chapterIds.forEach(function (id) {
      const chapter = document.getElementById(id);
      if (chapter) chapter.classList.add("hidden");
    });

    // OPEN THE LITTLE GIFT
    if (revealBtn) {
      revealBtn.addEventListener("click", function (event) {
        event.preventDefault();

        if (intro) intro.classList.add("hidden");
        if (birthday) birthday.classList.remove("hidden");

        window.scrollTo(0, 0);
      });
    }

    // OPEN A CHAPTER
    function openChapter(index) {
      if (index < 0 || index >= chapterIds.length) return;

      currentChapter = index;

      chapterIds.forEach(function (id, i) {
        const chapter = document.getElementById(id);

        if (chapter) {
          chapter.classList.toggle("hidden", i !== index);
        }
      });

      if (chapterModal) {
        chapterModal.classList.remove("hidden");
      }

      if (chapterCounter) {
        chapterCounter.textContent =
          (index + 1) + " / " + chapterIds.length;
      }

      if (prevChapter) {
        prevChapter.disabled = index === 0;
      }

      if (nextChapter) {
        nextChapter.disabled = index === chapterIds.length - 1;
      }

      if (chapterWindow) {
        chapterWindow.scrollTop = 0;
      }

      window.scrollTo(0, 0);
    }

    // SCRAPBOOK CHAPTER BUTTONS
    document.querySelectorAll("[data-chapter]").forEach(function (button) {
      button.addEventListener("click", function () {
        const chapterId = button.getAttribute("data-chapter");
        const index = chapterIds.indexOf(chapterId);

        if (index !== -1) {
          openChapter(index);
        }
      });
    });

    // CLOSE CHAPTER
    if (closeChapter) {
      closeChapter.addEventListener("click", function () {
        if (chapterModal) chapterModal.classList.add("hidden");
      });
    }

    // PREVIOUS CHAPTER
    if (prevChapter) {
      prevChapter.addEventListener("click", function () {
        openChapter(currentChapter - 1);
      });
    }

    // NEXT CHAPTER
    if (nextChapter) {
      nextChapter.addEventListener("click", function () {
        openChapter(currentChapter + 1);
      });
    }

    // HEART MESSAGE REVEALS
    document.querySelectorAll(".heart-reveal").forEach(function (button) {
      button.addEventListener("click", function () {
        const message = button.querySelector(".reveal-message");
        const label = button.querySelector(".reveal-label");

        if (!message) return;

        const opening = message.classList.contains("hidden");

        message.classList.toggle("hidden");
        button.classList.toggle("opened");

        if (label) {
          label.textContent = opening
            ? "♥ A little love revealed"
            : "♡ Tap to reveal my love";
        }
      });
    });

    // TAP OUTSIDE THE PAPER TO CLOSE
    if (chapterModal) {
      chapterModal.addEventListener("click", function (event) {
        if (event.target === chapterModal) {
          chapterModal.classList.add("hidden");
        }
      });
    }

    // CLOSE CHAPTER WITH ESCAPE KEY
    document.addEventListener("keydown", function (event) {
      if (event.key === "Escape" && chapterModal) {
        chapterModal.classList.add("hidden");
      }
    });
  }

  // Run after the HTML has loaded
  if (document.readyState === "loading") {
    document.addEventListener("DOMContentLoaded", startBirthdayWebsite);
  } else {
    startBirthdayWebsite();
  }
})();
