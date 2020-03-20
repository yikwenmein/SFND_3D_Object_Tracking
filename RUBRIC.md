FP.0: This File ;)

FP.1 Match 3D Objects:  To match the current Bounding Boxes from the current with the previous Frame iterate over all
                        the matched bounding boxes from the current Frame. In each iteration store the matches which
                        are contained inside the roi to the bounding box structure. When for a bounding box all the
                        matches iterate through them and match them to the previous Frame Bounding Boxes. In a map
                        store the boxId with the amount of matched keypoints. Get the boxId with the highest matches
                        and add them to the bbBestMatches.

FP.2  Compute TTC Lidar: Iterate over all the the Lidarpoints inside of the bounding box. To get a stable version calculate
                         the mean over the x direction off all points. The difference between the current mean and the
                         previous mean can be used to calculate the TTC.for

FP.3 Associate Keypoint Correspondences with Bounding Boxes: Get distance between matching points inside the roi and
                                                              calculate the mean. Afterwards iterate again over the
                                                              matches and remove those who are above the mean.

FP.4 Compute Camera Based TTC: Compute the distances between all matched points. Store the calculated distance inside a
                               vector whom afterwars can be sorted. From the sorted array get the median value. Do this
                               for the current and the previous frame. From those values calculate the ratio which is
                               needed to calculate the TTC.

FP.5 Performance Evaluation 1: As can be seen in the graph in FP.5 inside of measurment_final_project.odc there
                               are different Images in which the TTC measurement is higher than in the previous ones.
                               The most interessting ones are image 2, 9 and 10.

                               Analysis Image 2:
                               Analysis Image 9:
                               Analysis Image 10:

                               Based on the 2D Image plane with the Bounding boxes the offset could happens because
                               of the outliers which falsify the mean calculated with the x-values of each point.
                               A possible solution would be to harden the mean algorithm or reduce the threshold by whom
                               it is decided which lidar points gets selected.

FP.6 Performance Evaluation 2: All the data are contained in measurement_measurment_final_project.odc in tab FP.6
