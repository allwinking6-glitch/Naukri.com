<!DOCTYPE html>
<html>
<head>
  <title>Job Portal</title>
  <style>
    body {
      margin: 0;
      font-family: Arial;
      color: #333;
    }

    /* Hero Section */
    .hero {
      background: url('https://images.unsplash.com/photo-1521737604893-d14cc237f11d') no-repeat center center/cover;
      height: 100vh;
      color: white;
      text-align: center;
      display: flex;
      flex-direction: column;
      justify-content: center;
      background-blend-mode: darken;
      background-color: rgba(0,0,0,0.6);
    }

    .hero h1 {
      font-size: 50px;
    }

    .hero p {
      font-size: 20px;
    }

    .btn {
      padding: 10px 20px;
      background: orange;
      border: none;
      cursor: pointer;
      margin-top: 10px;
    }

    /* Sections */
    .section {
      padding: 40px;
      text-align: center;
    }

    .cards {
      display: flex;
      justify-content: center;
      gap: 20px;
      flex-wrap: wrap;
    }

    .card {
      border: 1px solid #ddd;
      padding: 20px;
      width: 200px;
      border-radius: 10px;
    }

    input {
      padding: 8px;
      margin: 5px;
    }

    .job {
      border: 1px solid #ccc;
      padding: 10px;
      margin-top: 10px;
      border-radius: 8px;
    }

  </style>
</head>

<body>

<!-- Hero -->
<div class="hero">
  <h1>Find Your Dream Job</h1>
  <p>Helping 10,000+ People Get Jobs Successfully</p>
  <button class="btn" onclick="scrollToJobs()">Find Jobs</button>
</div>

<!-- Categories -->
<div class="section">
  <h2>Jobs for Everyone</h2>
  <div class="cards">
    <div class="card">Freshers</div>
    <div class="card">Experienced</div>
    <div class="card">Students</div>
    <div class="card">Drivers</div>
    <div class="card">Delivery Jobs</div>
    <div class="card">Office Jobs</div>
  </div>
</div>

<!-- Profile -->
<div class="section">
  <h2>Create Your Profile</h2>
  <input id="name" placeholder="Your Name">
  <input id="location" placeholder="Location">
  <input id="salary" placeholder="Expected Salary">
  <br>
  <button class="btn" onclick="saveProfile()">Save Profile</button>
</div>

<!-- Post Job -->
<div class="section">
  <h2>Post a Job</h2>
  <input id="jobTitle" placeholder="Job Title">
  <input id="jobLocation" placeholder="Location">
  <input id="jobSalary" placeholder="Salary">
  <br>
  <button class="btn" onclick="postJob()">Post Job</button>
</div>

<!-- Jobs -->
<div class="section" id="jobSection">
  <h2>Available Jobs</h2>
  <div id="jobs"></div>
</div>

<script>
let jobs = [];

function scrollToJobs() {
  document.getElementById("jobSection").scrollIntoView();
}

function saveProfile() {
  const user = {
    name: document.getElementById('name').value,
    location: document.getElementById('location').value,
    salary: document.getElementById('salary').value
  };
  localStorage.setItem('user', JSON.stringify(user));
  alert("Profile saved successfully!");
}

function postJob() {
  const job = {
    title: document.getElementById('jobTitle').value,
    location: document.getElementById('jobLocation').value,
    salary: document.getElementById('jobSalary').value
  };
  jobs.push(job);
  displayJobs();
}

function applyJob(title) {
  alert("Applied for " + title);
}

function displayJobs() {
  const jobDiv = document.getElementById('jobs');
  jobDiv.innerHTML = "";
  jobs.forEach(job => {
    jobDiv.innerHTML += `
      <div class="job">
        <h3>${job.title}</h3>
        <p>Location: ${job.location}</p>
        <p>Salary: ${job.salary}</p>
        <button class="btn" onclick="applyJob('${job.title}')">Apply</button>
      </div>
    `;
  });
}
</script>

</body>
</html>
