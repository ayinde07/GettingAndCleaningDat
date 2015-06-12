## Getting and Cleaning Data - Course Project

 ----
                                 Dataset Overview

The original data for this process was collected from a smartphone by a variety of subjects while engaging in several activties. All subjects engaged in all activities. Raw data was gathered from the phone's accelerometer and its gyroscope. The values used in this process were derived from a variety of calculations (described below).

Conceptually, this process summarizes the original data by:
1. Subsetting the data, pulling out only fields which are a mean or a standard deviation 
2. Grouping the data by the subject and activity 
3. Averaging all the data for a given subject/activity pairing.

The final dataset is written to "tidy.txt" and can be read in with the following R command:

verify <- read.table("data/tidy.txt", sep=" ", headers=TRUE)
 ----
 ----
                              Data Cleaning Description
 ----
  ----
 
      Cleaning data labels

The input labels used abbreviated forms of descriptive terms. Abbreviations were expanded, duplications and punctuation were removed so that "tBodyAccJerk-std()-X" became "timeBodyAccelerometerJerkStdDevX" and "fBodyBodyGyroMag-mean()" became "frequencyBodyGyroscopeMagnitudeMean".
 ----
      Merging data

The data was divided in two different ways. First, it was partitioned into train and test subsets. Each of those was then divided into a measurements file, a subject identifier file, and an activity code file. There was also a single activity label file which paired the numeric code to a string label.

For each of train and test, the measurements file as read in using the cleaned up columns from above. Then the subject id and activity id were read in and combined (via cbind) with the measurements data. Then the complete train and test sets were merged together with rbind.
 ----
     Filtering data

From the fully merged data frame, a subset of columns was extracted where the columns indicated a mean or a standard deviation, along with the subject id and activity id. The activity ids were then replaced with corresponding activity labels.
 ----
 
      Summarizing the data
 
For each subject/activity pair, all the data points for a given column were averaged together and the resulting data frame written to file.
 ----
      Data Column Description
 
The first two columns identify the person and the activity engaged in.
1. Subject - Identifier for the subject providing the data, ranging from 1 to 30.
2. Activity - A label for the level activity of a data point. One of "WALKING", "WALKING_UPSTAIRS", "WALKING_DOWNSTAIRS", "SITTING", "STANDING", or "LAYING".

Each subsequent column is an average of values for a give Subject/AcivityLevel in the range -1 to 1. See below for more detail on the variables and their derivation.

The label for each variable is a combination of these facets:

1. time, frequency, or angle 
2. Body or Gravity
3. Accelerometer or Gyroscope
4. Jerk (or empty)
5. Magnitude (or empty)
6. Mean or StdDev(standard deviation)
7. Freq (or empty)
8. X, Y, or Z axis
9. Complete list of columns
10. Subject
11. Activity
12. timeBodyAccelerometerMeanX
13. timeBodyAccelerometerMeanY
14. timeBodyAccelerometerMeanZ
15. timeGravityAccelerometerMeanX
16. timeGravityAccelerometerMeanY
17. timeGravityAccelerometerMeanZ
18. timeBodyAccelerometerJerkMeanX
19. timeBodyAccelerometerJerkMeanY
20. timeBodyAccelerometerJerkMeanZ
21. timeBodyGyroscopeMeanX
22. timeBodyGyroscopeMeanY
23. timeBodyGyroscopeMeanZ
24. timeBodyGyroscopeJerkMeanX
25. timeBodyGyroscopeJerkMeanY
26. timeBodyGyroscopeJerkMeanZ
27. timeBodyAccelerometerMagnitudeMean
28. timeGravityAccelerometerMagnitudeMean
29. timeBodyAccelerometerJerkMagnitudeMean
30. timeBodyGyroscopeMagnitudeMean
31. timeBodyGyroscopeJerkMagnitudeMean
32. frequencyBodyAccelerometerMeanX
33. frequencyBodyAccelerometerMeanY
34. frequencyBodyAccelerometerMeanZ
35. frequencyBodyAccelerometerMeanFreqX
36. frequencyBodyAccelerometerMeanFreqY
37. frequencyBodyAccelerometerMeanFreqZ
38. frequencyBodyAccelerometerJerkMeanX
39. frequencyBodyAccelerometerJerkMeanY
40. frequencyBodyAccelerometerJerkMeanZ
41. frequencyBodyAccelerometerJerkMeanFreqX
42. frequencyBodyAccelerometerJerkMeanFreqY
43. frequencyBodyAccelerometerJerkMeanFreqZ
44. frequencyBodyGyroscopeMeanX
45. frequencyBodyGyroscopeMeanY
46. frequencyBodyGyroscopeMeanZ
47. frequencyBodyGyroscopeMeanFreqX
48. frequencyBodyGyroscopeMeanFreqY
49. frequencyBodyGyroscopeMeanFreqZ
50. frequencyBodyAccelerometerMagnitudeMean
51. frequencyBodyAccelerometerMagnitudeMeanFreq
52. frequencyBodyAccelerometerJerkMagnitudeMean
53. frequencyBodyAccelerometerJerkMagnitudeMeanFreq
54. frequencyBodyGyroscopeMagnitudeMean
55. frequencyBodyGyroscopeMagnitudeMeanFreq
56. frequencyBodyGyroscopeJerkMagnitudeMean
57. frequencyBodyGyroscopeJerkMagnitudeMeanFreq
58. angletBodyAccelerometerMeangravity
59. angletBodyAccelerometerJerkMeangravityMean
60. angletBodyGyroscopeMeangravityMean
61. angletBodyGyroscopeJerkMeangravityMean
62. angleXgravityMean
63. angleYgravityMean
64. angleZgravityMean
65. timeBodyAccelerometerStdDevX
66. timeBodyAccelerometerStdDevY
67. timeBodyAccelerometerStdDevZ
68. timeGravityAccelerometerStdDevX
69. timeGravityAccelerometerStdDevY
70. timeGravityAccelerometerStdDevZ
71. timeBodyAccelerometerJerkStdDevX
72. timeBodyAccelerometerJerkStdDevY
73. timeBodyAccelerometerJerkStdDevZ
74. timeBodyGyroscopeStdDevX
75. timeBodyGyroscopeStdDevY
76. timeBodyGyroscopeStdDevZ
77. timeBodyGyroscopeJerkStdDevX
78. timeBodyGyroscopeJerkStdDevY
79. timeBodyGyroscopeJerkStdDevZ
80. timeBodyAccelerometerMagnitudeStdDev
81. timeGravityAccelerometerMagnitudeStdDev
82. timeBodyAccelerometerJerkMagnitudeStdDev
83. timeBodyGyroscopeMagnitudeStdDev
84. timeBodyGyroscopeJerkMagnitudeStdDev
85. frequencyBodyAccelerometerStdDevX
86. frequencyBodyAccelerometerStdDevY
87. frequencyBodyAccelerometerStdDevZ
88. frequencyBodyAccelerometerJerkStdDevX
89. frequencyBodyAccelerometerJerkStdDevY
90. frequencyBodyAccelerometerJerkStdDevZ
91. frequencyBodyGyroscopeStdDevX
92. frequencyBodyGyroscopeStdDevY
93. frequencyBodyGyroscopeStdDevZ
94. frequencyBodyAccelerometerMagnitudeStdDev
95. frequencyBodyAccelerometerJerkMagnitudeStdDev
96. frequencyBodyGyroscopeMagnitudeStdDev
97. frequencyBodyGyroscopeJerkMagnitudeStdDev

------
                                  Data description from source
------

The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz.

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag).

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals).
