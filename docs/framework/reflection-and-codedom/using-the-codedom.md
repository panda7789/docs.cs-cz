---
title: "Použití modelu CodeDOM"
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
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cd2b8e8ecb0e5d451ebf3c6823144e4a90e0d79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="using-the-codedom"></a><span data-ttu-id="4c359-102">Použití modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="4c359-102">Using the CodeDOM</span></span>
<span data-ttu-id="4c359-103">Modelu CodeDOM obsahuje typy, které představují mnoho běžných typů elementy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4c359-103">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="4c359-104">Můžete navrhnout program, který vytvoří model zdrojového kódu pomocí modelu CodeDOM elementů ke kompilaci grafu objektu.</span><span class="sxs-lookup"><span data-stu-id="4c359-104">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="4c359-105">Tento objekt graf lze vykreslit jako zdrojový kód pomocí modelu CodeDOM generátor kódu pro podporované programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="4c359-105">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="4c359-106">Modelu CodeDOM můžete použít také ke kompilaci zdrojového kódu do binární sestavení.</span><span class="sxs-lookup"><span data-stu-id="4c359-106">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="4c359-107">Některé běžné použití modelu CodeDOM patří:</span><span class="sxs-lookup"><span data-stu-id="4c359-107">Some common uses for the CodeDOM include:</span></span>  
  
-   <span data-ttu-id="4c359-108">Generování kódu s použitím šablon: generování kódu pro ASP.NET, XML webové proxy servery služeb klienta, průvodců kódem, Designer nebo další mechanismy pro generování kódu.</span><span class="sxs-lookup"><span data-stu-id="4c359-108">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
-   <span data-ttu-id="4c359-109">Dynamická kompilace: podpora kompilace kódu v jedné nebo více jazyků.</span><span class="sxs-lookup"><span data-stu-id="4c359-109">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="4c359-110">Vytvoření grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="4c359-110">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="4c359-111"><xref:System.CodeDom> Obor názvů obsahuje třídy představující logické struktury zdrojového kódu nezávislé na syntaxi jazyka.</span><span class="sxs-lookup"><span data-stu-id="4c359-111">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="4c359-112">Struktura grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="4c359-112">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="4c359-113">Struktura grafu modelu CodeDOM je jako stromu kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="4c359-113">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="4c359-114">Nejvyšší, nebo je kontejner každý kompilační grafu modelu CodeDOM kořenový adresář, <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="4c359-114">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="4c359-115">Každý element, zdrojový kód modelu musí být propojena na graf prostřednictvím vlastnosti <xref:System.CodeDom.CodeObject> v grafu.</span><span class="sxs-lookup"><span data-stu-id="4c359-115">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="4c359-116">Vytváření Model zdrojového kódu pro ukázka programu Hello World</span><span class="sxs-lookup"><span data-stu-id="4c359-116">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="4c359-117">Následující postup poskytuje příklad k vytvoření grafu modelu CodeDOM objekt, který představuje kód pro jednoduchou aplikaci Hello World.</span><span class="sxs-lookup"><span data-stu-id="4c359-117">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="4c359-118">Úplný zdrojový kód pro tento příklad kódu, najdete v článku <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> tématu.</span><span class="sxs-lookup"><span data-stu-id="4c359-118">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="4c359-119">Vytváření jednotka kompilace</span><span class="sxs-lookup"><span data-stu-id="4c359-119">Creating a compile unit</span></span>  
 <span data-ttu-id="4c359-120">Modelu CodeDOM definuje objektu s názvem <xref:System.CodeDom.CodeCompileUnit>, který může odkazovat grafu modelu CodeDOM objekt modelů zdrojového kódu ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="4c359-120">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="4c359-121">A **vlastnosti CodeCompileUnit** má vlastnosti pro ukládání odkazů na sestavení, atributy a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="4c359-121">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="4c359-122">Zprostředkovatele CodeDom, které jsou odvozeny od <xref:System.CodeDom.Compiler.CodeDomProvider> třída obsahuje metody, které zpracovávají grafu objektu odkazuje **vlastnosti CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="4c359-122">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="4c359-123">K vytvoření grafu objektu pro jednoduchou aplikaci, sestavte kód modelu zdroje a odkazovat z **vlastnosti CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="4c359-123">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="4c359-124">Můžete vytvořit novou jednotku kompilace pomocí syntaxe ukázáno v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="4c359-124">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="4c359-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> může obsahovat části zdrojový kód, který je již v jazyce target, ale nemůže být vykreslen na jiný jazyk.</span><span class="sxs-lookup"><span data-stu-id="4c359-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="4c359-126">Definování oboru názvů</span><span class="sxs-lookup"><span data-stu-id="4c359-126">Defining a namespace</span></span>  
 <span data-ttu-id="4c359-127">Definici oboru názvů, vytvoření <xref:System.CodeDom.CodeNamespace> a přiřadit název pro pomocí vhodný konstruktor nebo nastavením jeho **název** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4c359-127">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="4c359-128">Import oboru názvů</span><span class="sxs-lookup"><span data-stu-id="4c359-128">Importing a namespace</span></span>  
 <span data-ttu-id="4c359-129">Chcete-li přidat direktivu import oboru názvů do oboru názvů, přidejte <xref:System.CodeDom.CodeNamespaceImport> určující importovat do oboru názvů **CodeNamespace.Imports** kolekce.</span><span class="sxs-lookup"><span data-stu-id="4c359-129">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="4c359-130">Následující kód přidá importu pro **systému** názvů **importy** kolekce **CodeNamespace** s názvem `samples`:</span><span class="sxs-lookup"><span data-stu-id="4c359-130">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="4c359-131">Propojování elementy kódu do grafu objektů</span><span class="sxs-lookup"><span data-stu-id="4c359-131">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="4c359-132">Všechny elementy kódu, které vytvářejí grafu modelu CodeDOM musí být propojena s <xref:System.CodeDom.CodeCompileUnit> tedy kořenový prvek stromu pomocí řady odkazů mezi elementy přímo na něj odkazovat z vlastnosti kořenový objekt grafu.</span><span class="sxs-lookup"><span data-stu-id="4c359-132">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="4c359-133">Nastavení objektu na vlastnost objektu kontejneru vytvořit odkaz z objektu kontejneru.</span><span class="sxs-lookup"><span data-stu-id="4c359-133">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="4c359-134">Následující příkaz přidá `samples` **CodeNamespace** k **obory názvů** vlastnost kolekce kořenové **vlastnosti CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="4c359-134">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="4c359-135">Definování typu</span><span class="sxs-lookup"><span data-stu-id="4c359-135">Defining a type</span></span>  
 <span data-ttu-id="4c359-136">Deklarace třídy, struktury, rozhraní nebo pomocí modelu CodeDOM – výčet, vytvořte novou <xref:System.CodeDom.CodeTypeDeclaration>a přiřaďte ho název.</span><span class="sxs-lookup"><span data-stu-id="4c359-136">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="4c359-137">Následující příklad ukazuje to pomocí přetížení konstruktoru, chcete-li nastavit **název** vlastnost:</span><span class="sxs-lookup"><span data-stu-id="4c359-137">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="4c359-138">Přidání typu do oboru názvů, přidejte <xref:System.CodeDom.CodeTypeDeclaration> , která představuje typ pro přidání do oboru názvů **typy** kolekce **CodeNamespace**.</span><span class="sxs-lookup"><span data-stu-id="4c359-138">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="4c359-139">Následující příklad ukazuje, jak přidat třídu s názvem `class1` k **CodeNamespace** s názvem `samples`:</span><span class="sxs-lookup"><span data-stu-id="4c359-139">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="4c359-140">Přidávání do třídy členy třídy</span><span class="sxs-lookup"><span data-stu-id="4c359-140">Adding class members to a class</span></span>  
 <span data-ttu-id="4c359-141"><xref:System.CodeDom> Obor názvů obsahuje různé elementy, které můžete použít k reprezentování členy třídy.</span><span class="sxs-lookup"><span data-stu-id="4c359-141">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="4c359-142">Každý člen třídy mohou být přidány do **členy** kolekce <xref:System.CodeDom.CodeTypeDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="4c359-142">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="4c359-143">Definování metodu kód vstupní bod pro spustitelný soubor</span><span class="sxs-lookup"><span data-stu-id="4c359-143">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="4c359-144">Pokud vytváříte kód pro spustitelný program, je nezbytné k označení vstupní bod programu tak, že vytvoříte <xref:System.CodeDom.CodeEntryPointMethod> představují metodu na program, který by měl začínat provádění.</span><span class="sxs-lookup"><span data-stu-id="4c359-144">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="4c359-145">Následující příklad ukazuje, jak definovat metodu vstupního bodu, která obsahuje <xref:System.CodeDom.CodeMethodInvokeExpression> , který volá **System.Console.WriteLine** tisknout "Hello, World!":</span><span class="sxs-lookup"><span data-stu-id="4c359-145">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="4c359-146">Následující příkaz přidá metoda s názvem `Start` k **členy** kolekce `class1`:</span><span class="sxs-lookup"><span data-stu-id="4c359-146">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="4c359-147">Nyní <xref:System.CodeDom.CodeCompileUnit> s názvem `compileUnit` obsahuje grafu modelu CodeDOM jednoduché programu Hello World.</span><span class="sxs-lookup"><span data-stu-id="4c359-147">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="4c359-148">Informace o generování a kompilace kódu z grafu modelu CodeDOM najdete v tématu [zdrojový kód generování a kompilace programu z grafu modelu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span><span class="sxs-lookup"><span data-stu-id="4c359-148">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="4c359-149">Další informace o vytváření grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="4c359-149">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="4c359-150">Modelu CodeDOM podporuje mnoho běžných typů elementy kódu v programovacích jazyků, které podporují modul common language runtime nalezen.</span><span class="sxs-lookup"><span data-stu-id="4c359-150">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="4c359-151">Modelu CodeDOM nebyla určená k poskytnutí prvky představující všechny možné programovací jazyk funkce.</span><span class="sxs-lookup"><span data-stu-id="4c359-151">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="4c359-152">Kód, který nelze snadno pomocí modelu CodeDOM elementy můžete zapouzdřené v <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, nebo <xref:System.CodeDom.CodeSnippetCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="4c359-152">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="4c359-153">Ale fragmenty nelze přeložit na ostatních jazyků automaticky pomocí modelu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="4c359-153">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="4c359-154">Dokumentace pro každou z typů CodeDOM, najdete v referenční dokumentaci k nástroji pro <xref:System.CodeDom> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4c359-154">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="4c359-155">V rychlé grafu najít CodeDOM elementu, který představuje konkrétní typ elementu kód, najdete v článku [Stručná referenční příručka CodeDOM](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524).</span><span class="sxs-lookup"><span data-stu-id="4c359-155">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524).</span></span>
