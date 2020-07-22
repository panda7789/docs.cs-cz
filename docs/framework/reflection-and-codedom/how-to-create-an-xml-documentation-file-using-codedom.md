---
title: 'Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM'
description: V tomto podrobném příkladu naleznete informace v tématu Jak vygenerovat kód, který vytvoří soubor dokumentace XML pomocí Code Document Object Model (CodeDOM).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
ms.openlocfilehash: f905b996910c6cfbc62378cc4cd6bb8c0e0e6fd4
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865148"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="ba144-103">Postupy: vytvoření souboru dokumentace XML pomocí CodeDOM</span><span class="sxs-lookup"><span data-stu-id="ba144-103">How to: Create an XML documentation file using CodeDOM</span></span>

<span data-ttu-id="ba144-104">CodeDOM lze použít k vytvoření kódu, který generuje dokumentaci XML.</span><span class="sxs-lookup"><span data-stu-id="ba144-104">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="ba144-105">Proces zahrnuje vytvoření grafu CodeDOM, který obsahuje dokumentační komentáře XML, generování kódu a kompilování generovaného kódu s možností kompilátoru, která vytvoří výstup dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="ba144-105">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
## <a name="create-a-codedom-graph"></a><span data-ttu-id="ba144-106">Vytvoření grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="ba144-106">Create a CodeDOM graph</span></span>
  
1. <span data-ttu-id="ba144-107">Vytvořte objekt <xref:System.CodeDom.CodeCompileUnit> obsahující graf CodeDom pro ukázkovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ba144-107">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="ba144-108">Použijte <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktor s `docComment` parametrem nastaveným na `true` k vytvoření prvků komentáře XML dokumentace a text.</span><span class="sxs-lookup"><span data-stu-id="ba144-108">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="ba144-109">Generování kódu z CodeCompileUnit</span><span class="sxs-lookup"><span data-stu-id="ba144-109">Generate the code from the CodeCompileUnit</span></span>
  
1. <span data-ttu-id="ba144-110">Použijte <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodu pro vytvoření kódu a vytvoření zdrojového souboru, který se má zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="ba144-110">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="ba144-111">Zkompiluje kód a vygeneruje soubor dokumentace.</span><span class="sxs-lookup"><span data-stu-id="ba144-111">Compile the code and generate the documentation file</span></span>
  
1. <span data-ttu-id="ba144-112">Přidejte možnost kompilátoru **/doc** do <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters> objektu a předejte objekt <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metodě pro vytvoření souboru dokumentace XML při kompilování kódu.</span><span class="sxs-lookup"><span data-stu-id="ba144-112">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="ba144-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba144-113">Example</span></span>

<span data-ttu-id="ba144-114">Následující příklad kódu vytvoří graf CodeDOM s komentáři k dokumentaci, vygeneruje soubor kódu z grafu a zkompiluje soubor a vytvoří přidružený soubor dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="ba144-114">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="ba144-115">Příklad kódu vytvoří v souboru *HelloWorldDoc.xml* následující dokumentaci XML.</span><span class="sxs-lookup"><span data-stu-id="ba144-115">The code example creates the following XML documentation in the *HelloWorldDoc.xml* file.</span></span>  
  
```xml  
<?xml version="1.0" ?>
<doc>  
  <assembly>  
    <name>HelloWorld</name>
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.
      </summary>
      <seealso cref="M:Samples.Class1.Main" />
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.
        <para>Add a new paragraph to the description.</para>
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## <a name="compile-permissions"></a><span data-ttu-id="ba144-116">Oprávnění k zkompilování</span><span class="sxs-lookup"><span data-stu-id="ba144-116">Compile permissions</span></span>
  
<span data-ttu-id="ba144-117">Tento příklad kódu vyžaduje `FullTrust` úspěšné provedení sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="ba144-117">This code example requires the `FullTrust` permission set to execute successfully.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ba144-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba144-118">See also</span></span>

- [<span data-ttu-id="ba144-119">Dokumentování kódu pomocí XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba144-119">Document your code with XML (Visual Basic)</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="ba144-120">Komentáře dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="ba144-120">XML documentation comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="ba144-121">Dokumentace XML (C++)</span><span class="sxs-lookup"><span data-stu-id="ba144-121">XML documentation (C++)</span></span>](/cpp/ide/xml-documentation-visual-cpp)
