---
title: Částečné metody (Visual Basic)
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
ms.openlocfilehash: a974a68010fe80a07e83ac31e109bbf1c2b955e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568774"
---
# <a name="partial-methods-visual-basic"></a>Částečné metody (Visual Basic)
Částečné metody umožňují vývojářům k vložení vlastní logiky do kódu. Kód je obvykle součástí třídy generovaný návrhářem. Částečné metody jsou definovány v dílčí třídě vytvořený generátor kódu a běžně se používají k poskytování oznámení, něco se změnila. Umožňují vývojářům určit vlastní chování v reakci na změnu.  
  
 Návrhář generátoru kódu definuje podpis metody a jeden nebo více volání metody. Vývojáři jim pak můžou implementace metody, pokud je to vyžadováno k přizpůsobení chování generovaného kódu. Pokud je k dispozici žádná implementace, odeberou se volání metody kompilátorem, což vede k žádné dalším výkonnostním režiím.  
  
## <a name="declaration"></a>Deklarace  
 Generovaný kód označí definicí částečné metody tak, že klíčové slovo `Partial` na začátku řádku podpisu.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 Definice musí splňovat následující podmínky:  
  
-   Metoda musí být `Sub`, nikoli `Function`.  
  
-   Tělo metody musí být prázdná.  
  
-   Modifikátor přístupu musí být `Private`.  
  
## <a name="implementation"></a>Implementace  
 Implementace sestává především z vyplnění textu částečné metody. Implementace je obvykle v samostatné částečné třídy z definice a je vytvořená systémem pro vývojáře, kteří chtějí rozšířit generovaného kódu.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 V předchozím příkladu přesně duplikuje podpisu v deklaraci, ale změny jsou možné. Zejména jiných modifikátory lze přidat, jako například `Overloads` nebo `Overrides`. Pouze jeden `Overrides` smí obsahovat modifikátor. Další informace o modifikátory metodu, najdete v části [příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Použití  
 Částečná metoda zavoláte jako jakýkoli jiný zavolal `Sub` postup. Pokud byl implementován metody, jsou vyhodnoceny argumenty a provede se tělo metody. Nezapomeňte však, že implementace částečné metody je volitelné. Pokud metoda není implementována, volání k němu nemá žádný vliv, a není u nich vyhodnoceno výrazy předané jako argumenty metody.  
  
## <a name="example"></a>Příklad  
 Do souboru s názvem Product.Designer.vb definovat `Product` třídu, která má `Quantity` vlastnost.  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 Do souboru s názvem Product.vb poskytnout implementaci pro `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 Nakonec do metody Main projektu deklarovat `Product` instance a zadejte počáteční hodnotu pro jeho `Quantity` vlastnost.  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 Okno se zprávou by měl vypadat, který se zobrazí tato zpráva:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Procedury Sub](./sub-procedures.md)
- [Nepovinné parametry](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Generování kódu v LINQ to SQL](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Přidání obchodní logiky pomocí částečných metod](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
