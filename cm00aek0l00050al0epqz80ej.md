---
title: "Finally Updating Pychartjs: Making It Framework-Agnostic and Compatible with All Python Web Frameworks"
seoTitle: "Pychartjs Update: Now Framework-Agnostic"
seoDescription: "Pychartjs is now framework-agnostic and compatible with all Python web frameworks, offering flexibility in rendering dynamic charts"
datePublished: Mon Aug 19 2024 00:58:05 GMT+0000 (Coordinated Universal Time)
cuid: cm00aek0l00050al0epqz80ej
slug: finally-updating-pychartjs-making-it-framework-agnostic-and-compatible-with-all-python-web-frameworks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724028964110/9f0e3bae-eeb6-485c-bf3b-4b618f0a4ff8.png
tags: charts, chartjs, python, python3

---

After years of taking over the maintenance of [`pychartjs`](https://github.com/tavallaie/pychartjs), I'm excited to finally have the time to bring some much-needed updates to the project. It's been a journey, but I'm proud to say that [`pychartjs`](https://github.com/tavallaie/pychartjs) is now framework-agnostic and fully compatible with all major Python web frameworks, complete with render options that make it incredibly flexible for developers.

## The Journey Back to Pychartjs

Several years ago, I inherited [`pychartjs`](https://github.com/tavallaie/pychartjs)—a Python library designed to generate dynamic charts using Chart.js. While the library had a strong foundation, it had become outdated over time, and I knew it needed a refresh to stay relevant in the rapidly evolving Python ecosystem. With the growing demand for versatile and modern tools, I decided it was time to bring [`pychartjs`](https://github.com/tavallaie/pychartjs) up to date and make it more flexible for developers across various frameworks.

## What’s New in Pychartjs

### 1\. **Framework-Agnostic Design**

One of the major changes I’ve implemented is making [`pychartjs`](https://github.com/tavallaie/pychartjs) framework-agnostic. No longer confined to a specific web framework, [`pychartjs`](https://github.com/tavallaie/pychartjs) can now be integrated seamlessly into any Python web framework—whether it's Django, Flask, FastAPI, Robyn, or any other WSGI/ASGI framework. This opens up the library to a much broader audience and allows developers to choose the framework that best suits their needs without sacrificing charting capabilities.

### 2\. **Flexible Render Options**

Another key feature of the update is the introduction of flexible render options. With the new rendering capabilities, developers can customize how charts are generated and displayed within their web applications. Whether you need to render charts dynamically based on context variables or generate static charts for reports, [`pychartjs`](https://github.com/tavallaie/pychartjs) now provides the tools to do so with ease.

### 3\. **Seamless Integration with Any Python Web Framework**

Understanding the diverse needs of the Python web development community, I've updated [`pychartjs`](https://github.com/tavallaie/pychartjs) to integrate smoothly with any Python web framework. Whether you're using traditional frameworks like Django or Flask, or newer, faster options like FastAPI and Robyn, [`pychartjs`](https://github.com/tavallaie/pychartjs) is designed to fit right in. Its framework-agnostic approach means you can use it with any HTML rendering engine, such as Jinja, Mako, or your framework's built-in options.

#### **Robyn and Beyond**

Robyn, a relatively new but fast-growing web framework, is fully supported by [`pychartjs`](https://github.com/tavallaie/pychartjs). You can easily create and render charts directly in your Robyn routes, and because [`pychartjs`](https://github.com/tavallaie/pychartjs) is framework-agnostic, it adapts well to any WSGI or ASGI framework.

Here’s how you can quickly set up a simple Robyn application with [`pychartjs`](https://github.com/tavallaie/pychartjs):

```bash
from robyn import Robyn
from pychartjs.charts import Chart
from pychartjs.datasets import Dataset
from pychartjs.enums import ChartType
from robyn.templating import JinjaTemplate

app = Robyn(__file__)

template = JinjaTemplate("templates")

@app.get("/")
async def get_chart(request):
    dataset = Dataset(
        label="Sales Data",
        data=[10, 20, 30, 40, 50],
        backgroundColor="rgba(75, 192, 192, 0.2)",
        borderColor="rgba(75, 192, 192, 1)",
        borderWidth=1,
    )
    chart = Chart(
        chart_type=ChartType.LINE,
        datasets=[dataset],
        labels=["January", "February", "March", "April", "May"]
    )
    charts_html = chart.render()
    return template.render_template("index.html", charts_html=charts_html)

if __name__ == "__main__":
    app.start(port=8080)
```

### Flexibility with HTML Rendering Options

One of the strengths of the updated [pychartjs](https://github.com/tavallaie/pychartjs) is its compatibility with a wide range of HTML rendering engines. Whether you're using Jinja in Flask, Django templates, or any other templating system, [`pychartjs`](https://github.com/tavallaie/pychartjs) fits seamlessly into your workflow. You can inject the rendered chart HTML into your templates, allowing for dynamic and interactive data visualizations in your web pages.

## How to Get Started

Getting started with the new and improved [`pychartjs`](https://github.com/tavallaie/pychartjs) is straightforward:

1. **Install** [`pychartjs`](https://github.com/tavallaie/pychartjs) using Poetry:
    
    ```bash
    poetry add pychartjs
    ```
    
    [Or,](https://github.com/tavallaie/pychartjs) if you're [using pip](https://github.com/tavallaie/pychartjs):
    
    ```bash
    pip install pychartjs
    ```
    
2. **Integrate with Your Framework:**
    
    Use [`pychartjs`](https://github.com/tavallaie/pychartjs) in your preferred Python web framework by creating and rendering charts directly in your views or routes.
    
    For example, in a Robyn app, you can render the charts directly into your HTML templates, as shown in the example above.
    
3. **Customize Your Charts:**
    
    With flexible rendering options, you can now tailor your charts to meet the specific needs of your application. Whether it’s context-aware rendering, custom styles, or integrating with dynamic data sources, [`pychartjs`](https://github.com/tavallaie/pychartjs) offers the flexibility to create exactly what you need.
    

## Looking Ahead

This update is just the beginning. As [`pychartjs`](https://github.com/tavallaie/pychartjs) continues to evolve, I’m looking forward to seeing how the Python community will leverage its new capabilities. Whether you’re building data dashboards, integrating charts into web apps, or generating reports, [`pychartjs`](https://github.com/tavallaie/pychartjs) is here to make charting simple, flexible, and powerful.

Thank you to everyone who has supported [`pychartjs`](https://github.com/tavallaie/pychartjs) over the years. Your feedback and contributions have been invaluable in shaping this release. I’m excited to see what you all build with the new [`pychartjs`](https://github.com/tavallaie/pychartjs).