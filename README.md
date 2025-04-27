# csci2400-lab-4---code-optimization-solved
**TO GET THIS SOLUTION VISIT:** [CSCI2400 Lab 4 – Code Optimization Solved](https://www.ankitcodinghub.com/product/csci2400-solved-2/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;120176&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CSCI2400 Lab 4 - Code Optimization  Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
Introduction

This assignment deals with optimizing memory intensive code. Image processing offers many examples of functions that can benefit from optimization. In this lab, youâ€™ll be improving the overall performance of an â€œimage processingâ€ application by a factor of about 25 â€“ an extra credit phase will challenge you do increase the speed further. In the past, some students have sped up the code by a factor of 200-300. The score you receive for the “performance” portion of the lab depends on the score returned by the Judge script with the filters for the default image (blocks-small.bmp). Your code must function correctly for each filter and can be tested using make test

The application youâ€™ll be modifying reads in an â€œimageâ€ (a picture) and a â€œfilterâ€. An image is represented as a three-dimensional array, described in cs1300bmp.h. Each pixel is represented as a combination of (red, green, blue) values. When coded in the BMP picture format, the individual (R,G,B) values can taken on the values 0…255, but the cs1300bmp.h code is designed to handle larger pixel values. The code in cs1300bmp.cpp provides routines for reading and writing images in the BMP format. You are free to modify the format or the layout of the data structures in that code.

The â€œfilterâ€ is an n x n array of numbers. Weâ€™ll go through the logistics of how a â€œfilterâ€ works in recitation and in class and briefly summarize it here. Basically, you can cause a number of visual affects by applying a filter to an image. The filter is implemented as a convolution, which means that elements of the filter matrix are multiplied by the image matrix to compute a new value for the image. Pictorially, this is represented as:

Computationally, this is structured as five nested for loops (three to go over the colors, row and columns and two more to apply the filter). In the solution provided to you, filters are represented using the Filter class, implemented in Filter.h and Filter.cpp.

The majority of the work performed by the filter application is in the routine shown below:

“` long long cycStart, cycStop; rdtscll(cycStart); output -&gt; width = input -&gt; width; output -&gt; height = input -&gt; height;

for(int col = 1; col &lt; (input -&gt; width) – 1; col = col + 1) { for(int row = 1; row &lt; (input -&gt; height) – 1 ; row = row + 1) { for(int plane = 0; plane &lt; 3; plane++) { output -&gt; color[plane][row][col] = 0; for (int j = 0; j &lt; filter -&gt; getSize(); j++) { for (int i = 0; i &lt; filter -&gt; getSize(); i++) { output -&gt; color[plane][row][col] = output -&gt; color[plane][row][col] + input -&gt; color[plane][row + i – 1][col + j – 1] * filter -&gt; get(i, j); } } output -&gt; color[plane][row][col] = output -&gt; color[plane][row][col] / filter -&gt; getDivisor(); if ( output -&gt; color[plane][row][col] &lt; 0 ) { output -&gt; color[plane][row][col] = 0; } if ( output -&gt; color[plane][row][col] &gt; 255 ) { output -&gt; color[plane][row][col] = 255; } output -&gt; color[plane] [row][col] = output -&gt; color[plane][row][col]; } } } rdtscll(cycStop); double diff = cycStop – cycStart; fprintf(stderr, “Took %f cycles to process, or %f cycles per pixel “, diff, diff / (output -&gt; width * output -&gt; height)); “ This routine is â€œinstrumentedâ€ using therdscll` function. This inline function records the starting and finish times in terms of CPU cycles. We use this to determine the â€œcycles per elementâ€ needed to apply the filter to a given image. A sample of the output for the provided setup code looks like the following when run:

Took 170624720.000000 cycles to process, or 3229.816007 cycles per pixel

The cycle counter measures times using the CPU clock of your computer. It is fairly accurate, but many things (such as other running programs) influence the reported time. Thus, we will use the median of a number of runs to determine the time for a particular implementation of the program for a number of different filters. ` Your job is going to be to improve the performance of this application using techniques detailed in Chapter 5 of the text. Youâ€™ll be using two images (boats.bmp and blocks-small.bmp) The first image is fairly small (useful for quickly testing ideas) and the second image is larger (and used for grading / evaluation). You can run your program using a command line similar to this:

$ filter hline.filter boats.bmp

This invocation will leave the output image in filter-hline-boats.bmp and will report the time taken, as in the examples above. You can repeat the image name (or use different images) on the same command line to run the filter multiple times &amp; return the average. For example:

$ ./filter hline.filter boats.bmp boats.bmp Took 139255936.000000 cycles to process, or 2636.025138 cycles per pixel Took 137527184.000000 cycles to process, or 2603.300977 cycles per pixel Average cycles per sample is

2619.663057

Performance and Correctness

Weâ€™ll be using a script called Judge to score your program. The Judge program takes three optional arguments. * -n specifies the number of times each filter should be executed, * -i specifies the image file and, * -p specifies the program name.

The default options are shown explicitly in the following example.

% make g++ -m32 -g -O0 -fno-omit-frame-pointer -o filter FilterMain.cpp Filter.cpp cs1300b ./Judge -p ./filter

-i blocks-small.bmp gauss: 4003.824003..4038.171866..3872.371058..3990.658428..3931.838805..4319.173193 avg:

3807.727624..3822.502626..3962.588553..4237.542068..4322.871861..4056.862357.. hline:

4171.320541..4234.822551..3851.320030..4385.223120..4366.434546..4422.357822 emboss:

3694.797139..3924.230283..3927.254491..4309.121033..3981.110480..3990.70275 Scores are 3694 3807 3822 3851 3872 3924 3927 3931 3962 3981 3990 3990 4003 4038 40 median CPE for is 4003 Resulting score for is 0 echo “Done” Done

This would result in an average of 4003 cycles per second. Scoring is based on the a function based on the CPE for the blocks-small.bmp image running on the GitHub Actions. In other words, the GitHub Actions is being the source of truth for grading.

The Makefile includes a target make test that compares your output to the reference solution. Run make test frequently, because itâ€™s easy to accidentally break the code when trying to optimize. Your code must be correct as well as quick.

The Makefile also provides a make judge rule that runs the test images and filters. Lastly, it provides a make clean rule to delete any temporary files or images.

Your measured time needs to include any active processing you do to the image after it is read in and before it is written out. Youâ€™re free to go â€œwhole hogâ€ on any optimization that might work, as long as it works with all the test images and filters included in the assignment. Your modified code does not need to handle any filters or images not included in the evaluation suite. This means you can go ahead and e.g change the matrix layout in the BMP image library, replace the Filter library, etc. However, youâ€™d be well advised to make certain those changes are important and effective before you sink a lot of time.

Extra Credit

The most â€œextremeâ€ solution is to use SIMD extensions such as MMX, SSE, SSE2 or SSE3. See http:// jeffmatherphotography.com/dispatches/2012/02/an-experiment-with-sse/ for more information.

For this lab, the CSCI 2400 machines will also each have multiple CPUâ€™s or cores and you could use the OpenMP language extensions (see http://bisqwit.iki.fi/story/howto/openmp/ to try to use both cores. This is an easy thing to do, but hard to get big speedup.

Alternative, you can take advantage of the sk1llz of other l33t h4x0rs and use a libary like the â€œOpen Computer Visionâ€ library, OpenCV. This is complicated because you have to get your image into their data structure format and you need to include the time to get it into that format in your timing.

One year, one student (who later interned for Google) got a CPE of about 20ish. Another year, another student (who later interned for Apple) for a CPE of about 3-4.

Some students have used these methods in the past, but youâ€™re well advised to go for the easy low-hanging fruit before tackling the most aggressive optimization.

If you come up with a solution that uses OpenMP, youâ€™ll get up to an additional 5 points extra credit. If you come up with a solution using SSE/vectors, youâ€™ll get up to 10 points extra credit (assuming your changes result in faster code and you know why) and likewise switching to OpenCV is good for 10 points of extra credit. In each case, youâ€™ll have to know what you did and why it works like always.

Logistics

The only â€œhand-inâ€ will be electronic through your GitHub repo. Any clarifications and revisions to the assignment will be posted on the course Web page.

Different computers will run this code at different speeds (even measured in â€œcycles per secondâ€). In order to have a level playing field, everyone must use the CSCI 2400 machines on the https://coding.csel.io platform to time their projects.

Since itâ€™s usually true that making something run faster on one machine makes it run faster on another, you might be able to do your development on one machine and then use the https://coding.csel.io machines simply to validate your measurements or improvements.

Grading

The score calculated by running the program provides 40% of the total score. You need to be able to explain why your code modifications improve the running time for the program and explain what would happen with minor modifications for the other 60%.

Again, you must be able to explain why you got the performance you did, so you should take notes for why you made each modification to bring to your grading meetings.
