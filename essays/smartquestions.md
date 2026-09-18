---
layout: essay
type: essay
title: "Importance of smart questions"
# All dates must be YYYY-MM-DD format!
date: 2026-09-10
published: true
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="300px" class="rounded float-start pe-4" src="../img/smart-questions/rtfm.png">

## What is a smart question?

To ask a smart question, you need to understand what a smart question is. Eric Raymond thinks a smart question has multiple components. The components are doing some research, explaining the problem clearly, show what you have already tried, giving specific details, asking specific questions, not making people do unnecessary work, etc. This helps you and others that try to help you save time, energy and can make the whole process smoother

## Why are smart questions important?

Software engineers rarely work independently, due to the job you will be often than not working with others. During your work you might face multiple problems that might be too hard to solve on your own. This is when communication will be an important skill to utilize to effectively solve a certain problem. This is when smart questions can be very useful. By asking smart questions people will be inclined to answer questions and solving problems will be quicker and easier than ever. Today we will be exploring some examples to help you understand it better. First, we will look at a good example of a smart question.
```
Q: Why is conditional processing of a sorted array faster than of an unsorted array? [Link](https://stackoverflow.com/questions/11227809/why-is-conditional-processing-of-a-sorted-array-faster-than-of-an-unsorted-array?)

In this C++ code, sorting the data (before the timed region) makes the primary loop ~6x faster:

#include <algorithm>
#include <ctime>
#include <iostream>

int main()
{
    // Generate data
    const unsigned arraySize = 32768;
    int data[arraySize];

    for (unsigned c = 0; c < arraySize; ++c)
        data[c] = std::rand() % 256;

    // !!! With this, the next loop runs faster.
    std::sort(data, data + arraySize);

    // Test
    clock_t start = clock();
    long long sum = 0;
    for (unsigned i = 0; i < 100000; ++i)
    {
        for (unsigned c = 0; c < arraySize; ++c)
        {   // Primary loop.
            if (data[c] >= 128)
                sum += data[c];
        }
    }

    double elapsedTime = static_cast<double>(clock()-start) / CLOCKS_PER_SEC;

    std::cout << elapsedTime << '\n';
    std::cout << "sum = " << sum << '\n';
}
Without std::sort(data, data + arraySize);, the code runs in 11.54 seconds.
With the sorted data, the code runs in 1.93 seconds.
(Sorting itself takes more time than this one pass over the array, so it's not actually worth doing if we needed to calculate this for an unknown array.)

Initially, I thought this might be just a language or compiler anomaly, so I tried Java:

import java.util.Arrays;
import java.util.Random;

public class Main
{
    public static void main(String[] args)
    {
        // Generate data
        int arraySize = 32768;
        int data[] = new int[arraySize];

        Random rnd = new Random(0);
        for (int c = 0; c < arraySize; ++c)
            data[c] = rnd.nextInt() % 256;

        // !!! With this, the next loop runs faster
        Arrays.sort(data);

        // Test
        long start = System.nanoTime();
        long sum = 0;
        for (int i = 0; i < 100000; ++i)
        {
            for (int c = 0; c < arraySize; ++c)
            {   // Primary loop.
                if (data[c] >= 128)
                    sum += data[c];
            }
        }

        System.out.println((System.nanoTime() - start) / 1000000000.0);
        System.out.println("sum = " + sum);
    }
}
With a similar but less extreme result.

My first thought was that sorting brings the data into the cache, but that's silly because the array was just generated.

What is going on?
Why is processing a sorted array faster than processing an unsorted array?
The code is summing up some independent terms, so the order should not matter.
```
First the title already gives the reader a good idea on what he is trying to ask making the reader understand his question instantly. Second, he provied actual code as evidence making all readers understand what point he is at and what he is talking about. Showing code makes the readers try it themselves to see if they can answer the question with their testing. Third, he is stating the observation and assumption differently as mixing them up can cause confusion slowing down how fast the readers can answer it. Lastly, he shows what he has already tested with c++ code and java to see if the language caused it but in this experiment it did not matter. 
I will not be showing all answers on here but there are 25 different replies that tried to answer his question. Because of his question being a good questions readers are more inclined to answer giving him 25 replies with all great responses that help the original question solved. The answer with the most upvotes thinks that it is due to branch prediction with a good reasoning and has a lot of thought behind it. If you want to know more about it click on the link and you can see all the interactions there.


## The not so smart way of asking a question.

This will be a not so smart question that makes readers hard or not wanting to answer his question. 

```
Q: dynamic treeview with html,php and javascript and mysql [link](https://stackoverflow.com/questions/38863933/dynamic-treeview-with-html-php-and-javascript-and-mysql?)

2

I have created a table in mysql database using php, and also i can displayed that table on the web form, But the thing is that i want to do, I have six field in my table.

That are,Sr_no which is auto increment, Process_no, Process Name, Ownership, Sheet Revision_no and Revision Date.

Now i want to make a dynamic tree view type in my field Process_no.

For eg: i have the value in that field M01, so when i'll click on M01 then there should be a sub-list under it, such as M01.1, M01.2,.... and so on. and this thing i want in every column of that field.

i had tried a lot but fail to do it.

if you have any solution or any code for it, then please help me. i'm not a experience candidate, new at php and mysql.

so please help.
```

For this question its hard to understand what he is trying to ask and he also doesn't show any examples/code so we're not sure what he even is talking about. When a question like this is asked its hard for readers to answer making them less inclined to answer them. He also didn't show any code that he has already tried but instead says tried alot but failed making him seem like lazy and haven't really tried all that much. Because of this question the answers on this post couldn't really solve his problem because the reader needed more information to understand what the problem is. This showed inefficiency and why its important to ask a smart question for easier answers.
