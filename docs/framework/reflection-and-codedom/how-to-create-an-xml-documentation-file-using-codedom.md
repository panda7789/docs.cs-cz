---
title: 'Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
ms.openlocfilehash: cdd1f173274b6bd33c4a67ed8eb0974c4c8e8e70
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130179"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="9d8f7-102">Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="9d8f7-102">How to: Create an XML Documentation File Using CodeDOM</span></span>
<span data-ttu-id="9d8f7-103">CodeDOM lze použít k vytvoření kódu, který generuje dokumentaci XML.</span><span class="sxs-lookup"><span data-stu-id="9d8f7-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="9d8f7-104">Proces zahrnuje vytvoření grafu CodeDOM, který obsahuje dokumentační komentáře XML, generování kódu a kompilování generovaného kódu s možností kompilátoru, která vytvoří výstup dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="9d8f7-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a><span data-ttu-id="9d8f7-105">Vytvoření grafu CodeDOM, který obsahuje dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="9d8f7-105">To create a CodeDOM graph that contains XML documentation comments</span></span>  
  
1. <span data-ttu-id="9d8f7-106">Vytvořte <xref:System.CodeDom.CodeCompileUnit> obsahující graf CodeDOM pro ukázkovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9d8f7-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="9d8f7-107">Použijte konstruktor <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> s parametrem `docComment` nastaveným na `true` k vytvoření prvků komentáře XML dokumentace a textu.</span><span class="sxs-lookup"><span data-stu-id="9d8f7-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="9d8f7-108">Generování kódu z CodeCompileUnit</span><span class="sxs-lookup"><span data-stu-id="9d8f7-108">To generate the code from the CodeCompileUnit</span></span>  
  
1. <span data-ttu-id="9d8f7-109">K vygenerování kódu a vytvoření zdrojového souboru, který se má zkompilovat, použijte metodu <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d8f7-109">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="9d8f7-110">Pro zkompilování kódu a generování souboru dokumentace</span><span class="sxs-lookup"><span data-stu-id="9d8f7-110">To compile the code and generate the documentation file</span></span>  
  
1. <span data-ttu-id="9d8f7-111">Přidejte možnost kompilátoru **/doc** do vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> objektu <xref:System.CodeDom.Compiler.CompilerParameters> a předejte objekt metodě <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A>, abyste vytvořili soubor dokumentace XML při kompilování kódu.</span><span class="sxs-lookup"><span data-stu-id="9d8f7-111">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="9d8f7-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d8f7-112">Example</span></span>  
 <span data-ttu-id="9d8f7-113">Následující příklad kódu vytvoří graf CodeDOM s komentáři k dokumentaci, vygeneruje soubor kódu z grafu a zkompiluje soubor a vytvoří přidružený soubor dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="9d8f7-113">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="9d8f7-114">Příklad kódu vytvoří následující dokumentaci XML v souboru HelloWorldDoc. XML.</span><span class="sxs-lookup"><span data-stu-id="9d8f7-114">The code example creates the following XML documentation in the HelloWorldDoc.xml file.</span></span>  
  
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
        <seealso cref="M:Samples.Class1.Main" />   
      </summary>  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d8f7-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9d8f7-115">Compiling the Code</span></span>  
  
- <span data-ttu-id="9d8f7-116">Tento příklad kódu vyžaduje úspěšné provedení sady oprávnění `FullTrust`.</span><span class="sxs-lookup"><span data-stu-id="9d8f7-116">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8f7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d8f7-117">See also</span></span>

- [<span data-ttu-id="9d8f7-118">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="9d8f7-118">Documenting Your Code with XML</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="9d8f7-119">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="9d8f7-119">XML Documentation Comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="9d8f7-120">Dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="9d8f7-120">XML Documentation</span></span>](/cpp/ide/xml-documentation-visual-cpp)
