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
ms.openlocfilehash: a8d3bf7363cb887834a1c251aead05c75e2e3fe8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130224"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="af337-102">Generování a kompilace zdrojového kódu z grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="af337-102">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="af337-103">Obor názvů <xref:System.CodeDom.Compiler> poskytuje rozhraní pro generování zdrojového kódu z grafů objektů CodeDOM a pro správu kompilace s podporovanými kompilátory.</span><span class="sxs-lookup"><span data-stu-id="af337-103">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="af337-104">Poskytovatel kódu může vytvořit zdrojový kód v konkrétním programovacím jazyce podle grafu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="af337-104">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="af337-105">Třída, která je odvozena z <xref:System.CodeDom.Compiler.CodeDomProvider>, může obvykle poskytnout metody pro generování a kompilování kódu pro jazyk, který poskytovatel podporuje.</span><span class="sxs-lookup"><span data-stu-id="af337-105">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="af337-106">Použití poskytovatele kódu CodeDOM ke generování zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="af337-106">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="af337-107">Chcete-li generovat zdrojový kód v konkrétním jazyce, potřebujete graf CodeDOM, který představuje strukturu zdrojového kódu, který má být vygenerován.</span><span class="sxs-lookup"><span data-stu-id="af337-107">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="af337-108">Následující příklad ukazuje, jak vytvořit instanci <xref:Microsoft.CSharp.CSharpCodeProvider>:</span><span class="sxs-lookup"><span data-stu-id="af337-108">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="af337-109">Graf pro generování kódu je obvykle obsažen v <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="af337-109">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="af337-110">Chcete-li vygenerovat kód pro **CodeCompileUnit** , který obsahuje graf CodeDOM, zavolejte metodu <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> poskytovatele kódu.</span><span class="sxs-lookup"><span data-stu-id="af337-110">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="af337-111">Tato metoda má parametr pro <xref:System.IO.TextWriter>, který používá ke generování zdrojového kódu, takže je někdy nutné nejprve vytvořit modul **TextWriter** , do kterého lze zapisovat.</span><span class="sxs-lookup"><span data-stu-id="af337-111">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="af337-112">Následující příklad ukazuje vygenerování kódu z **CodeCompileUnit** a zápis generovaného zdrojového kódu do souboru s názvem HelloWorld.cs.</span><span class="sxs-lookup"><span data-stu-id="af337-112">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="af337-113">Použití poskytovatele kódu CodeDOM ke kompilaci sestavení</span><span class="sxs-lookup"><span data-stu-id="af337-113">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="af337-114">**Vyvolání kompilace**</span><span class="sxs-lookup"><span data-stu-id="af337-114">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="af337-115">Chcete-li zkompilovat sestavení pomocí poskytovatele CodeDom, je nutné mít buď zdrojový kód pro zkompilování v jazyce, pro který máte kompilátor, nebo graf CodeDOM, ze kterého lze zdrojový kód kompilovat, vytvořit.</span><span class="sxs-lookup"><span data-stu-id="af337-115">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="af337-116">Pokud kompilujete z grafu CodeDOM, předejte <xref:System.CodeDom.CodeCompileUnit> obsahující graf do metody <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> poskytovatele kódu.</span><span class="sxs-lookup"><span data-stu-id="af337-116">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="af337-117">Máte-li soubor zdrojového kódu v jazyce, který zná kompilátor, předejte název souboru obsahujícího zdrojový kód do metody <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> zprostředkovatele CodeDom.</span><span class="sxs-lookup"><span data-stu-id="af337-117">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="af337-118">Můžete také předat řetězec obsahující zdrojový kód v jazyce, který kompilátor rozumí metodě <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> zprostředkovatele CodeDom.</span><span class="sxs-lookup"><span data-stu-id="af337-118">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="af337-119">**Konfigurace parametrů kompilace**</span><span class="sxs-lookup"><span data-stu-id="af337-119">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="af337-120">Všechny metody standardního volání kompilace poskytovatele CodeDom mají parametr typu <xref:System.CodeDom.Compiler.CompilerParameters>, který určuje možnosti, které se mají použít pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="af337-120">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="af337-121">Můžete zadat název souboru pro výstupní sestavení ve vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> **CompilerParameters**.</span><span class="sxs-lookup"><span data-stu-id="af337-121">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="af337-122">V opačném případě se použije výchozí název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="af337-122">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="af337-123">Ve výchozím nastavení je nová **CompilerParameters** inicializována s vlastností <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> nastavenou na **hodnotu false**.</span><span class="sxs-lookup"><span data-stu-id="af337-123">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="af337-124">Pokud kompilujete spustitelný program, je nutné nastavit vlastnost **GenerateExecutable** na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="af337-124">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="af337-125">Pokud je **GenerateExecutable** nastaveno na **false**, kompilátor vygeneruje knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="af337-125">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="af337-126">Pokud kompilujete spustitelný soubor z grafu CodeDOM, <xref:System.CodeDom.CodeEntryPointMethod> musí být definován v grafu.</span><span class="sxs-lookup"><span data-stu-id="af337-126">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="af337-127">Pokud existuje více vstupních bodů kódu, může být nutné nastavit vlastnost <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> **CompilerParameters** na název třídy definující vstupní bod, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="af337-127">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="af337-128">Chcete-li zahrnout informace o ladění do generovaného spustitelného souboru, nastavte vlastnost <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="af337-128">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="af337-129">Pokud váš projekt odkazuje na jakákoli sestavení, je nutné zadat názvy sestavení jako položky v <xref:System.Collections.Specialized.StringCollection> jako vlastnost <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> **CompilerParameters** , kterou použijete při volání kompilace.</span><span class="sxs-lookup"><span data-stu-id="af337-129">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="af337-130">Můžete zkompilovat sestavení, které je zapsáno do paměti, nikoli na disk nastavením vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="af337-130">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="af337-131">Když je sestavení generované v paměti, váš kód může získat odkaz na vygenerované sestavení z vlastnosti <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> <xref:System.CodeDom.Compiler.CompilerResults>.</span><span class="sxs-lookup"><span data-stu-id="af337-131">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="af337-132">Pokud je sestavení zapisováno na disk, můžete získat cestu k generovanému sestavení z vlastnosti <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> **CompilerResults**.</span><span class="sxs-lookup"><span data-stu-id="af337-132">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="af337-133">Chcete-li zadat vlastní řetězec argumentů příkazového řádku, který má být použit při vyvolání procesu kompilace, nastavte řetězec ve vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A>.</span><span class="sxs-lookup"><span data-stu-id="af337-133">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="af337-134">Pokud je k vyvolání procesu kompilátoru vyžadován token zabezpečení Win32, zadejte token do vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A>.</span><span class="sxs-lookup"><span data-stu-id="af337-134">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="af337-135">Chcete-li propojit soubor prostředků Win32 s kompilovaným sestavením, zadejte název souboru prostředků Win32 ve vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A>.</span><span class="sxs-lookup"><span data-stu-id="af337-135">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="af337-136">Chcete-li určit úroveň upozornění, při které má být kompilace zastavena, nastavte vlastnost <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> na celé číslo, které představuje úroveň upozornění, při které má být kompilace zastavena.</span><span class="sxs-lookup"><span data-stu-id="af337-136">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="af337-137">Můžete také nakonfigurovat kompilátor pro zastavení kompilace, pokud jsou zjištěna upozornění, nastavením vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="af337-137">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="af337-138">Následující příklad kódu ukazuje, jak zkompilovat zdrojový soubor pomocí poskytovatele CodeDom odvozeného z třídy <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="af337-138">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="af337-139">Jazyky s počáteční podporou</span><span class="sxs-lookup"><span data-stu-id="af337-139">Languages with Initial Support</span></span>  
 <span data-ttu-id="af337-140">.NET Framework poskytuje kompilátory kódu a generátory kódu pro následující jazyky: C#, Visual Basic, C++a JScript.</span><span class="sxs-lookup"><span data-stu-id="af337-140">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="af337-141">Podporu CodeDOM lze rozšířit i na jiné jazyky implementací generátorů kódu specifických pro jazyk a kompilátorů kódu.</span><span class="sxs-lookup"><span data-stu-id="af337-141">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af337-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af337-142">See also</span></span>

- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [<span data-ttu-id="af337-143">Dynamické vytváření a kompilování zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="af337-143">Dynamic Source Code Generation and Compilation</span></span>](dynamic-source-code-generation-and-compilation.md)
- <span data-ttu-id="af337-144">[Rychlá referenční příručka CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="af337-144">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>
