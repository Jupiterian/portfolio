---
layout: post
codemirror: true
title: Sprint 6 Final Project Skills - Operators
description: Mathematical Equations, String Concatenation, Boolean Expressions
permalink: /sprint6-operators-skills
---

## Table of Contents
* TOC
{:toc}


## 4. Operators

### Mathematical
We calculate physics constraints such as velocities or collisions boundaries.

{% capture op_mathematical_chal %}Demonstrating Mathematical Operators.{% endcapture %}
{% capture op_mathematical_code %}
const grav = 9.8;
let vY = -15; // Negative Y goes up
vY += grav * 0.1; // Mathematical addition & multiplication
console.log("New Velocity: " + vY.toFixed(2));
{% endcapture %}
{% include runners/code.html language="javascript" runner_id="op_mathematical" challenge=op_mathematical_chal code=op_mathematical_code %}


### String Operations
We perform path building and dynamic HTML insertions via concatenations.

{% capture op_string_ops_chal %}Demonstrating String Operations.{% endcapture %}
{% capture op_string_ops_code %}
const root = "/images/";
const file = "player.png";
// String Concatenation
const fullPath = root + file;
console.log("Full Asset Path: " + fullPath);
{% endcapture %}
{% include runners/code.html language="javascript" runner_id="op_string_ops" challenge=op_string_ops_chal code=op_string_ops_code %}


### Boolean Expressions
We check complex bounds evaluating true/false logic statements.

{% capture op_boolean_expr_chal %}Demonstrating Boolean Expressions.{% endcapture %}
{% capture op_boolean_expr_code %}
const playerLeft = 50, enemyRight = 45;
// Boolean evaluating 'Greater Than' operator
const isColliding = playerLeft < enemyRight;
// Logical NOT (!) operator
const safe = !isColliding;
console.log("Is Safe: " + safe);
{% endcapture %}
{% include runners/code.html language="javascript" runner_id="op_boolean_expr" challenge=op_boolean_expr_chal code=op_boolean_expr_code %}
