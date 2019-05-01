---
title: Priorita operátorů v jazyce Visual Basic
ms.date: 07/20/2015
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
ms.openlocfilehash: 568927eb4759c214311ad34a5b45e28094dd80be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013527"
---
# <a name="operator-precedence-in-visual-basic"></a>Priorita operátorů v jazyce Visual Basic
Pokud dojde k několika operací ve výrazu, každá část je vyhodnocen a vyřešené v předurčeném pořadí volá *priorita operátorů*.  
  
## <a name="precedence-rules"></a>Priorita pravidla  
 Výrazy obsahovat operátory z více než jednu kategorii, jsou vyhodnocovány podle následujících pravidel:  
  
- Zřetězení a aritmetické operátory mají pořadí podle priority je popsáno v následující části, a všechny mají vyšší prioritu než relační, logické a bitové operátory.  
  
- Všechny operátory porovnání mají stejnou prioritu a všechny mají vyšší prioritu než logické a bitové operátory, ale nižší prioritu než operátory aritmetické operace a zřetězení.  
  
- Logické a bitové operátory mají pořadí podle priority je popsáno v následující části, a všechny mají nižší prioritu než aritmetické, zřetězení a operátory porovnání.  
  
- Operátorů shodné priority jsou vyhodnoceny zleva doprava v pořadí, v jakém jsou uvedeny ve výrazu.  
  
## <a name="precedence-order"></a>Pořadí priority  
 Operátory jsou vyhodnocovány v následujícím pořadí podle priority:  
  
### <a name="await-operator"></a>Await – operátor  
 operátor await  
  
### <a name="arithmetic-and-concatenation-operators"></a>Aritmetické operátory a operátory zřetězení  
 Umocnění (`^`)  
  
 Unární identity a negace (`+`, `–`)  
  
 Násobení a dělení s pohyblivou čárkou (`*`, `/`)  
  
 Dělení celého čísla (`\`)  
  
 Aritmetické numerického zbytku (`Mod`)  
  
 Sčítání a odčítání (`+`, `–`)  
  
 Zřetězení řetězců (`&`)  
  
 Aritmetický bitový posun (`<<`, `>>`)  
  
### <a name="comparison-operators"></a>Operátory porovnání  
 Všechny operátory porovnání (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)  
  
### <a name="logical-and-bitwise-operators"></a>Logické a bitové operátory  
 Negace (`Not`)  
  
 Spojení (`And`, `AndAlso`)  
  
 Inkluzivní disjunkce (`Or`, `OrElse`)  
  
 Exkluzivní disjunkce (`Xor`)  
  
### <a name="comments"></a>Komentáře  
 `=` Operátor je pouze rovnosti relační operátor, operátor přiřazení.  
  
 Operátoru pro zřetězení řetězců (`&`) není aritmetickém operátoru, ale v prioritu seskupen s aritmetické operátory.  
  
 `Is` a `IsNot` operátory jsou operátory porovnání odkaz na objekt. Neporovnávejte hodnoty dvou objektů přihlášením ke jenom k určení, zda dva objektových proměnných odkazují na stejnou instanci objektu.  
  
## <a name="associativity"></a>Asociativita  
 Když pohromadě operátory stejnou prioritu ve výrazu, například úlohy násobení a dělení, kompilátor vyhodnocuje každou operaci jako nalezne zleva doprava. Toto dokládá následující příklad.  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 První výraz je vyhodnocen jako dělení 96 / 8 (což vede k 12) a potom dělení 12 / 4, což vede k tři. Protože kompilátor vyhodnocuje operace pro `n1` zleva doprava, hodnocení je stejný při tomto pořadí explicitně označena pro `n2`. Obě `n1` a `n2` mají tři příčiny. Naopak `n3` má výsledek 48, protože závorky vynutí vyhodnocení 8 kompilátor / 4 první.  
  
 Kvůli tomuto chování se označují jako operátory *asociativní zleva* v jazyce Visual Basic.  
  
## <a name="overriding-precedence-and-associativity"></a>Přepsání Priorita a asociativita  
 Můžete použít závorky k vynucení některé části výrazu, který se má vyhodnotit před ostatními. To můžete přepsat v pořadí podle priority a levém asociativity. Visual Basic vždy provádí operace, které jsou uzavřeny v závorkách před uživateli mimo. Ale v závorkách udržuje běžné přednost a asociativita operátorů, pokud nechcete použít závorky v závorkách. Toto dokládá následující příklad.  
  
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
  
## <a name="see-also"></a>Viz také:

- [= – operátor](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operátor Like](../../../visual-basic/language-reference/operators/like-operator.md)
- [Operátor Typeof](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Operátor Await](../../../visual-basic/language-reference/operators/await-operator.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
