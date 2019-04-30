---
title: Generování a kompilace zdrojového kódu z grafu modelu CodeDOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- CodeDOM, generating source code
- Code Document Object Model, graphs
- templated code generation
- source code, generating
- dynamically representing source code
- generating CodeDOM graphs
- Code Document Object Model, generating source code
- translating language to language
- compiling assemblies
- generating source code in multiple languages
- graphing with CodeDOM
- dynamic compilation
- assemblies [.NET Framework], CodeDOM
- source code generation
- outputting source code by CodeDOM
- code generators
- compiling source code, multiple languages
- CodeDOM, graphs
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bfc915287e579374c69636135c4b049184ef6ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793287"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="78300-102">Generování a kompilace zdrojového kódu z grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="78300-102">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="78300-103"><xref:System.CodeDom.Compiler> Obor názvů poskytuje rozhraní pro generování zdrojového kódu z grafu modelu CodeDOM objekt a pro správu kompilace s podporované kompilátory.</span><span class="sxs-lookup"><span data-stu-id="78300-103">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="78300-104">Zdrojový kód v konkrétním programovacím jazyce podle grafu CodeDOM může vytvořit poskytovatele kódu.</span><span class="sxs-lookup"><span data-stu-id="78300-104">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="78300-105">Třída, která je odvozena z <xref:System.CodeDom.Compiler.CodeDomProvider> lze obvykle poskytují metody pro generování a kompilace kódu pro jazyk zprostředkovatel podporuje.</span><span class="sxs-lookup"><span data-stu-id="78300-105">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="78300-106">Vygenerování zdrojového kódu pomocí zprostředkovatele kódu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="78300-106">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="78300-107">Vygenerování zdrojového kódu v určitém jazyce, je nutné, která reprezentuje strukturu těchto zdrojový kód pro generování grafu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="78300-107">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="78300-108">Následující příklad ukazují, jak vytvořit instanci <xref:Microsoft.CSharp.CSharpCodeProvider>:</span><span class="sxs-lookup"><span data-stu-id="78300-108">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="78300-109">Graf pro generování kódu je obvykle součástí <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="78300-109">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="78300-110">Pro generování kódu pro **CodeCompileUnit** , která obsahuje graf CodeDOM, zavolejte <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metoda zprostředkovatele kódu.</span><span class="sxs-lookup"><span data-stu-id="78300-110">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="78300-111">Tato metoda má parametr <xref:System.IO.TextWriter> , který se použije k vygenerování zdrojového kódu, takže někdy je potřeba nejprve vytvořit **TextWriter** , který je možné zapisovat na.</span><span class="sxs-lookup"><span data-stu-id="78300-111">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="78300-112">Následující příklad ukazuje generování kódu z **CodeCompileUnit** a zápis vygenerované zdrojový kód do souboru s názvem HelloWorld.cs.</span><span class="sxs-lookup"><span data-stu-id="78300-112">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="78300-113">Použití zprostředkovatele kódu CodeDOM pro kompilaci sestavení</span><span class="sxs-lookup"><span data-stu-id="78300-113">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="78300-114">**Vyvolání kompilace**</span><span class="sxs-lookup"><span data-stu-id="78300-114">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="78300-115">Kompilace sestavení pomocí zprostředkovatele CodeDom, musí mít buď zdrojový kód a zkompilovat v jiném jazyce, pro který máte kompilátor nebo grafu CodeDOM tohoto zdroje kód mohl zkompilovat se dá vygenerovat na.</span><span class="sxs-lookup"><span data-stu-id="78300-115">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="78300-116">Pokud kompilujete z grafu modelu CodeDOM, předejte <xref:System.CodeDom.CodeCompileUnit> obsahující graf tak, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> metoda zprostředkovatele kódu.</span><span class="sxs-lookup"><span data-stu-id="78300-116">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="78300-117">Pokud máte soubor zdrojového kódu v jazyce, který kompilátor rozpozná, předejte název souboru, který obsahuje zdrojový kód <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metoda zprostředkovatele CodeDom.</span><span class="sxs-lookup"><span data-stu-id="78300-117">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="78300-118">Můžete také předat řetězec obsahující zdrojový kód v jazyce, který kompilátor rozpozná na <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> metoda zprostředkovatele CodeDom.</span><span class="sxs-lookup"><span data-stu-id="78300-118">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="78300-119">**Konfigurace parametrů kompilace**</span><span class="sxs-lookup"><span data-stu-id="78300-119">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="78300-120">Všechny standardní metody vyvolání kompilace poskytovatele CodeDom mít parametr typu <xref:System.CodeDom.Compiler.CompilerParameters> , který určuje možnosti pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="78300-120">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="78300-121">Můžete zadat název souboru pro výstupní sestavení v <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> vlastnost **CompilerParameters**.</span><span class="sxs-lookup"><span data-stu-id="78300-121">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="78300-122">V opačném případě se použije výchozí název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="78300-122">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="78300-123">Ve výchozím nastavení nový **CompilerParameters** je inicializován s jeho <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> vlastnost nastavena na hodnotu **false**.</span><span class="sxs-lookup"><span data-stu-id="78300-123">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="78300-124">Pokud kompilujete spustitelný program, je nutné nastavit **GenerateExecutable** vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="78300-124">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="78300-125">Když **GenerateExecutable** je nastavena na **false**, bude kompilátor generovat knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="78300-125">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="78300-126">Pokud kompilujete z grafu modelu CodeDOM, spustitelný soubor <xref:System.CodeDom.CodeEntryPointMethod> musí být definován v grafu.</span><span class="sxs-lookup"><span data-stu-id="78300-126">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="78300-127">Pokud existuje více vstupních bodů kódu, může být potřeba nastavit <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> vlastnost **CompilerParameters** k názvu třídy, která definuje vstupní bod, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="78300-127">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="78300-128">Chcete-li zahrnout informace o ladění generované spustitelné soubory, nastavte <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="78300-128">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="78300-129">Pokud váš projekt odkazuje na všechna sestavení, je nutné zadat názvy sestavení jako položky v <xref:System.Collections.Specialized.StringCollection> jako <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> vlastnost **CompilerParameters** použijete při vyvolání kompilace.</span><span class="sxs-lookup"><span data-stu-id="78300-129">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="78300-130">Kompilujete sestavení, která je napsána na paměť a místo na disku tak, že nastavíte <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="78300-130">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="78300-131">Při generování sestavení v paměti, váš kód lze získat odkaz na vygenerované sestavení z <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> vlastnost <xref:System.CodeDom.Compiler.CompilerResults>.</span><span class="sxs-lookup"><span data-stu-id="78300-131">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="78300-132">Pokud sestavení se zapisují do disku, můžete získat cestu do generovaného sestavení z <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> vlastnost **CompilerResults**.</span><span class="sxs-lookup"><span data-stu-id="78300-132">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="78300-133">Pokud chcete zadat vlastní argumenty příkazového řádku řetězec použitý při vyvolání procesu kompilace, nastavte řetězec <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="78300-133">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="78300-134">Pokud je token Win32 zabezpečení požadované k vyvolání procesu kompilátoru, zadejte token v <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="78300-134">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="78300-135">Chcete-li propojit soubor prostředků Win32 do zkompilovaného sestavení, zadejte název souboru prostředků Win32 v <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="78300-135">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="78300-136">Chcete-li určit úroveň upozornění, ve kterém se má zastavit kompilace, nastavte <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> vlastnost na celé číslo představující úroveň pro upozornění, kam chcete zastavit kompilace.</span><span class="sxs-lookup"><span data-stu-id="78300-136">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="78300-137">Můžete taky nakonfigurovat kompilátor, aby kompilace zastaví, pokud jsou zjištěna upozornění tak, že nastavíte <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="78300-137">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="78300-138">Následující příklad kódu ukazuje kompilování zdrojového souboru pomocí odvozený od zprostředkovatele CodeDom <xref:System.CodeDom.Compiler.CodeDomProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="78300-138">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="78300-139">Jazyky, základem je podpora</span><span class="sxs-lookup"><span data-stu-id="78300-139">Languages with Initial Support</span></span>  
 <span data-ttu-id="78300-140">Rozhraní .NET Framework poskytuje kompilátory kódu a generátory kódu pro následující jazyky: C#, Visual Basic, C++ a JScript.</span><span class="sxs-lookup"><span data-stu-id="78300-140">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="78300-141">Podpora codeDOM je možné rozšířit do jiných jazyků implementací generátory kódu specifické pro jazyk a kompilátory kódu.</span><span class="sxs-lookup"><span data-stu-id="78300-141">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78300-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78300-142">See also</span></span>

- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [<span data-ttu-id="78300-143">Dynamické vytváření a kompilování zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="78300-143">Dynamic Source Code Generation and Compilation</span></span>](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
- <span data-ttu-id="78300-144">[CodeDOM – Stručná referenční příručka](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="78300-144">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>
