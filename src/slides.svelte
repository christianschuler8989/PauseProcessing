<script lang="ts">
	import { Presentation, Slide, Notes, Media } from '@components'
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
					<div class="flex w-[22vw] text-[1vh] items-center justify-center gap-[50px] p-1">
						https://christianschuler8989.github.io/
					</div>
					<div class="flex w-[22vw] text-[1vh] items-center justify-center gap-[50px] p-1">
						https://bajuka.github.io/
					</div>
					<div class="flex w-[22vw] text-[1vh] items-center justify-center gap-[50px] p-1">
						https://debjoy10.github.io/
					</div>
					<div class="flex w-[22vw] text-[1vh] items-center justify-center gap-[50px] p-1">
						https://timobaumann.de/work/Main/HomePage
					</div>
					<!-- Images -->
					<figure class="h-[60vh] w-[22vw] float-left mx-auto my-auto">
						<img src="Christian_Schuler_01_Lecturing.jpg" alt="christian" class="h-[40vh]">
						<figcaption class="text-[2.3vh]">
							About to finish his masters in computer science at University of Hamburg.<br>
							Christian Schuler likes colors, languages and eats more pizza in one year than any of you in your lifetime!<br>
						</figcaption>
					</figure>
					<figure class="h-[60vh] w-[22vw] float-left mx-auto my-auto">
						<img src="Shravan_Nayak_github.jpeg" alt="shravan" class="h-[40vh]">
						<figcaption class="text-[2.3vh]">
							Pursuing his research masters in computer science at Mila and the University of Montreal, supervised by Prof. Aishwarya Agrawal.<br>
							His focus lies in developing vision language systems that transcend linguistic barriers and cater to diverse demographics. 
						</figcaption>
					</figure>
					<figure class="h-[60vh] w-[22vw] float-left mx-auto my-auto">
						<img src="Debjoy_Saha_Googlescholar.jpeg" alt="debjoy" class="h-[40vh]">
						<figcaption class="text-[2.3vh]">
							B.Tech + M.Tech (Dual Degree) student at IIT Kharagpur, pursuing joint degrees in Electronics and Computer Science.<br>
							Broadly, his research interests lie in machine learning for image, language and speech processing.
						</figcaption>
					</figure>
					<figure class="h-[60vh] w-[22vw] float-left mx-auto my-auto">
						<img src="Timo_Baumann_01.jpg" alt="timo" class="h-[40vh]">
						<figcaption class="text-[2.3vh]">
							Professor in Artificial Intelligence and Natural Language Processing at the School for CS and Maths at OTH Regensburg.<br>
							He researches spoken language, in particular in interactive and multi-modal scenarios, such as in spoken dialogue systems.
						</figcaption>
					</figure>
					
					<figure class="flex h-[12vh] w-[22vw] items-center justify-center mx-auto my-auto">
						<img src="UHH_Universität_Hamburg_Logo_mit_Schrift_2010_Farbe_CMYK.svg.png" alt="christian_hamburg" class="h-[10vh]">
					</figure>
					<figure class="flex h-[12vh] w-[22vw] items-center justify-center mx-auto my-auto">
						<img src="250px-Universite_de_Montreal_logo.svg.png" alt="shravan_montreal" class="h-[10vh]">
					</figure>
					<figure class="flex h-[12vh] w-[22vw] items-center justify-center mx-auto my-auto">
						<img src="IIT_Kharagpur_Logo.svg.png" alt="debjoy_kharagpur" class="h-[10vh]">
					</figure>
					<figure class="flex h-[12vh] w-[22vw] items-center justify-center mx-auto my-auto">
						<img src="Logo-OTH-Regensburg.png" alt="timo_regensburg" class="h-[10vh]">
					</figure>

					<!-- <img src="Christian_Schuler_01_Lecturing.jpg" class="h-[40vh]" alt="Text">
					<img src="Shravan_Nayak_github.jpeg" class="h-[40vh]" alt="Text">
					<img src="Debjoy_Saha_Googlescholar.jpeg" class="h-[40vh]" alt="Text">
					<img src="Timo_Baumann_01.jpg" class="h-[40vh]" alt="Text">	 -->

					<!-- Description -->
					<!-- <div class="flex w-[22vw] text-[2vh] items-center justify-center gap-[50px] p-2">
						About to finish his masters in computer science at University of Hamburg
						Christian Schuler likes colors and languages and eats more pizza in one year than any of you in your lifetime!<br>
					</div>
					<div class="flex w-[22vw] text-[2vh] items-center justify-center gap-[50px] p-2">
						Currently pursuing his research masters in computer science at Mila and the University of Montreal, supervised by Prof. Aishwarya Agrawal.<br>
						At MILA, his focus lies in developing vision language systems that transcend linguistic barriers and cater to diverse demographics. 
					</div>
					<div class="flex w-[22vw] text-[2vh] items-center justify-center gap-[50px] p-2">
						B.Tech + M.Tech (Dual Degree) student at IIT Kharagpur, pursuing joint degrees in Electronics and Computer Science.<br>
						Broadly, his research interests lie in machine learning for image, language and speech processing.
					</div>
					<div class="flex w-[22vw] text-[2vh] items-center justify-center gap-[50px] p-2">
						Professor in Artificial Intelligence and Natural Language Processing at the School for CS and Maths at OTH Regensburg.<br>
						He researches spoken language, in particular in interactive and multi-modal scenarios, such as in spoken dialogue systems.
					</div> -->
					<!-- Affiliations -->
					<!-- <img src="UHH_Universität_Hamburg_Logo_mit_Schrift_2010_Farbe_CMYK.svg.png" class="flex h-[10vh] items-center justify-center mx-auto my-auto" alt="Text">
					<img src="250px-Universite_de_Montreal_logo.svg.png" class="flex h-[10vh] items-center justify-center mx-auto my-auto" alt="Text">
					<img src="IIT_Kharagpur_Logo.svg.png" class="flex h-[10vh] items-center justify-center mx-auto my-auto" alt="Text">
					<img src="Logo-OTH-Regensburg.png" class="flex h-[10vh] w-[22vw] items-center justify-center mx-auto my-auto" alt="Text"> -->
					
					<!-- https://de.wikipedia.org/wiki/Datei:UHH_Universit%C3%A4t_Hamburg_Logo.svg#/media/Datei:UHH_Universit%C3%A4t_Hamburg_Logo_mit_Schrift_2010_Farbe_CMYK.svg -->
					<!-- https://en.wikipedia.org/wiki/File:Universite_de_Montreal_logo.svg -->
					<!-- https://en.wikipedia.org/wiki/IIT_Kharagpur#/media/File:IIT_Kharagpur_Logo.svg -->
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
					<img src="PauseProcessingLargeImages-DataPausesMerkelSmall.png" alt="virtual" class="w-[75vw] mx-auto my-[3vh]">
					<figcaption>
						Can we detect linguistic information hidden in the video sequence during a pause?
					</figcaption>
				</figure>
			</mybody>
		</Layout>
		<Notes>
			What is it, that we are doing?
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
				<figure class="h-[27vh] w-[95vw] float-left mx-auto my-auto">
					<a href="https://github.com/deeplsd/Merkel-Podcast-Corpus" target="_blank" rel="noopener noreferrer">
						<img src="merkel_podcast_corpus_title.jpg" alt="merkel_podcast_corpus" class="w-[95vw] mx-auto my-[1vh]">
					</a>
					<figcaption>
						The corpus is split roughly equally between (semi-)prepared speeches and interview dialogues.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			What is it, that others were doing?
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data Annotation for Pause Processing I - Ideal Case
			</titlebar>

			<mybody>
				<figure class="h-[75vh] float-left mx-auto my-auto">
					<img src="annotation_merkel_slick.png" alt="data_annotation_ideal_case" class="h-[65vh] mx-auto my-[1vh]">
					<figcaption>
						Ideal case: Merkel focus and center of the video during the pause.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Ideal case: Merkel focus and center of the video during the pause.
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data Annotation for Pause Processing II - Obvious Bad Cases
			</titlebar>

			<mybody>
				<figure class="h-[75vh] float-left mx-auto my-auto">
					<img src="annotation_interviewer_slick.png" alt="data_annotation_bad_case_interviewer" class="h-[65vh] mx-auto my-[1vh]">
					<figcaption>
						Someone else than Merkel during the pause.
					</figcaption>
				</figure>

				<figure class="h-[75vh] float-left mx-auto my-auto">
					<img src="annotation_distractor_slick.png" alt="data_annotation_bad_case_distractor" class="h-[65vh] mx-auto my-[1vh]">
					<figcaption>
						Distractors preventing view during the pause.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Obvious bad cases: Someone else than Merkel or distractors present during the pause.
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data Annotation for Pause Processing III - Tricky Bad Cases
			</titlebar>

			<mybody>
				<figure class="h-[75vh] float-left mx-auto my-auto">
					<img src="annotation_cut_from_merkel_slick.png" alt="data_annotation_tricky_case_merkel" class="h-[65vh] mx-auto my-[1vh]">
					<figcaption>
						Pause starts with Merkel in view.
					</figcaption>
				</figure>

				<figure class="h-[75vh] float-left mx-auto my-auto">
					<img src="annotation_cut_to_interviewer_slick.png" alt="data_annotation_tricky_case_interviewer" class="h-[65vh] mx-auto my-[1vh]">
					<figcaption>
						Cutting to the interviewer during the Pause.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Pause starts with Merkel in view. <br>
			Cutting to the interviewer during the Pause.
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data Quality for Pause Processing
			</titlebar>

			<mybody>
				<figure class="h-[40vh] w-[95vw] float-left mx-auto my-auto">
					<img src="PauseProcessingLargeImages-DataPausesMerkel.png" alt="data_quality" class="w-[95vw] mx-auto my-[1vh]">
					<figcaption>
						Data example of a pause sequence and surrounding video sequences.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Data example of a pause sequence and surrounding video sequences.
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data for Annotation Scheme
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="PauseProcessing-AnnotationSetup.png" alt="annotation_setup" class="h-[65vh] mx-auto my-[1vh]">
					<figcaption>
						Data preparation for annotation task.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Data preparation for annotation task.
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
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="PauseProcessing-DataPauses.png" alt="virtual" class="w-[65vw] mx-auto my-[3vh]">
					<figcaption>
						General overview of our experiment setup for first word prediction and discriminator training.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			General overview of our experiment setup for first word prediction and discriminator training.
		</Notes>
	</Slide>





	<!-- Experiment ####################################################### -->
	<script>newChapter("Experiment");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Experiment
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="construction-itsupport.png" alt="experiment" class="h-[55vh] mx-auto my-[3vh]">
					<figcaption>
						Bacon Ipsum Dolor Cheesecake.<br>
						Pizza? You mean "yum-yum in my tum-tum"! :D
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Experiment
		</Notes>
	</Slide>


	<!-- Results & Discussion ####################################################### -->
	<script>newChapter("Results & Discussion");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Results
			</titlebar>

			<mybody>
				<figure>
					<table>
						<tr>
							<th></th>
							<th>Correct</th>
							<th>Mean</th>
							<th>Stddev</th>
							<th>Median</th>
							<th>p-value<br>binomial</th>
							<th>p-value<br>t-test</th>
						</tr>
						<tr>
							<td><b>OpenFace</b></td>
							<td>0.51</td>
							<td>0.52</td>
							<td>0.47</td>
							<td>0.57</td>
							<td>.28</td>
							<td>.12</td>
						</tr>
						<tr>
							<td><b>CLIP</b></td>
							<td>0.56</td>
							<td>0.51</td>
							<td>0.07</td>
							<td>0.51</td>
							<td>.002</td>
							<td>.0001</td>
						</tr>
						<tr>
							<td><b>Timesformer</b></td>
							<td>0.53</td>
							<td>0.51</td>
							<td>0.08</td>
							<td>0.51</td>
							<td>.07</td>
							<td>.0001</td>
						</tr>
					  </table>
					<figcaption>
						Comparing the experiment result statistics of OpenFace, CLIP, and Timesformer.
					</figcaption>
				</figure>
			</mybody>
		</Layout>
		<Notes>
			Results
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Discussion
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="construction-itsupport.png" alt="discussion" class="h-[55vh] mx-auto my-[3vh]">
					<figcaption>
						Bacon Ipsum Dolor Cheesecake.<br>
						Pizza? You mean "yum-yum in my tum-tum"! :D
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Discussion
		</Notes>
	</Slide>


	<!-- Conclusions & Future Work ####################################################### -->
	<script>newChapter("Conclusions & Future Work");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Conclusions
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="construction-itsupport.png" alt="conlcusions" class="h-[55vh] mx-auto my-[3vh]">
					<figcaption>
						Bacon Ipsum Dolor Cheesecake.<br>
						Pizza? You mean "yum-yum in my tum-tum"! :D
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Conclusions
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Future Work
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="construction-itsupport.png" alt="future_work" class="h-[55vh] mx-auto my-[3vh]">
					<figcaption>
						Bacon Ipsum Dolor Cheesecake.<br>
						Pizza? You mean "yum-yum in my tum-tum"! :D
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Future Work
		</Notes>
	</Slide>


	<!-- Appendix ####################################################### -->
	<script>newChapter("Appendix");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Appendix
			</titlebar>

			<mybody>
				<div class="w-full h-[1000px] bg-gray-700"> <!-- Main Panel Bottom-->
					<iframe src="2024-ESSV-Schuler_Nayak_Saha_Baumann-CanWeSeeYourResponseBeforeYouSpeak.pdf#page=1&zoom=80" frameBorder="0" scrolling="auto" height="100%" width="100%" title="Documentation"></iframe>
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			Appendix
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
		/* caption{
			caption-side: bottom;
			padding: 10px;
			font-weight: bold;
		} */
		table{
			border-collapse: collapse;
			border: 2px solid rgb(140,140,140);
			font-family: sans-serif;
			font-size: 2.8rem;
			letter-spacing: 1px;
		}
		tablecaption{
			caption-side: bottom;
			background-color: rgb(192,242,202);
			color: black;
			font-style: italic;
			padding: 2px;
			text-align: center;
		} 
	</style>
</Presentation>
