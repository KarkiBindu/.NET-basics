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
    - These information can be changed/updated from <i>AssemblyInfo.cs file</i>
    
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
    1. A language native compiler (csc.exe for MS C#) converts all the code written in specific language into an assembly
    2. Assembly has the CIL (Common Intermediate Language) which is passed to JIT (Just In Time) compiler of CLR
    3. JIT converts CIL to machine language code ate run time, JIT only converts the code required for execution
    4. Finally the CPU (Central Processing Unit) executes the code directly
    
5. <b> ILDASM (IL Disassembler) </b> :
    - It is a visual studio commandline tool
    - It is used to peek at the assembly manifest and IL
    - It can also be used to export manifest and IL into text file
    - To disammble an assembly open visual studio command prompt and enter `ILDASM fullassemblypath`
    - Then following window will be shown :
    ![Disassembled Assembly](https://github.com/KarkiBindu/.NET-basics/blob/master/ILDASM.png)
    - To create text file Go to File-> Dump and click ok and provide the filename, these files are saved with <i>.il</i> extension
    
6. <b> ILASM (IL Assembler) </b> :
    - It is a visual studio commandline tool
    - It is used to reconstruct an assembly from a text file that contains manifest and IL
    - To create assembly from <i> .il </i> file; open visual studio command prompt and enter `ILASM full.ilFilepath`
   
7. <b> Strong Naming an Assembly </b> :
    - Assemblies signed with private and public key pair are  strong named
    - They are supposed to be unique and solves DLL hell
    - To install an assembly into GAC they must be strongly named
    - To create key pair open visal studio command prompt and enter `sn.exe -k Generationpath\Filename.snk`, -k asserts generation
    - To make an assembly Strongly Named in <i>AssemblyIno.cs</i> use <i>AssemblyKeyFile</i> attribute `[assembly : AssemblyKeyFile("Generationpath\Filename.snk")]` 
    
8. <b> Global Assembly Cache (GAC) </b> :
    - It is a location where all .net framework class library are installed
    - It is found in Assembly folder inside OS directory in windows OS it is found in C:\Windows\Assembly
    - Assemblies installed in GAC can be shared by multiple applications without referencing (copying locally) it
    - Only add assembly to GAC if it is shared by other applications
    - These assemblies will not be copied when trying to copy the project to another machine
    - There are two GAC location : </br> 1. C:\Windows\assembly for .NET2.0-3.5 </br> 2. C:\Windows\Microsoft.NET\assembly for .NET 4 and above
    - Assembly can be installed in GAC in two ways: </br> 1. Drag and drop </br> 2. Use GacUtil.exe (GAC utility tool)
    - Assemblies with same name and same public keytoken can be together and perform together with different version number
    - To install using GAC open VS command prompt and navigate to assembly location and enter `gacutil -i fullassemblypathname`
    - To uninstall using GAC eneter `gacutil -u AssemblyName`, no extension required
    - To uninstall specific assembly using GAC `gacutil -u AssemblyName,version = versionnmber,publickeytoken = value`

9. <b> DLL Hell </b> :
    - If an application installs new vwesion of shared component that is not backward compatible with the version already available on the machine then it will break all the applications that relies in it which is known as dll hell.
    - Example: We have one application A1 sharing assembly of another application A2. If methods and its signature is changed in A2 and provided to the A1 application, A1 will not be able to find that method as the signatuure is A1 is of the unchanged method which will crash the application.
    - To reolve this problem an assembly should be strongly named. So that the versions of the assemblies will be created preventing the applicatio to crash. If the method is not found in newer version then it will check the older version. 

9. <b> How .NET finds shared assembly </b> :
    - The manifest contains the information about the dependent assemblies
    - If the dependent assembly is strongly named then the CLR checks in GAC
    - If it is not found in GAC then it checks for the location in .config file if it exists
    - Else it searches in the directory containing the executable files or assemblies (debug/release)
    - If the assembly is not found then the application terminates with error
    
    
<b>Reference</b> :
1. "Assemblies In .NET". Docs.Microsoft.Com, 08/15/2019, https://docs.microsoft.com/en-us/dotnet/standard/assembly/.
