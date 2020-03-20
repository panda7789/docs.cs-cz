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
ms.openlocfilehash: a0ccb469a43c3a21a76eaf24fa7ce7b490dd5c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180513"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Postupy: Vytváření souborů dokumentace XML pomocí modelu CodeDOM
CodeDOM lze použít k vytvoření kódu, který generuje dokumentaci XML. Proces zahrnuje vytvoření grafu CodeDOM, který obsahuje komentáře dokumentace XML, generování kódu a kompilaci generovaného kódu s možností kompilátoru, který vytvoří výstup dokumentace XML.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>Vytvoření grafu CodeDOM, který obsahuje komentáře k dokumentaci XML  
  
1. Vytvořte <xref:System.CodeDom.CodeCompileUnit> obsahující codedom graf pro ukázkovou aplikaci.  
  
2. Pomocí <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktoru `docComment` s parametrem nastaveným pro `true` vytvoření prvků komentářů a textu dokumentace XML.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>Chcete-li generovat kód z CodeCompileUnit  
  
1. Pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody vygenerujte kód a vytvořte zdrojový soubor, který má být kompilován.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Kompilace kódu a generování souboru dokumentace  
  
1. Přidejte možnost kompilátoru <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> <xref:System.CodeDom.Compiler.CompilerParameters> **/doc** do vlastnosti objektu a předajte objekt metodě <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> a vytvořte soubor dokumentace XML při kompilaci kódu.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří graf CodeDOM s poznámkami v dokumentaci, vygeneruje soubor kódu z grafu a zkompiluje soubor a vytvoří přidružený soubor dokumentace XML.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Příklad kódu vytvoří následující dokumentaci XML v souboru HelloWorldDoc.xml.  
  
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
  
- Tento příklad kódu `FullTrust` vyžaduje oprávnění nastavena úspěšně spustit.  
  
## <a name="see-also"></a>Viz také

- [Dokumentace kódu s XML](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Komentáře k dokumentaci XML](../../csharp/programming-guide/xmldoc/index.md)
- [Dokumentace XML](/cpp/ide/xml-documentation-visual-cpp)
