# TP2- Jeux de mots

## réalisé par Lakhmiri Mohammed Elias

## Synthèse et analyse spectrale d’une gamme de musique

# Objectifs

- ### Comprendre comment manipuler un signal audio avec Matlab, en effectuant certaines opérations classiques sur un fichier audio d’une phrase enregistrée via un smartphone.

- ### Comprendre la notion des sons purs à travers la synthèse et l’analyse spectrale d’une gamme de musique.

### **Commentaires** : Il est à remarquer que ce TP traite en principe des signaux continus. Or, l'utilisation de Matlab suppose l'échantillonnage du signal. Il faudra donc être vigilant par rapport aux différences de traitement entre le temps continu et le temps discret.

### **Tracé des figures** : toutes les figures devront être tracées avec les axes et les légendes des axes appropriés.

### **Travail demandé** : un script Matlab commenté contenant le travail réalisé et des commentaires sur ce que vous avez compris et pas compris, ou sur ce qui vous a semblé intéressant ou pas, bref tout commentaire pertinent sur le TP.

## Jeux de mots

### « phrase.wave » est un fichier audio enregistré à l’aide d’un smartphone, en prononçant lentement la phrase :

### `   « Rien ne sert de courir, il faut partir à point ».    `

1- Sauvegardez ce fichier sur votre répertoire de travail, puis charger-le dans MATLAB à l’aide de la commande « audioread ».

2- Tracez le signal enregistré en fonction du temps, puis écoutez-le en utilisant la commande « sound ».

3- Cette commande permet d’écouter la phrase à sa fréquence d’échantillonnage d’enregistrement. Ecoutez la phrase en modifiant la fréquence d’échantillonnage à double ou deux fois plus petite pour vous faire parler comme « Terminator » ou « Donald Duck ». En effet, modifier la fréquence d’échantillonnage revient à appliquer un changement d’échelle y(t) = x(at) en fonction de la valeur du facteur d’échelle, cela revient à opérer une compression ou une dilatation du spectre initial d’où la version plus grave ou plus aigüe du signal écouté.

```matlab
clear all
close all
clc
[y,Fs] = audioread('phrase.wav');
% sound(y,Fs);
figure(1)
 plot(y);
t=2*Fs;
% sound(y,t);
```

![image](https://user-images.githubusercontent.com/53974876/150514074-f6627238-525e-4023-b0c0-40976ffffdaf.png)

4- Tracez le signal en fonction des indices du vecteur x, puis essayez de repérer les indices de début et de fin de la phrase « Rien ne sert de »

![image](https://user-images.githubusercontent.com/53974876/150514974-6907636d-86e8-44dd-ac8f-d2bc9ed1ed9b.png)



5- Pour segmenter le premier mot, il faut par exemple créer un vecteur « riennesertde » contenant les n premières valeurs du signal enregistré x qui correspondent à ce morceau. Créez ce vecteur, puis écoutez le mot segmenté.

```matlab
Te=1/Fs;
N=length(y);
t=0:Te:(N-1)*Te;
figure(2)
plot(t,y)
figure(3)
riennesertde=y(16270:74701);
ch=length(riennesertde);
t=(0:ch-1)*1/Fs;
plot(t,riennesertde);

```

6- Segmentez cette fois-ci toute la phrase en créant les variables suivantes : riennesertde, courir, ilfaut, partirapoint.

```matlab
riennesertde=y(16270:74701);
ch=length(riennesertde);
t=(0:ch-1)*1/Fs;
subplot(2,2,1)
plot(t,riennesertde);
%sound(riennesertde,Fs);
%%%%%%%

 courir=y(79693:90562);
 ch1=length(courir);
 t=(0:ch1-1)*1/Fs;
 subplot(2,2,2)
 plot(t,courir);
 %%%%%%%%
 
  ilfaut=y(101892:120179);
  ch2=length(ilfaut);
  t=(0:ch2-1)*1/Fs;
  subplot(2,2,3)
  plot(t,ilfaut);
%  sound(ilfaut,Fs);
 
 %%%%%%%%%
 
   partirapoint=y(126658:161014);
  ch3=length(partirapoint);
  t=(0:ch3-1)*1/Fs;
  subplot(2,2,4)
  plot(t,partirapoint);
```
![image](https://user-images.githubusercontent.com/53974876/150516682-812d1988-da4a-45a0-a47f-98657a2d212f.png)

7- Notez que le signal initial de parole est un vecteur colonne contenant un certain 
nombre de valeurs (length(x)). Réarrangez ce vecteur pour écouter la phrase 
synthétisée « Rien ne sert de partir à point, il faut courir ». 

```matlab
  figure(4)
  phra=[riennesertde,partirapoint,ilfaut,courir];
  % sound(phra,Fs);
   plot(phra);

```


![image](https://user-images.githubusercontent.com/53974876/150517836-a994aad9-441c-453f-8f20-0b352b10ea43.png)





# Synthèse et analyse spectrale d’une gamme de musique

Les notes de musique produites par un piano peuvent être synthétisées approximativement numériquement. En effet, chaque note peut être considérée comme étant un son pur produit par un signal sinusoïdal. La fréquence de la note « La » est par exemple de 440 Hz.

1- Créez un programme qui permet de jouer une gamme de musique. La fréquence de chaque note est précisée dans le tableau ci-dessous. Chaque note aura une durée de 1s. La durée de la gamme sera donc de 8s. La fréquence d’échantillonnage fe sera fixée à 8192 Hz.


![image](https://user-images.githubusercontent.com/53974876/150517510-38b45075-b3d3-4ee1-b810-d9f59e793ab5.png)




