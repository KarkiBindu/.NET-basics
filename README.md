# .NET-basics

1. <b> Assembly </b> :
    - An assembly is a collection of types and resources that are built to work together and form a logical unit of functionality.<sup>1</sup> 
    - It contains the manifest and Intermediate language (IL)
    - It mainly in the form of <i> .exe or .dll </i>
    - It consists of four parts : </br> 1. Simple textual name (project name mostly) </br> 2. Version Number </br> 3. Culture Information </br> 4. Public key token
    - An assembly can either be strongly named or weakly named
    - Assembly with public key token are strongly named
    - <b>Version Number </b> signifies the version of an assembly; by default version number is 1.0.0.0
    - Version Number consists of four parts : </br> 1. Major version </br> 2. Minor version </br> 3. Build number </br> 4. Revision number
    - Culture information determines whether the assembly is language(English/ Spanish) neutral or not and when culture is defined the assembly will be satellite assembly
    
2. <b> Manifest </b> : 
    - It contains the assembly metadata that specifies the assembly's version number, requirements and security identity
    - These metadata also helps define all scope of the assembly and resolve references to resorces and classes

3. <b> Common Language Runtime (CLR) </b> :
    - It is the foundation of .net framework and acts as its execution engine
    - It manages the execution of programs and provides suitable environment for programs to run
    - It is a kind of compiler and supports multiple programming languages
    
<b>Reference</b> :
1. "Assemblies In .NET". Docs.Microsoft.Com, 08/15/2019, https://docs.microsoft.com/en-us/dotnet/standard/assembly/.
