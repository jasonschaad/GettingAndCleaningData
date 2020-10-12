The run_analysis.R script performs prepares the data and then performs the following 5 steps:

1.Merges the training and the test sets to create one data set.
2.Extracts only the measurements on the mean and standard deviation for each measurement.
3.Uses descriptive activity names to name the activities in the data set
4.Appropriately labels the data set with descriptive variable names.
5.From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

Download the dataset from the website. The Dataset is downloaded then the zip is extracted into a folder called UCI HAR Dataset.

Assign the data frames to variables
x_train, y_train, x_test, y_test, subject_train and subject_test contain the data from the downloaded files.
x_data, y_data and subject_data merge the previous datasets to further analysis.
features contains the correct names for the x_data dataset, which are applied to the column names stored in

We merge the training and the test sets to create one data set
X is created by merging x_train and x_test using rbind() function
Y is created by merging y_train and y_test using rbind() function
Subject is created by merging subject_train and subject_test using rbind() function
Merged_Data is created by merging Subject, Y and X using cbind() function

We extractthe mean and standard deviation
TidyData is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

Uses descriptive activity names to name the activities in the data set
The code column of the TidyData is replaced with the corresponding activity from the second column

Appropriately labels the data set with descriptive variable names
code column in TidyData renamed into activities
Acc replaced by Accelerometer
Gyro name replaced by Gyroscope
BodyBody name replaced by Body
Mag in column’s  by Magnitude
characters that start with  f replaced by Frequency
characters that start with t replaced by Time

From the data set in step 4, create second,independent tidy data set with the average of each variable for each activity and each subject
FinalDataSet is created by sumarizing TidyData by taking the means of each variable for each activity and  subject (after it is grouped by subject and activity).
Export into a file called FinalDataSet.txt