---
layout: single
title: "About"
permalink: /about/
author_profile: true
---


Dynamic software engineer crafting robust full-stack solutions with Java/Python.

Delivers scalable architectures that drive business impact.

Designs cutting-edge RAG and generative AI applications.


## WORK EXPERIENCE

Duration | Employer | Title
--- | ---
2023 ~ now | Mingdy Consulting | Software Engineer
2017 ~ 2023 | State Grid | Software Engineer
2014 ~ 2017 | State Grid | Electrical Engineer
2011 ~ 2014 | Zhejiang University | Research Assistant

## Skills


<div class="skills-container">  
  <div class="chart-container">  
    <canvas id="skillsRadarChart"></canvas>  
  </div>  
</div>  

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>  

<script>  
document.addEventListener('DOMContentLoaded', function() {  
  const ctx = document.getElementById('skillsRadarChart').getContext('2d');  
  
  const allLabels = [  
    'Java', 'Python', 'Javascript', 'HTML', 'CSS', 'SQL',  
    // Python Web 
    'Flask', 'Django', 'Flask-RESTful', 'Flask-Login', 'Redis-Py', 'SQLAlchemy', 'Jinja',  
    // Java Web
    'Servlet', 'Spring', 'Struts', 'Hibernate', 'Maven', 'WebSocket', 'ElasticSearch',  
    // front end  
    'Vue.js', 'Bootstrap', 'Ajax',  
    // GenAI  
    'LangChain', 'FAISS', 'OpenAI API / HF', 'Sentence Transformers', 'Streamlit'  
  ];  
  
  const skillsData = {  
    labels: allLabels,  
    datasets: [  
      {  
        label: 'PL',  
        data: [5, 5, 4, 5, 4, 5, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],  
        backgroundColor: 'rgba(54, 162, 235, 0.2)',  
        borderColor: 'rgba(54, 162, 235, 1)',  
        pointBackgroundColor: 'rgba(54, 162, 235, 1)',  
        pointBorderColor: '#fff',  
        pointHoverBackgroundColor: '#fff',  
        pointHoverBorderColor: 'rgba(54, 162, 235, 1)'  
      },  
      {  
        label: 'Python Web',  
        data: [0, 0, 0, 0, 0, 0, 5, 5, 5, 5, 5, 4, 5, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],  
        backgroundColor: 'rgba(75, 192, 192, 0.2)',  
        borderColor: 'rgba(75, 192, 192, 1)',  
        pointBackgroundColor: 'rgba(75, 192, 192, 1)',  
        pointBorderColor: '#fff',  
        pointHoverBackgroundColor: '#fff',  
        pointHoverBorderColor: 'rgba(75, 192, 192, 1)'  
      },  
      {  
        label: 'Java Web',  
        data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 5, 4, 4, 4, 4, 4, 4, 0, 0, 0, 0, 0, 0, 0, 0],  
        backgroundColor: 'rgba(255, 159, 64, 0.2)',  
        borderColor: 'rgba(255, 159, 64, 1)',  
        pointBackgroundColor: 'rgba(255, 159, 64, 1)',  
        pointBorderColor: '#fff',  
        pointHoverBackgroundColor: '#fff',  
        pointHoverBorderColor: 'rgba(255, 159, 64, 1)'  
      },  
      {  
        label: 'Front',  
        data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 3, 4, 3, 0, 0, 0, 0, 0],  
        backgroundColor: 'rgba(255, 99, 132, 0.2)',  
        borderColor: 'rgba(255, 99, 132, 1)',  
        pointBackgroundColor: 'rgba(255, 99, 132, 1)',  
        pointBorderColor: '#fff',  
        pointHoverBackgroundColor: '#fff',  
        pointHoverBorderColor: 'rgba(255, 99, 132, 1)'  
      },  
      {  
        label: 'GenAI',  
        data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 5, 4, 5, 4, 5],  
        backgroundColor: 'rgba(153, 102, 255, 0.2)',  
        borderColor: 'rgba(153, 102, 255, 1)',  
        pointBackgroundColor: 'rgba(153, 102, 255, 1)',  
        pointBorderColor: '#fff',  
        pointHoverBackgroundColor: '#fff',  
        pointHoverBorderColor: 'rgba(153, 102, 255, 1)'  
      }  
    ]  
  };  
  
  const options = {  
    scales: {  
      r: {  
        angleLines: { display: true },  
        suggestedMin: 0,  
        suggestedMax: 5,  
        ticks: {  
          stepSize: 1,  
          callback: function(value) {  
            if (value === 0) return '';  
            return value.toString();  
          }  
        }  
      }  
    },  
    plugins: {  
      legend: {   
        position: 'top',  
        labels: {  
          font: {  
            size: 14  
          }  
        }  
      },  
      tooltip: {  
        callbacks: {  
          label: function(context) {  
            const datasetLabel = context.dataset.label || '';  
            const label = context.label || '';  
            const value = context.raw || 0;  
            if (value === 0) return null;  
            const skillLevel = ['1', '2', '3', '4', '5'][value-1];  
            return `${datasetLabel} - ${label}: ${value}/5 (${skillLevel})`;  
          }  
        }  
      }  
    },  
    elements: {  
      line: {  
        borderWidth: 3  
      }  
    },  
    responsive: true,  
    maintainAspectRatio: false  
  };  
  
  const skillsRadarChart = new Chart(ctx, {  
    type: 'radar',  
    data: skillsData,  
    options: options  
  });  
});  
</script>  

<style>  
.skills-container {  
  margin: 2rem auto;  
  max-width: 900px;  
}  
.chart-container {  
  position: relative;  
  height: 700px;  
  width: 100%;  
  margin: 0 auto;  
}  
@media (max-width: 768px) {  
  .chart-container {  
    height: 600px;  
  }  
}  
</style>  

