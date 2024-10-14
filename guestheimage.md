<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title></title>
</head>
<style>
	img {
		width:200px;height:200px;
	}
	img:hover{
		border: 1px solid red;
	}

</style>
<body>
	<script>
		document.addEventListener("DOMContentLoaded", () => {
		resimler=["dino.jpg","dino2.jpg","kabak.jpg","kabak2.jpg","kedi2.jpg","köpek.jpg","yilan.jpg","yilan3.jpg","dino.jpg","dino2.jpg","kabak.jpg","kabak2.jpg","kedi2.jpg","köpek.jpg","yilan.jpg","yilan3.jpg"];
		cikansayilar=[];
		karistir = false ;
		 ekranimg = document.getElementsByTagName('img');
		 ekranimg = Array.prototype.slice.call(ekranimg);
		 resim1=-1;
		 resim2=-1;
		})
		function rndsayi() {
			devam=true;
			buldumu=false;
			while(devam){
				randomsayi =Math.floor(Math.random()*100);
				if (randomsayi>15) {
					continue;
				}
				for(i of cikansayilar){
					if (i==randomsayi) {
						buldumu=true;
						break;
					}
				}
				if (buldumu) {
					buldumu=false;
					continue;
				}
				cikansayilar.push(randomsayi);
				devam=false;
				return randomsayi;
			}
		}
		function resimno(){
			karistir=true;
			for (var i = 0;i<16;i++) {
				yer = rndsayi();
			}
		}
		function resim(gelenno){
			if (karistir == false) {
				resimno();
			}
			Number(document.getElementById("skor").value)=Number(document.getElementById("skor").value) +1;
			if (resim1!=-1 && resim2 != -1) {
				if (ekranimg[resim1].src == ekranimg[resim2].src ) {
					ekranimg[resim1].src = "img/ok.jpg" ;
					ekranimg[resim2].src = "img/ok.jpg" ;
					ekranimg[resim1].onclick = "";
					ekranimg[resim2].onclick = "";
				}else {
					ekranimg[resim1].src = "img/bos.jpg" ;
					ekranimg[resim2].src = "img/bos.jpg" ;
				}
				resim1=gelenno ; 
				resim2=-1 ;
				ekranimg[gelenno].src = "img/" + resimler[cikansayilar[gelenno]];
				return;
			}
			if (resim1==-1 && resim2==-1) {
				resim1=gelenno;
				ekranimg[gelenno].src = "img/" + resimler[cikansayilar[gelenno]];
				return;
			}
			if (resim2==-1) {
				resim2=gelenno;
				ekranimg[gelenno].src = "img/" + resimler[cikansayilar[gelenno]];
				return;
			}
		}
	</script>
<table>
	<tr>
		<th colspan="4">Tıklama Sayınız:<input disabled id="skor"></th>
	</tr>
	<tr>
		<td><img onclick="resim(0);" src="img/bos.jpg"></td>
		<td><img onclick="resim(1);" src="img/bos.jpg"></td>
		<td><img onclick="resim(2);" src="img/bos.jpg"></td>
		<td><img onclick="resim(3);" src="img/bos.jpg"></td>
	</tr>
	<tr>
		<td><img onclick="resim(4);" src="img/bos.jpg"></td>
		<td><img onclick="resim(5);" src="img/bos.jpg"></td>
		<td><img onclick="resim(6);" src="img/bos.jpg"></td>
		<td><img onclick="resim(7);" src="img/bos.jpg"></td>
	</tr>
	<tr>
		<td><img onclick="resim(8);" src="img/bos.jpg"></td>
		<td><img onclick="resim(9);" src="img/bos.jpg"></td>
		<td><img onclick="resim(10);" src="img/bos.jpg"></td>
		<td><img onclick="resim(11);" src="img/bos.jpg"></td>
	</tr>
	<tr>
		<td><img onclick="resim(12);" src="img/bos.jpg"></td>
		<td><img onclick="resim(13);" src="img/bos.jpg"></td>
		<td><img onclick="resim(14);" src="img/bos.jpg"></td>
		<td><img onclick="resim(15);" src="img/bos.jpg"></td>
	</tr>
</table>
<button onclick="resimno()"></button>
</body>
</html>
