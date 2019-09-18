---
title: 'Postupy: Vytváření třídy pomocí modelu CodeDOM'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c932587c13532e14c956f3ebd058ae41d30519dc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046046"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="cb305-102">Postupy: Vytváření třídy pomocí modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="cb305-102">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="cb305-103">Následující postupy ukazují, jak vytvořit a zkompilovat graf CodeDOM, který generuje třídu obsahující dvě pole, tři vlastnosti, metodu, konstruktor a vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="cb305-103">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1. <span data-ttu-id="cb305-104">Vytvořte konzolovou aplikaci, která bude používat kód CodeDOM k vygenerování zdrojového kódu pro třídu.</span><span class="sxs-lookup"><span data-stu-id="cb305-104">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="cb305-105">V tomto příkladu je generována třída s `Sample`názvem a generovaný kód je třída s názvem `CodeDOMCreatedClass` v souboru s názvem SampleCode.</span><span class="sxs-lookup"><span data-stu-id="cb305-105">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2. <span data-ttu-id="cb305-106">Ve třídě generování proveďte inicializaci grafu CodeDOM a použijte metody CodeDOM k definování členů, konstruktoru a vstupního bodu (`Main` metody) generované třídy.</span><span class="sxs-lookup"><span data-stu-id="cb305-106">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="cb305-107">V tomto příkladu vygenerovaná třída má dvě pole, tři vlastnosti, konstruktor, metodu a `Main` metodu.</span><span class="sxs-lookup"><span data-stu-id="cb305-107">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3. <span data-ttu-id="cb305-108">Ve třídě generování vytvořte poskytovatele kódu specifického pro jazyk a zavolejte jeho <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodu pro generování kódu z grafu.</span><span class="sxs-lookup"><span data-stu-id="cb305-108">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4. <span data-ttu-id="cb305-109">Zkompilujte a spusťte aplikaci pro generování kódu.</span><span class="sxs-lookup"><span data-stu-id="cb305-109">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="cb305-110">V tomto příkladu je vygenerovaný kód v souboru s názvem SampleCode.</span><span class="sxs-lookup"><span data-stu-id="cb305-110">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="cb305-111">Zkompilujte a spusťte tento kód, aby se zobrazil ukázkový výstup.</span><span class="sxs-lookup"><span data-stu-id="cb305-111">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="cb305-112">Vytvoření aplikace, která spustí kód CodeDOM</span><span class="sxs-lookup"><span data-stu-id="cb305-112">To create the application that will execute the CodeDOM code</span></span>  
  
- <span data-ttu-id="cb305-113">Vytvořte třídu konzolové aplikace, která bude obsahovat kód CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="cb305-113">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="cb305-114">Definujte globální pole, která mají být použita ve třídě pro odkaz na sestavení (<xref:System.CodeDom.CodeCompileUnit>) a třídu (<xref:System.CodeDom.CodeTypeDeclaration>), zadejte název generovaného zdrojového `Main` souboru a deklarujte metodu.</span><span class="sxs-lookup"><span data-stu-id="cb305-114">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="cb305-115">Inicializace grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="cb305-115">To initialize the CodeDOM graph</span></span>  
  
- <span data-ttu-id="cb305-116">V konstruktoru třídy konzolové aplikace inicializujte sestavení a třídu a přidejte příslušné deklarace do grafu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="cb305-116">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="cb305-117">Přidání členů do grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="cb305-117">To add members to the CodeDOM graph</span></span>  
  
- <span data-ttu-id="cb305-118">Přidejte pole do grafu <xref:System.CodeDom.CodeMemberField> CodeDOM přidáním objektů <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> do vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="cb305-118">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- <span data-ttu-id="cb305-119">Přidejte vlastnosti do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberProperty> objektů <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> do vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="cb305-119">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- <span data-ttu-id="cb305-120">Přidejte metodu do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberMethod> objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> do vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="cb305-120">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- <span data-ttu-id="cb305-121">Přidejte konstruktor do grafu <xref:System.CodeDom.CodeConstructor> CodeDOM přidáním objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> do vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="cb305-121">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- <span data-ttu-id="cb305-122">Přidejte vstupní bod do grafu <xref:System.CodeDom.CodeEntryPointMethod> CodeDOM přidáním objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> do vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="cb305-122">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="cb305-123">Generování kódu z grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="cb305-123">To generate the code from the CodeDOM graph</span></span>  
  
- <span data-ttu-id="cb305-124">Vygenerujte zdrojový kód z grafu CodeDOM voláním <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cb305-124">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="cb305-125">Vytvoření grafu a generování kódu</span><span class="sxs-lookup"><span data-stu-id="cb305-125">To create the graph and generate the code</span></span>  
  
1. <span data-ttu-id="cb305-126">Přidejte metody vytvořené v předchozích krocích do `Main` metody definované v prvním kroku.</span><span class="sxs-lookup"><span data-stu-id="cb305-126">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. <span data-ttu-id="cb305-127">Zkompilujte a spusťte třídu generování.</span><span class="sxs-lookup"><span data-stu-id="cb305-127">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb305-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb305-128">Example</span></span>  
 <span data-ttu-id="cb305-129">Následující příklad kódu ukazuje kód z předchozích kroků.</span><span class="sxs-lookup"><span data-stu-id="cb305-129">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="cb305-130">Když je předchozí příklad kompilován a proveden, vytvoří následující zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="cb305-130">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="cb305-131">Generovaný zdrojový kód vytvoří následující výstup, když je zkompilován a proveden.</span><span class="sxs-lookup"><span data-stu-id="cb305-131">The generated source code produces the following output when compiled and executed.</span></span>  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb305-132">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cb305-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="cb305-133">Tento příklad kódu vyžaduje `FullTrust` úspěšné provedení sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="cb305-133">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb305-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb305-134">See also</span></span>

- [<span data-ttu-id="cb305-135">Použití modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="cb305-135">Using the CodeDOM</span></span>](using-the-codedom.md)
- [<span data-ttu-id="cb305-136">Generování a kompilace zdrojového kódu z grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="cb305-136">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)
