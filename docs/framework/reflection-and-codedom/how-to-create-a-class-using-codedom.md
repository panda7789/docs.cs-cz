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
ms.openlocfilehash: 6b3f7363ec5f8c954dd55a9500dcf8f2e302424f
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894902"
---
# <a name="how-to-create-a-class-using-codedom"></a>Postupy: Vytváření třídy pomocí modelu CodeDOM
Následující postupy ukazují, jak vytvořit a zkompilovat graf CodeDOM, který generuje třídu obsahující dvě pole, tři vlastnosti, metodu, konstruktor a vstupní bod.  
  
1. Vytvořte konzolovou aplikaci, která bude používat kód CodeDOM k vygenerování zdrojového kódu pro třídu.  
  
     V tomto příkladu je generována třída s `Sample`názvem a generovaný kód je třída s názvem `CodeDOMCreatedClass` v souboru s názvem SampleCode.  
  
2. Ve třídě generování proveďte inicializaci grafu CodeDOM a použijte metody CodeDOM k definování členů, konstruktoru a vstupního bodu (`Main` metody) generované třídy.  
  
     V tomto příkladu vygenerovaná třída má dvě pole, tři vlastnosti, konstruktor, metodu a `Main` metodu.  
  
3. Ve třídě generování vytvořte poskytovatele kódu specifického pro jazyk a zavolejte jeho <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metodu pro generování kódu z grafu.  
  
4. Zkompilujte a spusťte aplikaci pro generování kódu.  
  
     V tomto příkladu je vygenerovaný kód v souboru s názvem SampleCode. Zkompilujte a spusťte tento kód, aby se zobrazil ukázkový výstup.  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a>Vytvoření aplikace, která spustí kód CodeDOM  
  
- Vytvořte třídu konzolové aplikace, která bude obsahovat kód CodeDOM. Definujte globální pole, která mají být použita ve třídě pro odkaz na sestavení (<xref:System.CodeDom.CodeCompileUnit>) a třídu (<xref:System.CodeDom.CodeTypeDeclaration>), zadejte název generovaného zdrojového `Main` souboru a deklarujte metodu.  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a>Inicializace grafu CodeDOM  
  
- V konstruktoru třídy konzolové aplikace inicializujte sestavení a třídu a přidejte příslušné deklarace do grafu CodeDOM.  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a>Přidání členů do grafu CodeDOM  
  
- Přidejte pole do grafu <xref:System.CodeDom.CodeMemberField> CodeDOM přidáním objektů <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> do vlastnosti třídy.  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- Přidejte vlastnosti do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberProperty> objektů <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> do vlastnosti třídy.  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- Přidejte metodu do grafu CodeDOM přidáním <xref:System.CodeDom.CodeMemberMethod> objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> do vlastnosti třídy.  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- Přidejte konstruktor do grafu <xref:System.CodeDom.CodeConstructor> CodeDOM přidáním objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> do vlastnosti třídy.  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- Přidejte vstupní bod do grafu <xref:System.CodeDom.CodeEntryPointMethod> CodeDOM přidáním objektu <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> do vlastnosti třídy.  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a>Generování kódu z grafu CodeDOM  
  
- Vygenerujte zdrojový kód z grafu CodeDOM voláním <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> metody.  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a>Vytvoření grafu a generování kódu  
  
1. Přidejte metody vytvořené v předchozích krocích do `Main` metody definované v prvním kroku.  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. Zkompilujte a spusťte třídu generování.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje kód z předchozích kroků.  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 Když je předchozí příklad kompilován a proveden, vytvoří následující zdrojový kód.  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 Generovaný zdrojový kód vytvoří následující výstup, když je zkompilován a proveden.  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Tento příklad kódu vyžaduje `FullTrust` úspěšné provedení sady oprávnění.  
  
## <a name="see-also"></a>Viz také:

- [Použití modelu CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)
- [Generování a kompilace zdrojového kódu z grafu modelu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
