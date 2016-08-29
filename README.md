# Dot Counter

## Overview
This is a utility class to help monitor processing of very large collections of records in batch processing.

### Instructions

Use a DotCounter instance to track the progress of batch processing very large database records, or any long-running 
process with iteration.  The counter will track the number and current rate of iterations and will log progress to 
standard error.

Use the inc() method to increment the counter by one.  For any increment, the counter may write to standard error.  For 
the first nine iterations, it writes a single dot (ie, nine dots in a single line).  On the tenth iteration, it writes 
one more dot, and then reports the total count (10), total duration in seconds, and processing rate in records per 
second, followed by a newline.

From then on it logs dots on iterations that are multiples of 10 until it reaches 100.  Then it counts by 100's until
1000.  Then it logs on multiples of 1000 until 10,000; and so on.

Note: Although there is a main() in DotCounter. it serves merely as a demonstration and is not intended to be used for 
any purpose.

### Example Code

DotCounter dc = new DotCounter();
String line;
while ((line = System.in.readline() != null) {
    dc.inc();
    // process line 
}
dc.finish();

### Example Output

...........10(totalSeconds=0.0, recordsPerSec=Infinity)
..........100(totalSeconds=0.001, recordsPerSec=100000.0)
..........1000(totalSeconds=0.047, recordsPerSec=21276.59574468085)
..........10000(totalSeconds=0.048, recordsPerSec=208333.33333333334)
...32767(totalSeconds=0.049, recordsPerSec=668714.2857142857)

### See Also

https://thehub.thomsonreuters.com/groups/analog/blog/2013/04/11/the-power-of-logs-in-process-logging