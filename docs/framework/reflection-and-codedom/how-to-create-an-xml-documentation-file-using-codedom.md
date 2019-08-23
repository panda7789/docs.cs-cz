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
ms.openlocfilehash: 283fc91762bc4065bd9bd09efaa2bc0061451ef9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962730"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM
CodeDOM lze použít k vytvoření kódu, který generuje dokumentaci XML. Proces zahrnuje vytvoření grafu CodeDOM, který obsahuje dokumentační komentáře XML, generování kódu a kompilování generovaného kódu s možností kompilátoru, která vytvoří výstup dokumentace XML.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>Vytvoření grafu CodeDOM, který obsahuje dokumentační komentáře XML  
  
1. Vytvořte objekt <xref:System.CodeDom.CodeCompileUnit> obsahující graf CodeDom pro ukázkovou aplikaci.  
  
2. Použijte konstruktor s parametrem nastaveným na `true` k vytvoření prvků komentáře XML dokumentace a text. `docComment` <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>Generování kódu z CodeCompileUnit  
  
1. <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> Použijte metodu pro vytvoření kódu a vytvoření zdrojového souboru, který se má zkompilovat.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Pro zkompilování kódu a generování souboru dokumentace  
  
1. Přidejte možnost kompilátoru **/doc** <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> do vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters> <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> objektu a předejte objekt metodě pro vytvoření souboru dokumentace XML při kompilování kódu.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří graf CodeDOM s komentáři k dokumentaci, vygeneruje soubor kódu z grafu a zkompiluje soubor a vytvoří přidružený soubor dokumentace XML.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Příklad kódu vytvoří následující dokumentaci XML v souboru HelloWorldDoc. XML.  
  
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
  
- Tento příklad kódu vyžaduje `FullTrust` úspěšné provedení sady oprávnění.  
  
## <a name="see-also"></a>Viz také:

- [Dokumentace kódu s XML](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Dokumentační komentáře XML](../../csharp/programming-guide/xmldoc/index.md)
- [Dokumentace XML](/cpp/ide/xml-documentation-visual-cpp)
