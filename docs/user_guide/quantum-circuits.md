#Quantum Circuits

##Latex-Rendering


PatternAtlas supports inline LaTeX code rendering for quantum circuits.
This requires the setup of [Latex-Renderer](https://github.com/UST-QuAntiL/latex-renderer). 
 
PatternAtlas supports [Qcircuit](http://physics.unm.edu/CQuIC/Qcircuit/Qtutorial.pdf) and [Quantikz](https://arxiv.org/pdf/1809.03842.pdf) circuit defintions. 
Simply copy your Qcircuit or Quantikz code into the content of a Pattern.  
**Qcircuit example:** 

   `\Qcircuit @C=1em @R=.7em {  
   & \ctrl{1} & \targ & \qw \\  
   & \targ & \ctrl{-1} & \qw  
   end}    `

!!! info
    The "end" tag is **required** to close the Qcircuit section in PatternAtlas    

**Quantikz example:**
 
  `\begin{quantikz}
   & \targ{} & \gate{U} & \qw \\  
   & \ctrl{1} \vqw{-1} & \meter{} \vcw{-1} \\  
   & \targ{} & \qw  
   \end{quantikz}  `


##Discussion

PatternAtlas supports the Discussion of the rendered Qcircuit and Quantikz circuits. 
Simply click the "Comment Picture" button and mark an area within the circuit and then add your comment.
To answer on comments click the marked area and submit your comment.     

##OpenQASM

PatternAtlas supports the Integration of [OpenQASM 2.0](https://github.com/Qiskit/openqasm/tree/OpenQASM2.x) Algorithms. The algorithm will get displayed as a graphical circuit.
Simply copy your OpenQASM code into the content of a Pattern and add the "end" tag:
  
   `OPENQASM 2.0;  
   include "qelib1.inc";  
   qreg q[2];  
   h q[0];  
   cx q[0], q[1]; end `     

!!! info
    The "end" tag is **required** to close the OpenQASM section in PatternAtlas      

