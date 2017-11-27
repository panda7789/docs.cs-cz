---
title: "Priorita operátorů v jazyce Visual Basic"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c0fb466b404cafdd4b91d061971fd683375c715
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="operator-precedence-in-visual-basic"></a>Priorita operátorů v jazyce Visual Basic
Pokud dojde k několik operací ve výrazu, každou část je vyhodnotit a vyřešit v předurčeném pořadí názvem *operátorů*.  
  
## <a name="precedence-rules"></a>Pravidla priorit  
 Pokud výrazy obsahují operátory z více než jednu kategorii, jsou vyhodnocovány podle následujících pravidel:  
  
-   Operátory aritmetické a zřetězení mít pořadí priority popsané v následující části, a všechny mají vyšší prioritu než relační, logické a bitové operátory.  
  
-   Všechny operátory porovnání mají stejnou přednost a všechny mají vyšší prioritu než logické a bitové operátory, ale nižší prioritu než operátory aritmetické a zřetězení.  
  
-   Logické a bitové operátory mít pořadí priority popsané v následující části, a všechny mají nižší prioritu než aritmetické, zřetězení a operátory porovnání.  
  
-   Operátory s stejnou přednost se vyhodnocují zleva doprava v pořadí, ve kterém se zobrazí ve výrazu.  
  
## <a name="precedence-order"></a>Pořadí priorit  
 Operátory jsou vyhodnocovány v následujícím pořadí podle priority:  
  
### <a name="await-operator"></a>Await – operátor  
 await  
  
### <a name="arithmetic-and-concatenation-operators"></a>Aritmetické operátory a operátory zřetězení  
 Exponenciální zápis (`^`)  
  
 Unární identity a negace (`+`, `–`)  
  
 Násobení a dělení s plovoucí desetinnou čárkou (`*`, `/`)  
  
 Dělení celého čísla (`\`)  
  
 Aritmetické numerického zbytku (`Mod`)  
  
 Sčítání a odečítání (`+`, `–`)  
  
 Spojení řetězců (`&`)  
  
 Aritmetické bitové posunutí (`<<`, `>>`)  
  
### <a name="comparison-operators"></a>Operátory porovnání  
 Všechny operátory porovnání (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)  
  
### <a name="logical-and-bitwise-operators"></a>Logické a bitové operátory  
 Negace (`Not`)  
  
 Spojení (`And`, `AndAlso`)  
  
 Včetně disjunkce (`Or`, `OrElse`)  
  
 Exkluzivní disjunkce (`Xor`)  
  
### <a name="comments"></a>Komentáře  
 `=` Operátor je pouze rovnosti relační operátor, operátor přiřazení.  
  
 Operátor zřetězení řetězců (`&`) není aritmetický operátor, ale v přednost se seskupují s aritmetické operátory.  
  
 `Is` a `IsNot` operátory jsou operátory porovnání odkaz na objekt. Není jejich porovnání hodnoty dva objekty; Zkontrolujte, že pouze k určení, zda dva objektové proměnné odkazují na stejnou instanci objektu.  
  
## <a name="associativity"></a>Asociativita  
 Pokud operátory stejnou přednost objeví spolu ve výrazu, například násobení a dělení, kompilátor vyhodnotí jednotlivých operací, jako narazí zleva doprava. Toto dokládá následující příklad.  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 První výraz vyhodnotí dělení 96 / 8 (což vede k 12) a pak dělení 12 / 4, což vede k tři. Protože kompilátor vyhodnotí operací pro `n1` zleva doprava vyhodnocení je stejná při tomto pořadí explicitně uvedené pro `n2`. Obě `n1` a `n2` mít výsledek tři. Naopak `n3` má výsledku 48, protože závorkách vynutit kompilátoru vyhodnotit 8 / 4 první.  
  
 Z důvodu toto chování operátory jsou označeny jako *zbývajících asociativní* v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="overriding-precedence-and-associativity"></a>Přepsání přednost a Asociativnost  
 Závorky můžete vynutit některé části výraz, který se vyhodnotí než jiné. To můžete přepsat pořadí priorit a levé asociativnost. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]vždycky provádí operace, které jsou uvedeny v závorkách dříve, než mimo. Ale v uvozovkách, udržuje obyčejnou přednost a asociativnost, pokud nechcete použít závorky v závorkách. Toto dokládá následující příklad.  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a>Viz také  
 [= – Operátor](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Is – operátor](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot – operátor](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Like – operátor](../../../visual-basic/language-reference/operators/like-operator.md)  
 [Typeof – operátor](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Await – operátor](../../../visual-basic/language-reference/operators/await-operator.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
