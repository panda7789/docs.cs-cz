---
title: 'Postupy: Vytváření třídy pomocí modelu CodeDOM'
description: Přečtěte si podrobný příklad, který vysvětluje, jak vytvořit třídu pomocí Code Document Object Model (CodeDOM).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
ms.openlocfilehash: 3d7151d384402dba6fbb5da8fe54621346251f7b
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865304"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="f80b4-103">Postupy: Vytváření třídy pomocí modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f80b4-103">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="f80b4-104">Následující postupy ukazují, jak vytvořit a zkompilovat graf CodeDOM, který generuje třídu obsahující dvě pole, tři vlastnosti, metodu, konstruktor a vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="f80b4-104">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1. <span data-ttu-id="f80b4-105">Vytvořte konzolovou aplikaci, která bude používat kód CodeDOM k vygenerování zdrojového kódu pro třídu.</span><span class="sxs-lookup"><span data-stu-id="f80b4-105">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="f80b4-106">V tomto příkladu je generována třída s názvem `Sample` a generovaný kód je třída s názvem `CodeDOMCreatedClass` v souboru s názvem SampleCode.</span><span class="sxs-lookup"><span data-stu-id="f80b4-106">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2. <span data-ttu-id="f80b4-107">Ve třídě generování proveďte inicializaci grafu CodeDOM a použijte metody CodeDOM k definování členů, konstruktoru a vstupního bodu ( `Main` metody) generované třídy.</span><span class="sxs-lookup"><span data-stu-id="f80b4-107">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="f80b4-108">V tomto příkladu vygenerovaná třída má dvě pole, tři vlastnosti, konstruktor, metodu a `Main` metodu.</span><span class="sxs-lookup"><span data-stu-id="f80b4-108">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3. <span data-ttu-id="f80b4-109">Ve třídě generování vytvořte poskytovatele kódu specifického pro jazyk a zavolejte jeho <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodu pro generování kódu z grafu.</span><span class="sxs-lookup"><span data-stu-id="f80b4-109">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4. <span data-ttu-id="f80b4-110">Zkompilujte a spusťte aplikaci pro generování kódu.</span><span class="sxs-lookup"><span data-stu-id="f80b4-110">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="f80b4-111">V tomto příkladu je vygenerovaný kód v souboru s názvem SampleCode.</span><span class="sxs-lookup"><span data-stu-id="f80b4-111">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="f80b4-112">Zkompilujte a spusťte tento kód, aby se zobrazil ukázkový výstup.</span><span class="sxs-lookup"><span data-stu-id="f80b4-112">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="f80b4-113">Vytvoření aplikace, která spustí kód CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f80b4-113">To create the application that will execute the CodeDOM code</span></span>  
  
- <span data-ttu-id="f80b4-114">Vytvořte třídu konzolové aplikace, která bude obsahovat kód CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="f80b4-114">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="f80b4-115">Definujte globální pole, která mají být použita ve třídě pro odkaz na sestavení ( <xref:System.CodeDom.CodeCompileUnit> ) a třídu ( <xref:System.CodeDom.CodeTypeDeclaration> ), zadejte název generovaného zdrojového souboru a deklarujte `Main` metodu.</span><span class="sxs-lookup"><span data-stu-id="f80b4-115">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="f80b4-116">Inicializace grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f80b4-116">To initialize the CodeDOM graph</span></span>  
  
- <span data-ttu-id="f80b4-117">V konstruktoru třídy konzolové aplikace inicializujte sestavení a třídu a přidejte příslušné deklarace do grafu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="f80b4-117">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="f80b4-118">Přidání členů do grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f80b4-118">To add members to the CodeDOM graph</span></span>  
  
- <span data-ttu-id="f80b4-119">Přidejte pole do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberField> objektů do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="f80b4-119">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- <span data-ttu-id="f80b4-120">Přidejte vlastnosti do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberProperty> objektů do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="f80b4-120">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- <span data-ttu-id="f80b4-121">Přidejte metodu do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberMethod> objektu do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="f80b4-121">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- <span data-ttu-id="f80b4-122">Přidejte konstruktor do grafu CodeDOM přidáním <xref:System.CodeDom.CodeConstructor> objektu do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="f80b4-122">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- <span data-ttu-id="f80b4-123">Přidejte vstupní bod do grafu CodeDOM přidáním <xref:System.CodeDom.CodeEntryPointMethod> objektu do <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="f80b4-123">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="f80b4-124">Generování kódu z grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f80b4-124">To generate the code from the CodeDOM graph</span></span>  
  
- <span data-ttu-id="f80b4-125">Vygenerujte zdrojový kód z grafu CodeDOM voláním <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f80b4-125">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="f80b4-126">Vytvoření grafu a generování kódu</span><span class="sxs-lookup"><span data-stu-id="f80b4-126">To create the graph and generate the code</span></span>  
  
1. <span data-ttu-id="f80b4-127">Přidejte metody vytvořené v předchozích krocích do `Main` metody definované v prvním kroku.</span><span class="sxs-lookup"><span data-stu-id="f80b4-127">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. <span data-ttu-id="f80b4-128">Zkompilujte a spusťte třídu generování.</span><span class="sxs-lookup"><span data-stu-id="f80b4-128">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f80b4-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="f80b4-129">Example</span></span>  
 <span data-ttu-id="f80b4-130">Následující příklad kódu ukazuje kód z předchozích kroků.</span><span class="sxs-lookup"><span data-stu-id="f80b4-130">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="f80b4-131">Když je předchozí příklad kompilován a proveden, vytvoří následující zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="f80b4-131">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="f80b4-132">Generovaný zdrojový kód vytvoří následující výstup, když je zkompilován a proveden.</span><span class="sxs-lookup"><span data-stu-id="f80b4-132">The generated source code produces the following output when compiled and executed.</span></span>  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f80b4-133">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f80b4-133">Compiling the Code</span></span>  
  
- <span data-ttu-id="f80b4-134">Tento příklad kódu vyžaduje `FullTrust` úspěšné provedení sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="f80b4-134">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f80b4-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="f80b4-135">See also</span></span>

- [<span data-ttu-id="f80b4-136">Použití modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f80b4-136">Using the CodeDOM</span></span>](using-the-codedom.md)
- [<span data-ttu-id="f80b4-137">Generování a kompilace zdrojového kódu z grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="f80b4-137">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)
