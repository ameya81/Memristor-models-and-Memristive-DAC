# Memristor-models-and-Memristive-DAC
Memristor models and Memristive DAC
\documentclass[conference]{IEEEtran}
\IEEEoverridecommandlockouts
% The preceding line is only needed to identify funding in the first footnote. If that is unneeded, please comment it out.
\usepackage{cite}
\usepackage{amsmath,amssymb,amsfonts}
\usepackage{algorithmic}
\usepackage{graphicx}
\usepackage{textcomp}
\usepackage{xcolor}
\def\BibTeX{{\rm B\kern-.05em{\sc i\kern-.025em b}\kern-.08em
    T\kern-.1667em\lower.7ex\hbox{E}\kern-.125emX}}
\begin{document}

\title{Memristor based DAC (Digital to analog) converter}

\author{\IEEEauthorblockN{Ameya Milind Deshpande}
		\IEEEauthorblockA{\textit{Indian Institute Of Technology, Ropar} \\
			\textit{Department of Electrical Engineering}\\
			Ropar,Punjab\\
			2022eem1027@iitrpr.ac.in}
		\and
		\IEEEauthorblockN{Dr. Devarshi Das}
		\IEEEauthorblockA{\textit{Indian Institute Of Technology, Ropar} \\
			\textit{Department of Electrical Engineering}\\
				Ropar,Punjab\\
			devarshi.das@iitrpr.ac.in}
		\and
		
	}


\maketitle

\begin{abstract}
Memristor as an element have been discovered many years ago and have also be used in many applications.Memristor circuits also do have applications in in-memory computing.In this term paper, a Memristor base DAC is proposed.Memristor- based ADC's have lesser area,lesser power consumption and a lower threshold voltage than the CMOS ADC's.The basic DAC cell was used to make a 4-bit DAC and also 4-bit and 8-bit Thermometer code DAC's.the digital inputs are taken to be 1 V.The proposed designs were simulated in Cadence virtuoso using the VTEAM (Voltage threshold adaptive model) of the memristor.

\end{abstract}

\begin{IEEEkeywords}
component, formatting, style, styling, insert
\end{IEEEkeywords}

\section{Introduction}
The existence of memristor as a device characterized by the relation between Charge $q_{t}$ and flux linkage $\phi_{t}$ was discovered by Chua in \cite{b1}.This element is also being regarded as the fourth fundamental element linking flux linkages and charge.
In 2008, the existence of the memristor was proved by the team at Hewlett Packard(HP).\cite{b2}\par
\vspace{1 cm}
Nowadays there are numerous applications of memristors in neuromorphic electronics,memory design,ANN (Artificial neural networks) ,digital circuits due to its ability to retain memory.It is also being used in analog circuits like oscillators ,ADC's (Analog to digital converters) and DAC's(Digital to analog converters),etc as it has a comparatively lesser area as compared to the mosfets and also is faster than the traditional mosfet-based circuits.Also it is one of the major components in application of the In-Memory computer systems which do not follow the traditional Von-neumann architecture.In-memory architecture aims to execute some command sin the memory itself instead of carrying on the command to ALU (Arithmetic and logical unit) hence saving time as well as speed.\par
\vspace{1 cm}
A memristor is like a dual of the fundamental digital to analog conversion n as the Resistance of the memristors is high or low depending on the voltage applied across it.Recent research is aimed at reducing the area and power consumption of the DAC circuits and also enable DAC's supporting In-memory compute.A memristor based DAC aims to solve theses problems by using a memristor based DAC which has a comparatively lesser area as well as better speed than the mosfet-based DAC's.Though the deign of memristor- based circuits still face some problems like the sneak path problems .Some solutions to these problems like the 1T1M (1 transistor 1 memristor) ,1D1M (1 diode 1 memristor) and 1S1M(1 selector 1 memristor ) have been proposed in various papers.\cite{b7}\par


%----------------------------------------------------------------------------------------
% Literature review
%----------------------------------------------------------------------------------------

\section{Memristor Basics}
Numerous mathematical models have been developed by the researchers to model the behaviour of the memristor.Some of the well-known examples are Linear ion drift model,Non-linear ion drift model,Simmons tunnel barrier model,TEAM Model, VTEAM(voltage threshold adaptive memristor) Model,Stanford pku RRAM model,etc\cite{b6}.Here, we have used the VTEAM model to model the behaviour of the memristor.It accurately depicts the non-linear switching characteristics of the memristor.\par
\vspace{0.3 cm}
The VTEAM Model displayed adequate accuracy compared to the existing model and also included the threshold voltage necessary to fulfil these experimental findings which was not included in the earlier models.Figure 1 depicts the ideal I-V curve for memristors. The memristor element changes from the off-state to the on-state when the applied voltage exceeds +Vth. The memristor element transitions from the off-state to the on-state when the applied voltage falls below -Vth.\par
\vspace{0.3 cm}
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.45]{figure/mem.png}}
	\caption{Ideal I-V characteristics of the memristor}
	\label{fig1}
    \end{figure}
\vspace{0.5 cm} 

\subsection{VTEAM model setup and characteristics}
Here, we will be using the VTEAM model of the memristor to test the characteristics of the device. Figure “n” shows the setup to test the memristor characteristics. The parameters of the VTEAM model used here are $R_{on}$=50 \Mho  , $R_{off}$=1000 \Mho ,$V_{on}$=-0.2 V, $V_{off}$=0.02 V.The time step dt is set at $10^{-14}$ for simulation. The input provided is a sine wave of frequency 1 MHz and Amplitude of 1 V Cadence virtuoso is been used to simulate the Verilog -a model of VTEAM form acquired from \cite{b4}.
\newline
\vspace{0.5 cm}
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.5]{figure/vteam_setup.png}}
	\caption{VTEAM model setup schematic}
	\label{fig1}
    \end{figure}
\vspace{0.5 cm}    
\newline
The mathematical model of the VTEAM model is expressed as follows \cite{b4}:

\begin{equation}
\begin{aligned}
&v(t)=\left[R_{o n} \frac{W(t)}{D}+R_{o f f}\left(1-\frac{W(t)}{D}\right)\right] i(t)\\
&\frac{d w(t)}{d t}=\left\{\begin{array}{l}
k_{\text {off }}\left(\frac{v(t)}{V_{\text {off }}}-1\right)^{\alpha_{o f f}} f_{\text {off }}(w), 0<V_{\text {off }}<v \\
0, V_{\text {on }}<v<V_{\text {off }} \\
k_{\text {on }}\left(\frac{v(t)}{V_{\text {on }}}-1\right)^{\alpha_{\text {on }}} f_{\text {on }}(w), v<V_{\text {on }<0}
\end{array}\right.
\end{aligned}
\end{equation}
 
\newline
\vspace{0.4 cm}
V(t) is the voltage across the memristor terminals.
\newline
i(t) is the current passing through the memristor.
\newline
$\alpha_{off}$ , $\alpha_{on}$ , $k_{off}$ , $k_{on}$ are fitting parameters.
\newline
$V_{on}$ and $V_{off}$ are the threshold voltages.
\newline
$f_{on}$ and $f_{off}$ are window functions used to limit w
to have a value between 0 and 1.\cite{b6}


\vspace{0.5 cm}
V(t) can be expressed as time varying resistance $R_{m}$(t) as :

\[V(t) = R_{m}(t) * i(t)\]
\[R_{m}(t) = R_{on}*\frac{W(t)}{D} + R_{off}*(1-\frac{W(t)}{D})\]\cite{b6}
\newline
\vspace{0.5 cm}
$R_{on}$ is the on-state resistance
\newline
$R_{off}$ is the off-state resistance
\vspace{0.5 cm}
\begin{center}
\begin{tabular}{ |c|c|c|c| } 
 \hline
$R_{on}$  & 1000 \Omega &$a_{on}$  &2*10^{-9} m \\ 
$R_{off}$ &  50 \Omega &$a_{off}$  &1.2*10^{-9} m\\ 
$v_{on}$  & -0.2 V &  $k_{on}$& -10\\
$v_{off}$ & 0.02 V & $k_{off}$ &5*10^{-5}\\
$alpha_{on}$  & 3  &  $x_{on}$& 0 m\\
$alpha_{off}$ & 1 & $x_{off}$ &3*10^{-9} m \\
 \hline
\end{tabular}
\end{center}
\begin{center}
    \caption{Table 1:Parameters of the VTEAM Model}[4]
\end{center}
 \vspace{0.5 cm}
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.5]{figure/team_vi.png}}
	\caption{V and I graphs for the VTEAM model (Red- voltage,Blue-Current)}
	\label{fig1}
    \end{figure}  
    \vspace{0.3 cm}
From the I-v graphs we can see that the current change is lesser when the applied voltage is positive since the resistance of the memristor is $R_{off}$ which is high.
\newline
\vspace{0.3 cm}
Also when negative voltage is applied across the memristor terminals, the current decreases sharply as the resistance now changes to $R_{on}$ .\par

\newline
\vspace{0.3 cm}
Also the current doesnt change much till the +ve voltage applied crosses a the threshold $V_{th1}$.
\vspace{0.3 cm}
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.6]{figure/team_hystereis.png}}
	\caption{I-V Characteristics of the VTEAM model}
	\label{fig1}
    \end{figure}      
\vspace{1 cm}
 
\section{Memristor Ratioed logic}
\vspace{0.5cm}
Many different logic have been defined to construct digital and analog circuits using the memristor.Some of the major types are MAGIC (memristor aided logic), Hybrid memristor logic,Imply logic,etc.\par
\vspace{0.5cm}

In this section we will briefly discuss the Memristor ratioed logic also known as MAGIC.\par


In many ways, solely memristor elements are employed to create logic gate circuits, whereas in other approaches, hybrid memristor elements and CMOS structures are used . fundamental logic gates such as AND gate and Or gate can be implemented with the memristor ratioed logic.\par
\vspace{1 cm}
\begin{figure}%
    \centering
    \fbox{\subfloat{{\includegraphics[width=5cm]{figure/and.png} }}}%
    \qquad
    \fbox{\subfloat{{\includegraphics[width=5cm]{figure/or.png}} }}%
    \caption{(a) AND gate schematic (b) OR gate schematic}%
    \label{fig:example}%
\end{figure}

\begin{center}
\begin{tabular}{||c c c c c||} 
 \hline
 D0 &  & D1 & Rm2 & Rm1 & output \\ [0.8ex] 
 \hline\hline
 1 & 1 & $R_{off}$ & $R_{off}$ & high \\ 
 \hline
 1 & 0 & $R_{on}$ & $R_{off}$ & low\\
 \hline
 0 & 1 & $R_{off}$ &$R_{on}$ & low\\
 \hline
 0 & 0 & $R_{off}$ & $R_{off}$ & low\\[1ex] 
 \hline
\end{tabular}

\end{center}
\begin{center}
\caption{Table 2 :Different states of AND gate}
\end{center}
\vspace{0.5 cm}
\begin{center}
\begin{tabular}{||c c c c c||} 
 \hline
 D0 &  & D1 & Rm2 & Rm1 & output \\ [0.8ex] 
 \hline\hline
 1 & 1 & $R_{off}$ & $R_{off}$ & high \\ 
 \hline
 1 & 0 & $R_{on}$ & $R_{off}$ & high\\
 \hline
 0 & 1 & $R_{off}$ &$R_{on}$ & high\\
 \hline
 0 & 0 & $R_{off}$ & $R_{off}$ & low\\[1ex] 
 \hline
\end{tabular}
\end{center}
\begin{center}
\caption{Table 3 :Different states of OR gate}
\end{center}
\vspace{0.5 cm}



Two memristors paired with the proper polarities have been used to create AND- and OR-gates . In order to fully comprehend the link between two memristors and how it operates, this method has been simulated and illustrated as follows:
Figure 5a depicts an AND-gate in which the input voltages V and V are connected to a negative memristor sign, and the output voltage V is gathered by the positive memristor sign. The V is expressed as:

\[V_{o1} = \frac{R_{m1}*V_{in2}+R_{m2}*V_{in1}}{R_{m1}+R_{m2}}\]
\vspace{0.5cm}
Here,$R_{m1}$ and $R_{m2}$ are the memristor resistances.They can be $R_{on}$ or $R_{off}$ depending on the voltage applied across them.

\vspace{0.5 cm}

One of the major problems encountered in the Memristive DAC's is the "Sneak path problem".Several types of research has been published to solve the problem including the 1T1M(1 transistor 1 memristor) model,1D1M(1 diode 1 memristor) model and the 1S1M(1 selector 1 memristor) model\cite{b8}.In our approach for the DAC , the sneak path problem will occur when the two stages are connected with each other as there is a possibility of a alternative current path leading to a division of the current.\par

\begin{figure}%
    \centering
    \fbox{\subfloat{{\includegraphics[width=7cm]{figure/SNEAK_PROBLEM.png} }}}%
    \qquad
    \fbox{\subfloat{{\includegraphics[width=7cm]{figure/SNEAK_SOLUTION.png}} }}%
    \caption{(a)Sneak path problem in a 4-bit DAC , (b)Solution for the sneak path problem }%
\end{figure}

\newpage
\section{DAC metrics and terminologies}
\vspace{0.5cm}

\subsection{Input dynamic range}
Input dynamic range is defines the ratio of the largest to smallest possible signal value that can be resolved by the ADC.
\newline
For a n-bit ADC,
\[DR = 20*\log (2^{n}-1) db\]


\subsection{DNL (Differential non-linearity)}
Digital-to-analog (DAC) and analog-to-digital (ADC) converters frequently use the performance indicator known as differential nonlinearity (abbreviated DNL). It's a phrase used to describe the difference between two analogue values that match to neighbouring digital input values. This specification is crucial for assessing inaccuracy in a digital-to-analog converter (DAC); it mostly determines how accurate a DAC will be. Any two consecutive digital codes should, in theory, translate into output analogue voltages that are separated by exactly one Least Significant Bit (LSB). A measurement of the worst-case departure from the ideal 1 LSB step is differential non-linearity. For instance, a DAC that shows 12 LSB differential non-linearity has an output change of 1.5 LSB for a change in digital code of 1 LSB. In bits or fractions, differential nonlinearity can be stated..\par
\vspace{0.5 cm}
Differential non-linearity is defined as the difference between the step size with respect to the standard step size.
\[DNL =| \frac{V_{out}(i+1)-V_{out}(i)}{Step} -1 |\]
Step - Step width of the ADC.

\newline
\vspace{0.5 cm}
\begin{itemize}
\item Missing codes, or codes for which there is no input voltage to obtain the at the ADC output, appear in the transfer function if the DNL of an ADC is less than -1.
\item A DAC's transfer function becomes non-monotonic if the DNL of the DAC exceeds 1. In closed-loop control applications, a non-monotonic DAC is especially undesirable since it may result in stability issues, i.e. oscillations.
\end{itemize}
\vspace{0.5 cm} 
\subsection{INL (Integral non-linearity)}
A typical performance metric in digital-to-analog (DAC) and analog-to-digital (ADC) converters is integral nonlinearity, abbreviated as INL. It is a measurement of the difference between the actual measured output value for a specific input code and the desired output value in DACs. It is the difference between the actual threshold level of an output code and the desired input threshold value in ADCs. After offset and gain errors have been eliminated, this measurement is done. [1]

The ideal transfer function for a DAC or ADC is a straight line. The ideal line that is chosen determines the INL measurement. A common option is the line joining the endpoints of the transfer function or the line connecting the smallest and largest.
Utilizing a best fit line as an alternative involves minimising the average (or alternatively, the mean squared) INL.\par
\vspace{0.5 cm}
Integral non-linearity measures the maximum deviation of the ADC characteristics from the best-fit line.
\newline
For a best straight line approcah INL is given by:
\[INL = | Vo_{ideal} - Vo_{real}|\]
Vo - Output voltage of the ADC

\vspace{1 cm} 
\section{Thermometer code DAC}
One of the types of digital to analog converter is a thermometer code to analogue signal (DAC).It is used to convert a thermometer code to an analog signal.Thermometer code DAC can give upto "n" output levels for "n" digital inputs. It can use a capacitor array, which takes up substantially more space to implement, or the more common resistance string.
However, it can be accomplished in a tiny space with minimal power usage by using the memristor.\par
 \vspace{0.5 cm}
\subsection{4-bit thermometer code DAC}
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.4]{figure/4BIT_SCM.png}}
	\caption{4-bit DAC cell(thermometer code) transient results (Red - output ,Yellow - Expected ideal output)}
	\label{fig1}
    \end{figure} 
 \vspace{0.2 cm}
 Here resistances of all the memristors is taken to be the same having values according to the VTEAM model.
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.3]{figure/thermo4_out.png}}
	\caption{4-bit DAC cell (thermometer code) transient results (Red - output ,Yellow - Expected ideal output)}
	\label{fig1}
    \end{figure} 
 \vspace{0.2 cm}
 
 \begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.55]{figure/io.png}}
	\caption{Ideal output and actual output of 4-bit thermometer code DAC (Red - output ,Blue - Expected ideal output)}
	\label{fig1}
	\label{fig1}
    \end{figure} 
 \vspace{0.2 cm}
Figure 9 shows the ideal and the actual outputs of the 4-bit DAC.Ideally we expect a ADC output to be a straight continuous line but the actual output has more like a staircase structure. 
  
 \begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.28]{figure/inl.png}}
	\caption{INL of 4-bit thermometer code DAC}
	\label{fig1}
    \end{figure} 
 \vspace{0.2 cm}
The maximum magnitude of the INL is 190 mV which is lesser than the LSB size which is 250 mV.

\vspace{0.5 cm}
\subsection{8-bit thermometer code DAC}

\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.4]{figure/thermo8_scm.png}}
	\caption{8-bit DAC cell(thermometer code) schematic}
	\label{fig1}
    \end{figure} 
 \vspace{0.5 cm}
 
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.5]{figure/thermo8_tria.png}}
	\caption{8-bit DAC cell(thermometer code) transient results (Red - output ,Yellow - Expected ideal output)}
	\label{fig1}
    \end{figure} 
 
There are 8 levels in the output with the LSB of 125 mV. 
 \begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.32]{figure/thermo8_dnl.png}}
	\caption{INL of 8-bit thermometer code DAC}
	\label{fig1}
    \end{figure} 

The maximum magnitude of the INL is 80 mV which is lesser than the LSB size which is 125 mV. 
  
 \begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.35]{figure/thermo8_inl.png}}
	\caption{DNL of 8-bit thermometer code DAC}
	\label{fig1}
    \end{figure} 

 The maximum magnitude of the DNL is 17 mV which is much lesser than the LSB size which is 125 mV thus ensuring that there are no missing codes.\par
\vspace{0.5 cm}
 The binary-weighted DAC's main benefit over the thermometer-coded DAC is its low
thus no decoding logic is necessary, cost and resolution dramatically enhances decoding logic. Contrary to binary-weighted, thermometer-coded DACs, are monotonic by nature and have laxer matching requirements
standards for the same DNL. Additionally, the glitching issue that appears in the middle of the code in
Also it is possible to get more output levels and hence more accuracy with binary-weighted DAC's.

\section{Proposed memristor-based DAC}
\vspace{0.3 cm}
The string DAC and thermometer DAC architectures are by far the simplest DAC architectures.The basic cell proposed is the same for both the architectures whereas there are differences in the values of the resistance of the memristors used in the standard cells.
\vspace{0.3 cm}
\subsection{Binary weighted memristor-based DAC cell}

In thermometer code based DAC cells, we keep resistances of all the memristors the same. Here, we modify the cell  by making the on and off resistances of the memristors double of the other.This modification enables us to get more output levels as compared to the thermometer based DAC-cell.\par
\vspace{0.2 cm}
In thermometer DAC we assume that for a 2-bit cell both the $R_{m1}$ of both the memristors is the same.This leads to 3-output levels in a thermometer style DAC as the 01 and 10 inputs lead to the same output.\par
\vspace{0.2 cm}

\begin{figure}[h]
	\centering	\fbox{\includegraphics[scale=0.35]{figure/cell_scm.png}}
4	\caption{2-bit DAC cell (binary weighted) schematic}
	\label{fig1}
    \end{figure} 
 \vspace{0.2 cm}
In a binary weighted 2-bit cell DAC cell,we take $R_{m1}$ to be double that of $R_{m2}$. This leads to 4 output levels for a 2-bit DAC instead of 3 output levels as we got earlier in a thermometer style DAC.   
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.6]{figure/2bit.png}}
	\caption{Transient simulation of a binary weighted 2-bit DAC cell}
	\label{fig1}
    \end{figure}     
    \newline
The voltage step for the 2-bit DAC is 333.33 mV.
\subsection{4-Bit DAC}

Here we will construct the 4-bit DAC with the 2-bit binary weighted cell mentioned in the earler subsection.

\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.4]{figure/4BIT_SCM.png}}	\caption{4-bit DAC cell circuit}
	\label{fig1}
    \end{figure} 
 \vspace{0.2 cm}
 
The input voltage levels for the Digital inputs (D0-D3) is taken a s 1 V.$R_{m1}$,$R_{m3}$ and $R_{m5}$ are double of $R_{m2}$,$R_{m4}$ and $R_{m6}$ respectively according to the binary weighted configuration explained in the earlier subsection.
The voltage step for the 4-bit DAC is 66.667 mV.
\vspace{0.3 cm}
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.6]{figure/4bit.png}}
	\caption{Transient simulation of 4-bit DAC cell}
	\label{fig1}
    \end{figure}   

The 4-bit cell output is seen to have a bit of spikes which can be resolved with the appropriate use of filters.These spikes are due to sudden change in resistance.    
\newpage
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.5]{figure/4b_ideal_out.png}}
	\caption{Output vs ideal output}
	\label{fig1}
    \end{figure}   

    \vspace{0.4 cm}
\newline
Figure 19 compares output of the 4-bit to the ideal expected output.
 \vspace{0.2 cm}   
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.3]{figure/4bDNL.png}}
	\caption{DNL of 4-bit binary weighted DAC cell}
	\label{fig1}
    \end{figure} 
    \newline
    \vspace{0.4 cm}
The maximum magnitude of DNL seen is 40 mV range is well within the LSB of 66.667 mV.This implies that there are no missing codes.
\vspace{0.2 cm}
\begin{figure}[h]
	\centering
	\fbox{\includegraphics[scale=0.3]{figure/inl4.png}}
	\caption{INL of 4-bit binary weighted DAC cell}
	\label{fig1}
    \end{figure}   
    \vspace{0.4 cm}
    \newline
The maximum magnitude of INL is 480 mV which is way above the LSB of 66.667 mV.This is due to the voltage spikes seen in the circuit and needs to be resolved.Higher resolution DAC's can be made using this 4-bit DAC as a building block.Further works may include resolving the spikes in the circuit so as to get the INL in the limit and also extend to the 8-bit binary weighted DAC.

\vspace{2 cm}

\section{Conclusion}
In this term paper 4-bit and 8-bit Thermometer code DAC's and a 4-bit Binary weighted DAC were proposed.The VTEAM model of the memristor was used for the simulation of the DAC.The sneak path problem is solved by using a diode between the connecting stages of the DAC.The proposed design will have a lesser area due to the employment of memristors which have lesser area than CMOS.Also, this enables digital to analog conversions in the memory itself as a part of the In-memory computation.Memristors with tunable non-volatile resistance
statescan be used for in-memory computing that reduces
the von-Neumann bottleneck which is that the data should be fetched from the memory to the processor each time when a computation is to be done..\cite{b8}

\vspace{1 cm}
  % Includes a new page

\pagenumbering{roman} % Changes page numbering to roman page numbers
%\bibliography{literature}

\begin{thebibliography}{00}
\vspace{0.5 cm}
\bibitem{b1} {Chua, L. Memristor-The missing circuit element. IEEE Trans. Circuit Theory 1971, 18, 507–519}
\bibitem{b2} {Strukov, D.B.; Snider, G.S.; Stewart, D.R.; Williams, R.S. The missing memristor found. Nature 2008, 453, 80–83}
\bibitem{b3}{Kvatinsky, S.; Ramadan, M.; Friedman, E.G.; Kolodny, A. VTEAM: A General Model for Voltage-Controlled memristors. IEEE
Transactions Circuits Syst. II Express Briefs 2015, 62, 786–790}
\bibitem{b4}{Maxim integrated "INL/DNL MEASUREMENTS FOR TYPES OF HIGH-SPEED ANALOG-TO-DIGITAL CONVERTERS (ADCS)"}
\bibitem{b5}{S. Kvatinsky, N. Wald, G. Satat, A. Kolodny, U. C. Weiser and E. G. Friedman, "MRL — Memristor Ratioed Logic", 2012 13th International Workshop on Cellular Nanoscale Networks and their Applications, pp. 1-6, 2012}
\bibitem{b6}{ Fahmy, G.A.; Zorkany, M.
Design of a Memristor-Based Digital
to Analog Converter (DAC).
Electronics 2021, 10, 622. https://
doi.org/10.3390/electronics10050622}
\bibitem{b7}{Gül, F. Addressing the sneak-path problem in crossbar RRAM devices using memristor-based one Schottky diode-one resistor
array. Results Phys. 2019, 12, 1091–1096}
\bibitem{b8}{Li, C., Belkin, D., Li, Y., Yan, P., Hu, M., Ge, N., … Xia, Q. (2018). In-Memory Computing with Memristor Arrays. 2018 IEEE International Memory Workshop (IMW). doi:10.1109/imw.2018.8388838}

\end{thebibliography}

\end{document}
