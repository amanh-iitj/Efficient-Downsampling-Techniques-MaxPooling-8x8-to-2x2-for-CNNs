# Efficient-Downsampling-Techniques-MaxPooling-8x8-to-2x2-for-CNNs


## Introduction:

- This project explores efficient downsampling technique in Convolutional Neural Networks (CNNs) using MaxPooling to transform an 8x8 matrix into a 2x2 matrix. Implemented entirely in Verilog, the goal is to enhance 
the performance and efficiency of CNNs by reducing computational complexity while preserving essential features.


## Background:

- MaxPooling is a popular downsampling technique in CNNs, widely used to reduce the spatial dimensions of feature maps. By selecting the maximum value within a defined window, MaxPooling helps in achieving translation invariance and reducing overfitting. This project specifically focuses on transforming an 8x8 matrix into a 2x2 matrix using MaxPooling.



## Design:

- Input here is a 8x 8 matrix that can be thought of as a collection of four 4 x 4 submatrices or sixteen 2x2 submatrices . When you apply the first 2 x 2 max-pooling, you basically obtain a 4x4 matrix which when again filtered with 2x2 max-pooling yields a 2x2 matrix as the final output.

- ![image](https://github.com/amanh-iitj/Efficient-Downsampling-Techniques-MaxPooling-8x8-to-2x2-for-CNNs/assets/155350256/e3f069ec-596f-40b2-9456-4a9f86352e13)

- ![image](https://github.com/amanh-iitj/Efficient-Downsampling-Techniques-MaxPooling-8x8-to-2x2-for-CNNs/assets/155350256/53644ce3-a4b8-4052-8203-7b6e25d30331)


## Design code:

- Main code:

```
always @ (posedge clk) begin
if(enable) begin
if($signed(initialMax) < $signed(input1)) begin
if($signed(input2) < $signed(input1)) begin
if($signed(input3) < $signed(input1)) begin
if($signed(input4) < $signed(input1)) begin
output1 <= input1;
maxPoolingDone <= 1;
end
else begin
output1 <= input4;
maxPoolingDone <= 1;
end
end
else begin
if($signed(input3) < $signed(input4)) begin
output1 <= input4;
maxPoolingDone <= 1;
end
else begin
output1 <= input3;
maxPoolingDone <= 1;
end
end
end
else begin
if($signed(input3) < $signed(input2)) begin
if($signed(input4) < $signed(input2)) begin
output1 <= input2;
maxPoolingDone <= 1;
end
else begin
output1 <= input4;
maxPoolingDone <= 1;
end
end
else begin
if($signed(input3) < $signed(input4)) begin
output1 <= input4;
maxPoolingDone <= 1;
end
else begin
output1 <= input3;
maxPoolingDone <= 1;
end
end
end
end
else begin
output1 <= initialMax;
maxPoolingDone <= 1;
end
end
else begin
output1 <= 0;
maxPoolingDone <= 0;
end
end
```


## Result waveform:

- ![maxpool_op](https://github.com/amanh-iitj/Efficient-Downsampling-Techniques-MaxPooling-8x8-to-2x2-for-CNNs/assets/155350256/d9fef262-9771-4a44-8dd1-e84a835e90fc)



## Tool used:

- Xilinx Vivado


