---
title: "Generování a kompilace zdrojového kódu z grafu modelu CodeDOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56e2effec282900101fc0cbe489c76b523184ab2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="bde35-102">Generování a kompilace zdrojového kódu z grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="bde35-102">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="bde35-103"><xref:System.CodeDom.Compiler> Obor názvů poskytuje rozhraní pro generování zdrojového kódu z objektu grafů CodeDOM a pro správu kompilace pomocí podporovaných kompilátory.</span><span class="sxs-lookup"><span data-stu-id="bde35-103">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="bde35-104">Zprostředkovatel kódu může vytvářet zdrojový kód v konkrétní programovací jazyk podle grafu modelu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="bde35-104">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="bde35-105">Třída odvozená z <xref:System.CodeDom.Compiler.CodeDomProvider> obvykle poskytne metody pro generování a kompilace kódu pro jazyk zprostředkovatel podporuje.</span><span class="sxs-lookup"><span data-stu-id="bde35-105">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="bde35-106">Generování zdrojového kódu pomocí zprostředkovatele kódu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="bde35-106">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="bde35-107">Generování zdrojového kódu v určitém jazyce, je nutné představující strukturu zdrojového kódu ke generování grafu modelu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="bde35-107">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="bde35-108">Následující příklad ukazují, jak vytvořit instanci <xref:Microsoft.CSharp.CSharpCodeProvider>:</span><span class="sxs-lookup"><span data-stu-id="bde35-108">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="bde35-109">Graf pro generování kódu je obvykle součástí <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="bde35-109">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="bde35-110">Generovat kód pro **vlastnosti CodeCompileUnit** obsahující grafu modelu CodeDOM, volejte <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metoda zprostředkovatele kódu.</span><span class="sxs-lookup"><span data-stu-id="bde35-110">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="bde35-111">Tato metoda má parametr pro <xref:System.IO.TextWriter> používající ke generování zdrojového kódu, proto je někdy nutné nejprve vytvořit **TextWriter** je možné zapsat do.</span><span class="sxs-lookup"><span data-stu-id="bde35-111">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="bde35-112">Následující příklad ukazuje generování kódu z **vlastnosti CodeCompileUnit** a zápis do souboru s názvem HelloWorld.cs generovaný zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="bde35-112">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="bde35-113">Pomocí kódu zprostředkovatele CodeDOM kompilace sestavení</span><span class="sxs-lookup"><span data-stu-id="bde35-113">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="bde35-114">**Vyvolání kompilace**</span><span class="sxs-lookup"><span data-stu-id="bde35-114">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="bde35-115">Kompilace sestavení pomocí zprostředkovatele CodeDom, musí mít buď zdrojový kód v jazyce, pro které máte kompilátor zkompilovat nebo CodeDOM graf tento zdroj z lze vytvořit kód mohl zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="bde35-115">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="bde35-116">Pokud jsou kompilaci z grafu modelu CodeDOM, předat <xref:System.CodeDom.CodeCompileUnit> obsahující graf tak, aby <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> metoda zprostředkovatele kódu.</span><span class="sxs-lookup"><span data-stu-id="bde35-116">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="bde35-117">Pokud máte souboru zdrojového kódu v jazyce, který funguje s technologií kompilátor, předat název souboru, který obsahuje zdrojový kód, který <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metoda zprostředkovatele CodeDom.</span><span class="sxs-lookup"><span data-stu-id="bde35-117">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="bde35-118">Můžete také předat řetězec obsahující zdrojového kódu v jazyce, který kompilátor rozumí k <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> metoda zprostředkovatele CodeDom.</span><span class="sxs-lookup"><span data-stu-id="bde35-118">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="bde35-119">**Konfigurace parametrů kompilace**</span><span class="sxs-lookup"><span data-stu-id="bde35-119">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="bde35-120">Všechny standardní metody vyvolání kompilace zprostředkovatele CodeDom mít parametr typu <xref:System.CodeDom.Compiler.CompilerParameters> určující možnosti sloužící ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="bde35-120">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="bde35-121">Můžete zadat název souboru pro sestavení výstupu v <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> vlastnost **CompilerParameters**.</span><span class="sxs-lookup"><span data-stu-id="bde35-121">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="bde35-122">Jinak bude potřeba použít výchozí název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="bde35-122">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="bde35-123">Ve výchozím nastavení nový **CompilerParameters** inicializován s jeho <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> vlastnost nastavena na hodnotu **false**.</span><span class="sxs-lookup"><span data-stu-id="bde35-123">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="bde35-124">Pokud jsou kompilování spustitelný program, je nutné nastavit **GenerateExecutable** vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="bde35-124">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="bde35-125">Když **GenerateExecutable** je nastaven na **false**, vygeneruje kompilátor knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="bde35-125">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="bde35-126">Pokud jsou kompilování spustitelného souboru z grafu modelu CodeDOM, <xref:System.CodeDom.CodeEntryPointMethod> musí být definován v grafu.</span><span class="sxs-lookup"><span data-stu-id="bde35-126">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="bde35-127">Pokud existují více vstupních bodů kódu, může být potřeba nastavit <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> vlastnost **CompilerParameters** na název třídy, která definuje vstupní bod používat.</span><span class="sxs-lookup"><span data-stu-id="bde35-127">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="bde35-128">Chcete-li zahrnout informace o ladění generovaného spustitelný soubor, nastavte <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> vlastnost, která má **true**.</span><span class="sxs-lookup"><span data-stu-id="bde35-128">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="bde35-129">Pokud váš projekt odkazuje žádné sestavení, je nutné zadat názvy sestavení jako položky v <xref:System.Collections.Specialized.StringCollection> jako <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> vlastnost **CompilerParameters** použijete při vyvolání kompilace.</span><span class="sxs-lookup"><span data-stu-id="bde35-129">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="bde35-130">Zkompilujete sestavení, které je zapsán do paměť a místo na disku podle nastavení <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="bde35-130">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="bde35-131">Generování sestavení v paměti kódu můžete získat odkaz na generovaného sestavení z <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> vlastnost <xref:System.CodeDom.Compiler.CompilerResults>.</span><span class="sxs-lookup"><span data-stu-id="bde35-131">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="bde35-132">Pokud sestavení je zapsán do disku, můžete získat cestu vygenerované sestavení z <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> vlastnost **CompilerResults**.</span><span class="sxs-lookup"><span data-stu-id="bde35-132">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="bde35-133">Chcete-li zadat vlastní argumenty příkazového řádku řetězec pro použití při vyvolání kompilaci proces, nastavte řetězec v <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bde35-133">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="bde35-134">Pokud token zabezpečení Win32 je vyžadovaná k vyvolání proces kompilátoru, zadejte token v <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bde35-134">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="bde35-135">Odkaz zdrojového souboru Win32 do kompilované sestavení, zadejte název zdrojového souboru Win32 ve <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bde35-135">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="bde35-136">Chcete-li zadat úroveň pro upozornění, kdy má být zastavení kompilace, nastavte <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> vlastnost na celé číslo, které představuje úroveň pro upozornění, kdy má být zastavení kompilace.</span><span class="sxs-lookup"><span data-stu-id="bde35-136">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="bde35-137">Můžete také nakonfigurovat kompilátoru zastavit kompilace, pokud jsou zjištěna upozornění nastavením <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="bde35-137">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="bde35-138">Následující příklad kódu ukazuje kompilování zdrojového souboru pomocí zprostředkovatele CodeDom odvozené z <xref:System.CodeDom.Compiler.CodeDomProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="bde35-138">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="bde35-139">Jazyky, základem je podpora</span><span class="sxs-lookup"><span data-stu-id="bde35-139">Languages with Initial Support</span></span>  
 <span data-ttu-id="bde35-140">Rozhraní .NET Framework poskytuje kompilátory kódu a generátory kódu pro následující jazyky: C#, Visual Basic, C++ a JScript.</span><span class="sxs-lookup"><span data-stu-id="bde35-140">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="bde35-141">Podpora codeDOM lze rozšířit do jiných jazyků implementací generátory kódu jazyka a kompilátory kódu.</span><span class="sxs-lookup"><span data-stu-id="bde35-141">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bde35-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="bde35-142">See Also</span></span>  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [<span data-ttu-id="bde35-143">Dynamické vytváření a kompilování zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="bde35-143">Dynamic Source Code Generation and Compilation</span></span>](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [<span data-ttu-id="bde35-144">Stručná referenční příručka modelu codeDOM</span><span class="sxs-lookup"><span data-stu-id="bde35-144">CodeDOM Quick Reference</span></span>](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
