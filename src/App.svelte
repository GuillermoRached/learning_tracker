<script>
  import Profile from "./lib/Profile.svelte";
  import ProgressBar from "./lib/ProgressBar.svelte";
  import NewTask from "./lib/NewTask.svelte";
  import TodoList from "./lib/TodoList.svelte";
  import SelectedTask from "./lib/SelectedTask.svelte";

  const today = new Date();

  const previousData = [
    {
      day: 1,
      time: "14:30:00",
      imageUrl: "https://i.redd.it/duv11av99nm11.png",
      feelings: [],
      tasks: [
        {
          id: 1,
          name: "Read chapter 1 of Networking Basics",
          description: "Learning about protocols",
          minutes: 30,
          done: true,
        },
        {
          id: 2,
          name: "Complete a svelte component",
          description:
            "practice html, css, and js by creating a svelete component",
          minutes: 45,
          done: true,
        },
      ],
    },
    {
      day: 2,
      time: "14:30:00",
      imageUrl:
        "https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Marcus_Aurelius_Glyptothek_Munich.jpg/1200px-Marcus_Aurelius_Glyptothek_Munich.jpg",
      feelings: [],
      tasks: [
        {
          id: 1,
          name: "Read entry of Meditations",
          description:
            "Learning what Marcus Aurelius had thought of as important",
          minutes: 2,
          done: true,
        },
        {
          id: 2,
          name: "Complete a svelte component",
          description:
            "practice html, css, and js by creating a svelete component",
          minutes: 60,
          done: true,
        },
        {
          id: 3,
          name: "Watch a HealthyGamer video",
          description:
            "Education about mental health in relation to gaming and goals.",
          minutes: 20,
          done: true,
        },
      ],
    },
    {
      day: 3,
      time: "14:30:00",
      imageUrl:
        "https://static.wikia.nocookie.net/mrrobot/images/3/3e/Elliot.jpg/revision/latest?cb=20240118015330",
      feelings: [],
      tasks: [
        {
          id: 1,
          name: "Read entry of Meditations",
          description:
            "Learning what Marcus Aurelius had thought of as important",
          minutes: 2,
          done: true,
        },
        {
          id: 2,
          name: "Meet with professor for senior design advising",
          description:
            "Starting senior design and meeting with professor to get feedback on project idea.",
          minutes: 40,
          done: true,
        },
        {
          id: 3,
          name: "Complete a svelte component",
          description:
            "practice html, css, and js by creating a svelete component",
          minutes: 45,
          done: true,
        },
        {
          id: 4,
          name: "Read a chapter of Practical Malware Analysis",
          description:
            "Learning about lower level concepts and how to analyze malware safely.",
          minutes: 60,
          done: true,
        },
      ],
    },
  ];

  const getActiveDays = () => {
    return previousData.length;
  };

  const getPreviousDays = () => {
    let dayList = [];
    for (const record of previousData) {
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
      dayList.push();
    }
    return dayList;
  };

  const sampleUser = {
    name: "Sample User",
    started: new Date(),
    activeDays: getActiveDays(),
    imageUrl: "",
  };

  let tasks = [
    {
      id: 1,
      name: "Task 1",
      description: "Description for task 1",
      done: false,
    },
  ];

  let selectedTask;

  const getProgress = () =>
    Math.round((tasks.filter((t) => t.done).length / tasks.length) * 100);
</script>

<div class="app-container">
  <div class="top-row">
    <div class="profile-progress">
      <Profile user={sampleUser} />
      <ProgressBar percentage={getProgress()} />
    </div>
    <NewTask bind:taskList={tasks} />
  </div>
  <div class="bottom-row">
    <TodoList {tasks} bind:selectedTask />
    {#if selectedTask}
      <div class="bottom-separator">
        <svg>
          <circle cx="25%" cy="50%" r="5" />
          <circle cx="50%" cy="50%" r="5" />
          <circle cx="75%" cy="50%" r="5" />
        </svg>
      </div>
      <SelectedTask bind:selectedTask />
    {/if}
  </div>

  <!-- Feelings of the day -->
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
    justify-content: space-around;
    margin-bottom: 10rem;
  }

  .bottom-row {
    display: flex;
    align-items: center;
    justify-content: space-around;
  }
</style>
