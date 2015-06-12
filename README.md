
##Script Overview

The script starts by ensuring the source data directory is present and that an output data directory is available.

Then it defines the names of the input files that will be used.

Next the script reads in and cleans up the labels for the data columns and also reads in the activity labels.

For each of the test and train data sets, the script will read in the measured data, the subject identifiers, and the activity codes.

It merges (via cbind) those three data frames together.

Then it uses rbind to merge the train and test together into the full data frame.

An abbreviated data frame is created with just the columns that have "mean" and "std" in the name, along with the subject identifer and the activity code.

The activity labels are added to the abbreviated data set by matching the code to the index in the activity labels file.

The script then removes the activity code column, since it is now redundant with the label.

Now, the script creates a new data frame with the averages of all data points for a given subject/activity pairing.

This tidy data frame is then written to file.

 ----
 Project Instructions
 ----
 1. Merges the training and the test sets to create one data set.
 2. Extracts only the measurements on the mean and standard deviation for each measurement. 
 3. Uses descriptive activity names to name the activities in the data set
 4. Appropriately labels the data set with descriptive variable names. 
 5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each      activity and each subject.
