<script>
  import Profile from "./lib/Profile.svelte";
  import ProgressBar from "./lib/ProgressBar.svelte";
  import NewTask from "./lib/NewTask.svelte";
  import TodoList from "./lib/TodoList.svelte";
  import SelectedTask from "./lib/SelectedTask.svelte";
  import HamburgerMenu from "./lib/HamburgerMenu.svelte";
  import FeelingToday from "./lib/FeelingToday.svelte";

  const today = new Date();

  const data = [
    {
      day: 1,
      time: "14:30:00",
      imageUrl: "https://i.redd.it/duv11av99nm11.png",
      feeling: "bad",
      tasks: [
        {
          id: 1,
          name: "Read chapter 1 of Networking Basics",
          description: "Learning about protocols",
          minutes: 30,
          essay: "",
          done: true,
        },
        {
          id: 2,
          name: "Complete a svelte component",
          description:
            "practice html, css, and js by creating a svelete component",
          minutes: 45,
          essay: "",
          done: true,
        },
      ],
    },
    {
      day: 2,
      time: "14:30:00",
      imageUrl:
        "https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Marcus_Aurelius_Glyptothek_Munich.jpg/1200px-Marcus_Aurelius_Glyptothek_Munich.jpg",
      feeling: "good",
      tasks: [
        {
          id: 1,
          name: "Read entry of Meditations",
          description:
            "Learning what Marcus Aurelius had thought of as important",
          minutes: 2,
          essay: "",
          done: true,
        },
        {
          id: 2,
          name: "Complete a svelte component",
          description:
            "practice html, css, and js by creating a svelete component",
          minutes: 60,
          essay: "",
          done: true,
        },
        {
          id: 3,
          name: "Watch a HealthyGamer video",
          description:
            "Education about mental health in relation to gaming and goals.",
          minutes: 20,
          essay: "",
          done: true,
        },
      ],
    },
    {
      day: 3,
      time: "14:30:00",
      imageUrl:
        "https://openpsychometrics.org/tests/characters/test-resources/pics/MR/1.jpg",
      feeling: "good",
      tasks: [
        {
          id: 1,
          name: "Read entry of Meditations",
          description:
            "Learning what Marcus Aurelius had thought of as important",
          minutes: 2,
          essay: "",
          done: true,
        },
        {
          id: 2,
          name: "Meet with professor for senior design advising",
          description:
            "Starting senior design and meeting with professor to get feedback on project idea.",
          minutes: 40,
          essay: "",
          done: true,
        },
        {
          id: 3,
          name: "Complete a svelte component",
          description:
            "practice html, css, and js by creating a svelete component",
          minutes: 45,
          essay: "",
          done: true,
        },
        {
          id: 4,
          name: "Read a chapter of Practical Malware Analysis",
          description:
            "Learning about lower level concepts and how to analyze malware safely.",
          minutes: 60,
          essay: "",
          done: true,
        },
      ],
    },
  ];

  let dayData = {
    day: 4,
    time: `${today.getHours()}:${today.getMinutes()}:${today.getSeconds()}`,
    imageUrl:
      "images/calcifer.png",
    feeling: "",
    tasks: [
    ],
  };

  data.push(dayData)  

  const getDay = (index) => {
    return data[index];
  }

  const getDays = (data) => {
    let dayList = [];
    for (const record of data) {
      let d = new Date();
      d.setDate(d.getDate() - record.day);
      d.setHours(
        Number(record.time.substring(0, record.time.indexOf(":"))),
        Number(
          record.time.substring(
            record.time.indexOf(":") + 1,
            record.time.lastIndexOf(":"),
          ),
        ),
        Number(record.time.substring(record.time.lastIndexOf(":") + 1)),
      );
      dayList.push(d);
    }
    return dayList;
  };

  const getActiveDays = () => {
    return data.length;
  };
  
  const sampleUser = {
    name: "Guillermo Rached",
    started: new Date(),
    activeDays: getActiveDays(),
    imageUrl: dayData.imageUrl,
  };

  let selectedTask;

  let progress;

  const getProgress = (taskList) =>
    Math.round((taskList.filter((t) => t.done).length / taskList.length) * 100);

  $: progress = getProgress(tasks);

  let allDays;
  let currentDay = data.length - 1;
  let feelingTotal;
  let minutesTotal;

  const getTotalFeeling = (data) => {
    let totalGood = 0,
      totalBad = 0,
      totalNeutral = 0;
    for (const record of data) {
      if (record.feeling == "good") totalGood += 1;
      else if (record.feeling == "bad") totalBad += 1;
      else if (record.feeling == "neutral") totalNeutral += 1;
    }

    return [totalBad, totalNeutral, totalGood];
  };

  const getTotalMinutes = (data) => {
    let mins = 0;
    for (const record of data) {
      for (const task of record.tasks) {
        mins += task.minutes;
      }
    }
    return mins;
  }

  $: feelingTotal = getTotalFeeling(data);
  $: allDays = getDays(data);
  $: dayData = getDay(currentDay)
  $: tasks = dayData.tasks
  $: minutesTotal = getTotalMinutes(data);
</script>

<div class="app-container">
  <HamburgerMenu days={allDays} bind:currentDay/>
  <div class="top-row">
    <div class="profile-progress">
      <Profile user={sampleUser} feelings={feelingTotal} dayData={dayData} minutes={minutesTotal}/>
      <ProgressBar percentage={progress} />
    </div>
    <NewTask bind:dayData={dayData} />
  </div>
  <div class="bottom-row">
    <TodoList {tasks} bind:selectedTask />
    {#if selectedTask}
      <svg>
        <circle cx="25%" cy="50%" r="5" />
        <circle cx="50%" cy="50%" r="5" />
        <circle cx="75%" cy="50%" r="5" />
      </svg>
      <SelectedTask bind:tasks bind:selectedTask />
    {/if}
  </div>

  <!-- Feelings of the day -->
  <FeelingToday bind:dayData />
</div>

<style>
  .app-container {
    display: flex;
    flex-direction: column;
    padding: 20px;
    font-family: Arial, sans-serif;
  }

  .top-row {
    display: flex;
    justify-content: center;
    margin-bottom: 2rem;
  }

  .profile-progress {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-right:auto;
    margin-left:auto;
  }

  .bottom-row {
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>
