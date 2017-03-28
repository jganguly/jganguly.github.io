---
title: Machine Learning & the Grand Challenge
author: Jaideep Ganguly
---

{% include header.html %}

The Grand Challenge

In the previous article, we talked about the effectiveness of a particular deep learning algorithm, the [Long Short Term Memory (LSTM)](http://en.wikipedia.org/wiki/Long_short-term_memory) model that has been used quite successfully in a number of areas. While lots of applications using Machine Learning are being built here and there, in this article, I talk about a Grand Challenge for Machine Learning. Ever since [Watson](http://en.wikipedia.org/wiki/James_Watson) and [Crick](http://en.wikipedia.org/wiki/Francis_Crick) discovered the structure of the DNA, Protein Structure Prediction (PSP) is an open problem and of great importance in medicine and [drug design](http://en.wikipedia.org/wiki/Drug_design). It turns out that many diseases like [alzheimer](http://en.wikipedia.org/wiki/Alzheimer%27s_disease) and [cancer](http://en.wikipedia.org/wiki/Cancer) are due to misshapen protein folds. We will see later how genes in DNA encode instructions to make strings of amino acids which go on to fold and form proteins. Proteins must fold correctly to carry out their functions. Incidentally, of the 20 amino acids in our body's proteins, nine are essential to our diet because our cells cannot manufacture them.

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_01.png){:width="600px"}

</div>

The goal is to predict the 3D structure of a protein given its sequence of amino acids. Any scientist solving the problem would unquestionably win a Nobel prize. The human genome contains about 20,000 protein-encoding genes and possibly about 100,000 unique unique types of proteins within a typical human cell. A genome is an organism’s complete set of DNA including all its genes. A gene is a distinct sequence of nucleotides forming part of a chromosome. For most individual proteins, the 3D structure can be measured experimentally but it can cost about $1M per protein. The problem is, in theory, solvable using sequence learning techniques because physical experiments show that the DNA sequence contains enough information to determine the 3D structure. 

**Proteins are us! You are what you eat!**

Proteins do just about anything that you can think of in our body. Proteins are in muscles in arms and legs, proteins carry pigments in our eyes and when light strikes those pigments causing proteins to change shapes and send signals to our brain, proteins are in our stomach that receive the food and break it up to make new proteins. In short, proteins do just about everything in our Biology.

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_02.png){:width="300px"}

</div>


The solution is unquestionably of super importance to human well-being. Remember the phrase – “You are what you eat”. That’s because we eat food that contains proteins, we break these into amino acids and then, magically, our body weaves them back into proteins that make us. Chemically, proteins are microscopic molecules inside of cells that perform diverse and vital jobs. Very interestingly, it turns out that a protein’s function greatly depends on its shape, and when that protein formation goes bad, the resulting misshapen proteins cause wide ranging diseases. And this is why it is so important to understand protein's folding, i.e., its 3D shape.

**Computational Biology**

The 3D structure of a protein is determined largely by its amino acid sequence. However, it is extremely challenging to predict protein structure from sequence alone. Since protein structure is critical to analysis of its function and many applications like drug or enzyme design, understanding the complex sequence-structure relationship is one of the greatest challenges in computational biology. Accurate protein structure and function prediction relies, in part, on the accuracy of secondary structure (SS) prediction. Protein secondary structure refers to the local conformation of the polypeptide backbone of proteins. More than 60 years ago, [Linus Pauling](http://en.wikipedia.org/wiki/Linus_Pauling) suggested that there are two regular SS states - alpha-helix (H) and beta-strand (E), and one irregular SS type - coil region (C). The DSSP algorithm developed by Sander classifies SS into 8 fine-grained states - 3 types for helix, 2 types for strand, and 3 types for coil.  SS prediction is usually evaluated by Q3 or Q8 accuracy, which measures the percent of residues for which 3-state or 8-state secondary structure is correctly predicted. So far the best Q3 prediction is about 80% without templates.

**So what are proteins?**

Proteins are a class of nitrogenous organic compounds that consist of large molecules composed of one or more long chains of amino acids. They are an essential part of all living organisms, especially as structural components of body tissues such as muscle, hair, collagen as well as enzymes and antibodies. Proteins are the workhorses of the cell providing stiffness to muscles as well as to tiny neurons. Some work as transport agents by binding to molecules, some help as catalytic agents. It is the folding of proteins that enables it to do its diverse activities. The primary structure is a linear amino acid sequence which, chemically, is a polypeptide chain composed of amino acids joined by peptide bonds. Amino acids are simple organic compounds containing both a carboxyl (—COOH) and an amino (—NH2) group. The secondary structure is due to interactions that occur between the C, O, and NH groups on amino acids in a polypeptide chain to form α-helices, β-sheets, turns, loops, and other forms, and that facilitate the folding into a 3D structure. Structural similarity between proteins is a very good predictor of functional similarity.

**Cell, DNA and RNA**

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_03.png){:width="600px"}

</div>


The Eukaryotic cell, i.e, a cell with a nucleus, is a treasure trove of genetic information stored within its nucleus.

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_04.png){:width="600px"}

</div>

credit: Bosemanscience

The nucleus of the cell packs the double helix structured DNA, i.e., the Deoxyribonucleic acid that stores our genetic instructions, a 6 billion letter code that defines everything that we are! Watson and Crick is credited for discovering the double helix structure of the DNA which is made up of molecules that are basic structural units called nucleotides. Each nucleotide contains a phosphate group, a sugar group and a nitrogen base. The four types of nitrogen bases are Adenine (A), Thymine (T), Guanine (G) and Cytosine (C). The order of these bases is what determines DNA's instructions, or genetic code. DNA is a self-replicating material present in nearly all living organisms as the main constituent of chromosomes. It is the carrier of genetic information, the fundamental and distinctive characteristics of someone. During cell division, the paired strands unravel and each strand serves as the template for synthesis of a new complementary strand. 

**Transcription**

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_05.png){:width="600px"}

</div>

Transcription is the first step in decoding a cell's genetic information. During transcription, the DNA is unzipped into a leading strand and a lagging strand. A Primase, i.e., an enzyme (acts as a catalyst to bring about a biochemical reaction), creates a primer on a DNA strand by adding RNA nucleotides to the strand according to the DNA template sequence.  The primase generates short strands of RNA that bind to the single-stranded DNA to initiate DNA synthesis (replication) by the DNA polymerase. This enzyme can work only in the 5' to 3' direction, so it replicates the leading strand continuously. Lagging-strand replication is discontinuous, with short Okazaki fragments being formed and later linked together. The RNA molecules differ from DNA molecules in two important ways. They are single stranded and their sugar component is a ribose rather than a deoxyribose and they contain uracil (U) nucleotides instead of thymine (T) nucleotides.

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_06.png){:width="600px"}

</div>

credit: Bosemanscience

RNA or Ribonucleic acid, is a nucleic acid that is present in all living cells. Its principal role is to act as a messenger carrying instructions from DNA for controlling the synthesis of proteins (in some viruses RNA rather than DNA carries the genetic information). A transfer RNA (tRNA) is an adaptor molecule composed of RNA, typically 76 to 90 nucleotides in length, that serves as the physical link between the mRNA and the amino acid sequence of proteins. The transfer RNA brings the amino acids into the ribosome of the cell.

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_07.png){:width="600px"}

</div>

There are three general classes of RNA molecules involved in expressing the genes encoded within a cell's DNA. Messenger RNA (mRNA) molecules carry the coding sequences for protein synthesis and are called transcripts, ribosomal RNA (rRNA) molecules form the core of a cell's ribosomes (the structures in which protein synthesis takes place) and transfer RNA (tRNA) molecules carry amino acids to the ribosomes during protein synthesis. In eukaryotic cells, each class of RNA has its own polymerase. There are thousands of different mRNA molecules present in a cell at any given time. Some mRNA molecules number in thousands for encoding structural proteins while some are rare for signaling proteins. Their longevity spans from ten hours to less than ten minutes.

**Ribosomes**

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_08.png){:width="600px"}

</div>

Ribosomes are the sites in a cell in which protein synthesis takes place, i.e., bind messenger RNA and transfer RNA to synthesize polypeptides and proteins. Structurally, they are minute particles consisting of RNA and associated proteins, found in large numbers in the cytoplasm of living cells that are attached to the endoplasmic reticulum. Cells have many ribosomes, and the exact number depends on how active a particular cell is in synthesizing proteins. Within the ribosome, the rRNA molecules direct the catalytic steps of protein synthesis — the stitching together of amino acids to make a protein molecule. These are then sent to the Golgi apparatus, which are a complex of vesicles and folded membranes within the cytoplasm of most eukaryotic cells for intracellular transport.

Translation

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_09.png){:width="600px"}

</div>

After the transcription of DNA to mRNA is complete, translation, or the reading of these mRNAs to make proteins begins. Each mRNA decides the order in which amino acids should be added to a growing protein as it is synthesized. Every amino acid is represented by a three-nucleotide sequence or codon along the mRNA molecule. Codons are a sequence of three nucleotides that together form a unit of genetic code in a DNA or RNA molecule. Molecules of tRNA are responsible for matching amino acids with the appropriate codons in mRNA. Each tRNA molecule has two distinct ends, one of which binds to a specific amino acid, and the other which binds to the corresponding mRNA codon. During translation, these tRNAs carry amino acids to the ribosome and join with their complementary codons. Then, the assembled amino acids are joined together as the ribosome, with its resident rRNAs, moves along the mRNA molecule in a ratchet-like motion. The resulting protein chains can be hundreds of amino acids in length, and synthesizing these molecules requires a huge amount of chemical energy. In eukaryotic cells, the two processes are separated in both space and time; mRNAs are synthesized in the nucleus and proteins are later made in the cytoplasm.

**Protein Folding**

In all amino acids, we have a an alpha carbon in the middle, in the left there is an amino group and on the right there is a carboxyl group. Every amino acid have these in common, the only thing that differs is at the bottom and is called the R group. The amino acids line up through a dehydration synthesis, i.e, the OH and H combine to loose water and form a covalent bond. A chain of amino acids form to create what is called a polypeptide with the strand at the top being the same and only the bottom differs.

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_10.png){:width="600px"}

</div>

A protein starts off in the cell as a long chain of, on average, 300 building blocks of amino acids which is the primary structure. The 20 different types of amino acids, and their ordering determine how the protein chain will fold upon itself. When folding, two types of structures usually form first. Some regions of the protein chain coil up into slinky-like formations called “alpha helices,” while other regions fold into zigzag patterns called “beta sheets,” which resemble the folds of a paper fan. These are called secondary structures. These two structures can interact to form more complex structures called tertiary structures with the hydrophobic parts in the inside and the hydrophilic outside. Finally, there is the quaternary structure formed by combination of a number of subunits.

<div style="text-align:center" markdown="1">

![my photo]({{ site.url }}/assets/images/gc_11.png){:width="600px"}

</div>

In one protein structure, several beta sheets wrap around themselves to form a hollow tube with a few alpha helices jutting out from one end. The tube is short and squat such that the overall structure resembles snakes (alpha helices) emerging from a can (beta sheet tube). Protein structures with descriptive names include “beta barrel,” “beta propeller,” “alpha/beta horseshoe,” and “jelly-roll fold.” Proteins fold up rapidly in a hierarchical sequence by forming local secondary structures followed by consolidation of tertiary structures. The folding happens in a continuous and at a very high frequency, possibly a few million times per second.

**Summary**

As early as in 1958, Francis Creek stated the [Central Dogma](http://en.wikipedia.org/wiki/Central_dogma_of_molecular_biology) – “Once ‘information’ has passed into protein it cannot get out again. In more detail, the transfer of information from nucleic acid to nucleic acid, or from nucleic acid to protein may be possible, but transfer from protein to protein, or from protein to nucleic acid is impossible. Information means here the precise determination of sequence, either of bases in the nucleic acid or of amino acid residues in the protein”.

In summary, cellular DNA contains instructions for building the various proteins the cell needs to survive. In order for a cell to manufacture these proteins, specific genes within its DNA must first be transcribed into molecules of mRNA. Thereafter, these transcripts must be translated into chains of amino acids, which later fold into fully functional proteins and the folding largely defines the function of a protein. The grand challenge for machine learning is to apply the deep learning algorithms to predict the structural shape of proteins.


