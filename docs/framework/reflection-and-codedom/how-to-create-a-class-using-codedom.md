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
ms.openlocfilehash: 78c50b3813ebb0bb65955e411eb84e4cd9e0a001
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581932"
---
# <a name="how-to-create-a-class-using-codedom"></a>Postupy: Vytváření třídy pomocí modelu CodeDOM
Následující postupy ukazují, jak vytvořit a zkompilujte grafu CodeDOM, který generuje třídy obsahující dvě pole, tři vlastnosti, metody, konstruktor a vstupní bod.  
  
1.  Vytvořte konzolovou aplikaci, která se použije k vygenerování zdrojového kódu pro třídu kódu CodeDOM.  
  
     V tomto příkladu je pojmenována generování třídy `Sample`, a třídu s názvem je generovaný kód `CodeDOMCreatedClass` do souboru s názvem SampleCode.  
  
2.  V generování třídy, inicializovat grafu CodeDOM a použitím metody CodeDOM definovat členy, konstruktor a vstupního bodu (`Main` metoda) generované třídy.  
  
     V tomto příkladu má generované třídy, dvě pole, tři vlastnosti, konstruktor, metody a `Main` metoda.  
  
3.  V generování třídy, vytvořit poskytovatele kódu specifické pro jazyk a volání jeho <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metoda ke generování kódu z grafu.  
  
4.  Kompilace a spuštění aplikace pro generování kódu.  
  
     V tomto příkladu je generovaný kód do souboru s názvem SampleCode. Kompilace a spuštění tohoto kódu zobrazíte ukázkový výstup.  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a>Chcete-li vytvořit aplikaci, která spustí kód modelu CodeDOM  
  
-   Vytvořte třídu konzoly aplikace tak, aby obsahovala kód CodeDOM. Definovat globální pole, které mají být použity ve třídě tak, aby odkazovaly sestavení (<xref:System.CodeDom.CodeCompileUnit>) a třídy (<xref:System.CodeDom.CodeTypeDeclaration>), zadejte název vytvořeném zdrojovém souboru a deklarovat `Main` metody.  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a>Inicializace grafu CodeDOM  
  
-   V konstruktoru pro třídu aplikace konzoly inicializace sestavení a třídy a přidejte odpovídající deklarace do grafu CodeDOM.  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a>Postup přidání členů do grafu CodeDOM  
  
-   Přidat pole do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberField> objektů <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   Přidání vlastností do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberProperty> objektů <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   Přidání metody do grafu CodeDOM tak, že přidáte <xref:System.CodeDom.CodeMemberMethod> objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   Přidejte konstruktor do grafu CodeDOM tak, že přidáte <xref:System.CodeDom.CodeConstructor> objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   Přidat vstupní bod na grafu CodeDOM tak, že přidáte <xref:System.CodeDom.CodeEntryPointMethod> objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a>Ke generování kódu z grafu modelu CodeDOM  
  
-   Vygenerování zdrojového kódu z grafu modelu CodeDOM voláním <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody.  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a>K vytvoření grafu a generování kódu  
  
1.  Přidejte metody, které jsou vytvořené v předchozích kroků `Main` metody definované v prvním kroku.  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  Zkompilovat a spustit při generování třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje kód z předchozích kroků.  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 Když v předchozím příkladu je kompilován a spuštěn, vytvoří následující zdrojový kód.  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 Generovaného zdrojového kódu vytvoří následující výstup při zkompilovat a spustit.  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Tento příklad kódu vyžaduje `FullTrust` oprávnění nastaveno na hodnotu úspěšně vykonat.  
  
## <a name="see-also"></a>Viz také:
- [Použití modelu CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)
- [Generování a kompilace zdrojového kódu z grafu modelu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
