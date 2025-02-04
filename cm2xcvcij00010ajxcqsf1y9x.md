---
title: "Effortlessly Resize Images with Cloudflare's On-the-Fly Solution"
datePublished: Thu Oct 31 2024 13:42:56 GMT+0000 (Coordinated Universal Time)
cuid: cm2xcvcij00010ajxcqsf1y9x
slug: effortlessly-resize-images-with-cloudflares-on-the-fly-solution
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1730379489437/21a10177-1ac0-42d9-ae2d-c8970a938a22.png

---

Resizing images has traditionally been a complex and time-consuming task, often requiring intricate code and handling various image processing libraries. Developers had to manage different image formats, maintain quality, and ensure performance, which could be quite challenging.

However, with Cloudflare's on-the-fly image resizing solution, this process has become remarkably simple. Cloudflare allows developers to resize, optimize, and deliver images efficiently without the need for extensive backend processing.

This service streamlines the workflow, reduces server load, and enhances the user experience by delivering appropriately sized images quickly and effortlessly.

Thankfully now, if your solution is built and hosted with Optimizely, it is now built in with cloudflare. Since Optimizely uses Cloudflare CDN in it’s layers.

The CDN's image resizing feature enables you to optimize and transform images dynamically by adding parameters to the image's URL. This allows you to resize, crop, rotate, adjust quality, and apply filters to images without needing to store multiple versions on your server. As a result, it can enhance the performance and user experience of your website or application.

[Source](https://docs.developers.optimizely.com/digital-experience-platform/docs/image-resizing-using-cdn) : To utilize Cloudflare's image resizing feature, you can modify the image URL by appending specific parameters in the following format:

`https://<DOMAIN>/cdn-cgi/image/<OPTIONS>/<SOURCE-IMAGE>`

* `<DOMAIN>`: The domain on Optimizely, for example, [www.domain.com](http://www.domain.com).
    
* `/cdn-cgi/image/`: A fixed prefix indicating that this path is managed by the image resizing feature.
    
* `<OPTIONS>`: A comma-separated list of options like width, height, and quality.
    
* `<SOURCE-IMAGE>`: The absolute path on the origin server pointing to the image you want to resize, such as globalassets/image.png.
    

Check [more here](https://docs.developers.optimizely.com/digital-experience-platform/docs/image-resizing-using-cdn) and start utilizing this awesome feature, *just for free*