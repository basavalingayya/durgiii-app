let pass = prompt("Enter password ❤️");

if (pass === null || pass.trim() !== "BR0711") {
  document.body.innerHTML = "<h2 style='text-align:center'>Access Denied 💔</h2>";
} else {

  let mood = "";

  window.onload = function () {

    let hour = new Date().getHours();
    let msg = "";

    if (hour < 12) msg = "Good Morning Durgiii ❤️";
    else if (hour < 18) msg = "Take care Durgiii ❤️";
    else msg = "Good Night Durgiii ❤️";

    document.getElementById("greet").innerText = msg;

    let saved = localStorage.getItem("durgiiiData");

    if (saved) {
      let data = JSON.parse(saved);

      mood = data.mood || "";
      document.getElementById("moodText").innerText = "Mood: " + mood;

      document.getElementById("tiffin").checked = data.tiffin;
      document.getElementById("lunch").checked = data.lunch;
      document.getElementById("snacks").checked = data.snacks;
      document.getElementById("dinner").checked = data.dinner;
    }
  };

  window.setMood = function (m) {
    mood = m;
    document.getElementById("moodText").innerText = "Mood: " + m;
  };

  document.addEventListener("DOMContentLoaded", () => {
    document.getElementById("date").addEventListener("change", function () {
      let d = new Date(this.value);
      d.setDate(d.getDate() + 28);
      document.getElementById("prediction").innerText =
        "Next: " + d.toDateString();
    });
  });

  window.submit = function () {

    let tiffin = document.getElementById("tiffin").checked ? "Yes" : "No";
    let lunch = document.getElementById("lunch").checked ? "Yes" : "No";
    let snacks = document.getElementById("snacks").checked ? "Yes" : "No";
    let dinner = document.getElementById("dinner").checked ? "Yes" : "No";
    let date = document.getElementById("date").value;

    let message =
      "❤️ Durgiii Update ❤️\n\n" +
      "Mood: " + mood + "\n" +
      "Tiffin: " + tiffin + "\n" +
      "Lunch: " + lunch + "\n" +
      "Snacks: " + snacks + "\n" +
      "Dinner: " + dinner + "\n" +
      "Period Date: " + date;

    localStorage.setItem("durgiiiData", JSON.stringify({
      mood, tiffin, lunch, snacks, dinner, date
    }));

    window.open(
      "https://wa.me/918310949668?text=" + encodeURIComponent(message),
      "_blank"
    );

    document.getElementById("done").innerText =
      "Sent ❤️";
  };
}