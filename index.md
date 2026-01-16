# LLM as Thought-Partner: A Demonstration of Socratic AI Tutoring

**Prepared for the ADSA Leadership Summit**  
*March 16–18, 2026 | Tucson, AZ*

Tony Thrall  
*Session Co-Chair, Student Readiness and Workforce Development in this Era of AI*

---

## Introduction

What follows is a transcript of a simulated tutoring session between an AI assistant (Claude) and a student (Sam). The session was conducted as a role-playing exercise to explore a pedagogical concept I call "LLM as Thought-Partner."

The concept is simple in principle but challenging in execution: rather than using AI to provide answers, we use it to ask questions. The AI becomes a Socratic companion—probing the student's understanding, surfacing misconceptions, connecting new material to prior knowledge, and resisting the temptation to simply explain.

This approach inverts the typical anxiety about AI in education. Instead of worrying that students will use AI to bypass learning, we ask: what if AI could deepen learning by doing what good tutors do—asking the right question at the right moment?

### The Student: Sam

Sam (Samantha) holds a BA in Mathematics. She was a passionate and diligent student with a high GPA, but she now seeks employment for a year or more before resuming graduate studies. She has no programming experience but is interested in gaining employable technical skills—both for financial security and for self-validation in a utilitarian rather than aesthetic setting.

Sam has worked through "R for Data Science" via self-study and is now tackling the "EDA Companion," a more mathematically demanding text. She has just started Chapter 8 on Principal Component Analysis (PCA).

Sam represents an ideal learner: curious, persistent, willing to try things and report back honestly when they fail. She brings mathematical maturity but lacks programming fluency and domain experience. Not all students are like Sam—requirements for the success of this Socratic approach deserve careful consideration.

### The Context

Sam approaches the AI Companion seeking both technical help with PCA and help understanding the larger context: why would someone actually use this technique in a work setting?

The session that follows is unscripted. I (Tony Thrall) played Sam, drawing on my own experience as a mathematics student decades ago—the uncertainty, the eagerness, the gaps in practical knowledge. Claude played the Companion, responding in real time to Sam's questions and code output.

The transcript has been lightly edited for formatting but is otherwise verbatim.

### What to Watch For

As you read the transcript, notice:

**The Companion rarely provides direct answers.** Instead, it asks questions that lead Sam to discover insights herself—why categorical data is unsuitable for PCA, why scaling matters, what the loadings mean.

**Errors are treated as learning opportunities.** When Sam's code fails or her wording is imprecise, the Companion acknowledges the attempt, offers gentle correction, and moves forward.

**The workplace frame is load-bearing.** Sam's original question—"Can you help me imagine a work setting?"—gets honored throughout and explicitly revisited at the end.

**Mathematical intuition is valued.** When Sam spontaneously constructs an eigenvalue demonstration to prove to herself why scaling matters, the Companion recognizes this as exactly the right approach.

**The session covers far more than PCA.** Data cleaning, missing values, outlier detection, distributional oddities—the unglamorous work of exploratory data analysis—occupy most of the session. The actual `prcomp()` call is almost anticlimactic.

---

## Session Transcript

**Sam:**  
Um, hello! This is the first time I've tried to interact with an LLM. How should I address you?

**Claude:**  
Hello, Sam! Welcome. You can just call me Claude—no formality required.

And there's no special protocol here. Think of this less like using a piece of software and more like talking with... well, a study partner who happens to have read a lot of books. I'm here to think alongside you, not to lecture at you or grade you.

I understand you're working through the EDA Companion and you've just started the chapter on Principal Component Analysis. That's a meaty topic—but I suspect your math background gives you more of a head start than you might realize.

What brings you to the Companion today? Is there something specific you're wrestling with, or are you still getting your bearings with the chapter?

**Sam:**  
I'm just getting my bearings. I started reading the book online, and then decided I needed to work through the material. So I'm working in RStudio now. You're right; I just started the chapter on Principal Component Analysis. I thought I'd try to find my own data set to work on, and I remembered the General Social Survey (gss) data from "R for Data Science". I've loaded `forcats::gss_cat` into my RStudio session. But I really have no idea where to go from here. Can you help me to imagine a work setting in which we would want to figure something out from the gss data? I'm lost.

**Claude:**  
That's a great instinct, Sam—finding your own data rather than just following canned examples. That's how real learning happens.

Before we imagine the work scenario, let me ask you something that will help us figure out if `gss_cat` is the right dataset for exploring PCA.

You have a math background, so think back to what you know about the machinery underneath PCA. When you compute principal components, what kind of mathematical object are you decomposing? And what does that object need from your data in order to exist?

I'm not asking you to recite a definition—I'm asking you to think about what PCA actually *does* with the numbers it's given. What operations does it need to perform?

Once you've got that in mind, take a quick look at `gss_cat`. Maybe just run `str(gss_cat)` or `glimpse(gss_cat)` in your console and tell me what you see. What kinds of variables are in there?

I have a hunch about where this is going, but I want you to discover it yourself.

**Sam:**  
Um, well I only took an introductory course in linear algebra, and aside from my working through "R for Data Science", I'm really new to statistics: just an intro course on mathematical statistics. So let's see. I guess the object you're hinting at is the sample variance-covariance matrix of the data. And the principal components seem to be eigenvectors of this matrix, yes?

Here's the output you suggested, but I'm having trouble making any sense out of it.

```r
> gss_tbl <- forcats::gss_cat
> gss_tbl |> str()
tibble [21,483 × 9] (S3: tbl_df/tbl/data.frame)
 $ year   : int [1:21483] 2000 2000 2000 2000 2000 2000 2000 2000 2000 2000 ...
 $ marital: Factor w/ 6 levels "No answer","Never married",..: 2 4 5 2 4 6 2 4 6 6 ...
 $ age    : int [1:21483] 26 48 67 39 25 25 36 44 44 47 ...
 $ race   : Factor w/ 4 levels "Other","Black",..: 3 3 3 3 3 3 3 3 3 3 ...
 $ rincome: Factor w/ 16 levels "No answer","Don't know",..: 8 8 16 16 16 5 4 9 4 4 ...
 $ partyid: Factor w/ 10 levels "No answer","Don't know",..: 6 5 7 6 9 10 5 8 9 4 ...
 $ relig  : Factor w/ 16 levels "No answer","Don't know",..: 15 15 15 6 12 15 5 15 15 15 ...
 $ denom  : Factor w/ 30 levels "No answer","Don't know",..: 25 23 3 30 30 25 30 15 4 25 ...
 $ tvhours: int [1:21483] 12 NA 2 4 1 NA 3 NA 0 3 ...
```

**Claude:**  
Yes, exactly right—you're decomposing the sample variance-covariance matrix, and the principal components are its eigenvectors. Your linear algebra course gave you exactly what you need here.

Now, hold that thought and look at what `str()` is telling you about `gss_cat`. You said you're having trouble making sense of it, but I think you actually have all the pieces—you just need to connect them.

Look at each variable and its type. You see things like:

- `year: int`
- `age: int`
- `tvhours: int`
- `marital: Factor w/ 6 levels`
- `race: Factor w/ 4 levels`
- `rincome: Factor w/ 16 levels`

So here's my question: if you wanted to compute a covariance matrix from this data, which of these variables could you actually use?

Put differently: what does it even *mean* to compute the covariance between `age` and `marital`? Between `race` and `religion`? Can you take those "Factor" variables and put them into the mathematical machinery you just described?

**Sam:**  
Um, hmm, I always think of "data" as meaning numbers, but "marital" is a data column consisting of English phrases. Oh yeah, "R for Data Science" included material on "factors", which I see is how the "marital" column is categorized. Jeez, how do you do anything with factors?

**Claude:**  
You've just discovered something really important, Sam. This is exactly the kind of thing that separates "doing statistics" from "understanding what you're doing."

You're right to be puzzled. Think about it mathematically: covariance measures how two variables *move together*. When age goes up, do TV hours go up or down? That question makes sense because both are numbers on a scale—you can compute differences, averages, variances.

But what about marital status? The levels are "Never married," "Married," "Divorced," "Widowed," "Separated." Is "Divorced" *greater than* "Married"? Is the *distance* from "Never married" to "Married" the same as the distance from "Widowed" to "Separated"?

Those questions don't really have answers, do they? There's no natural numerical scale here. The labels could be rearranged in any order and be equally valid.

So you've stumbled onto a fundamental distinction: **continuous** (or at least ordinal) variables versus **categorical** variables. PCA, as you correctly identified, needs to compute covariances—which means it needs numbers with meaningful distances and directions.

Given that, look back at `gss_cat`. You have nine columns. How many of them could you actually feed into a covariance matrix? Is that enough to make PCA interesting or worthwhile?

What do you think—is this dataset a good fit for learning PCA, or should we find you something better suited to the technique?

**Sam:**  
Uh, we have just "year", "age", and "tvhours": 3 data columns. Um, sure, I thought I'd try this data set, but I'm open to suggestions for a different data set.

**Claude:**  
Right. Three numeric variables—and honestly, "year" is a bit odd since it's really just *when* the survey was conducted, not a characteristic of the person being surveyed. So you're effectively down to age and tvhours, which is only two dimensions. You could do PCA on that, but... what would be the point? With two variables, you could just make a scatterplot and *see* everything directly.

The power of PCA emerges when you have *many* correlated variables and you're trying to find the underlying structure—to discover that maybe ten measurements are really just reflecting two or three underlying dimensions. With only two variables, there's no complexity to untangle.

So yes, let's find you something better. But before I just hand you a dataset, let me ask: now that you understand the constraint—you need multiple numeric variables that measure different aspects of the same "thing"—what kind of data can you imagine that would fit?

Think about a scenario where someone has measured several different quantities on each observation, and you suspect those measurements might be related to each other in some deeper way. It could be physical measurements, economic indicators, performance metrics, sensor readings...

What comes to mind? What's a situation where you'd have, say, five or ten numeric measurements per observation, and you'd want to understand how they hang together?

**Sam:**  
Ah, OK, thanks for that explanation of PCA. That helps.

Um, again I'm thinking back to "R for Data Science". Didn't Hadley work with multiple weather measurements over time and location? Or if that doesn't ring a bell, do you know of some similar data set?

**Claude:**  
Yes! You're thinking of the `nycflights13` package—there's a `weather` dataset in there with hourly measurements from the NYC-area airports. That's a promising direction.

Why don't you load it up and take a look? Try:

```r
library(nycflights13)
weather |> str()
```

or `glimpse(weather)` if you prefer that format. Then tell me what you see. Same question as before: which variables are numeric, and might they plausibly be related to each other in interesting ways?

And while you're doing that, start thinking about the workplace scenario you originally asked about. Imagine you're an analyst at an airline, or a logistics company, or even a local TV station's weather desk. You've got all these measurements—temperature, humidity, wind, visibility, whatever's in there—and someone asks you: "What are the main *types* of weather conditions we see at these airports? Can you characterize them simply?"

That's a PCA question. You're asking whether ten correlated measurements might really boil down to two or three underlying "weather patterns."

Go take a look at the data and tell me what you find.

**Sam:**  
Oops, I got the following error message:

```r
> library(nycflights13)
Error in library(package, pos = pos, lib.loc = lib.loc, character.only = TRUE,  : 
  there is no package called 'nycflights13'
```

**Claude:**  
Ah, that's a very common hiccup when you're starting out in R. There's a distinction between *having* a package on your computer and *loading* it into your current session.

`library()` loads a package—but the package has to already be installed. You need to install it first, which you only have to do once:

```r
install.packages("nycflights13")
```

Then you can load it with `library(nycflights13)`.

Think of it like books: `install.packages()` is buying a book and putting it on your shelf. `library()` is taking it off the shelf and opening it on your desk. You only buy once, but you open it each time you start a new work session.

Go ahead and install it, then load it and look at the `weather` data. I'll be here.

**Sam:**  
Cool! Turns out there's also a `nycflights23` package, but I guess it doesn't matter for this exercise. Here's my current status:

```r
> install.packages("nycflights13")
Installing package into 'C:/Users/tthra/AppData/Local/R/win-library/4.5'
(as 'lib' is unspecified)trying URL 'https://cran.rstudio.com/bin/windows/contrib/4.5/nycflights13_1.0.2.zip'
Content type 'application/zip' length 4511639 bytes (4.3 MB)
downloaded 4.3 MB

package 'nycflights13' successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Users\tthra\AppData\Local\Temp\RtmpqK8cDr\downloaded_packages

> library(nycflights13)
> weather |> glimpse()
Rows: 26,115
Columns: 15
$ origin     <chr> "EWR", "EWR", "EWR", "EWR", "EWR", "EWR", "EWR", …
$ year       <int> 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2013, 2…
$ month      <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
$ day        <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
$ hour       <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 13, 14, 15, 16…
$ temp       <dbl> 39.02, 39.02, 39.02, 39.92, 39.02, 37.94, 39.02, …
$ dewp       <dbl> 26.06, 26.96, 28.04, 28.04, 28.04, 28.04, 28.04, …
$ humid      <dbl> 59.37, 61.63, 64.43, 62.21, 64.43, 67.21, 64.43, …
$ wind_dir   <dbl> 270, 250, 240, 250, 260, 240, 240, 250, 260, 260,…
$ wind_speed <dbl> 10.35702, 8.05546, 11.50780, 12.65858, 12.65858, …
$ wind_gust  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
$ precip     <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0…
$ pressure   <dbl> 1012.0, 1012.3, 1012.5, 1012.2, 1011.9, 1012.4, 1…
$ visib      <dbl> 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 1…
$ time_hour  <dttm> 2013-01-01 01:00:00, 2013-01-01 02:00:00, 2013-0…
```

**Claude:**  
Now *that's* more like it. Look at all those numeric variables.

So, same exercise as before but now you should get a more satisfying answer: which of these fifteen columns could you actually put into a covariance matrix? Which are the *measurements* of weather conditions, as opposed to identifiers of *when* and *where* the measurement was taken?

And as you're sorting them out, do any of the numeric ones give you pause? Any that might be trickier than they first appear, or that might have practical problems?

Take a minute to group them in your mind and tell me what you come up with.

**Sam:**  
OK, here's my grouping:

**Location**: "origin" (airport code)  
**Time**: "year", "month", "day", "hour", "time_hour"  
**Weather measurement**: "temp", "dewp", "humid", "wind_dir", "wind_speed", "wind_gust", "precip", "pressure", "visib"

So, can we just use "time_hour" to identify the time of measurement. Anyway, the weather measurements are already arranged by time and location, so do I want to try to correlate time with the weather measurements?

Um, "wind_dir" might be tricky, because the values fall on a circle. How am I doing?

**Claude:**  
Excellent, Sam. Your groupings are spot on.

And the `wind_dir` observation? That's *exactly* the kind of mathematical thinking that will serve you well. You're absolutely right: 350° and 10° are very close to each other in reality, but numerically they look far apart. Compass directions live on a circle, not a line, so the usual notion of "distance" doesn't apply. Covariance with `wind_dir` would be... problematic. Good catch.

To your question about time: no, for PCA we're typically not trying to correlate time with measurements. We're asking a different question—what's the structure *among* the weather measurements themselves? Each row is an observation, a snapshot of weather conditions at a particular moment. PCA asks: across all these snapshots, do the measurements move together in patterns? Maybe when temperature is high, humidity tends to be low and visibility high—that would be one "dimension" of weather variation.

Time matters for *other* kinds of analysis (time series, forecasting), but for PCA we're treating each hourly observation as just another data point.

Now, you've identified eight or nine candidate weather variables (setting aside `wind_dir`). Before we dive into PCA, look back at that `glimpse()` output. Did you notice anything in the actual data values that might cause practical problems when we try to compute a covariance matrix?

**Sam:**  
OK, I see initial missing values ("NA") for the "wind_gust" data column. And the "precip" data column has repeated zeros, initially. For that matter, "visib" has 10 as a repeated value initially. I'm not sure whether repeated values are a problem.

**Claude:**  
Good eye. The missing values are the critical issue—you simply *can't* compute a covariance with NA values in the mix. R will either refuse or give you NA back. So we'll need a strategy for that.

The repeated values are a different kind of concern. Repeated values *per se* don't break the math, but they might be telling you something about the variable. Your intuition is worth following. For `visib`, that repeated 10—do you suppose visibility actually was *exactly* 10.0 miles for all those hours, or might 10 be a cap, meaning "10 or more, we stopped measuring"? For `precip`, those zeros—if it doesn't rain most hours, you'll have lots of zeros. That's real, but it does mean the variable is distributed in an unusual way.

But let's not get ahead of ourselves. First things first: you noticed NAs in `wind_gust` at the beginning of the data. But how *pervasive* is the problem? Is it just a few missing values, or is half the column empty?

Can you think of a way to check how many NAs there are in each column? You might need to explore a bit—try `sum(is.na(...))` on a column, or see if you can summarize across all columns at once.

**Sam:**  
Let's see. Let's try `summary()` for starters:

```r
> weather |> summary()
    origin               year          month             day       
 Length:26115       Min.   :2013   Min.   : 1.000   Min.   : 1.00  
 Class :character   1st Qu.:2013   1st Qu.: 4.000   1st Qu.: 8.00  
 Mode  :character   Median :2013   Median : 7.000   Median :16.00  
                    Mean   :2013   Mean   : 6.504   Mean   :15.68  
                    3rd Qu.:2013   3rd Qu.: 9.000   3rd Qu.:23.00  
                    Max.   :2013   Max.   :12.000   Max.   :31.00

      hour            temp             dewp           humid       
 Min.   : 0.00   Min.   : 10.94   Min.   :-9.94   Min.   : 12.74  
 1st Qu.: 6.00   1st Qu.: 39.92   1st Qu.:26.06   1st Qu.: 47.05  
 Median :11.00   Median : 55.40   Median :42.08   Median : 61.79  
 Mean   :11.49   Mean   : 55.26   Mean   :41.44   Mean   : 62.53  
 3rd Qu.:17.00   3rd Qu.: 69.98   3rd Qu.:57.92   3rd Qu.: 78.79  
 Max.   :23.00   Max.   :100.04   Max.   :78.08   Max.   :100.00  
                 NA's   :1        NA's   :1       NA's   :1

    wind_dir       wind_speed         wind_gust    
 Min.   :  0.0   Min.   :   0.000   Min.   :16.11  
 1st Qu.:120.0   1st Qu.:   6.905   1st Qu.:20.71  
 Median :220.0   Median :  10.357   Median :24.17  
 Mean   :199.8   Mean   :  10.517   Mean   :25.49  
 3rd Qu.:290.0   3rd Qu.:  13.809   3rd Qu.:28.77  
 Max.   :360.0   Max.   :1048.361   Max.   :66.75  
 NA's   :460     NA's   :4          NA's   :20778

     precip            pressure          visib       
 Min.   :0.000000   Min.   : 983.8   Min.   : 0.000  
 1st Qu.:0.000000   1st Qu.:1012.9   1st Qu.:10.000  
 Median :0.000000   Median :1017.6   Median :10.000  
 Mean   :0.004469   Mean   :1017.9   Mean   : 9.255  
 3rd Qu.:0.000000   3rd Qu.:1023.0   3rd Qu.:10.000  
 Max.   :1.210000   Max.   :1042.1   Max.   :10.000  
                    NA's   :2729

   time_hour                  
 Min.   :2013-01-01 01:00:00  
 1st Qu.:2013-04-01 21:30:00  
 Median :2013-07-01 14:00:00  
 Mean   :2013-07-01 18:26:37  
 3rd Qu.:2013-09-30 13:00:00  
 Max.   :2013-12-30 18:00:00
```

OK, I see we have a lot of missing values for: "wind_dir", "wind_gust", and "pressure". Oh, and you're also right about "visib": it maxes out at 10 miles. Should I just use the remaining weather measurements? Do I need to eliminate "wind_speed" because it has 4 missing values?

**Claude:**  
`summary()` was a great choice—gives you a lot at a glance.

Look at the NA counts more carefully, though. Think proportionally. Out of 26,115 rows:

- `wind_gust`: 20,778 NAs — that's about 80% missing. The variable is mostly empty.
- `pressure`: 2,729 NAs — roughly 10% missing.
- `wind_dir`: 460 NAs — under 2%, but we're already setting it aside because of the circular problem.
- `wind_speed`: 4 NAs — that's 0.015%. Negligible.
- `temp`, `dewp`, `humid`: 1 NA each.

So here's a different way to frame the question: you have two distinct problems. Some *variables* are so riddled with missing data that they're essentially unusable. Other variables are fine, but a few *rows* happen to have missing values.

What if, instead of dropping `wind_speed` as a variable, you kept it and just filtered out the handful of rows where any of your chosen variables are NA? How many observations would you lose?

And while you're looking at that summary output—did anything else catch your eye? Look at the min and max values for `wind_speed`. Does anything seem... odd?

**Sam:**  
Oh, yeah, "wind_speed" has a max value of 1048. That's got to be an error. So do I eliminate "wind_speed" as a flawed measurement?

**Claude:**  
That's a great instinct—you're doing real exploratory data analysis here. A wind speed of 1048 mph would be... well, not weather. That's a fighter jet.

But before you discard the entire variable, think about it this way: you have over 26,000 observations of wind speed. If one of them (or even a handful) is obviously erroneous, does that condemn all the others?

What's an alternative to throwing out the whole variable? And how would you figure out whether it's just one bad reading or a systemic problem with the measurements?

See if you can investigate. How many wind speed values are unreasonably high? What would you consider a plausible maximum wind speed for the NYC area?

**Sam:**  
I get it. Thanks for helping me think about this in real-world terms. Hmm, I'm again thinking back to "R for Data Science". I think I'll try a histogram of log10(wind_speed). Oh, I better allow for a wind-speed of 0. Here's what I have:

```r
> weather |> ggplot(mapping = aes(x = log10(1 + wind_speed))) + geom_histogram()
`stat_bin()` using `bins = 30`. Pick better value `binwidth`.
```

I have a clump of values at zero, and then nearly all of the remaining values falling between something like 0.6 and 1.6. So it looks like I could eliminate values below 50 mph without losing any values other than that erroneous max value.

**Claude:**  
Nice work, Sam. You're doing exactly what a good analyst does: visualize, investigate, make a reasoned judgment. The log transform was a clever move—it spreads out the bulk of the data so you can see its shape while revealing the outlier.

One small clarification on your wording—I think you mean you could *keep* values below 50 mph (or equivalently, *filter out* values above 50), and you'd only lose the erroneous reading(s). Yes?

Before you commit to that threshold, why not check directly? Try filtering to see what's actually lurking above, say, 40 or 50 mph:

```r
weather |> filter(wind_speed > 50)
```

That way you'll know exactly how many suspicious values you're dealing with, and you can eyeball whether there's one crazy outlier or a cluster of questionable readings.

And stepping back for a moment—notice what you've been doing for the last several minutes. You haven't touched PCA yet, but you've been doing *exploratory data analysis*: understanding your variables, checking for problems, making informed decisions about what to include. This is the unglamorous but essential work that comes before any modeling. PCA on garbage data gives you garbage components.

So: check those high wind speeds, and then let's talk about assembling your cleaned dataset for PCA.

**Sam:**  
Thanks for the perspective—much appreciated. And for catching my over/under error in my wording. And for the filtering suggestion, which I'll try now.

```r
> weather |> filter(wind_speed > 50)
# A tibble: 1 × 15
  origin  year month   day  hour  temp  dewp humid wind_dir wind_speed
  <chr>  <int> <int> <int> <int> <dbl> <dbl> <dbl>    <dbl>      <dbl>
1 EWR     2013     2    12     3  39.0  27.0  61.6      260      1048.
# ℹ 5 more variables: wind_gust <dbl>, precip <dbl>, pressure <dbl>,
#   visib <dbl>, time_hour <dttm>
```

Looks like the there's just one value of wind-speed above 50 mph, namely, the erroneous max value of 1048. OK, so the opposite filter, `(wind_speed <= 50)`, would eliminate that single erroneous value.

**Claude:**  
Exactly. Just one bad reading out of 26,000+. That's a variable worth keeping.

Alright, you've done solid detective work. Let's take stock. For your PCA, you're considering:

**Include:**
- `temp` (1 NA)
- `dewp` (1 NA)
- `humid` (1 NA)
- `wind_speed` (4 NAs, 1 outlier to filter)

**Exclude:**
- `wind_dir` (circular—mathematically problematic)
- `wind_gust` (~80% missing—essentially useless)

**Uncertain:**
- `precip` (lots of zeros)
- `pressure` (~10% missing)
- `visib` (capped at 10)

That middle category is where judgment comes in. There's no single right answer. But here's a question to help you think about it: if you include `pressure` and then filter to only complete cases (no NAs in any variable), you'll lose about 10% of your rows. Is that acceptable? What's the tradeoff?

And for `precip` and `visib`—those aren't missing data problems, they're distributional oddities. They won't break PCA, but they might behave strangely. You could include them and see what happens, or start simple and add complexity later.

What's your inclination? What dataset do you want to assemble for your first pass at PCA?

**Sam:**  
Thanks for the summary of where we're at. I'm trying to make sense out of PCA—that's my main goal here. But I think I should use whatever relevant data I have for starters, so let's keep all three data columns: "precip", "pressure", "visib".

**Claude:**  
Good. Start with everything, see what happens, learn from it. That's a sensible approach.

So your variable list is: `temp`, `dewp`, `humid`, `wind_speed`, `precip`, `pressure`, `visib`. Seven weather measurements.

Now you need to assemble a clean dataset. You'll want to:

1. Keep only those seven columns
2. Filter out the erroneous wind speed reading
3. Remove any rows that have NA in any of these variables

Can you construct that pipeline? You'll probably want `select()` for the columns, `filter()` for the wind speed outlier, and then you'll need something to drop rows with NAs—take a look at `drop_na()` from tidyr, or you could use `filter()` with `complete.cases()`.

Once you've built the cleaned dataset, check how many rows you have left. That'll tell you the cost of keeping `pressure` in the mix.

**Sam:**  
OK, here's my work.

```r
> weather_f <- weather |> dplyr::select(temp, dewp, humid, wind_speed, precip, pressure, visib) |> dplyr::filter(wind_speed <= 50, complete.cases())
Error in `dplyr::filter()`:
ℹ In argument: `complete.cases()`.
Caused by error in `complete.cases()`:
! no input has determined the number of cases
Run `rlang::last_trace()` to see where the error occurred.

> weather_f <- weather |> dplyr::select(temp, dewp, humid, wind_speed, precip, pressure, visib) |> dplyr::filter(wind_speed <= 50)

> weather_f |> complete.cases() |> summary()
   Mode   FALSE    TRUE 
logical    2728   23382 

> wf_cc_vec <- weather_f |> complete.cases()
> wf_cc <- weather_f[wf_cc_vec]
Error in `weather_f[wf_cc_vec]`:
! Cannot subset columns with `wf_cc_vec`.
✖ Logical subscript `wf_cc_vec` must be size 1 or 7, not 26110.
Run `rlang::last_trace()` to see where the error occurred.

> wf_cc <- weather_f |> dplyr::filter(wf_cc_vec)

> wf_cc
# A tibble: 23,382 × 7
    temp  dewp humid wind_speed precip pressure visib
   <dbl> <dbl> <dbl>      <dbl>  <dbl>    <dbl> <dbl>
 1  39.0  26.1  59.4      10.4       0    1012     10
 2  39.0  27.0  61.6       8.06      0    1012.    10
 3  39.0  28.0  64.4      11.5       0    1012.    10
 4  39.9  28.0  62.2      12.7       0    1012.    10
 5  39.0  28.0  64.4      12.7       0    1012.    10
 6  37.9  28.0  67.2      11.5       0    1012.    10
 7  39.0  28.0  64.4      15.0       0    1012.    10
 8  39.9  28.0  62.2      10.4       0    1012.    10
 9  39.9  28.0  62.2      15.0       0    1013.    10
10  41    28.0  59.6      13.8       0    1012.    10
# ℹ 23,372 more rows
# ℹ Use `print(n = ...)` to see more rows
```

**Claude:**  
You got there! A bit of a winding path, but that's how learning R actually works—you try something, it complains, you adjust, you try again.

For future reference, `tidyr::drop_na()` does exactly what you wanted in one step:

```r
weather_f <- weather |> 
  dplyr::select(temp, dewp, humid, wind_speed, precip, pressure, visib) |> 
  dplyr::filter(wind_speed <= 50) |> 
  tidyr::drop_na()
```

But your approach worked, and you learned something about how `complete.cases()` returns a logical vector that you then use for filtering. That's not wasted effort.

Now look at what you've got: 23,382 rows out of about 26,000. You lost roughly 10%—almost entirely from those missing `pressure` values. That's a reasonable tradeoff for keeping seven variables.

So. You have a clean data frame with seven numeric weather measurements, no missing values, no wild outliers. You're ready for PCA.

Here's the moment of truth: how do you think you should actually *do* it? The Companion's chapter on PCA presumably shows some function or method. What's your understanding of the next step—mechanically, what do you need to compute, and what R function might do that?

**Sam:**  
Thanks for the tip on `tidyr::drop_na()`. Well, from what I understand so far, I think I should compute the variance-covariance matrix of the cleaned data and then compute the eigen-decomposition of that matrix. Oh wait, section `8.6: Computation` mentions function `stats::prcomp()` that gives the principal components using singular value decomposition (SVD), which is new to me. Shall I just feed my cleaned data, `wf_cc`, to `stats::prcomp()`?

**Claude:**  
You could, and it would run. But pause for a moment before you do.

Think back to the covariance matrix. The covariance between two variables depends on their *scales*—the units they're measured in. Look at your seven variables and think about what units they're in and what range of values they span:

- `temp` and `dewp`: degrees Fahrenheit, ranging maybe 10–100
- `humid`: percentage, 0–100
- `wind_speed`: miles per hour, mostly 0–30
- `precip`: inches of rain, mostly 0 with occasional small values up to ~1
- `pressure`: millibars, roughly 980–1040
- `visib`: miles, 0–10

Now, if you compute the variance of each of these, which one will have the largest variance just because of its *scale*, not because it's actually more "variable" in any meaningful sense?

And if one variable dominates the covariance matrix simply because its numbers are bigger, what do you think will happen to your principal components?

This is leading somewhere important. What do you think?

**Sam:**  
Let's see if I follow you. Suppose we had just two standard normal variables having some correlation coefficient `r`. The variance-covariance matrix is (1, r, r, 1). One of the eigenvalues is `1+r`, with corresponding eigenvector `(1, 1)`. The other eigenvalue is `1-r`, with corresponding eigenvector `(1, -1)`. Setting `r = 0.5` the eigenvalues are (1.5, 0.5).

Now we multiply the second normal variable by some large scale value `S`. The new variance-covariance matrix is (1, r*S, r*S, S^2). Oops, I thought the calculation would be easy. Let's set `r = 0.5` and `S = 16`. Here's a numerical calculation.

```r
> tst_cov2 <- function(r = 0, S = 1) matrix(c(1, r*S, r*S, S^2), nrow = 2, ncol = 2)

> tst_cov2(r = 1/2)
     [,1] [,2]
[1,]  1.0  0.5
[2,]  0.5  1.0

> tst_cov2(r = 1/2) |> eigen()
eigen() decomposition
$values
[1] 1.5 0.5 

$vectors
          [,1]       [,2]
[1,] 0.7071068 -0.7071068
[2,] 0.7071068  0.7071068

> tst_cov2(r = 1/2, S = 16)
     [,1] [,2]
[1,]    1    8
[2,]    8  256

> tst_cov2(r = 1/2, S = 16) |> eigen()
eigen() decomposition
$values
[1] 256.2507339   0.7492661

$vectors
           [,1]        [,2]
[1,] 0.03132635 -0.99950921
[2,] 0.99950921  0.03132635
```

So by scaling up the second normal variable, the respective eigenvalues become `(256.25, 0.75)` and the coefficients of the eigenvector of the largest eigenvalue are now `(0.0313, 0.9995)`, with the second variable now dominating the linear combination, merely by virtue of being scaled up. So far so good?

**Claude:**  
Exactly right, Sam. That's a beautiful demonstration.

You've just proved to yourself why scale matters: the second variable contributes almost nothing "real" beyond what it contributed before—the correlation is still 0.5—but it now *dominates* the first principal component simply because its variance is 256 times larger. The PCA is picking up "this variable has big numbers," not "this variable explains the most shared variation."

So. What's the fix? If we don't want variables to dominate simply because of their units, what should we do to the data before computing the covariance matrix—or equivalently, what matrix should we decompose instead of the raw covariance matrix?

Think about what would make your two variables "equal" in some sense, so that their contribution to the principal components reflects their *correlational structure* rather than their arbitrary scales.

**Sam:**  
Ah, you're saying, let's use the correlation matrix rather than the covariance matrix for the eigen-decomposition, yes?

**Claude:**  
Exactly. The correlation matrix *is* the covariance matrix of standardized variables—variables that have each been shifted to mean zero and scaled to variance one. That puts all your variables on equal footing, regardless of whether they're measured in millibars, degrees, or inches.

Now, you could standardize your data manually and then run PCA on the result. Or you can let `prcomp()` do it for you. Take a quick look at the help page:

```r
?prcomp
```

Look for an argument that controls whether the variables get scaled before the analysis. What do you find?

**Sam:**  
Got it. The help documentation lists parameter `scale`. But I also see parameter `center`. Can I simply call `prcomp()` with `scale = TRUE`, or do I need to also set `center = TRUE`. Oops, I just answered my own question. I now see that `center` is set equal to `TRUE` by default, so I only need to specify `scale = TRUE`.

**Claude:**  
You're reading documentation carefully—that's a skill that will serve you well.

So yes: `prcomp(wf_cc, scale = TRUE)` will center each variable (subtract the mean) and scale it (divide by the standard deviation), then perform PCA on the result. That's equivalent to doing the eigendecomposition of the correlation matrix.

Go ahead and run it. Store the result so you can examine it:

```r
pca_result <- prcomp(wf_cc, scale = TRUE)
```

Then take a look at what you get back. Try `summary(pca_result)` and `str(pca_result)` to see what's inside. What do you find?

**Sam:**  
Here are my results.

```r
> pca_result <- wf_cc |> prcomp(scale. = TRUE)
> pca_result |> summary()
Importance of components:
                          PC1    PC2    PC3    PC4     PC5     PC6
Standard deviation     1.5527 1.2395 1.1191 0.8781 0.75184 0.67930
Proportion of Variance 0.3444 0.2195 0.1789 0.1102 0.08075 0.06592
Cumulative Proportion  0.3444 0.5639 0.7428 0.8529 0.93368 0.99960
                           PC7
Standard deviation     0.05264
Proportion of Variance 0.00040
Cumulative Proportion  1.00000

> pca_result |> str()
List of 5
 $ sdev    : num [1:7] 1.553 1.239 1.119 0.878 0.752 ...
 $ rotation: num [1:7, 1:7] 0.48 0.599 0.443 -0.248 0.14 ...
  ..- attr(*, "dimnames")=List of 2
  .. ..$ : chr [1:7] "temp" "dewp" "humid" "wind_speed" ...
  .. ..$ : chr [1:7] "PC1" "PC2" "PC3" "PC4" ...
 $ center  : Named num [1:7] 55.22794 40.36274 59.76559 10.3394 0.00169 ...
  ..- attr(*, "names")= chr [1:7] "temp" "dewp" "humid" "wind_speed" ...
 $ scale   : Named num [1:7] 17.9699 19.4741 18.2749 5.5554 0.0147 ...
  ..- attr(*, "names")= chr [1:7] "temp" "dewp" "humid" "wind_speed" ...
 $ x       : num [1:23382, 1:7] -0.762 -0.588 -0.648 -0.718 -0.678 ...
  ..- attr(*, "dimnames")=List of 2
  .. ..$ : NULL
  .. ..$ : chr [1:7] "PC1" "PC2" "PC3" "PC4" ...
 - attr(*, "class")= chr "prcomp"
```

The first row of the summary shows the standard deviation of each principal component: PC1, ..., PC7. The next row of the summary shows "proportion of Variance", whatever that may be, and the third row shows the "Cumulative Proportion", which looks like the cumulative sum of the preceding row, the final entry being 1.0.

I'm even less clear on the structure of `pca_result`. Is this something I need to know, or can I leave it "under the hood" for now?

**Claude:**  
Good observations. Let's make sense of this piece by piece.

First, the "Proportion of Variance." You said you're decomposing the correlation matrix, and you know eigenvalues come out of that decomposition. Here's a question: if you're working with 7 standardized variables (each with variance 1), what's the *total* variance across all seven variables?

And the standard deviations in that first row—`1.55, 1.24, 1.12, ...`—those are the standard deviations of the principal components themselves. If PC1 has standard deviation 1.55, what's its *variance*? And what fraction of the total variance would that be?

See if the numbers click into place.

As for the structure: you don't need to memorize it, but a few pieces are worth understanding:

- `$sdev`: the standard deviations you already see in the summary
- `$rotation`: this is the important one—it contains the eigenvectors, the *loadings* that tell you how each original variable contributes to each PC
- `$x`: the *scores*—your original 23,382 observations, transformed into the new coordinate system defined by the principal components

Try looking at `pca_result$rotation`. What does it tell you about how your weather variables combine to form PC1?

**Sam:**  
Hmm, let's square the standard deviations of the components and sum those:

```r
> pca_result$sdev^2 |> cumsum()
[1] 2.410723 3.947078 5.199374 5.970519 6.535784 6.997229 7.000000
```

So that confirms your statement about each of the standardized variables have variance 1 (of course), so that the sum of those variances is the number of components, namely 7. (Why the sum of variances is noteworthy is beyond me, but I'm setting that aside.)

Now let's scale the last calculation: let's divide each PC variance by 7.

```r
> (pca_result$sdev^2 / 7) |> cumsum()
[1] 0.3443890 0.5638683 0.7427678 0.8529314 0.9336834 0.9996041
[7] 1.0000000
```

OK, that matches the "Cumulative Proportion" shown in the summary.

Now for `pca_result$rotation`.

```r
> pca_result$rotation
                  PC1         PC2         PC3         PC4         PC5
temp        0.4802839 -0.44454741 -0.13978411  0.31096689  0.22293147
dewp        0.5991198 -0.25398570 -0.02292862  0.09647018  0.15668025
humid       0.4426556  0.33483430  0.21661563 -0.38823057 -0.04989985
wind_speed -0.2475213  0.05257699 -0.70062621 -0.01778091  0.51798789
precip      0.1402217  0.51809018 -0.19477365  0.74222078 -0.32687420
pressure   -0.2644595 -0.02979551  0.63518380  0.41794374  0.52029942
visib      -0.2521332 -0.59471448 -0.02720332  0.13185335 -0.52668129
                  PC6          PC7
temp       -0.1620004 -0.616053895
dewp        0.1641700  0.717784122
humid       0.6223020 -0.323337100
wind_speed  0.4200580 -0.003928388
precip      0.1274320  0.002513340
pressure    0.2833900 -0.004074685
visib       0.5353006 -0.026044575
```

OK, if I'm following, each principal component is a linear combination of the original scaled variables. The `rotation` matrix gives me the coefficients of each linear combination. PC1 (simplified) is roughly `c1 * (temp + dewp + humid) - c2(wind_speed + precip + pressure + visib)`, where c1 actually ranges from 0.44 to 0.60 and c2 ranges from 0.14 to 0.26. Am I on the right track?

**Claude:**  
You're on the right track. Each PC is indeed a linear combination of the standardized variables, and the `rotation` matrix gives you the coefficients (also called *loadings*).

Your grouping by sign is exactly the right instinct. Variables with the same sign move *together* along that component; variables with opposite signs move in *opposite directions*.

So look at what you've found for PC1:

**Positive loadings** (high values push PC1 up): `temp` (0.48), `dewp` (0.60), `humid` (0.44), and weakly `precip` (0.14)

**Negative loadings** (high values push PC1 down): `wind_speed` (-0.25), `pressure` (-0.26), `visib` (-0.25)

Now here's the interpretive question: forget the math for a moment and think about *weather*. What kind of day has high temperature, high dew point, high humidity, and low visibility? What kind of day has lower temperature, higher pressure, and better visibility?

Can you give PC1 a name—a plain-English description of what "weather dimension" it's capturing?

**Sam:**  
Drizzly? Humid? Sultry? Steamy? (Are these aliases of the Seven Dwarfs?)

**Claude:**  
Ha! Those work. "Warm and muggy" versus "cool and clear" might be the prosaic version.

The point is: PC1 isn't just an abstract mathematical direction. It captures a recognizable pattern in how weather variables move together. Hot, humid days with high dew points tend to have lower visibility and lower pressure. Crisp, clear days tend to be the opposite. That's a real meteorological phenomenon, and PCA found it just by looking at correlations.

Now look back at your summary. PC1 captures about 34% of the total variance—the largest single chunk, but not a majority. PC2 captures another 22%.

Glance at the loadings for PC2. What variables load most strongly (positive or negative)? Does a different "weather story" emerge?

**Sam:**  
PC2 major contributors: temp (-0.44), precip (0.52), and visib (-0.59).

OK, so rather than "hot and muggy" (PC1), PC2 is more like "cold and coming down", yes?

**Claude:**  
Yes! Cold, rainy, low visibility—a different flavor of unpleasant weather than the summer mugginess of PC1. Notice that `humid` loads *positively* on PC2 as well (+0.33), which makes sense: precipitation and humidity go together, but this pattern is decoupled from temperature in a way that PC1 wasn't.

So you've found two distinct "axes" of weather variation in the NYC area. Not just "good weather vs. bad weather," but two different *kinds* of weather patterns: the warm-muggy axis and the cold-rainy axis.

Now step back and think about what you've accomplished. You started with seven correlated measurements. You've discovered that much of their variation can be described by just two or three underlying patterns. Look at the cumulative proportion: PC1 and PC2 together capture about 56% of the variance. Add PC3 and you're at 74%.

This is the payoff of PCA: **dimensionality reduction**. Instead of thinking about seven separate weather variables, you could summarize each hour's weather with two or three scores—its position along these interpretable axes.

Remember your original question—you wanted to imagine a workplace scenario. So: if you were an analyst at an airline and your boss asked, "Can you characterize the main types of weather we deal with at these airports?"—what would you tell her now?

**Sam:**  
Thanks for bringing us back to my original goal, to understand the potential relevance of PCA in a work environment. Your summary is really helpful.

I would reply to my boss: "This is work in progress, but I'm finding patterns in the measurements that correspond to 'warm and muggy', 'cold and rainy', and so on. I need to match the measurement patterns with the 12-month weather cycle to confirm these interpretations. I should have that for you with a few more hours of work." How'd I do?

**Claude:**  
That's excellent, Sam. Notice what you did there:

1. You hedged appropriately—"work in progress," not overclaiming
2. You translated math into language your boss can understand—"warm and muggy" rather than "PC1 loads positively on temp, dewp, and humid"
3. You proposed *validation*—matching patterns against the seasonal cycle to confirm your interpretation isn't just pattern-matching noise
4. You gave a realistic timeline

That's professional judgment, not just technical skill. And honestly, that judgment is harder to teach than the linear algebra.

Now, stepping out of the workplace scenario for a moment: look at what you've actually done in this session. You started with "I have no idea where to go from here." Since then you've:

- Recognized why `gss_cat` was unsuitable (categorical vs. continuous)
- Found appropriate data and assessed its quality
- Handled missing values, outliers, and distributional oddities
- Understood *why* scaling matters (and proved it to yourself mathematically)
- Run PCA and interpreted the output
- Translated the results into plain English

That's real exploratory data analysis. The PCA was almost the easy part—`prcomp()` is just one line of code. Everything else was the thinking.

Is there anything from this session that's still murky, or shall we call it here for today?

**Sam:**  
Whew! I'm glad you're letting me call time out! That was quite a workout, but it was really helpful. Thanks very much.

**Claude:**  
You're welcome, Sam. You did the hard work—I just asked questions. Go get some rest, and when you come back to Chapter 8, I think you'll find it reads differently now that you've gotten your hands dirty with real data.

Good luck with the job search. You're building real skills here.

---

## Epilogue: Observations and Implications

### What Worked

The Socratic approach succeeded here because Sam was an active participant. She tried things, reported results honestly, asked follow-up questions, and was willing to be confused. The Companion's questions only work if the student engages with them.

Several moments stand out:

**When Sam realized that `gss_cat` was unsuitable for PCA**, she discovered it herself by thinking through what a covariance matrix requires. The Companion asked the question; Sam found the answer.

**Sam's spontaneous eigenvalue demonstration was not prompted.** She decided on her own to construct a mathematical proof of why scaling matters. This is exactly what we hope deep learning looks like—the student taking ownership of understanding.

**The workplace scenario provided motivation throughout.** Sam started by asking how PCA might be useful at work. The Companion honored that question, weaving it through the session and returning to it explicitly at the end. The "boss question" wasn't a trick—it was the natural culmination of what Sam had asked for.

**Errors were productive.** Sam's struggles with `complete.cases()` inside `filter()` led to genuine learning about how logical vectors work in R. The Companion didn't rescue her prematurely.

### Boundary Conditions

This session was biased toward success. Sam was an ideal learner—the kind of student instructors are grateful to have. Several factors made the Socratic approach work:

**Mathematical maturity.** Sam could recognize that covariance requires numeric data, that compass directions live on a circle, that eigenvalues determine which variables dominate. A student without this background would need different scaffolding.

**Persistence and honesty.** Sam reported her code errors verbatim rather than hiding them or giving up. She stayed engaged through confusion.

**Prior R exposure.** Although new to programming, Sam had worked through "R for Data Science" and could write basic pipelines. A complete novice would need more direct instruction on syntax.

**Curiosity about context.** Sam genuinely wanted to know why PCA matters, not just how to run it. This gave the conversation a natural arc.

For students who are more passive, or who lack foundational preparation, or who become frustrated when questions are answered with questions—the Socratic approach may need modification. The art lies in recognizing when to push and when to simply provide scaffolding.

### Implications for ADSA

If AI can serve as a thought-partner rather than an answer-generator, several implications follow:

**Assessment may need to shift.** If students use AI companions during learning, what should we measure? Perhaps the ability to ask good questions, to recognize when AI output is wrong, to interpret and communicate results—the skills Sam demonstrated when she formulated her "boss answer."

**The role of human instructors changes but doesn't disappear.** An AI companion can handle many one-on-one Socratic interactions, but instructors are still needed to design curricula, recognize when students are struggling, and provide the human judgment that AI cannot.

**Not all students will benefit equally.** The Socratic approach requires student engagement. Students who most need support may be least able to participate in this mode of interaction. Equity considerations are paramount.

**The "LLM as Thought-Partner" framing offers an asset-based response to AI disruption.** Rather than asking "how do we prevent students from using AI to cheat?" we ask "how can AI help students develop deeper understanding?" This reframing may be as important as any technical implementation.

### An Invitation

This transcript is offered as a demonstration, not a prescription. The approach shown here is one possibility among many.

I invite colleagues at the Summit to consider: What would it take to study this systematically? How would we measure whether students learn more deeply with AI thought-partners than without? What are the failure modes we should anticipate? And how do we ensure that AI-assisted pedagogy serves all students, not just those who arrive with strong foundations?

These questions deserve careful empirical investigation. The transcript you've just read suggests the approach has promise. Whether that promise can be realized at scale, equitably, across diverse student populations—that remains to be seen.

---

*— Tony Thrall, January 2026*
