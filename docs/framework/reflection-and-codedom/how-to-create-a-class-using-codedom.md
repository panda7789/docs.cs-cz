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
ms.openlocfilehash: 906007902c6b66d88da0d3145625e56f2a7e2b55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592521"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="49265-102">Postupy: Vytváření třídy pomocí modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="49265-102">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="49265-103">Následující postupy ukazují, jak vytvořit a zkompilujte grafu CodeDOM, který generuje třídy obsahující dvě pole, tři vlastnosti, metody, konstruktor a vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="49265-103">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1. <span data-ttu-id="49265-104">Vytvořte konzolovou aplikaci, která se použije k vygenerování zdrojového kódu pro třídu kódu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="49265-104">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="49265-105">V tomto příkladu je pojmenována generování třídy `Sample`, a třídu s názvem je generovaný kód `CodeDOMCreatedClass` do souboru s názvem SampleCode.</span><span class="sxs-lookup"><span data-stu-id="49265-105">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2. <span data-ttu-id="49265-106">V generování třídy, inicializovat grafu CodeDOM a použitím metody CodeDOM definovat členy, konstruktor a vstupního bodu (`Main` metoda) generované třídy.</span><span class="sxs-lookup"><span data-stu-id="49265-106">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="49265-107">V tomto příkladu má generované třídy, dvě pole, tři vlastnosti, konstruktor, metody a `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="49265-107">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3. <span data-ttu-id="49265-108">V generování třídy, vytvořit poskytovatele kódu specifické pro jazyk a volání jeho <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metoda ke generování kódu z grafu.</span><span class="sxs-lookup"><span data-stu-id="49265-108">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4. <span data-ttu-id="49265-109">Kompilace a spuštění aplikace pro generování kódu.</span><span class="sxs-lookup"><span data-stu-id="49265-109">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="49265-110">V tomto příkladu je generovaný kód do souboru s názvem SampleCode.</span><span class="sxs-lookup"><span data-stu-id="49265-110">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="49265-111">Kompilace a spuštění tohoto kódu zobrazíte ukázkový výstup.</span><span class="sxs-lookup"><span data-stu-id="49265-111">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="49265-112">Chcete-li vytvořit aplikaci, která spustí kód modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="49265-112">To create the application that will execute the CodeDOM code</span></span>  
  
- <span data-ttu-id="49265-113">Vytvořte třídu konzoly aplikace tak, aby obsahovala kód CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="49265-113">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="49265-114">Definovat globální pole, které mají být použity ve třídě tak, aby odkazovaly sestavení (<xref:System.CodeDom.CodeCompileUnit>) a třídy (<xref:System.CodeDom.CodeTypeDeclaration>), zadejte název vytvořeném zdrojovém souboru a deklarovat `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="49265-114">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="49265-115">Inicializace grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="49265-115">To initialize the CodeDOM graph</span></span>  
  
- <span data-ttu-id="49265-116">V konstruktoru pro třídu aplikace konzoly inicializace sestavení a třídy a přidejte odpovídající deklarace do grafu CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="49265-116">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="49265-117">Postup přidání členů do grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="49265-117">To add members to the CodeDOM graph</span></span>  
  
- <span data-ttu-id="49265-118">Přidat pole do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberField> objektů <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.</span><span class="sxs-lookup"><span data-stu-id="49265-118">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- <span data-ttu-id="49265-119">Přidání vlastností do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberProperty> objektů <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.</span><span class="sxs-lookup"><span data-stu-id="49265-119">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- <span data-ttu-id="49265-120">Přidání metody do grafu CodeDOM tak, že přidáte <xref:System.CodeDom.CodeMemberMethod> objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.</span><span class="sxs-lookup"><span data-stu-id="49265-120">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- <span data-ttu-id="49265-121">Přidejte konstruktor do grafu CodeDOM tak, že přidáte <xref:System.CodeDom.CodeConstructor> objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.</span><span class="sxs-lookup"><span data-stu-id="49265-121">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- <span data-ttu-id="49265-122">Přidat vstupní bod na grafu CodeDOM tak, že přidáte <xref:System.CodeDom.CodeEntryPointMethod> objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.</span><span class="sxs-lookup"><span data-stu-id="49265-122">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="49265-123">Ke generování kódu z grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="49265-123">To generate the code from the CodeDOM graph</span></span>  
  
- <span data-ttu-id="49265-124">Vygenerování zdrojového kódu z grafu modelu CodeDOM voláním <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="49265-124">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="49265-125">K vytvoření grafu a generování kódu</span><span class="sxs-lookup"><span data-stu-id="49265-125">To create the graph and generate the code</span></span>  
  
1. <span data-ttu-id="49265-126">Přidejte metody, které jsou vytvořené v předchozích kroků `Main` metody definované v prvním kroku.</span><span class="sxs-lookup"><span data-stu-id="49265-126">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. <span data-ttu-id="49265-127">Zkompilovat a spustit při generování třídy.</span><span class="sxs-lookup"><span data-stu-id="49265-127">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49265-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="49265-128">Example</span></span>  
 <span data-ttu-id="49265-129">Následující příklad kódu ukazuje kód z předchozích kroků.</span><span class="sxs-lookup"><span data-stu-id="49265-129">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="49265-130">Když v předchozím příkladu je kompilován a spuštěn, vytvoří následující zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="49265-130">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="49265-131">Generovaného zdrojového kódu vytvoří následující výstup při zkompilovat a spustit.</span><span class="sxs-lookup"><span data-stu-id="49265-131">The generated source code produces the following output when compiled and executed.</span></span>  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49265-132">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="49265-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="49265-133">Tento příklad kódu vyžaduje `FullTrust` oprávnění nastaveno na hodnotu úspěšně vykonat.</span><span class="sxs-lookup"><span data-stu-id="49265-133">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49265-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49265-134">See also</span></span>

- [<span data-ttu-id="49265-135">Použití modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="49265-135">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)
- [<span data-ttu-id="49265-136">Generování a kompilace zdrojového kódu z grafu modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="49265-136">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
