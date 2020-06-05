---
title: Boolean – datový typ
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
ms.openlocfilehash: 851c524a83c5f24b77a151634a96798249c5905e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374418"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean – datový typ (Visual Basic)

Obsahuje hodnoty, které mohou být pouze `True` nebo `False` . Klíčová slova `True` a `False` odpovídají dvěma stavům `Boolean` proměnných.  
  
## <a name="remarks"></a>Poznámky  

 Použijte [datový typ Boolean (Visual Basic)](boolean-data-type.md) k tomu, aby obsahovala hodnoty se dvěma stavy, jako je true/false, ano/ne nebo zapnuto/vypnuto.  
  
 Výchozí hodnota `Boolean` je `False` .  
  
 `Boolean`hodnoty nejsou uloženy jako čísla a uložené hodnoty nejsou určeny pro ekvivalent čísel. Nikdy byste neměli psát kód, který spoléhá na ekvivalentní číselné hodnoty pro `True` a `False` . Kdykoli je to možné, měli byste omezit použití `Boolean` proměnných na logické hodnoty, pro které jsou navrženy.  
  
## <a name="type-conversions"></a>Převody typu  

 Když Visual Basic převede hodnoty číselného datového typu na, vrátí se `Boolean` 0 a zobrazí se `False` všechny ostatní hodnoty `True` . Když Visual Basic převede `Boolean` hodnoty na číselné typy, `False` změní se na 0 a `True` změní se na 1.  
  
 Pokud převedete mezi `Boolean` hodnotami a číselnými datovými typy, pamatujte, že metody převodu .NET Framework nevytváří vždy stejné výsledky jako klíčová slova převodu Visual Basic. Důvodem je to, že převod Visual Basic zachovává chování kompatibilní s předchozími verzemi. Další informace naleznete v tématu "logický typ nepřeváděný na číselný typ přesně" v článku [řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Tipy k programování  
  
- **Záporná čísla.** `Boolean`není numerický typ a nemůže představovat zápornou hodnotu. V žádném případě byste neměli používat `Boolean` k ukládání číselných hodnot.  
  
- **Znaky typu.** `Boolean`nemá žádný znak typu literálu nebo znak typu identifikátoru.  
  
- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.Boolean?displayProperty=nameWithType> Struktura.  
  
## <a name="example"></a>Příklad  

 V následujícím příkladu `runningVB` je `Boolean` Proměnná, která ukládá jednoduché nastavení ano/ne.  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Boolean?displayProperty=nameWithType>
- [Datové typy](index.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType – funkce](../functions/ctype-function.md)
