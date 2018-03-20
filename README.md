# ratakanarslan
Object Defining
/*Aşağıdaki uygulamada farklı fotoğraflarda yapılan kare, üçgen, daire gibi görüntülerin aynı anda yer aldığı bir fotoğrafta görüntülerin şeklinin ayırt edilmesi uygulaması gerçekleştirilmiştir.*/
daire = imread('daire.jpg');
BWD = im2bw(daire, 0.08);
[DaireBW,num1] = bwlabel(BWD);
sd = regionprops(DaireBW,'all');
Comp1 = sd.Perimeter^2/sd.Area ;
figure; imshow(DaireBW) ; title(['Circle Picture & Compactness =  ' , num2str(Comp1), ' mm']);
kare = imread('kare.jpg');
BWK = im2bw(kare, 0.08);
[KareBW,num2] = bwlabel(BWK);
sk = regionprops(KareBW,'all');
Comp2 = sk.Perimeter^2/sk.Area ;
figure(2); imshow(KareBW) ; title(['Square Picture & Compactness =  ' , num2str(Comp2), ' mm']);
ucgen = imread('ucgen.jpg');
BWU = im2bw(ucgen, 0.08);
[UcgenBW,num3] = bwlabel(BWU);
su = regionprops(UcgenBW,'all');
Comp3 = su.Perimeter^2/su.Area ;
figure(3); imshow(UcgenBW) ; title(['Triangle Picture & Compactness =  ' , num2str(Comp3), ' mm']);
triple = imread('uclu.jpg');
BWT = im2bw(triple, 0.08);
[TripleBW,num4] = bwlabel(BWT);
st = regionprops(TripleBW, 'all');
figure(4);
imshow(triple)
for i=1:num4
Compac(i) = st(i).Perimeter^2/st(i).Area;
    if  Compac(i)>10 & Compac(i)<14;
        text(st(i).Centroid(1) ,st(i).Centroid(2),'Circle')
    end
  
  if  Compac(i)>14 & Compac(i)<17;
       text(st(i).Centroid(1) ,st(i).Centroid(2),'Square')
    end
    if Compac(i)>17 & Compac(i)<24;
        text(st(i).Centroid(1) ,st(i).Centroid(2),'Triangle')
    end
    title('Detected Shapes');
end
