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
ms.openlocfilehash: b9e11a51048733dbfc42ff9f575e18effc80db07
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596243"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="782da-102">Postupy: vytvoření souboru dokumentace XML pomocí CodeDOM</span><span class="sxs-lookup"><span data-stu-id="782da-102">How to: Create an XML documentation file using CodeDOM</span></span>

<span data-ttu-id="782da-103">CodeDOM lze použít k vytvoření kódu, který generuje dokumentaci XML.</span><span class="sxs-lookup"><span data-stu-id="782da-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="782da-104">Proces zahrnuje vytvoření grafu CodeDOM, který obsahuje dokumentační komentáře XML, generování kódu a kompilování generovaného kódu s možností kompilátoru, která vytvoří výstup dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="782da-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
## <a name="create-a-codedom-graph"></a><span data-ttu-id="782da-105">Vytvoření grafu CodeDOM</span><span class="sxs-lookup"><span data-stu-id="782da-105">Create a CodeDOM graph</span></span>
  
1. <span data-ttu-id="782da-106">Vytvořte objekt <xref:System.CodeDom.CodeCompileUnit> obsahující graf CodeDom pro ukázkovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="782da-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="782da-107">Použijte <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktor s `docComment` parametrem nastaveným na `true` k vytvoření prvků komentáře XML dokumentace a text.</span><span class="sxs-lookup"><span data-stu-id="782da-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="782da-108">Generování kódu z CodeCompileUnit</span><span class="sxs-lookup"><span data-stu-id="782da-108">Generate the code from the CodeCompileUnit</span></span>
  
1. <span data-ttu-id="782da-109">Použijte <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodu pro vytvoření kódu a vytvoření zdrojového souboru, který se má zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="782da-109">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="782da-110">Zkompiluje kód a vygeneruje soubor dokumentace.</span><span class="sxs-lookup"><span data-stu-id="782da-110">Compile the code and generate the documentation file</span></span>
  
1. <span data-ttu-id="782da-111">Přidejte možnost kompilátoru **/doc** do <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters> objektu a předejte objekt <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metodě pro vytvoření souboru dokumentace XML při kompilování kódu.</span><span class="sxs-lookup"><span data-stu-id="782da-111">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="782da-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="782da-112">Example</span></span>

<span data-ttu-id="782da-113">Následující příklad kódu vytvoří graf CodeDOM s komentáři k dokumentaci, vygeneruje soubor kódu z grafu a zkompiluje soubor a vytvoří přidružený soubor dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="782da-113">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="782da-114">Příklad kódu vytvoří následující dokumentaci XML v souboru *HelloWorldDoc. XML* .</span><span class="sxs-lookup"><span data-stu-id="782da-114">The code example creates the following XML documentation in the *HelloWorldDoc.xml* file.</span></span>  
  
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
  
## <a name="compile-permissions"></a><span data-ttu-id="782da-115">Oprávnění k zkompilování</span><span class="sxs-lookup"><span data-stu-id="782da-115">Compile permissions</span></span>
  
<span data-ttu-id="782da-116">Tento příklad kódu vyžaduje `FullTrust` úspěšné provedení sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="782da-116">This code example requires the `FullTrust` permission set to execute successfully.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="782da-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="782da-117">See also</span></span>

- [<span data-ttu-id="782da-118">Dokumentování kódu pomocí XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="782da-118">Document your code with XML (Visual Basic)</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="782da-119">Komentáře dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="782da-119">XML documentation comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="782da-120">Dokumentace XML (C++)</span><span class="sxs-lookup"><span data-stu-id="782da-120">XML documentation (C++)</span></span>](/cpp/ide/xml-documentation-visual-cpp)
