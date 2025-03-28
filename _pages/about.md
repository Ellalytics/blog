---
layout: single
title: "About"
permalink: /about/
author_profile: true
---


Dynamic software engineer crafting robust full-stack solutions with Java/Python.<br>
Delivers scalable architectures that drive business impact.<br>
Designs cutting-edge RAG and GenAI applications.


## WORK EXPERIENCE

Duration | Employer | Title
--- | ---
2023 ~ now | Mingdy Consulting | Software Engineer
2017 ~ 2023 | State Grid | Software Engineer
2014 ~ 2017 | State Grid | Electrical Engineer
2011 ~ 2014 | Zhejiang University | Research Assistant

## SKILLS
<div class="radar-chart">
  <div class="chart-container">  
    <canvas id="radarChart"></canvas>  
    <div id="customLegend"></div>  
  </div>  
</div>  

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>  
<script>  
  const skillsHierarchy = [  
    {  
      category: "Core Programming",  
      color: {  
        border: 'rgba(255, 99, 132, 1)',  
        background: 'rgba(255, 99, 132, 0.2)',  
      },  
      skills: [  
        { name: "Java", score: 4 },  
        { name: "Python", score: 5 },  
        { name: "JavaScript", score: 4 }  
      ]  
    },  
    {  
      category: "Frontend",  
      color: {  
        border: 'rgba(54, 162, 235, 1)',  
        background: 'rgba(54, 162, 235, 0.2)',  
      },  
      skills: [  
        { name: "HTML", score: 5 },  
        { name: "CSS", score: 4 },  
        { name: "Vue.js", score: 4 },  
        { name: "Bootstrap", score: 5 },  
        { name: "Streamlit", score: 5 }  
      ]  
    },  
    {  
      category: "Backend",  
      color: {  
        border: 'rgba(255, 206, 86, 1)',  
        background: 'rgba(255, 206, 86, 0.2)',  
      },  
      subCategories: [  
        {  
          name: "Java Web",  
          skills: [  
            { name: "Spring", score: 5 },  
            { name: "Struts", score: 4 },  
            { name: "Servlet", score: 4 }  
          ]  
        },  
        {  
          name: "Python Web",  
          skills: [  
            { name: "Flask", score: 5 },  
            { name: "SQLAlchemy", score: 5 },  
            { name: "Flask-Login", score: 5 },  
            { name: "Jinja2", score: 4 },  
            { name: "Django", score: 5 }  
          ]  
        }  
      ]  
    },  
    {  
      category: "Data Management",  
      color: {  
        border: 'rgba(75, 192, 192, 1)',  
        background: 'rgba(75, 192, 192, 0.2)',  
      },  
      subCategories: [  
        {  
          name: "Relational DB",  
          skills: [  
            { name: "SQL", score: 5 },  
            { name: "MySQL", score: 5 },  
            { name: "Hibernate", score: 4 }  
          ]  
        },  
        {  
          name: "NoSQL",  
          skills: [  
            { name: "Redis", score: 5 },  
            { name: "Elasticsearch", score: 4 }  
          ]  
        }  
      ]  
    },  
    {  
      category: "AI Technologies",  
      color: {  
        border: 'rgba(153, 102, 255, 1)',  
        background: 'rgba(153, 102, 255, 0.2)',  
      },  
      subCategories: [  
        {  
          name: "LLM Integration",  
          skills: [  
            { name: "Transformer", score: 3 },  
            { name: "LangChain", score: 5 },  
            { name: "RAG", score: 5 },  
            { name: "Text Chunking", score: 5 },  
            { name: "Vector Embedding", score: 5 }  
          ]  
        },  


        {  
          name: "Agent Development",  
          skills: [  
            { name: "ChatPDF", score: 5 },  
            { name: "Prompt Engineering", score: 4 },  
            { name: "Complex Instructions", score: 5 }  
          ]  
        }  
      ]  
    }  
  ];  

  function prepareRadarData() {  
    let allLabels = [];  
    let datasets = [];  
    
    skillsHierarchy.forEach(category => {  
      const datasetTemplate = {  
        label: category.category,  
        backgroundColor: category.color.background,  
        borderColor: category.color.border,  
        pointBackgroundColor: category.color.border,  
        borderWidth: 0.6,  
        pointRadius: 2,  
        data: []  
      };  
      
      let dataset = {...datasetTemplate};  
      
      if (category.skills) {  
        category.skills.forEach(skill => {  
          const label = `${category.category}: ${skill.name}`;  
          allLabels.push(label);  
          dataset.data.push(skill.score);  
        });  
      }  
      
      if (category.subCategories) {  
        category.subCategories.forEach(subCategory => {  
          subCategory.skills.forEach(skill => {  
            const label = `${category.category} - ${subCategory.name}: ${skill.name}`;  
            allLabels.push(label);  
            dataset.data.push(skill.score);  
          });  
        });  
      }  
      
      datasets.push(dataset);  
    });  
    
    const finalDatasets = datasets.map(dataset => {  
      const fullData = Array(allLabels.length).fill(null);  
      
      allLabels.forEach((label, index) => {  
        if (label.startsWith(dataset.label)) {  
          fullData[index] = dataset.data[allLabels.filter(l => l.startsWith(dataset.label)).indexOf(label)];  
        }  
      });  
      
      return {  
        ...dataset,  
        data: fullData  
      };  
    });  
    
    return {  
      labels: allLabels,  
      datasets: finalDatasets  
    };  
  }  

  function createCustomLegend() {  
    const legendContainer = document.getElementById('customLegend');  
    legendContainer.style.display = 'flex';  
    legendContainer.style.flexWrap = 'nowrap';  
    legendContainer.style.justifyContent = 'space-between';  
    legendContainer.style.alignItems = 'center';  
    legendContainer.style.width = '100%';  
    legendContainer.style.marginTop = '20px';  
    legendContainer.style.marginLeft = '-20px';  // Add negative margin to move left

    legendContainer.style.padding = '10px 0';  
    
    skillsHierarchy.forEach(category => {  
      const legendItem = document.createElement('div');  
      legendItem.style.display = 'flex';  
      legendItem.style.alignItems = 'center';  
      legendItem.style.padding = '6px';  
      legendItem.style.whiteSpace = 'nowrap';
      legendItem.style.flex = '0 1 auto';
      
      const colorDot = document.createElement('span');  
      colorDot.style.width = '12px';  
      colorDot.style.height = '12px';  
      colorDot.style.borderRadius = '50%';  
      colorDot.style.marginRight = '8px';  
      colorDot.style.backgroundColor = category.color.border;  
      
      const text = document.createElement('span');  
      text.textContent = category.category;
      text.style.fontSize = '16px';         // Match the default text size
      text.style.fontWeight = '400';        // Normal font weight
      text.style.fontFamily = '-apple-system, BlinkMacSystemFont, "Roboto", "Segoe UI", "Helvetica Neue", "Lucida Grande", Arial, sans-serif';  // Match theme font
      text.style.color = '#494e52';         // Match theme text color
      text.style.lineHeight = '1.5';        // Match theme line height
      
      legendItem.appendChild(colorDot);  
      legendItem.appendChild(text);  
      legendContainer.appendChild(legendItem);  
    });  
  }  

  function sortDataByCategory() {  
    const data = prepareRadarData();  
    let sortedLabels = [];  
    let sortedDatasets = data.datasets.map(ds => ({...ds, data: []}));  
    
    skillsHierarchy.forEach(category => {  
      const categoryLabels = data.labels.filter(label =>   
        label.startsWith(category.category)  
      );  
      
      sortedLabels = [...sortedLabels, ...categoryLabels];  
      
      sortedDatasets.forEach(dataset => {  
        const datasetData = [];  
        
        categoryLabels.forEach(label => {  
          const originalIndex = data.labels.indexOf(label);  
          const originalDataset = data.datasets.find(ds => ds.label === dataset.label);  
          datasetData.push(originalDataset.data[originalIndex]);  
        });  
        
        dataset.data = [...dataset.data, ...datasetData];  
      });  
    });  
    
    return {  
      labels: sortedLabels,  
      datasets: sortedDatasets  
    };  
  }  

  document.addEventListener('DOMContentLoaded', function() {  
    const ctx = document.getElementById('radarChart').getContext('2d');  
    const chartData = sortDataByCategory();  
    
    const maxLabelLength = Math.max(...chartData.labels.map(l => l.length));  
    const fontSize = maxLabelLength > 35 ? 8 :   
                    maxLabelLength > 25 ? 9 :   
                    maxLabelLength > 20 ? 10 : 11;  
    
    const chart = new Chart(ctx, {  
      type: 'radar',  
      data: chartData,  
      options: {  
        responsive: true,  
        maintainAspectRatio: false,  
        scales: {  
          r: {  
            min: 0,  
            max: 5,  
            ticks: {  
              stepSize: 1,  
              backdropColor: 'rgba(255, 255, 255, 0.75)',  
              font: {  
                size: 10  
              }  
            },  
            pointLabels: {  
              font: {  
                size: fontSize  
              },  
              callback: function(value) {  
                return value.split(': ').pop();  
              },  
              color: '#334155'  
            },  
            grid: {  
              color: 'rgba(0, 0, 0, 0.05)'  
            },  
            angleLines: {  
              color: 'rgba(0, 0, 0, 0.1)'  
            }  
          }  
        },  
        plugins: {  
          legend: {  
            display: false  
          },  
          tooltip: {  
            backgroundColor: 'rgba(255, 255, 255, 0.9)',  
            titleColor: '#334155',  
            bodyColor: '#475569',  
            borderColor: '#e2e8f0',  
            borderWidth: 1,  
            padding: 10,  
            displayColors: true,  
            callbacks: {  
              title: function(context) {  
                return context[0].label;  
              },  
              label: function(context) {  
                if (context.raw !== null) {  
                  return `${context.dataset.label}: ${context.raw}/5`;  
                }  
                return '';  
              }  
            }  
          }  
        },  
        elements: {  
          line: {  
            tension: 0.1  
          }  
        }  
      }  
    });  
    
    createCustomLegend();  
  });  
</script>  

  
