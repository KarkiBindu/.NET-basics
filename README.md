# .NET-basics

1. <b> Assembly </b> :
    - An assembly is a collection of types and resources that are built to work together and form a logical unit of functionality.<sup>1</sup> 
    - It contains the manifest and Intermediate language (IL)
    - It mainly in the form of <i> .exe or .dll </i>
    - Windows and Console apps are in the form of .exe, Class Library and Web app are in the form of .dll
    - It consists of four parts : </br> 1. Simple textual name (project name mostly) </br> 2. Version Number </br> 3. Culture Information </br> 4. Public key token
    - An assembly can either be strongly named or weakly named
    - Assembly with public key token are strongly named
    - <b>Version Number </b> signifies the version of an assembly; by default version number is 1.0.0.0
    - Version Number consists of four parts : </br> 1. Major version </br> 2. Minor version </br> 3. Build number </br> 4. Revision number
    - Culture information determines whether the assembly is language(English/ Spanish) neutral or not and when culture is defined the assembly will be satellite assembly
    
2. <b> Manifest </b> : 
    - It contains the assembly metadata that specifies the assembly's version number, requirements and security identity
    - These metadata also helps define all scope of the assembly and resolve references to resorces and classes
    
3. <b> Intermediate Language (IL) </b> :
    - All the code in an assembly are coverted into an assembly language or platform independent set of instruction known as intermediate language
    - It is a generated by language specific compiler
    - This is how IL looks like : </br>
    ![Intermediate Language](https://github.com/KarkiBindu/.NET-basics/blob/master/IL.JPG)

3. <b> Common Language Runtime (CLR) </b> :
    - It is the foundation of .net framework and acts as its execution engine
    - It manages the execution of programs and provides suitable environment for programs to run
    - It is a kind of compiler and supports multiple programming languages
    
4. <b> Working principle </b> :
    1. A compiler converts all the code written in specific language into an assembly
    2. Assembly has the CIL (Common Intermediate Language) which is passed to JIT (Just In Time) compiler of CLR
    3. JIT converts CIL to machine language code ate run time, JIT only converts the code required for execution
    4. Finally the CPU (Central Processing Unit) executes the code directly
    
5. <b> ILDASM (IL Disassembler) </b> :
    - It is a visual studio commandline tool
    - It is used to peek at the assembly manifest and IL
    - It can also be used to export manifest and IL into text file
    - To disammble an assembly open visual studio command prompt and enter <i>ILDASM</i> fullassemblypath
    - Then following window will be shown :
    ![Disassembled Assembly](https://github.com/KarkiBindu/.NET-basics/blob/master/ILDASM.png)
    - To create text file Go to File-> Dump and click ok and provide the filename, these files are saved with <i>.il</i> extension
    
6. <b> ILASM (IL Assembler) </b> :
    - It is a visual studio commandline tool
    - It is used to reconstruct an assembly from a text file that contains manifest and IL
    - To create assembly from <i> .il </i> file; open visual studio command prompt and enter <i>ILASM</i> full.ilFilepath
   
    
7. <b> Global Assembly Cache (GAC) </b> :
    
##<b>Reference</b> :
1. "Assemblies In .NET". Docs.Microsoft.Com, 08/15/2019, https://docs.microsoft.com/en-us/dotnet/standard/assembly/.
