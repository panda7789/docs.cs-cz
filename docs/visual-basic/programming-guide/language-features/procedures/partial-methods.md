---
title: Částečné metody
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 7abf0565a985f1fb44fcf2bb91b9220d57a10f20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352626"
---
# <a name="partial-methods-visual-basic"></a>Částečné metody (Visual Basic)
Částečné metody umožňují vývojářům vkládat vlastní logiku do kódu. Kód je obvykle součástí třídy generované návrhářem. Částečné metody jsou definovány v částečné třídě, která je vytvořena generátorem kódu, a obvykle slouží k poskytnutí oznámení o tom, že došlo ke změně nějakého typu. Umožňují vývojářům zadat vlastní chování v reakci na změnu.  
  
 Návrhář generátoru kódu definuje pouze signaturu metody a jedno nebo více volání metody. Vývojáři pak mohou poskytnout implementace pro metodu, pokud chtějí přizpůsobit chování generovaného kódu. Není-li k dispozici žádná implementace, volání metody jsou odebrána kompilátorem, což má za následek žádné další nároky na výkon.  
  
## <a name="declaration"></a>Deklarace  
 Vygenerovaný kód označuje definici částečné metody umístěním klíčového slova `Partial` na začátku řádku podpisu.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 Definice musí splňovat následující podmínky:  
  
- Metoda musí být `Sub`, nikoli `Function`.  
  
- Tělo metody musí být ponecháno prázdné.  
  
- Modifikátor přístupu musí být `Private`.  
  
## <a name="implementation"></a>Implementace  
 Implementace se skládá hlavně z vyplnění těla částečné metody. Implementace je obvykle v samostatné částečné třídě z definice a je zapsána vývojářem, který chce zvětšit generovaný kód.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 Předchozí příklad duplikuje signaturu v deklaraci přesně, ale je možné variace. Konkrétně lze přidat jiné modifikátory, například `Overloads` nebo `Overrides`. Je povolený jenom jeden modifikátor `Overrides`. Další informace o modifikátorech metod naleznete v tématu [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Použití  
 Můžete zavolat částečnou metodu, protože byste volali jakoukoli jinou `Sub` proceduru. Pokud byla metoda implementována, jsou vyhodnoceny argumenty a je provedeno tělo metody. Nezapomeňte však, že implementace částečné metody je volitelná. Pokud není metoda implementována, volání na ni nemá žádný účinek a výrazy předané metodě nejsou vyhodnocovány.  
  
## <a name="example"></a>Příklad  
 V souboru s názvem Product. Designer. vb Definujte třídu `Product`, která má vlastnost `Quantity`.  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 V souboru s názvem Product. vb Poskytněte implementaci pro `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 Nakonec v hlavní metodě projektu deklarujte instanci `Product` a zadejte počáteční hodnotu pro její vlastnost `Quantity`.  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 Zobrazí se okno se zprávou s touto zprávou:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Procedury Sub](./sub-procedures.md)
- [Nepovinné parametry](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Generování kódu v LINQ to SQL](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Přidání obchodní logiky pomocí částečných metod](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
