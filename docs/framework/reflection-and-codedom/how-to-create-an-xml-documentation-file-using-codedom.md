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
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Postupy: vytvoření souboru dokumentace XML pomocí CodeDOM

CodeDOM lze použít k vytvoření kódu, který generuje dokumentaci XML. Proces zahrnuje vytvoření grafu CodeDOM, který obsahuje dokumentační komentáře XML, generování kódu a kompilování generovaného kódu s možností kompilátoru, která vytvoří výstup dokumentace XML.  
  
## <a name="create-a-codedom-graph"></a>Vytvoření grafu CodeDOM
  
1. Vytvořte objekt <xref:System.CodeDom.CodeCompileUnit> obsahující graf CodeDom pro ukázkovou aplikaci.  
  
2. Použijte <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> konstruktor s `docComment` parametrem nastaveným na `true` k vytvoření prvků komentáře XML dokumentace a text.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a>Generování kódu z CodeCompileUnit
  
1. Použijte <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodu pro vytvoření kódu a vytvoření zdrojového souboru, který se má zkompilovat.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a>Zkompiluje kód a vygeneruje soubor dokumentace.
  
1. Přidejte možnost kompilátoru **/doc** do <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> vlastnosti <xref:System.CodeDom.Compiler.CompilerParameters> objektu a předejte objekt <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> metodě pro vytvoření souboru dokumentace XML při kompilování kódu.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Příklad

Následující příklad kódu vytvoří graf CodeDOM s komentáři k dokumentaci, vygeneruje soubor kódu z grafu a zkompiluje soubor a vytvoří přidružený soubor dokumentace XML.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Příklad kódu vytvoří následující dokumentaci XML v souboru *HelloWorldDoc. XML* .  
  
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
  
## <a name="compile-permissions"></a>Oprávnění k zkompilování
  
Tento příklad kódu vyžaduje `FullTrust` úspěšné provedení sady oprávnění.
  
## <a name="see-also"></a>Viz také

- [Dokumentování kódu pomocí XML (Visual Basic)](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Komentáře dokumentace XML](../../csharp/programming-guide/xmldoc/index.md)
- [Dokumentace XML (C++)](/cpp/ide/xml-documentation-visual-cpp)
