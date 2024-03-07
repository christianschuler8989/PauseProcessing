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
	<!-- <Slide>
		<script>
			toc=true; // decides whether to generate table of content page
		</script>
		<Layout>
			<toc class="flex h-full items-center justify-center gap-[100px]">
				<chpicons> </chpicons>
				<chpnames class="text-left"> </chpnames>
			</toc>
		</Layout>
	</Slide> -->

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
					<figure class="h-[55vh] w-[20vw] float-left mx-auto my-auto">
						<img src="Christian_Schuler_01_Lecturing.jpg" alt="christian" class="h-[40vh]">
						<figcaption class="text-[2.3vh]">
							Master student in computer science at University of Hamburg.
						</figcaption>
						<figcaption class="text-[1.3vh]">
							With a passion for languages and colors, he aims to do a PhD. <br>Additionally, he eats more pizza in one year than any of you in your lifetime!
						</figcaption>
					</figure>
					<figure class="h-[55vh] w-[20vw] float-left mx-auto my-auto">
						<img src="Shravan_Nayak_github.jpeg" alt="shravan" class="h-[40vh]">
						<figcaption class="text-[2.3vh]">
							Master student in computer science at Mila and the University of Montreal.
						</figcaption>
						<figcaption class="text-[1.3vh]">
							His focus lies in developing vision language systems that transcend linguistic barriers and cater to diverse demographics.
						</figcaption>
					</figure>
					<figure class="h-[55vh] w-[20vw] float-left mx-auto my-auto">
						<img src="Debjoy_Saha_Googlescholar.jpeg" alt="debjoy" class="h-[40vh]">
						<figcaption class="text-[2.3vh]">
							B.Tech (Electronics) and M.Tech (Computer Science) student at IIT Kharagpur.
						</figcaption>
						<figcaption class="text-[1.3vh]">
							Broadly, his research interests lie in machine learning for image, language and speech processing.
						</figcaption>
					</figure>
					<figure class="h-[55vh] w-[20vw] float-left mx-auto my-auto">
						<img src="Timo_Baumann_01.jpg" alt="timo" class="h-[40vh]">
						<figcaption class="text-[2.3vh]">
							Professor in AI and NLP at the School for CS and Maths at OTH Regensburg.
						</figcaption>
						<figcaption class="text-[1.3vh]">
							He researches spoken language, in particular in interactive and multi-modal scenarios, such as in spoken dialogue systems.
						</figcaption>
					</figure>
					
					<figure class="flex h-[12vh] w-[20vw] items-center justify-center mx-auto my-auto">
						<img src="UHH_Universität_Hamburg_Logo_mit_Schrift_2010_Farbe_CMYK.svg.png" alt="christian_hamburg" class="h-[10vh]">
					</figure>
					<figure class="flex h-[12vh] w-[20vw] items-center justify-center mx-auto my-auto">
						<img src="250px-Universite_de_Montreal_logo.svg.png" alt="shravan_montreal" class="h-[10vh]">
					</figure>
					<figure class="flex h-[12vh] w-[20vw] items-center justify-center mx-auto my-auto">
						<img src="IIT_Kharagpur_Logo.svg.png" alt="debjoy_kharagpur" class="h-[10vh]">
					</figure>
					<figure class="flex h-[12vh] w-[20vw] items-center justify-center mx-auto my-auto">
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
				Motivation - Why Pauses?
			</titlebar>

			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto;">
					<video controls class="w-[68vw] h-[75vh] mx-auto my-auto" autoplay>
						<source src="motivation_speech.mp4" type="video/mp4" />
						<track kind="captions" label="english_captions" srclang="en" src="captions_motivation_speech.vtt" default/>
					</video>
			
					<div class="flex w-[95vw] text-[2vh] mx-auto my-auto items-center justify-center">
						Someone talking - scene from the show Westworld (2016).
					</div>
				</div>
			</mybody>
		</Layout>
		<Notes>
			Why even look into pauses, where nothing happens?
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Motivation - Why Pauses?
			</titlebar>

			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto;">
					<video controls class="w-[68vw] h-[75vh] mx-auto my-auto" autoplay loop >
						<source src="motivation_pause.mp4" type="video/mp4" />
						<track kind="captions" label="english_captions" srclang="en" src="captions_motivation_pause_empty.vtt" default/>
					</video>
			
					<div class="flex w-[95vw] text-[2vh] mx-auto my-auto items-center justify-center">
						Someone pausing - scene from the show Westworld (2016).
					</div>
				</div>
			</mybody>
		</Layout>
		<Notes>
			
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Motivation - Why Pauses?
			</titlebar>

			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto;">
					<video controls class="w-[68vw] h-[75vh] mx-auto my-auto" autoplay loop >
						<source src="motivation_pause_slow.mp4" type="video/mp4" />
						<track kind="captions" label="english_captions" srclang="en" src="captions_motivation_pause_full.vtt" default/>
					</video>
			
					<div class="flex w-[95vw] text-[2vh] mx-auto my-auto items-center justify-center">
						Slowed down - scene from the show Westworld (2016).
					</div>
				</div>
			</mybody>
		</Layout>
		<Notes>
			
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Hypothesis
			</titlebar>

			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto; p-5">
					<div class="flex w-[95vw] text-[4vh] items-center justify-center gap-[5px] p-2">
						We hypothesise that pausing behaviour in dialogue holds information that is helpful to predict subsequent interactional behaviour.
						<br>
						<br>
						The content of one's upcoming utterance might be reflected in the face while pondering and constructing a response.
					</div>
					<br>
					<figure class="w-80vw] float-left mx-auto my-auto">
						<img src="PauseProcessingLargeImages-DataPausesMerkelSmallPredict.png" alt="virtual" class="w-[75vw] h-[25vw] mx-auto my-[1vh]">
						<figcaption class="text-[3vh]">
							Can we detect linguistic information hidden in the video sequence during a pause?
						</figcaption>
					</figure>
				</div>
			</mybody>
		</Layout>
		<Notes>
			What is it, that we are trying to do / to find?
		</Notes>
	</Slide>
<!-- 
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Goal
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
			What is it, that we are trying to do?
		</Notes>
	</Slide> -->


	<!-- Methodology ####################################################### -->
	<script>newChapter("Methodology & Experiment");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Methodology
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="PauseProcessing-DataPauses.png" alt="virtual" class="w-[75vw] mx-auto my-[3vh]">
					<figcaption>
						Overview of our experiment setup.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Genral overview of our experiment setup for first word prediction and discriminator training.
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Methodology - What is inside of a Video?
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="PauseProcessing-ExperimentSetupVideo.png" alt="virtual" class="w-[85vw] mx-auto my-[3vh]">
					<figcaption>
						Video processing of pause contents.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			What we did to the video data of each pause we investigated.
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Methodology - Two Approaches
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="PauseProcessing-ExperimentSetupText.png" alt="virtual" class="w-[85vw] mx-auto my-[3vh]">
					<figcaption>
						Predicting the first word versus matching pairs of pause and response.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			We assess our hypothesis with two kinds of experiments: <br> <br>
			1. We train a classifier to predict the first word of the utterance based on a representation
			of the pause video. If this model outperforms the unigram perplexity, there must be
			information in the pause.<br> <br>
			2. We design a discriminator that estimates whether a pause video and utterance form a pair
			or not; we train this discriminator using contrastive learning. If this model is able to predict
			pairings with better-than-random performance, there must be information in the pause.
			
		</Notes>
	</Slide>





	<!-- Experiment #######################################################
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
	</Slide> -->


	<!-- Data ####################################################### --> 
	<script>newChapter("Data");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data from the Merkel Podcast Corpus
			</titlebar>

			<mybody>

				<div class="grid h-[75vh]" style="grid-template-columns: auto; p-2">
					<figure class="h-[38vh] w-[95vw] float-left mx-auto my-auto">
						<a href="https://github.com/deeplsd/Merkel-Podcast-Corpus" target="_blank" rel="noopener noreferrer">
							<img src="merkel_podcast_corpus_title.jpg" alt="merkel_podcast_corpus" class="w-[95vw] mx-auto my-[1vh]">
						</a>
						<figcaption>
							The corpus is split roughly equally between (semi-)prepared speeches and interview dialogues.<br>
							630 videos totalling 48.0 hours of which 2.8 hours are short silences.
						</figcaption>
					</figure>
	
					<figure class="h-[30vh] w-[95vw] float-left mx-auto my-auto">
						<img src="PauseProcessingLargeImages-DataPausesMerkel.png" alt="data_quality" class="w-[95vw] mx-auto my-[1vh]">
						<figcaption>
							Data example of a pause sequence and surrounding video sequences.
						</figcaption>
					</figure>
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

	<!-- <Slide>
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
	</Slide> -->

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data for Annotation - Naive
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="PauseProcessing-AnnotationSetupNaive.png" alt="annotation_setup" class="h-[65vh] mx-auto my-[1vh]">
					<figcaption>
						Single image shortly prior and after pause.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			By looking at the images right before and after the pause, we now know who is visible at these times.
		</Notes>
	</Slide>


	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data for Annotation - Surprises
			</titlebar>
			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto;">
					<video controls class="w-[68vw] h-[75vh] mx-auto my-auto">
						<source src="ESSV-01-padded.mp4" type="video/mp4" /> <!-- cropped_2011-07-23_083-07_084-45.mp4 -->
						<track kind="captions" label="english_captions" srclang="en" src="captions_pause.vtt"/>
					</video>
			
					<!-- <div class="flex w-[22vw] mx-auto my-auto gap-[100px]">
						subtitle position
					</div> -->
				</div>
			</mybody>
		</Layout>
		<Notes>
			Taking short video sequences instead, we are now able to tell, who is the one speaking at these times.
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data for Annotation - Optimistic
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="PauseProcessing-AnnotationSetupOptimist.png" alt="annotation_setup" class="h-[65vh] mx-auto my-[1vh]">
					<figcaption>
						Short video prior and after pause.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			Taking short video sequences instead, we are now able to tell, who is the one speaking at these times.
		</Notes>
	</Slide>
	
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Data for Annotation - Necessary
			</titlebar>

			<mybody>
				<figure class="h-[75vh] w-[95vw] float-left mx-auto my-auto">
					<img src="PauseProcessing-AnnotationSetup.png" alt="annotation_setup" class="h-[65vh] mx-auto my-[1vh]">
					<figcaption>
						Short videos every few seconds from all around the pause.
					</figcaption>
				</figure>
			</mybody>
			
		</Layout>
		<Notes>
			This provides a more comprehensive overview of who is speaking and who is visible at what times- resulting in a better understanding of the scene's context in which the pause is located.
		</Notes>
	</Slide>





	<!-- Results & Discussion ####################################################### -->
	<script>newChapter("Results & Discussion");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Results & Discussion
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

	<!-- <Slide>
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
	</Slide> -->


	<!-- Conclusions & Future Work ####################################################### -->
	<script>newChapter("Conclusions & Future Work");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Conclusions
			</titlebar>

			<mybody>
				<ol>
					<li>(1.) Expand annotation for the Merkel Podcast Corpus</li>
					<br>
					<li>(2.) Propose workflow for pause annotation</li>
					<br>
					<li>(3.) Present first assessment of pause content information</li>
				</ol> 
			</mybody>
			
		</Layout>
		<Notes>
			Our contribution in three parts
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Future Work - Starting Ealier
			</titlebar>

			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto;">
					<video controls class="w-[68vw] h-[75vh] mx-auto my-auto">
						<source src="ESSV-14-padded.mp4" type="video/mp4" />
						<track kind="captions" label="english_captions" srclang="en" src="captions_pause.vtt"/>
					</video>

					<!-- <div class="flex w-[22vw] mx-auto my-auto gap-[100px]">
						subtitle position
					</div> -->
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			Expand into time of question asking?
		</Notes>
	</Slide>


	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Future Work - What about Humans?
			</titlebar>

			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto;">
					<video controls class="w-[68vw] h-[75vh] mx-auto my-auto">
						<source src="ESSV-02-padded_prior.mp4" type="video/mp4" />
						<track kind="captions" label="english_captions" srclang="en" src="captions_pause.vtt"/>
					</video>
			
					<!-- <div class="flex w-[22vw] mx-auto my-auto gap-[100px]">
						subtitle position
					</div> -->
				</div>
			</mybody>
		</Layout>
		<Notes>
			Could you do it?
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Future Work - Can you predict her Response?
			</titlebar>

			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto;">
					<video controls class="w-[68vw] h-[75vh] mx-auto my-auto" autoplay loop muted>
						<source src="ESSV-02.mp4" type="video/mp4" />
						<track kind="captions" label="english_captions" srclang="en" src="captions_pause.vtt"/>
					</video>
			
					<!-- <div class="flex w-[22vw] mx-auto my-auto gap-[100px]">
						subtitle position
					</div> -->
				</div>
			</mybody>
		</Layout>
		<Notes>
			Could you do it?
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Future Work - How close was your Guess?
			</titlebar>

			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto;">
					<video controls class="w-[68vw] h-[75vh] mx-auto my-auto">
						<source src="ESSV-02-padded_post.mp4" type="video/mp4" />
						<track kind="captions" label="english_captions" srclang="en" src="captions_pause.vtt"/>
					</video>
			
					<!-- <div class="flex w-[22vw] mx-auto my-auto gap-[100px]">
						subtitle position
					</div> -->
				</div>
			</mybody>
		</Layout>
		<Notes>
			Could you do it?
		</Notes>
	</Slide>



	<!-- Appendix ####################################################### -->
	<script>newChapter("Appendix");</script>
	<Slide>
		<Layout>
			<titlebar style="display:block;">
				References
			</titlebar>

			<mybody>
				<div class="flex w-[95vw] text-[1.5vh] items-center justify-center gap-[5px] p-2">
					<ul>
						<li>[1] SHILLINGFORD, B., Y. ASSAEL, M. W. HOFFMAN, T. PAINE, C. HUGHES, U. PRABHU, H. LIAO, H. SAK, K. RAO, L. BENNETT, M. MULVILLE, B. COPPIN, B. LAURIE, A. SENIOR, and N. DE FREITAS: Large-scale visual speech recognition. 2018. 1807. 05162.</li>
						<li>[2] CHATZIAGAPI, A., D. SGOUROPOULOS, C. KAROUZOS, T. MELISTAS, T. GIANNAKOPOULOS, A. KATSAMANIS, and S. NARAYANAN: Audio and ASR-based Filled Pause Detection. In 2022 10th International Conference on Affective Computing and Intelligent Interaction (ACII), pp. 1–7. IEEE, Nara, Japan, 2022. doi:10.1109/ACII55700.2022.9953889.</li>
						<li>[3] KALIYEV, A., S. V. RYBIN, and Y. MATVEEV: The Pausing Method Based on Brown Clustering and Word Embedding. In A. KARPOV, R. POTAPOVA, and I. MPORAS (eds.), Speech and Computer, Lecture Notes in Computer Science, pp. 741–747. Springer International Publishing, Cham, 2017. doi:10.1007/978-3-319-66429-3_74.</li>
						<li>[4] MATSUNAGA, Y., T. SAEKI, S. TAKAMICHI, and H. SARUWATARI: Improving robustness of spontaneous speech synthesis with linguistic speech regularization and pseudo-filled-pause insertion. In 12th Speech Synthesis Workshop (SSW) 2023. 2023.</li>
						<li>[5] DENDUKURI, S., P. CHITKARA, J. R. A. MONIZ, X. YANG, M. TSAGKIAS, and S. PULMAN: Using Pause Information for More Accurate Entity Recognition. In Proceedings of the 3rd Workshop on Natural Language Processing for Conversational AI, pp. 243–250. Associ- ation for Computational Linguistics, Online, 2021. doi:10.18653/v1/2021.nlp4convai-1.22.</li>
						<li>[6] SCHLANGEN, D., T. BAUMANN, and M. ATTERER: Incremental Reference Resolution: The Task, Metrics for Evaluation, and a Bayesian Filtering Model that is Sensitive to Disfluencies. Proceedings of SIGDIAL 2009:, 10th(0th Annual Meeting of the Special Interest Group in Discourse and Dialogue), pp. 30–37, 2009.</li>
						<li>[7] YANG, D., T. KORIYAMA, Y. SAITO, T. SAEKI, D. XIN, and H. SARUWATARI: Duration-aware pause insertion using pre-trained language model for multi-speaker text-to-speech. 2023. doi:10.48550/arXiv.2302.13652. 2302.13652.</li>
						<li>[8] HOOGLAND, D., L. WHITE, and S. KNIGHT: Speech Rate and Turn-Transition Pause Duration in Dutch and English Spontaneous Question-Answer Sequences. Languages, 8(2), p. 115, 2023. doi:10.3390/languages8020115.</li>
						<li>[9] SCHETTINO, L., M. D. MARO, and F. CUTUGNO: Silent pauses as clarification trigger. Laughter and Other Non-Verbal Vocalisations Workshop: Proceedings (2020), 2020. doi:10.4119/lw2020-927. [10] BAUMANN, T.: How a Listener Influences the Speaker. In Proc. Speech Prosody 2020, pp. 970–974. 2020. doi:10.21437/SpeechProsody.2020-198.</li>
						<li>[11] KOUTSOMBOGERA, M. and C. VOGEL: Speech Pause Patterns in Collaborative Dialogs. In A. ESPOSITO, A. M. ESPOSITO, and L. C. JAIN (eds.), Innovations in Big Data Mining and Embedded Knowledge, Intelligent Systems Reference Library, pp. 99–115. Springer International Publishing, Cham, 2019. doi:10.1007/978-3-030-15939-9_6.</li>
						<li>[12] MATZINGER, T., M. PLEYER, and P. ˙ZYWICZY ´NSKI: Pause Length and Differences in Cognitive State Attribution in Native and Non-Native Speakers. Languages, 8(1), p. 26, 2023. doi:10.3390/languages8010026.</li>
						<li>[13] LIU, J., F. FU, L. LI, J. YU, D. ZHONG, S. ZHU, Y. ZHOU, B. LIU, and J. LI: Efficient Pause Extraction and Encode Strategy for Alzheimer’s Disease Detection Using Only Acoustic Features from Spontaneous Speech. Brain Sciences, 13(3), p. 477, 2023. doi:10.3390/brainsci13030477.</li>
						<li>[14] GREDEN, J. F., A. A. ALBALA, I. A. SMOKLER, R. GARDNER, and B. J. CARROLL: Speech pause time: A marker of psychomotor retardation among endogenous depressives. Biological Psychiatry, 16(9), pp. 851–859, 1981.</li>
						<li>[15] ADDLESEE, A., A. ESHGHI, and I. KONSTAS: Current Challenges in Spoken Dialogue Systems and Why They Are Critical for Those Living with Dementia. 2019. doi:10.48550/arXiv.1909.06644. 1909.06644. </li>
						<li>[16] SAHA, D., S. NAYAK, and T. BAUMANN: Merkel Podcast Corpus: A Multimodal Dataset Compiled from 16 Years of Angela Merkel’s Weekly Video Podcasts. In N. CALZOLARI, F. BÉCHET, P. BLACHE, K. CHOUKRI, C. CIERI, T. DECLERCK, S. GOGGI, H. ISAHARA, B. MAEGAARD, J. MARIANI, H. MAZO, J. ODIJK, and S. PIPERIDIS (eds.), Proceed- ings of the Thirteenth Language Resources and Evaluation Conference, pp. 2536–2540. European Language Resources Association, Marseille, France, 2022.</li>
						<li>[17] BALTRUSAITIS, T., A. ZADEH, Y. C. LIM, and L.-P. MORENCY: OpenFace 2.0: Facial Behavior Analysis Toolkit. In 2018 13th IEEE International Conference on Automatic Face & Gesture Recognition (FG 2018), pp. 59–66. 2018. doi:10.1109/FG.2018.00019.</li>
						<li>[18] RADFORD, A., J. W. KIM, C. HALLACY, A. RAMESH, G. GOH, S. AGARWAL, G. SAS- TRY, A. ASKELL, P. MISHKIN, J. CLARK, G. KRUEGER, and I. SUTSKEVER: Learning transferable visual models from natural language supervision. 2021. 2103.00020.</li>
						<li>[19] BERTASIUS, G., H. WANG, and L. TORRESANI: Is space-time attention all you need for video understanding? 2021. 2102.05095.</li>
						<li>[20] VASWANI, A., N. M. SHAZEER, N. PARMAR, J. USZKOREIT, L. JONES, A. N. GOMEZ, L. KAISER, and I. POLOSUKHIN: Attention is all you need. In Neural Information Process- ing Systems. 2017. URL https://api.semanticscholar.org/CorpusID:13756489.</li>
						<li>[21] REIMERS, N. and I. GUREVYCH: Making Monolingual Sentence Embeddings Multilingual using Knowledge Distillation. In Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP), pp. 4512–4525. Association for Computational Linguistics, Online, 2020. doi:10.18653/v1/2020.emnlp-main.365.</li>
						<li>[22] PEI, J., A. ANANTHASUBRAMANIAM, X. WANG, N. ZHOU, A. DEDELOUDIS, J. SAR-GENT, and D. JURGENS: Potato: The portable text annotation tool. In Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing: System Demonstrations. 2022.</li>
					</ul>
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			References
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Our Paper
			</titlebar>

			<mybody>
				<div class="h-[75vh] w-[95vw]">
					<iframe src="2024-ESSV-Schuler_Nayak_Saha_Baumann-CanWeSeeYourResponseBeforeYouSpeak.pdf#page=1&zoom=150" frameBorder="0" scrolling="auto" height="100%" width="100%" title="ESSV Publication"></iframe>
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			Our Paper
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Response Contents
			</titlebar>

			<mybody>
				<div class="flex w-[95vw] items-center justify-center gap-[5px] p-2">
				<figure>
					<table class="text-[1.5vh]">
						<tr>
						<td>"Wir": 72</td>
						<td>"Die": 49</td>
						<td>"Ich": 41</td>
						<td>"Und": 38</td>
						<td>"Das": 37</td>
						<td>"Es": 23</td>
						<td>"Deshalb": 17</td>
						<td>"Liebe": 17</td>
						<td>"Sie": 16</td>
						<td>"Aber": 14</td> </tr><tr>
						<td>"Deutschland": 14</td>
						<td>"Auch": 14</td>
						<td>"In": 14</td>
						<td>"Im": 11</td>
						<td>"Der": 10</td>
						<td>"Ein": 10</td>
						<td>"Ja": 10</td>
						<td>"Dazu": 9</td>
						<td>"Diese": 8</td>
						<td>"Denn": 8</td> </tr><tr>
						<td>"Europa": 8</td>
						<td>"Heute": 7</td>
						<td>"Dabei": 7</td>
						<td>"Wie": 7</td>
						<td>"Unsere": 6</td>
						<td>"Eine": 6</td>
						<td>"Viele": 5</td>
						<td>"Für": 5</td>
						<td>"Doch": 5</td>
						<td>"Bei": 5</td> </tr><tr>
						<td>"Was": 5</td>
						<td>"Dies": 5</td>
						<td>"So": 5</td>
						<td>"Vor": 4</td>
						<td>"Zum": 4</td>
						<td>"Mit": 4</td>
						<td>"An": 3</td>
						<td>"Überraschen": 3</td>
						<td>"Da": 3</td>
						<td>"Allerdings": 3</td> </tr><tr>
						<td>"Am": 3</td>
						<td>"Unser": 3</td>
						<td>"Damit": 3</td>
						<td>"Manche": 3</td>
						<td>"Genau": 3</td>
						<td>"Lassen": 3</td>
						<td>"Zu": 3</td>
						<td>"Um": 3</td>
						<td>"Also": 3</td>
						<td>"Jetzt": 2</td> </tr><tr>
						<td>"Wer": 2</td>
						<td>"Natürlich": 2</td>
						<td>"Schon": 2</td>
						<td>"Von": 2</td>
						<td>"Dieser": 2</td>
						<td>"Noch": 2</td>
						<td>"Nur": 2</td>
						<td>"Jeder": 2</td>
						<td>"Nachwachsende": 2</td>
						<td>"Ganz": 2</td> </tr><tr>
						<td>"Inzwischen": 2</td>
						<td>"Vielleicht": 2</td>
						<td>"Nun": 2</td>
						<td>"Anschließend": 2</td>
						<td>"Gleichzeitig": 2</td>
						<td>"Mein": 2</td>
						<td>"Beides": 2</td>
						<td>"Ihnen": 2</td>
						<td>"Ludwig": 2</td>
						<td>"Dem": 2</td> </tr><tr>
						<td>"Insbesondere": 2</td>
						<td>"Dennoch": 2</td>
						<td>"Mir": 2</td>
						<td>"Gelingen": 2</td>
						<td>"Dafür": 2</td>
						<td>"Wenn": 2</td>
						<td>"Sicherlich": 2</td>
						<td>"2014": 2</td>
						<td>"aber": 2</td>
						<td>"die": 2</td> </tr><tr>
						<td>"und": 2</td>
						<td>"following_sentence": 1</td>
						<td>"Zweitens": 1</td>
						<td>"Drittens": 1</td>
						<td>"Viertens": 1</td>
						<td>"Während": 1</td>
						<td>"Videoüberwachung": 1</td>
						<td>"Music": 1</td>
						<td>"Zehn": 1</td>
						<td>"Zur": 1</td> </tr><tr>
						<td>"Ausgangspunkt": 1</td>
						<td>"212": 1</td>
						<td>"Verantwortung": 1</td>
						<td>"Schicksale": 1</td>
						<td>"Fassungslos": 1</td>
						<td>"Holz": 1</td>
						<td>"Kann": 1</td>
						<td>"Womit": 1</td>
						<td>"Durch": 1</td>
						<td>"Warum": 1</td> </tr><tr>
						<td>"Einige": 1</td>
						<td>"Voriges": 1</td>
						<td>"Energieversorgung": 1</td>
						<td>"Sehen": 1</td>
						<td>"Mittelständische": 1</td>
						<td>"Normalerweise": 1</td>
						<td>"Dass": 1</td>
						<td>"All": 1</td>
						<td>"Wahr": 1</td>
						<td>"Andere": 1</td> </tr><tr>
						<td>"Man": 1</td>
						<td>"Oder": 1</td>
						<td>"Seien": 1</td>
						<td>"Dieses": 1</td>
						<td>"Insgesamt": 1</td>
						<td>"Glücklicherweise": 1</td>
						<td>"Seit": 1</td>
						<td>"everything": 1</td>
						<td>"Beide": 1</td>
						<td>"Menschenrechte": 1</td> </tr><tr>
						<td>"Mich": 1</td>
						<td>"Eines": 1</td>
						<td>"Alle": 1</td>
						<td>"Bund": 1</td>
						<td>"Erinnern": 1</td>
						<td>"1973": 1</td>
						<td>"Gemessen": 1</td>
						<td>"Darüber": 1</td>
						<td>"Meine": 1</td>
						<td>"Märkte": 1</td> </tr><tr>
						<td>"Opel": 1</td>
						<td>"Ob": 1</td>
						<td>"Audi": 1</td>
						<td>"Manch": 1</td>
						<td>"Politisch": 1</td>
						<td>"wie": 1</td>
						<td>"2010": 1</td>
						<td>"Davon": 1</td>
						<td>"Export": 1</td>
						<td>"Lithuania": 1</td> </tr><tr>
						<td>"Nach": 1</td>
						<td>"Montag": 1</td>
						<td>"Eingesetzt": 1</td>
						<td>"Will": 1</td>
						<td>"Entstanden": 1</td>
						<td>"oder": 1</td>
						<td>"Slowenien": 1</td>
						<td>"Auf": 1</td>
						<td>"Wahrscheinlich": 1</td>
						<td>"Damals": 1</td> </tr><tr>
						<td>"Opfer": 1</td>
						<td>"Osama": 1</td>
						<td>"Religion": 1</td>
						<td>"Jüngst": 1</td>
						<td>"2011": 1</td>
						<td>"Hier": 1</td>
						<td>"Trotz": 1</td>
						<td>"wo": 1</td>
						<td>"Seitdem": 1</td>
						<td>"Voraussetzung": 1</td> </tr><tr>
						<td>"Blicken": 1</td>
						<td>"Dann": 1</td>
						<td>"ist": 1</td>
						<td>"Brauchen": 1</td>
						<td>"Denken": 1</td>
						<td>"Zuversicht": 1</td>
						<td>"Weil": 1</td>
						<td>"Unternehmen": 1</td>
						<td>"Gerade": 1</td>
						<td>"Besonders": 1</td> </tr><tr>
						<td>"also": 1</td>
						<td>"vergleichbarer": 1</td>
						<td>"Kraft": 1</td>
						<td>"Jugend": 1</td>
						<td>"Kürzlich": 1</td>
						<td>"Übrigens": 1</td>
						<td>"Diesen": 1</td>
						<td>"Den": 1</td>
						<td>"Freiheit": 1</td>
						<td>"Ebenso": 1</td> </tr><tr>
						<td>"Ist": 1</td>
						<td>"National": 1</td>
						<td>"International": 1</td>
						<td>"Beim": 1</td>
						<td>"Einerseits": 1</td>
						<td>"Bürokratieabbau": 1</td>
						<td>"Reisen": 1</td>
						<td>"2016": 1</td>
						<td>"Indem": 1</td>
						<td>"Wo": 1</td> </tr><tr>
						<td>"2017": 1</td>
						<td>"Mut": 1</td>
						<td>"Zusammenhalt": 1</td>
						<td>"Keiner": 1</td>
						<td>"Stichwort": 1</td>
						<td>"alle": 1</td>
						<td>"Nein": 1</td>
						<td>"Diesem": 1</td>
						<td>"den": 1</td>
						<td>"eine": 1</td> </tr><tr>
						<td>"Anfang": 1</td>
						<td>"Geradezu": 1</td>
						<td>"Andererseits": 1</td>
						<td>"Gewissheiten": 1</td>
						<td>"Millionen": 1</td>
						<td>"genau": 1</td>
						<td>"Immer": 1</td>
						</tr>
						</table>
					<figcaption>
						Frequencies of First Words.
					</figcaption>
				</figure>
			</div>
			</mybody>
			
		</Layout>
		<Notes>
			Response contents
		</Notes>
	</Slide>
	

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Annotation Label Legend 
			</titlebar>

			<mybody>
				<div class="flex w-[95vw] text-[3vh] items-center justify-center gap-[5px] p-2">
					<ul>
						<li>m - Merkel</li>
						<li>n - No Merkel visible</li>
						<li>a - animation transition</li>
						<li>i - interviewer</li>
						<li>t - textlabel</li>
						<li>c - cut changing distance towards Merkel</li>
						<li>o - cut changing distance away from Merkel</li>
						<li>si - switch from Merkel to Interviewer</li>
						<li>sm - switch from Interviewer to Merkel</li>
						<li>b - both people in frame front of Merkel</li>
						<li>p - both people in frame front of Interviewer</li>
						<li>r - sign-language translator on the right side of screen</li>
						<li>l - sign-language translator on the left side of screen</li>
						<li>fi - fade-in (Merkel is visible at end of pause)</li>
						<li>fo - fade-out (Merkel is visible at begin of pause)</li>
					</ul>
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			Annotation Label Legend
		</Notes>
	</Slide>
	

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Future Work - With a Wink I
			</titlebar>

			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto;">
					<video controls class="w-[68vw] h-[75vh] mx-auto my-auto">
						<source src="cropped_2017-08-26_264-51_265-68_ESSV.mp4" type="video/mp4" />
						<track kind="captions" label="english_captions" srclang="en" src="captions_pause.vtt"/>
					</video>

					<!-- <div class="flex w-[22vw] mx-auto my-auto gap-[100px]">
						subtitle position
					</div> -->
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			Future Work with a Wink: Can we even estimate the next question going to be asked?
		</Notes>
	</Slide>

	<Slide>
		<Layout>
			<titlebar style="display:block;">
				Future Work - With a Wink II
			</titlebar>

			<mybody>
				<div class="grid mx-auto my-auto" style="grid-template-columns: auto;">
					<video controls class="w-[68vw] h-[75vh] mx-auto my-auto">
						<source src="cropped_2017-12-02_274-08_275-52_ESSV.mp4" type="video/mp4" />
						<track kind="captions" label="english_captions" srclang="en" src="captions_pause.vtt"/>
					</video>

					<!-- <div class="flex w-[22vw] mx-auto my-auto gap-[100px]">
						subtitle position
					</div> -->
				</div>
			</mybody>
			
		</Layout>
		<Notes>
			Future Work with a Wink: Can we even estimate the next question going to be asked?
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
			margin-left:2vh;
			margin-right:5vh;
		}
		li{
			text-align: left;
			padding-top:0.5vh;
		}
		titlebar{
			display:flex;
			background: var(--titlebarbackground); 
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
			background-color: var(--figcaptionbackground);
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
		video{
			width: 90vw;
		}
	</style>
</Presentation>


<!--
Merkel Video Snippets for ESSV Presentation

	# Back and forth (Camera and Turn)
ESSV-01.mp4 - cropped_2011-07-23_083-07_084-45.mp4

	# Good examples
ESSV-02.mp4 - cropped_2011-07-23_103-89_104-49_ESSV.mp4
ESSV-03.mp4 - cropped_2013-01-19_073-98_074-52_ESSV.mp4
ESSV-04.mp4 - cropped_2013-01-19_227-97_228-66_ESSV.mp4
ESSV-05.mp4 - cropped_2014-03-22_173-58_174-18_ESSV.mp4
ESSV-06.mp4 - cropped_2014-06-07_080-46_081-21_ESSV.mp4
ESSV-07.mp4 - cropped_2014-06-07_017-73_018-63_ESSV.mp4

	# Lala
ESSV-08.mp4 - cropped_2014-05-31_028-47_029-25_ESSV.mp4

	# Problematic
ESSV-09.mp4 - cropped_2013-01-19_019-08_020-88_ESSV.mp4

	# Merkel turns interviewer
ESSV-10.mp4 - cropped_2014-05-03_068-01_068-85_ESSV.mp4

	# Useless crap
ESSV-11.mp4 - cropped_2017-08-19_024-18_024-75_ESSV.mp4
ESSV-12.mp4 - cropped_2019-01-19_057-00_057-81_ESSV.mp4
ESSV-13.mp4 - cropped_2019-01-02_257-91_259-41_ESSV.mp4

	# Future Work: Expand into time of question asking?
ESSV-14.mp4 - cropped_2017-08-26_291-48_292-23_ESSV.mp4

	# Future Future Work: "Can we estimate the next question?" XD
ESSV-15.mp4 - cropped_2017-08-26_264-51_265-68_ESSV.mp4
ESSV-16.mp4 - cropped_2017-12-02_274-08_275-52_ESSV.mp4

-->
