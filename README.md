# Recognition-technique-using-in-Coin-Detection-
Recognition technique using in  Coin Detection - We develop a novel method for detecting the coins by using number wise images.
**1.Reading the Input Image**
I = imread('C1.jpg');
figure;imshow(I);
title('input image'); 
**2.converting the input image into gray image for processing**
I=rgb2gray(I);
imshow(I);
title('gray image'); 
**3.performing edge detection using canny filter**
c = edge(I,'canny',0.3); 
imshow(c);
title('edge detected image'); 
**4.performing dilation using disk type structural element **
se = strel('disk',2); 
I2 = imdilate(c,se)
imshow(I2);   
title('dilated image'); 
**5.filling the empty space with holes** 
d2 = imfill(I2, 'holes'); 
imshow(d2);  
title('filled image'); 
**6. performing labeling and finding connected components **
[Label,num]=bwlabeln(d2,4);
a1=(Label==1);
a2=(Label==2);
a3=(Label==3);
a4=(Label==4);
a5=(Label==5);
a6=(Label==6);
**7. recognition of coins using rule based concept**
    
for i=1:size(I,1)
    for j=1:size(I,2)
        if((a1(i,j)|a4(i,j))==1)
            AA(i,j)=I(i,j);
        else
             AA(i,j)=0;
        end
    end
end
figure,imshow(AA,[]);
title('10 paise coin detection'); 
for i=1:size(I,1)
    for j=1:size(I,2)
        if(a2(i,j)==1)
            AA(i,j)=I(i,j);
        else
             AA(i,j)=0;
        end
    end
end
figure,imshow(AA,[]);
title('5 paise coin detection'); 
for i=1:size(I,1)
    for j=1:size(I,2)
        if(a3(i,j)==1)
            AA(i,j)=I(i,j);
        else
             AA(i,j)=0;
        end
    end
end
figure,imshow(AA,[]);
title('25 paise coin detection'); 



