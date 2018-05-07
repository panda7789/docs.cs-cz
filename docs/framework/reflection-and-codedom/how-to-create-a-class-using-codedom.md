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
ms.openlocfilehash: cf244e796dad0f3817a3c5acd1fcda8eaf189e2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-class-using-codedom"></a>Postupy: Vytváření třídy pomocí modelu CodeDOM
Následující postupy ukazují, jak vytvořit a kompilaci grafu modelu CodeDOM, který generuje třída obsahující dvě pole, tři vlastností, metoda, konstruktor a vstupního bodu.  
  
1.  Vytvořte konzolovou aplikaci, která se použije k vygenerování zdrojového kódu pro třídu modelu CodeDOM kódu.  
  
     V tomto příkladu je generování třída s názvem `Sample`, a generovaný kód je třída s názvem `CodeDOMCreatedClass` do souboru s názvem SampleCode.  
  
2.  V generování třídy, inicializace grafu modelu CodeDOM a pomocí modelu CodeDOM metody můžete definovat členy, konstruktor a vstupního bodu (`Main` metoda) generované třídy.  
  
     V tomto příkladu generovaná třída má dvě pole, tři vlastnosti, konstruktor, metody a `Main` metoda.  
  
3.  V generování tříd, vytvořte zprostředkovatele pro specifický jazyk kódu a volání jeho <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metoda ke generování kódu z grafu.  
  
4.  Zkompilování a spuštění aplikace pro generování kódu.  
  
     V tomto příkladu je generovaný kód v souboru s názvem SampleCode. Zkompilování a spuštění tohoto kódu zobrazíte ukázkový výstup.  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a>Chcete-li vytvořit aplikaci, která spustí kód modelu CodeDOM  
  
-   Vytvořte třídu konzole aplikace tak, aby obsahovala kód CodeDOM. Definování globální polí, které mají být použita ve třídě, chcete-li sestavení (<xref:System.CodeDom.CodeCompileUnit>) a třídy (<xref:System.CodeDom.CodeTypeDeclaration>), zadejte název vytvořeném zdrojovém souboru a deklarovat `Main` metoda.  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a>K chybě při inicializaci grafu modelu CodeDOM  
  
-   V konstruktoru pro třídu aplikace konzoly inicializovat sestavení a třída a přidejte příslušné deklarace grafu modelu CodeDOM.  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a>Postup přidání členů do grafu modelu CodeDOM  
  
-   Přidat pole do grafu modelu CodeDOM přidáním <xref:System.CodeDom.CodeMemberField> objekty ke <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   Přidání vlastnosti do grafu modelu CodeDOM přidáním <xref:System.CodeDom.CodeMemberProperty> objekty ke <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   Přidání metody do grafu modelu CodeDOM přidáním <xref:System.CodeDom.CodeMemberMethod> do objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   Přidejte konstruktor do grafu modelu CodeDOM přidáním <xref:System.CodeDom.CodeConstructor> do objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   Přidání vstupního bodu do grafu modelu CodeDOM přidáním <xref:System.CodeDom.CodeEntryPointMethod> do objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> vlastnost třídy.  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a>Ke generování kódu z grafu modelu CodeDOM  
  
-   Generování zdrojového kódu z grafu modelu CodeDOM voláním <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metoda.  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a>Vytvoření grafu a generování kódu  
  
1.  Přidejte metody vytvořené v předchozí postup `Main` metoda definované v prvním kroku.  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  Zkompilování a spuštění generování tříd.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje kód z předchozích kroků.  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 Při kompilaci v předchozím příkladu je a provést, vytvoří následující zdrojový kód.  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 Vygenerovaný zdrojový kód vytváří následující výstupní při kompilaci a provést.  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Tento příklad kódu vyžaduje `FullTrust` nastavit oprávnění při spuštění.  
  
## <a name="see-also"></a>Viz také  
 [Použití modelu CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 [Generování a kompilace zdrojového kódu z grafu modelu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
