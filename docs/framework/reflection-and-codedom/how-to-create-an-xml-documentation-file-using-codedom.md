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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ae041ae278dc6f2423a679dab8982f4ccc35620
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592496"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM
CodeDOM lze použít k vytvoření kód, který generuje dokumentace XML. Tento proces zahrnuje vytvoření grafu CodeDOM, který obsahuje komentáře dokumentace XML, generování kódu a kompilace generovaného kódu s možností kompilátoru, která vytvoří výstup dokumentaci XML.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>Chcete-li vytvořit grafu CodeDOM, který obsahuje komentáře dokumentace XML  
  
1. Vytvoření <xref:System.CodeDom.CodeCompileUnit> obsahuje graf CodeDOM pro ukázkovou aplikaci.  
  
2. Použití <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktor s `docComment` parametr nastaven na `true` vytvořit prvky komentářů dokumentace XML a text.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>Ke generování kódu z CodeCompileUnit  
  
1. Použití <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodu pro generování kódu a vytvořte zdrojový soubor ke kompilaci.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Pro zkompilování kódu a generovat soubor dokumentace  
  
1. Přidat **/doc** – možnost kompilátoru do <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> vlastnost <xref:System.CodeDom.Compiler.CompilerParameters> objektu a předejte objekt, který má <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metodu pro vytvoření souboru dokumentace XML, pokud kód je zkompilován.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří graf CodeDOM se komentáře k dokumentaci, generuje soubor kódu z grafu a kompiluje soubor a vytvoří přidružený soubor dokumentace XML.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Příklad kódu vytvoří následující dokumentace XML v souboru HelloWorldDoc.xml.  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Tento příklad kódu vyžaduje `FullTrust` oprávnění nastaveno na hodnotu úspěšně vykonat.  
  
## <a name="see-also"></a>Viz také:

- [Dokumentace kódu s XML](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Dokumentační komentáře XML](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)
- [Dokumentace XML](/cpp/ide/xml-documentation-visual-cpp)
