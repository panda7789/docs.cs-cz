---
title: Datový typ Boolean
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 5d05514207c5d07e81aab897f40f728570f6bd87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347851"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean – datový typ (Visual Basic)

Obsahuje hodnoty, které mohou být pouze `True` nebo `False`. Klíčová slova `True` a `False` odpovídají dvěma stavům `Boolean` proměnných.  
  
## <a name="remarks"></a>Poznámky  

 Použijte [datový typ Boolean (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) k tomu, aby obsahovala hodnoty se dvěma stavy, jako je true/false, ano/ne nebo zapnuto/vypnuto.  
  
 Výchozí hodnota `Boolean` je `False`.  
  
 hodnoty `Boolean` nejsou uloženy jako čísla a uložené hodnoty nejsou určeny pro ekvivalent čísel. Nikdy byste neměli psát kód, který spoléhá na ekvivalentní číselné hodnoty pro `True` a `False`. Kdykoli je to možné, měli byste omezit využití `Boolean` proměnných na logické hodnoty, pro které jsou navrženy.  
  
## <a name="type-conversions"></a>Převody typu  

 Když Visual Basic převede hodnoty číselného datového typu na `Boolean`, 0 se změní na `False` a všechny ostatní hodnoty se budou `True`. Když Visual Basic převede `Boolean` hodnoty na číselné typy, `False` bude 0 a `True` se změní na hodnotu-1.  
  
 Pokud převedete mezi `Boolean` hodnoty a číselné datové typy, pamatujte, že metody převodu .NET Framework nikdy nepřinesou stejné výsledky jako klíčová slova převodu Visual Basic. Důvodem je to, že převod Visual Basic zachovává chování kompatibilní s předchozími verzemi. Další informace naleznete v tématu "logický typ nepřeváděný na číselný typ přesně" v článku [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Tipy k programování  
  
- **Záporná čísla.** `Boolean` není numerický typ a nemůže představovat zápornou hodnotu. V žádném případě byste neměli používat `Boolean` k ukládání číselných hodnot.  
  
- **Znaky typu.** `Boolean` nemá žádný znak typu literálu ani znak typu identifikátoru.  
  
- **Typ rozhraní.** Odpovídající typ v .NET Framework je struktura <xref:System.Boolean?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  

 V následujícím příkladu je `runningVB` proměnná `Boolean`, která ukládá jednoduché nastavení ano/ne.  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Boolean?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)
