---
title: 'How to: Build a multifile assembly'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: 0f8c6d57425657e321d80f9edffa20f27bc28770
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429569"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="6def4-102">How to: Build a multifile assembly</span><span class="sxs-lookup"><span data-stu-id="6def4-102">How to: Build a multifile assembly</span></span>

<span data-ttu-id="6def4-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span><span class="sxs-lookup"><span data-stu-id="6def4-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="6def4-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span><span class="sxs-lookup"><span data-stu-id="6def4-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="6def4-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span><span class="sxs-lookup"><span data-stu-id="6def4-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="6def4-106">Multifile assemblies are supported by .NET Framework only.</span><span class="sxs-lookup"><span data-stu-id="6def4-106">Multifile assemblies are supported by .NET Framework only.</span></span>

## <a name="create-a-multifile-assembly"></a><span data-ttu-id="6def4-107">Create a multifile assembly</span><span class="sxs-lookup"><span data-stu-id="6def4-107">Create a multifile assembly</span></span>

1. <span data-ttu-id="6def4-108">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span><span class="sxs-lookup"><span data-stu-id="6def4-108">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="6def4-109">The default extension for code modules is *.netmodule*.</span><span class="sxs-lookup"><span data-stu-id="6def4-109">The default extension for code modules is *.netmodule*.</span></span>

   <span data-ttu-id="6def4-110">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="6def4-110">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="6def4-111">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span><span class="sxs-lookup"><span data-stu-id="6def4-111">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. <span data-ttu-id="6def4-112">Use the following command to compile this code:</span><span class="sxs-lookup"><span data-stu-id="6def4-112">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   <span data-ttu-id="6def4-113">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span><span class="sxs-lookup"><span data-stu-id="6def4-113">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="6def4-114">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span><span class="sxs-lookup"><span data-stu-id="6def4-114">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span></span>

3. <span data-ttu-id="6def4-115">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span><span class="sxs-lookup"><span data-stu-id="6def4-115">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="6def4-116">This step uses the **/addmodule** compiler option.</span><span class="sxs-lookup"><span data-stu-id="6def4-116">This step uses the **/addmodule** compiler option.</span></span>

   <span data-ttu-id="6def4-117">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span><span class="sxs-lookup"><span data-stu-id="6def4-117">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span></span>

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. <span data-ttu-id="6def4-118">Use the following command to compile this code:</span><span class="sxs-lookup"><span data-stu-id="6def4-118">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   <span data-ttu-id="6def4-119">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span><span class="sxs-lookup"><span data-stu-id="6def4-119">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="6def4-120">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span><span class="sxs-lookup"><span data-stu-id="6def4-120">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span></span> <span data-ttu-id="6def4-121">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span><span class="sxs-lookup"><span data-stu-id="6def4-121">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6def4-122">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span><span class="sxs-lookup"><span data-stu-id="6def4-122">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
   >
   > <span data-ttu-id="6def4-123">Two compilations create a two-file assembly:</span><span class="sxs-lookup"><span data-stu-id="6def4-123">Two compilations create a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > <span data-ttu-id="6def4-124">One compilation creates a two-file assembly:</span><span class="sxs-lookup"><span data-stu-id="6def4-124">One compilation creates a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. <span data-ttu-id="6def4-125">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="6def4-125">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="6def4-126">This file contains reference information for all modules or resources that are part of the assembly.</span><span class="sxs-lookup"><span data-stu-id="6def4-126">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="6def4-127">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="6def4-127">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="6def4-128">**al** \<*module name*> \<*module name*> …</span><span class="sxs-lookup"><span data-stu-id="6def4-128">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="6def4-129">**/main:** \<*method name*>  **/out:** \<*file name*>  **/target:** \<*assembly file type*></span><span class="sxs-lookup"><span data-stu-id="6def4-129">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="6def4-130">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span><span class="sxs-lookup"><span data-stu-id="6def4-130">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="6def4-131">The **/main:** option specifies the method name that is the assembly's entry point.</span><span class="sxs-lookup"><span data-stu-id="6def4-131">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="6def4-132">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span><span class="sxs-lookup"><span data-stu-id="6def4-132">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="6def4-133">The **/target:** option specifies that the assembly is a console application executable ( *.exe*) file, a Windows executable ( *.win*) file, or a library ( *.lib*) file.</span><span class="sxs-lookup"><span data-stu-id="6def4-133">The **/target:** option specifies that the assembly is a console application executable (*.exe*) file, a Windows executable (*.win*) file, or a library (*.lib*) file.</span></span>

    <span data-ttu-id="6def4-134">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span><span class="sxs-lookup"><span data-stu-id="6def4-134">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span></span> <span data-ttu-id="6def4-135">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span><span class="sxs-lookup"><span data-stu-id="6def4-135">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span></span> <span data-ttu-id="6def4-136">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span><span class="sxs-lookup"><span data-stu-id="6def4-136">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span></span>

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="6def4-137">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span><span class="sxs-lookup"><span data-stu-id="6def4-137">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="6def4-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6def4-138">See also</span></span>

- [<span data-ttu-id="6def4-139">Create assemblies</span><span class="sxs-lookup"><span data-stu-id="6def4-139">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="6def4-140">How to: View assembly contents</span><span class="sxs-lookup"><span data-stu-id="6def4-140">How to: View assembly contents</span></span>](../../standard/assembly/view-contents.md)
- [<span data-ttu-id="6def4-141">How the runtime locates assemblies</span><span class="sxs-lookup"><span data-stu-id="6def4-141">How the runtime locates assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6def4-142">Multifile assemblies</span><span class="sxs-lookup"><span data-stu-id="6def4-142">Multifile assemblies</span></span>](multifile-assemblies.md)
