<script lang="ts">
	import { Presentation, Slide, Notes } from '@components'
	import Layout from './layout.svelte'
</script>

<Presentation>	
	<script>
		// information about this presentation 
		// const authorshort = "Schuler, Nayak, Saha, Baumann"; 
		const author = "Christian Schuler, Shravan Nayak, Debjoy Saha, Timo Baumann"; 
		const authorshort = "Schuler, Nayak, Saha, Baumann"; 
		const title = "Can We See Your Response Before You Speak?";
		const subtitle = "Exploring Linguistic Information Found In Inter-Utterance Pause";
		const department = "ESSV"; 
		const university = "35. Conference on Electronic Speech Signal Processing"; 
		var currentChapterName="";
		var currentChapterNumber=0;
		var chapterNames=[];
		var toc = false;  // whether toc is to be generated
		// data structure: [chapter number, chapter name, slideID]
		var presentationData = []; 
		function newChapter(chapterName){
			currentChapterName=chapterName; 
			currentChapterNumber++;
			chapterNames.push(chapterName);
		}
		// called when new slide is created
		var page=0; 
		function newPage(){
			page++; //note that page n has index n-1
			presentationData.push({chapternr: currentChapterNumber, chapter:currentChapterName,pagenr:page});
		}
	</script>

	<!-- title page -->
	<Slide>
		<Layout>
			<div class="m-16 flex h-[25vh] w-[90vw] bg-[var(--themecolor)] text-white items-center justify-center gap-[100px]">
				<div>
					<div class="text-[6vh]">
						<span id="mytitle"> </span>
					</div>
					<br>
					<div class="text-[4vh]">
						<span id="mysubtitle"> </span>
					</div>
				</div>
			</div>
			<br>
			<div> 
				<span id="myname"></span>
			</div>
			<br>
			<div class="text-[3vh]"> 
				<span id="myuni"></span>
			</div>
			<div class="text-[2.5vh]"> 
				<br>
				<span id="mydate"></span>
			</div>
			<br>
			<div class="flex items-center justify-center">
				<img class="h-[20vh] align-middle" src="logo.png" alt="Pause Processing Logo">
			</div>
			<!-- fill in the data for this presentation  -->
			<script> 
				document.getElementById("mytitle").innerHTML=title;
				document.getElementById("mysubtitle").innerHTML=subtitle;
				document.getElementById("myname").innerHTML=author;
				//document.getElementById("myuni").innerHTML=department+"<br>"+university;
				document.getElementById("myuni").innerHTML=university;
				let today = new Date(); 
				document.getElementById("mydate").innerHTML=today.toISOString().split('T')[0]; 
			</script>
		</Layout>
	</Slide>

	<!-- TOC -->
	<Slide>
		<script>
			toc=true; // decides whether to generate table of content page
		</script>
		<Layout>
			<toc class="flex h-full items-center justify-center gap-[100px]">
				<chpicons> </chpicons>
				<chpnames class="text-left"> </chpnames>
			</toc>
		</Layout>
	</Slide>

	<!-- Introduction ####################################################### -->
	<script> newChapter("Introduction"); </script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Project Team
			</titlebar>
			<mybody>
				<div class="grid" style="grid-template-columns: auto auto auto auto;">
					<!-- Names -->
					<div class="flex w-[22vw] items-center justify-center gap-[100px]">
						Christian Schuler
					</div>
					<div class="flex w-[22vw] items-center justify-center gap-[100px]">
						Shravan Nayak
					</div>
					<div class="flex w-[22vw] items-center justify-center gap-[100px]">
						Debjoy Saha
					</div>
					<div class="flex w-[22vw] items-center justify-center gap-[100px]">
						Timo Baumann
					</div>
					<!-- Homepage -->
					<div class="flex w-[22vw] text-[1vh] items-center justify-center gap-[50px]">
						https://christianschuler8989.github.io/
					</div>
					<div class="flex w-[22vw] text-[1vh] items-center justify-center gap-[50px]">
						https://bajuka.github.io/
					</div>
					<div class="flex w-[22vw] text-[1vh] items-center justify-center gap-[50px]">
						https://debjoy10.github.io/
					</div>
					<div class="flex w-[22vw] text-[1vh] items-center justify-center gap-[50px]">
						https://timobaumann.de/work/Main/HomePage
					</div>
					<!-- Images -->
					<img src="Christian_Schuler_01_Lecturing.jpg" class="h-[40vh]" alt="Text">
					<img src="Shravan_Nayak_github.jpeg" class="h-[40vh]" alt="Text">
					<img src="Debjoy_Saha_Googlescholar.jpeg" class="h-[40vh]" alt="Text">
					<img src="Timo_Baumann_01.jpg" class="h-[40vh]" alt="Text">	
					<!-- Description -->
					<div class="flex w-[22vw] text-[2vh] items-center justify-center gap-[50px] p-2">
						About to finish his masters in computer science at University of Hamburg
						Christian Schuler likes colors and languages and eats more pizza in one year than any of you in your lifetime!<br>
						<!-- https://christianschuler8989.github.io/ -->
					</div>
					<div class="flex w-[22vw] text-[2vh] items-center justify-center gap-[50px] p-2">
						Currently pursuing his research masters in computer science at Mila and the University of Montreal, supervised by Prof. Aishwarya Agrawal.<br>
						At MILA, his focus lies in developing vision language systems that transcend linguistic barriers and cater to diverse demographics. 
						<!-- https://bajuka.github.io/ -->
					</div>
					<div class="flex w-[22vw] text-[2vh] items-center justify-center gap-[50px] p-2">
						B.Tech + M.Tech (Dual Degree) student at IIT Kharagpur, pursuing joint degrees in Electronics and Computer Science.<br>
						Broadly, his research interests lie in machine learning for image, language and speech processing.
						<!-- https://debjoy10.github.io/ -->
					</div>
					<div class="flex w-[22vw] text-[2vh] items-center justify-center gap-[50px] p-2">
						Professor in Artificial Intelligence and Natural Language Processing at the School for CS and Maths at OTH Regensburg.<br>
						He researches spoken language, in particular in interactive and multi-modal scenarios, such as in spoken dialogue systems.
						<!-- https://timobaumann.de/work/Main/HomePage -->
					</div>
					<!-- Affiliations -->
					<img src="UHH_Universität_Hamburg_Logo_mit_Schrift_2010_Farbe_CMYK.svg.png" class="flex h-[10vh] items-center justify-center mx-auto my-auto" alt="Text">
					<!-- https://de.wikipedia.org/wiki/Datei:UHH_Universit%C3%A4t_Hamburg_Logo.svg#/media/Datei:UHH_Universit%C3%A4t_Hamburg_Logo_mit_Schrift_2010_Farbe_CMYK.svg -->
					<img src="250px-Universite_de_Montreal_logo.svg.png" class="flex h-[10vh] items-center justify-center mx-auto my-auto" alt="Text">
					<!-- https://en.wikipedia.org/wiki/File:Universite_de_Montreal_logo.svg -->
					<img src="IIT_Kharagpur_Logo.svg.png" class="flex h-[10vh] items-center justify-center mx-auto my-auto" alt="Text">
					<!-- https://en.wikipedia.org/wiki/IIT_Kharagpur#/media/File:IIT_Kharagpur_Logo.svg -->
					<img src="Logo-OTH-Regensburg.png" class="flex h-[10vh] w-[22vw] items-center justify-center mx-auto my-auto" alt="Text">
					<!-- https://de.m.wikipedia.org/wiki/Datei:Logo-OTH-Regensburg.png -->
				</div>
			</mybody>
		</Layout>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Problem / Motivation
			</titlebar>

			<mybody>
				<figure class="w-[90vw] float-left mx-auto my-auto">
					<img src="PauseProcessingLargeImages-DataPausesMerkelSmall.png" alt="virtual" class="h-[50vh] mx-auto my-[3vh]">
					<figcaption>Bacon Ipsum Dolor Cheesecake.<br>
						Pizza? You mean "yum-yum in my tum-tum"! :D</figcaption>
				</figure>


				<!-- <div class="grid" style="grid-template-columns: auto;">
					<img src="PauseProcessingLargeImages-DataPausesMerkelSmall.png" alt="Introduction Problem" class="h-[50vh]">
				
					<div class="flex w-full text-[5vh] items-center justify-center gap-[50px] p-5">
						Bacon Ipsum Dolor Cheesecake.<br>
						Pizza? You mean "yum-yum in my tum-tum"! :D
					</div>
				</div> -->
			</mybody>
		</Layout>
		<Notes>
			What is it, that we are doing?
		</Notes>
	</Slide>


	<!-- Methodology ####################################################### -->
	<script>newChapter("Methodology");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Methodology
			</titlebar>

			<mybody>
				<figure class="w-[100vw] float-left ml-[5vh] mt-[5vh]">
					<img src="PauseProcessing-DataPauses.png" alt="virtual" class="h-[50vh] mx-auto my-[3vh]">
					<figcaption>General overview of our experiment setup for first word prediction and discriminator training.</figcaption>
				</figure>

				<!-- <div class="grid" style="grid-template-columns: auto;">
					<img src="PauseProcessing-DataPauses.png" alt="Introduction Problem" class="w-[75vw]">
				
					<div class="flex w-full text-[5vh] items-center justify-center gap-[50px] p-5">
						General overview of our experiment setup for first word prediction and discriminator training.
					</div>
				</div> -->
			</mybody>
			
		</Layout>
		<Notes>
			What is it, that others were doing?
		</Notes>
	</Slide>


	<!-- Data ####################################################### --> 
	<script>newChapter("Data");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data from the Merkel Podcast Corpus
			</titlebar>

			<mybody>
				<div class="grid" style="grid-template-columns: auto;">
					<a href="https://github.com/deeplsd/Merkel-Podcast-Corpus" target="_blank" rel="noopener noreferrer">
						<img src="merkel_podcast_corpus_title.jpg" alt="Data Quality" class="w-[100vw]">
					</a>
					
					<div class="flex w-full text-[5vh] items-center justify-center gap-[50px] p-5">
						The corpus is split roughly equally between (semi-)prepared speeches and interview dialogues.
					</div>
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			What is it, that others were doing?
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data Quality for Pause Processing
			</titlebar>

			<mybody>
				<div class="grid" style="grid-template-columns: auto;">
					<img src="PauseProcessingLargeImages-DataPausesMerkel.png" alt="Data Quality" class="w-[100vw]">
				
					<div class="flex w-full text-[5vh] items-center justify-center gap-[50px] p-5">
						Data example of a pause sequence and surrounding video sequences.
					</div>
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			What is it, that others were doing?
		</Notes>
	</Slide>

	


	<!-- Experiment ####################################################### -->
	<script>newChapter("Experiment");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Motivation
			</titlebar>

			<mybody>
				<div class="flex w-full text-[5vh] items-center justify-center gap-[50px]">
					Bacon Ipsum Dolor Cheesecake.<br>
					Pizza? You mean "yum-yum in my tum-tum"! :D
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			What is it, that others were doing?
		</Notes>
	</Slide>


	<!-- Results & Discussion ####################################################### -->
	<script>newChapter("Results & Discussion");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Motivation
			</titlebar>

			<mybody>
				<div class="flex w-full text-[5vh] items-center justify-center gap-[50px]">
					Bacon Ipsum Dolor Cheesecake.<br>
					Pizza? You mean "yum-yum in my tum-tum"! :D
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			What is it, that others were doing?
		</Notes>
	</Slide>


	<!-- Conclusions & Future Work ####################################################### -->
	<script>newChapter("Conclusions & Future Work");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Motivation
			</titlebar>

			<mybody>
				<div class="flex w-full text-[5vh] items-center justify-center gap-[50px]">
					Bacon Ipsum Dolor Cheesecake.<br>
					Pizza? You mean "yum-yum in my tum-tum"! :D
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			What is it, that others were doing?
		</Notes>
	</Slide>


	<!-- Appendix ####################################################### -->
	<script>newChapter("Appendix");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Motivation
			</titlebar>

			<mybody>
				<div class="flex w-full text-[5vh] items-center justify-center gap-[50px]">
					Bacon Ipsum Dolor Cheesecake.<br>
					Pizza? You mean "yum-yum in my tum-tum"! :D
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			What is it, that others were doing?
		</Notes>
	</Slide>




	<!-- to mimic the latex template  -->
	<script>
		const totalSlides = document.getElementsByTagName('pagenumber').length;
		const totalChapters = chapterNames.length;
		var temp; 
		for (let i = 0; i < totalSlides; i++) {
			// one section, one slide
			document.getElementsByTagName('section')[i].setAttribute("id", "slide-"+(i+1));
			// add author name 
			document.getElementsByTagName('author')[i].innerText=authorshort;
			// add title 
			document.getElementsByTagName('mytitle')[i].innerHTML="<a href=\"#slide-1\">"+title+"</a>";
			// show slide number with total slide number
			document.getElementsByTagName("pagenumber")[i].innerHTML = (i+1)+"/"+totalSlides;
		}
		for (let i = 0; i < totalSlides; i++) {
			for (let j = 0; j < totalChapters; j++) {
				// fill in chapter names
				temp = document.querySelectorAll("table.topbar")[i]; 
				temp.getElementsByTagName("tr")[0].innerHTML += "<th data-chpcol=\"chpcol\" style=\"font-weight:normal\">"+chapterNames[j]+"</th>";
				//document.getElementsByTagName("test")[0].innerHTML="here!"; 
				// fill in dots
				let slidesInChapter = presentationData.filter(item => item.chapter == chapterNames[j]);
				let begin = slidesInChapter[0].pagenr;
				let end = slidesInChapter[slidesInChapter.length-1].pagenr;
				let circles=toCircle(begin,end);
				temp.getElementsByTagName("tr")[1].innerHTML += "<td>"+ circles +"</td>";
			}
		}
		for (let i = 0; i < totalSlides; i++) {
			// first, find out if title page and toc exist 
			let chapter0 = presentationData.filter(item => item.chapternr == 0).length;
			if (i>=chapter0){
				// then set corresponding circle to white
				let circle = document.getElementsByTagName("circle-"+(i+1))[i]; 
				circle.style.background="white";
				circle.style.border="0px";
				// also the chapter names 
				let chapterNr = presentationData.filter(item => item.pagenr == i+1)[0].chapternr;
				temp = document.getElementsByTagName("th")[(i)*(totalChapters)+chapterNr-1];
				if (temp.hasAttribute("data-chpcol")){ 
					temp.style.color="white";
				}
			}
		}
		// circles: start, start+1, . . . , end are created
		function toCircle(begin,end){
			let circles = ""; 
			for (let i=begin; i<=end; i++){
				circles+="<a href=\"#slide-" +i+ "\"><circle-" +i+ " class=\"dot\"> </circle-" +i+ "> </a>" ;
			}
			return circles;
		}
		// to create table of contents
		if (toc) {
			for (i=1; i<=chapterNames.length;i++){
				document.getElementsByTagName('chpicons')[0].innerHTML += "<div class=\"chpicon\">"+i+"</div> <br>";
				document.getElementsByTagName('chpnames')[0].innerHTML += "<div>"+chapterNames[i-1]+"</div> <br>";
			}
		}
	</script>
	
	<style>
		.chpicon{
			color: white;
			width:180%;
			background: var(--themecolor);
		}
		.dot{
			height: 15px;
			width: 15px;
			background: rgba(0,0,0,0);
			border-radius: 50%;
			border: 1.5px solid var(--themecolorlight);
			display: inline-block;
		}
		/* .titlebar{
			background: rgb(242,242,242); 
			width: Z_FULL_FLUSH; 
			height: 9vh; 
			text-align: left;
			padding-left: 2vh; 
			padding-top: 2vh;
			font-size: 5vh;
		} */
		ul.a{
			list-style-type: square;
			padding-top:4vh;
		}
		ul.b{
			list-style-type: circle;
			margin-left:5vh;
			margin-right:5vh;
			padding-top:2vh;
		}
		ul{
			text-align: left;
			margin-left:20vh;
			margin-right:5vh;
		}
		titlebar{
			display:flex;
			background: rgb(202,242,212); 
			width: 100vw; 
			height: 9vh; 
			text-align: left;
			padding-left: 5vh; 
			padding-top: 2vh;
			font-size: 5vh;
		}
		mybody{
			display: flex;
			justify-content: center;
			align-items: center;
			height:79vh;
		}
		figure{
			border: 1px #cccccc solid;
			padding: 4px;
			margin: auto;
		}
		figcaption{
			background-color: rgb(192,242,202);
			color: black;
			font-style: italic;
			padding: 2px;
			text-align: center;
		}
	</style>
</Presentation>