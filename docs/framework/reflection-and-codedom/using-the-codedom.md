---
title: Použití modelu CodeDOM
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 336a0fb5bc0fca5dd6ef917a2eeaf0908680d12b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591489"
---
# <a name="using-the-codedom"></a><span data-ttu-id="1bab7-102">Použití modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1bab7-102">Using the CodeDOM</span></span>
<span data-ttu-id="1bab7-103">CodeDOM obsahuje typy, které představují běžné typy prvků zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="1bab7-103">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="1bab7-104">Můžete navrhnout program, který vytváří model zdrojového kódu pomocí prvků CodeDOM k sestavení grafu objektu.</span><span class="sxs-lookup"><span data-stu-id="1bab7-104">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="1bab7-105">Tento graf objektu lze vykreslit jako zdrojový kód pomocí generátoru kódu CodeDOM pro podporovaný programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="1bab7-105">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="1bab7-106">CodeDOM lze použít také ke kompilaci zdrojového kódu do binárního sestavení.</span><span class="sxs-lookup"><span data-stu-id="1bab7-106">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="1bab7-107">Mezi běžné použití CodeDOM patří:</span><span class="sxs-lookup"><span data-stu-id="1bab7-107">Some common uses for the CodeDOM include:</span></span>  
  
- <span data-ttu-id="1bab7-108">Generování kódu z šablon: generování kódu pro ASP.NET, proxy klienta služby XML webových, průvodci kódem, návrháře nebo další mechanismy vytvářející kód.</span><span class="sxs-lookup"><span data-stu-id="1bab7-108">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
- <span data-ttu-id="1bab7-109">Dynamická kompilace: podpora kompilace kódu v jednom nebo více jazyků.</span><span class="sxs-lookup"><span data-stu-id="1bab7-109">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="1bab7-110">Vytváření grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1bab7-110">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="1bab7-111"><xref:System.CodeDom> Obor názvů poskytuje třídám pro reprezentaci logické struktury zdrojového kódu, nezávisle na syntaxi jazyka.</span><span class="sxs-lookup"><span data-stu-id="1bab7-111">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="1bab7-112">Struktura grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1bab7-112">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="1bab7-113">Struktura grafu CodeDOM je jako strom kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="1bab7-113">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="1bab7-114">Úplně nahoře, nebo kořenový, kontejner každého kompilovatelného grafu CodeDOM je <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="1bab7-114">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="1bab7-115">Každý prvek modelu zdrojového kódu musí být spojen s grafem pomocí vlastnosti <xref:System.CodeDom.CodeObject> v grafu.</span><span class="sxs-lookup"><span data-stu-id="1bab7-115">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="1bab7-116">Sestavení modelu zdrojového kódu pro vzorový Program Hello World</span><span class="sxs-lookup"><span data-stu-id="1bab7-116">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="1bab7-117">Následující návod znázorňuje, jak vytvořit graf objektu CodeDOM, který představuje kód pro jednoduchou aplikaci Hello World.</span><span class="sxs-lookup"><span data-stu-id="1bab7-117">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="1bab7-118">Úplný zdrojový kód pro tento příklad kódu, najdete v článku <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> tématu.</span><span class="sxs-lookup"><span data-stu-id="1bab7-118">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="1bab7-119">Vytvoří jednotku kompilace</span><span class="sxs-lookup"><span data-stu-id="1bab7-119">Creating a compile unit</span></span>  
 <span data-ttu-id="1bab7-120">CodeDOM definuje objekt zvaný <xref:System.CodeDom.CodeCompileUnit>, který může odkazovat na graf objektu CodeDOM, který modeluje zdrojový kód pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="1bab7-120">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="1bab7-121">A **CodeCompileUnit** má vlastnosti pro ukládání odkazů na atributy, obory názvů a sestavení.</span><span class="sxs-lookup"><span data-stu-id="1bab7-121">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="1bab7-122">Poskytovatelé CodeDom, které jsou odvozeny z <xref:System.CodeDom.Compiler.CodeDomProvider> třída obsahuje metody, které zpracovávají graf objektu odkazovaný **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="1bab7-122">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="1bab7-123">Chcete-li vytvořit grafu objektů pro jednoduchou aplikaci, musíte sestavit model zdrojového kódu a odkazovat na něj z **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="1bab7-123">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="1bab7-124">Novou jednotku sestavení můžete vytvořit pomocí syntaxe předvedené v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="1bab7-124">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="1bab7-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> může obsahovat část zdrojového kódu, který je již v cílovém jazyce, ale nelze ji vykreslit do jiného jazyka.</span><span class="sxs-lookup"><span data-stu-id="1bab7-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="1bab7-126">Definování oboru názvů</span><span class="sxs-lookup"><span data-stu-id="1bab7-126">Defining a namespace</span></span>  
 <span data-ttu-id="1bab7-127">Chcete-li definovat obor názvů, vytvořte <xref:System.CodeDom.CodeNamespace> a přiřaďte název pomocí odpovídajícího konstruktoru nebo nastavením jeho **název** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1bab7-127">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="1bab7-128">Import oboru názvů</span><span class="sxs-lookup"><span data-stu-id="1bab7-128">Importing a namespace</span></span>  
 <span data-ttu-id="1bab7-129">Chcete-li přidat direktivu import oboru názvů do oboru názvů, přidejte <xref:System.CodeDom.CodeNamespaceImport> , která určuje obor názvů pro import do **CodeNamespace.Imports** kolekce.</span><span class="sxs-lookup"><span data-stu-id="1bab7-129">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="1bab7-130">Následující kód přidává import pro **systému** obor názvů, aby **importy** kolekce **CodeNamespace** s názvem `samples`:</span><span class="sxs-lookup"><span data-stu-id="1bab7-130">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="1bab7-131">Propojování prvků kódu do grafu objektu</span><span class="sxs-lookup"><span data-stu-id="1bab7-131">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="1bab7-132">Všechny prvky kódu, které tvoří graf CodeDOM musí být propojen <xref:System.CodeDom.CodeCompileUnit> , který je kořenovým prvkem stromu, řadou odkazů mezi prvky přímo odkazovanými z vlastností kořenového objektu grafu.</span><span class="sxs-lookup"><span data-stu-id="1bab7-132">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="1bab7-133">Nastavte objekt na vlastnost objektu kontejneru pro vytvoření odkazu z objektu kontejneru.</span><span class="sxs-lookup"><span data-stu-id="1bab7-133">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="1bab7-134">Následující příkaz přidá `samples` **CodeNamespace** k **obory názvů** vlastnost kolekce kořenové **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="1bab7-134">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="1bab7-135">Definování typu</span><span class="sxs-lookup"><span data-stu-id="1bab7-135">Defining a type</span></span>  
 <span data-ttu-id="1bab7-136">Chcete-li deklarovat třídu, strukturu, rozhraní nebo výčet pomocí CodeDOM, vytvořte nový <xref:System.CodeDom.CodeTypeDeclaration>a přiřaďte jí název.</span><span class="sxs-lookup"><span data-stu-id="1bab7-136">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="1bab7-137">Následující příklad to ukazuje pomocí přetížení konstruktoru k nastavení **název** vlastnost:</span><span class="sxs-lookup"><span data-stu-id="1bab7-137">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="1bab7-138">Chcete-li přidat typ do oboru názvů, přidejte <xref:System.CodeDom.CodeTypeDeclaration> , který představuje typ, který chcete přidat do oboru názvů **typy** kolekce **CodeNamespace**.</span><span class="sxs-lookup"><span data-stu-id="1bab7-138">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="1bab7-139">Následující příklad ukazuje, jak přidat třídu s názvem `class1` k **CodeNamespace** s názvem `samples`:</span><span class="sxs-lookup"><span data-stu-id="1bab7-139">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="1bab7-140">Přidání členů třídy do třídy</span><span class="sxs-lookup"><span data-stu-id="1bab7-140">Adding class members to a class</span></span>  
 <span data-ttu-id="1bab7-141"><xref:System.CodeDom> Obor názvů poskytuje celou řadu prvků, které lze použít k reprezentaci členů třídy.</span><span class="sxs-lookup"><span data-stu-id="1bab7-141">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="1bab7-142">Každý člen třídy mohou být přidány do **členy** kolekce <xref:System.CodeDom.CodeTypeDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="1bab7-142">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="1bab7-143">Definování kódu metody vstupního bodu pro spustitelný soubor</span><span class="sxs-lookup"><span data-stu-id="1bab7-143">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="1bab7-144">Pokud vytváříte kód spustitelného programu, je nezbytné uvést vstupní bod programu vytvořením <xref:System.CodeDom.CodeEntryPointMethod> pro reprezentaci metody, který program spustit provádění.</span><span class="sxs-lookup"><span data-stu-id="1bab7-144">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="1bab7-145">Následující příklad ukazuje, jak definovat metodu vstupního bodu, který obsahuje <xref:System.CodeDom.CodeMethodInvokeExpression> , která volá **System.Console.WriteLine** tisknout "Hello World!":</span><span class="sxs-lookup"><span data-stu-id="1bab7-145">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="1bab7-146">Následující příkaz přidá metodu vstupního bodu s názvem `Start` k **členy** kolekce `class1`:</span><span class="sxs-lookup"><span data-stu-id="1bab7-146">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="1bab7-147">Nyní <xref:System.CodeDom.CodeCompileUnit> s názvem `compileUnit` obsahuje graf CodeDOM pro jednoduchý program Hello World.</span><span class="sxs-lookup"><span data-stu-id="1bab7-147">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="1bab7-148">Informace o generování a kompilaci kódu z grafu CodeDOM naleznete v tématu [generování zdrojového kódu a kompilace programu grafu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span><span class="sxs-lookup"><span data-stu-id="1bab7-148">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="1bab7-149">Další informace o vytváření grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="1bab7-149">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="1bab7-150">CodeDOM podporuje mnoho běžných typů prvků kódu v programovacích jazycích, které podporují modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1bab7-150">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="1bab7-151">CodeDOM nebyl navržen, aby poskytoval prvky představující všechny možné funkce programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="1bab7-151">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="1bab7-152">Kód, který nelze snadno reprezentovat prvky CodeDOM lze zapouzdřit <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, nebo <xref:System.CodeDom.CodeSnippetCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="1bab7-152">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="1bab7-153">Nicméně fragmenty kódu nelze přeložit do jiných jazyků automaticky pomocí CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="1bab7-153">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="1bab7-154">Dokumentace pro každý z typů CodeDOM naleznete v tématu v referenční dokumentaci <xref:System.CodeDom> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1bab7-154">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="1bab7-155">Rychlý graf pro nalezení prvku CodeDOM, který představuje určitý typ prvku kódu, najdete v článku [CodeDOM – Stručná referenční příručka](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1bab7-155">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span></span>
