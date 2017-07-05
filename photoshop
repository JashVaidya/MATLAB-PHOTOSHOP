%%
% Photoshop
clear,clc;
A = imread('baboon.bmp');
colormap(gray(256));
subplot(1,2,1), image(A);
title('Original');
option = menu('PhotoEditor Option','Properties','Darken','Brighten','Reduce Bits','Increase Contrast','Decrease Contrast','Sharpen','Soften','Crop','Reduce Array Size','Negative','Change Color','Chroma Key');
switch option
    case 1 %Properties
        info = imfinfo('baboon.bmp')
        %This lets me get the information of whichever image I would like
        %to know of. 
        
    case 2 %Darken
        A2 = A - 50;
        subplot(1,2,1), image(A); 
        title('Original');
        subplot(1,2,2), image(A2);
        title('Darker');
        %By subtracting 50 from the image, I can produce a darker version
       
    case 3 %Brighten
        A2 = A + 50;
        subplot(1,2,1), image(A);
         title('Original');
        subplot(1,2,2), image(A2);
         title('Brighter');
        %By adding 50, I can make the image brighter
    case 4 %Reduce Bits
        n = menu('Number of bits','1','2','8')
        
        C = A * ((2^n -1)/256);
        
        subplot(1,2,1),imagesc(A);
         title('Original');
        subplot(1,2,2),imagesc(C)
         title('Reduced Bit');
        
                
    case 5 %Increase Contrast
        A2 = A*2;
        subplot(1,2,1), image(A);
         title('Original');
        subplot(1,2,2), image(A2);
         title('Increased Contrast');
         %By multiplying by 2, I can get a higher contrast from the image
        
    case 6 %Decrease Contrast
         A2 = A/2;
        subplot(1,2,1), image(A);
         title('Original');
        subplot(1,2,2), image(A2);
         title('Decreased Contrast');
        %To decrease it, I need to do the opposite of increasing it. So i
        %need to divide the orginial image by 2 for this case. 
        
    case 7 %Sharpen
        A = double(A);
        for i = 2:1:255;
            for j = 2:1:255;
                A2(i,j) = -A(i-1,j) -A(i,j-1) + 5 * A(i,j) - A(i,j+1) - A(i+1,j);
            end
        end
        A = uint8(A);
        A2 = uint8(A2);
        subplot(1,2,1), image(A);
         title('Original');
        subplot(1,2,2), image(A2);
         title('Sharpend');
    case 8 %Soften   
         A = double(A);
        for i = 2:1:255;
            for j = 2:1:255;
                A2(i,j) = 0.5 * (A(i,j)+A(i,j-1));
            end
        end
        A = uint8(A);
        A2 = uint8(A2);
        subplot(1,2,1), image(A);
         title('Original');
        subplot(1,2,2), image(A2);
        title('Softened');        
    case 9 %Crop

        fprintf('Choose two diagonal corners.');
        [y,x] = ginput(2);
        r1 = x(1,1);
        r2 = x(2,1);
        c1 = y(1,1);
        c2 = y(2,1);
        
        R1 = A(r1:1:r2, c1:1:c2);
        
        subplot(1,2,2), image(R1);
        title('Cropped');
    case 10 %Reduce array size
        
        reduce = menu('Reduction option', 'Every Other', 'Average of 4');        
        
        switch reduce
            case 1 %every other pixel
                %for (i = 1:3)
                A = double(A);
                for r = 2:2:256
                    for c = 2:2:256
                        A1(r/2,c/2) = A(r,c); %color is A(r,c,i)
                    end
                end
                A = uint8(A);
                A1 = uint8(A1);
                subplot(1,2,1), image(A)
                 title('Original');
                subplot(1,2,2), image(A1)
                 title('Every Other Pixel');
                
            case 2 %Average of 4 pixels
                A = double(A);
                 for r = 2:2:256
                    for c = 2:2:256
                        A1(r/2,c/2) = 0.25*(A(r-1,c-1) + A(r,c-1) + A(r,c) + A(r-1,c)); 
                    end 
                 end
                A= uint8(A);
                A1 = uint8(A1);
                subplot(1,2,1), image(A)
                 title('Original');
                subplot(1,2,2), image(A1)
                 title('Average of 4 pixels');
        end
        
    case 11 %Negative
        A2 = 256 - A;
         subplot(1,2,1), image(A)
          title('Original');
         subplot(1,2,2), image(A2)
          title('Negative');
         
    case 12 %Change color
        map = menu('Colormap','Autumn','Summer','Spring','Winter')
        
        switch map
    case 1 
        subplot(1,2,1),imagesc(A);
        colormap(autumn(256))
        subplot(1,2,2),image(A)
         title('Autumn');
    case 2 
        subplot(1,2,1),imagesc(A);
        colormap(summer(256))
        subplot(1,2,2),imagesc(A);
         title('Summer');
     case 3
        subplot(1,2,1),imagesc(A);
        colormap(spring(256))
        subplot(1,2,2),imagesc(A); 
         title('Spring');
     case 4
        subplot(1,2,1),imagesc(A);
        colormap(winter(256))
        subplot(1,2,2),imagesc(A);
         title('Winter');
    end
        
    case 13 %Chroma Key
       
     Q = imread('chroma.jpg');
      Y = imread('earth.jpg');
      colormap(gray(256));
      Q = double(Q);
      Y = double(Y);
      
      for r = 1:1:177
          for c = 1:1:231
              if Q(r,c,1) < 125 && Q(r,c,3) > 100
                  
                  Q2(r,c,1) = 1;
                  Q2(r,c,2) = 1;
                  Q2(r,c,3) = 1;
              end
          end
      end
      
      Q3 = 1 - Q2;     
      D = Y .* Q2;
      E = Q .* Q3;
      F = D + E;
      F = uint8(F);
      subplot(1,1,1),image(F);
      title('Chroma Key');
end
