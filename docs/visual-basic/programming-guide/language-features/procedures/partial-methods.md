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
ms.openlocfilehash: a1708c1d953a60429c1bd87fd858da5c50a3e759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651593"
---
# <a name="partial-methods-visual-basic"></a>Částečné metody (Visual Basic)
Částečné metody umožňují vývojářům vložení vlastní logiky do kódu. Kód je obvykle součástí návrháře generované třídy. Částečné metody jsou definovány v konkrétní třídu, který byl vytvořený generátor kódu a běžně se používají k poskytování oznámení, že něco došlo ke změnám. Umožňují vývojáři určit vlastní chování v reakci na změny.  
  
 Návrhář generátoru kódu definuje pouze podpis metody a jeden nebo více volání metody. Vývojáři jim pak můžou implementace pro metodu, aby bylo možné přizpůsobit chování generovaného kódu. Pokud je k dispozici žádné implementace, se odeberou volání do metody kompilátorem, což vede k žádné další zatížení.  
  
## <a name="declaration"></a>Deklarace  
 Generovaný kód označí definici částečné metody tím, že umístíte klíčové slovo `Partial` na začátku řádku podpisu.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 Definice musí splňovat následující podmínky:  
  
-   Metoda musí být `Sub`, nikoli `Function`.  
  
-   Tělo metody musí být prázdné.  
  
-   Modifikátor přístupu musí být `Private`.  
  
## <a name="implementation"></a>Implementace  
 Implementace se primárně skládá z naplnění v těle částečné metody. Implementace je obvykle v samostatné částečné třídy z definice a je zapsán vývojáři, kteří chtějí rozšířit generovaného kódu.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 Předchozí příklad duplikuje podpis v deklaraci přesně, ale je možné, variace. Konkrétně jiných modifikátory lze přidat, jako například `Overloads` nebo `Overrides`. Pouze jeden `Overrides` Modifikátor je povoleno. Další informace o metoda modifikátory najdete v tématu [Sub – příkaz](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Použití  
 Při volání metody částečné, jako by všechny další volání `Sub` postupu. Pokud byl implementován metodu, argumenty, které se vyhodnocují a je proveden těla metody. Nezapomeňte však, že implementace částečné metoda je volitelné. Pokud metoda není implementována, volání k ní nemá žádný vliv, a nejsou vyhodnotí výrazy předány jako argumenty metodě.  
  
## <a name="example"></a>Příklad  
 V souboru s názvem Product.Designer.vb, definovat `Product` třídu, která má `Quantity` vlastnost.  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 V souboru s názvem Product.vb, poskytovat implementaci `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 Nakonec v metodě hlavní projektu deklarovat `Product` instance a zadat počáteční hodnotu pro jeho `Quantity` vlastnost.  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 Okno se zprávou by měla vypadat, zobrazí tato zpráva:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Nepovinné parametry](./optional-parameters.md)  
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [Generování kódu v LINQ to SQL](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [Přidání obchodní logiky pomocí částečných metod](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
