---
layout: title
title: 解决iOS中双击页面上移切 fixed 元素异常的问题
date: 2018-02-28 15:48:09
tags:
---

```bash

(() => {
	let UA = window.navigator.userAgent;
	if(UA.toLowerCase().indexOf("ios") < 0) {
		return;
	}
		
	let lastTouch;

	window.addEventListener("touchend", (e) => {
		const now = Date.now();

		if(lastTouch && (now - lastTouch) < 500) {
			e.preventDefault();
		}

		lastTouch = now;
	}, false);
})();

```
