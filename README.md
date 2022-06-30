# Shakespeare as a Service (SaaS)

We have recently joined an exciting new company, building distributed services for Shakespeare fans.

We need to help them expand on their capabilities.

### Getting the data

As input to our system, we have available a Shakespeare service which simply loads one line from Shakespeare’s work at a time.
This is important because we cannot hold all of Shakespeare's work in-memory.

----
## Task 1 - Read Shakespeare:

Let's start from `com.sqa.ShakespeareProcessor`.

Our task is to:
- read lines one by one from the `ShakespeareService`
- send all _**non-stop words**_ that we read to the `ShakespeareAnalyzerService`, by calling its `add()` method

Notes:
- You can ignore the functionality of the `ShakespeareAnalyzerService` for now
- The `ShakespeareService` provides a durable queue, such that a message that is not acknowledged will be tried again
- Like any other distributed service, the shakespeare service may not always be reliable (so it may fail to fetch data occasionally), but it does not lose data
- The list of stop words is available as a resource in `stop-words.txt`
- A couple of examples to consider when dealing with stop words:
  - `THE SONNETS` => `SONNETS` (`THE` is a stop word)
  - `Something to be.` => `Something .` (you may keep or drop the dot at the end of the sentence)
 
----
## Task 2 - Collect statistics of Shakespeare work:

Start from `ShakespeareAnalyzerService`

Our task is now to:
- Modify the add method to pass the data to its internal queue
- In the analyze method, use the words that you receive to calculate the **number of distinct non-stop words**

Notes:
- You have access to a `database`, which is available in your class

----
## Task 3 - Collect additional statistics:

Extend the functionality in the application to collect:
- Top 10 non-stop words

----
**Notes and tips:**
* The services may not always be reliable, but when we fail to connect to it, it does not lose data
* Unless you see "Do not edit" on a file, you can change it as you wish
* We care about performance, how can you make this fast?
* You have access to a database, see the DB file
* We care about clear communication, so please think out loud, and you may ask any questions you may have to clarify your understanding (like day-to-day work)
* We care about clean code, adherence to SOLID principles
