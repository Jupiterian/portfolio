---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Input/Output & APIs
description: Keyboard Inputs, GameEnv Configuration, API Integration, Asynchronous I/O, JSON Parsing
permalink: /sprint6-io-api-skills
---

## Table of Contents
* TOC
{:toc}


## 5. Input/Output & APIs

### Keyboard Input
We read keypress maps dynamically.

{% capture io_keyboard_chal %}Demonstrating Keyboard Input Tracking.{% endcapture %}
{% capture io_keyboard_code %}
const keyPressed = "w";
const yVelocity = (keyPressed === "w") ? -10 : 0;
console.log("Key [" + keyPressed + "] registered. Jump velocity: " + yVelocity);
{% endcapture %}
{% include runners/code.html language="javascript" runner_id="io_keyboard" challenge=io_keyboard_chal code=io_keyboard_code %}


### Canvas Rendering
Implementing graphics updates for character sprites.

{% capture io_canvas_chal %}Demonstrating Canvas Rendering logic.{% endcapture %}
{% capture io_canvas_code %}
// Mocking the Canvas draw call
function drawSprite(x, y) {
    return "Drawing player sprite at canvas position (" + x + ", " + y + ")";
}
console.log(drawSprite(100, 450));
{% endcapture %}
{% include runners/code.html language="javascript" runner_id="io_canvas" challenge=io_canvas_chal code=io_canvas_code %}


### GameEnv Configuration
Injecting limits via GameSetup configurations.

{% capture io_gameenv_chal %}Demonstrating GameEnv Configuration.{% endcapture %}
{% capture io_gameenv_code %}
class GameEnv {
    static innerWidth = 1200;
    static innerHeight = 800;
}
console.log("GameEnv configured to bounds: " + GameEnv.innerWidth + "x" + GameEnv.innerHeight);
{% endcapture %}
{% include runners/code.html language="javascript" runner_id="io_gameenv" challenge=io_gameenv_chal code=io_gameenv_code %}


### API Integration
Fetching URLs from a designated backend.

{% capture io_api_integration_chal %}Demonstrating API Integration mapping.{% endcapture %}
{% capture io_api_integration_code %}
const targetAPI = "https://api.github.com/users/github";
console.log("Preparing to integrate and connect to: " + targetAPI);
{% endcapture %}
{% include runners/code.html language="javascript" runner_id="io_api_integration" challenge=io_api_integration_chal code=io_api_integration_code %}


### Asynchronous I/O
Executing Promises dynamically out of band from the animation loop.

{% capture io_async_io_chal %}Demonstrating Asynchronous I/O processing.{% endcapture %}
{% capture io_async_io_code %}
async function gatherData() {
    console.log("Awaiting async task...");
    // Simulated async sleep
    await new Promise(r => setTimeout(r, 500));
    console.log("Async operation completed cleanly!");
}
gatherData();
{% endcapture %}
{% include runners/code.html language="javascript" runner_id="io_async_io" challenge=io_async_io_chal code=io_async_io_code %}


### JSON Parsing
Deseralizing response stringified payloads back into objects.

{% capture io_json_parsing_chal %}Demonstrating JSON Parsing.{% endcapture %}
{% capture io_json_parsing_code %}
const mockResponse = '{"status": "success", "score": 900}';
// Parsing JSON natively
const resultObj = JSON.parse(mockResponse);
console.log("Parsed Status: " + resultObj.status + " | Final Score: " + resultObj.score);
{% endcapture %}
{% include runners/code.html language="javascript" runner_id="io_json_parsing" challenge=io_json_parsing_chal code=io_json_parsing_code %}
