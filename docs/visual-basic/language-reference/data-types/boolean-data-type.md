---
title: Boolean – datový typ (Visual Basic)
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
ms.openlocfilehash: bbd914d8b4239bbae1de7031e68b2900cf5ad6a3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862380"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean – datový typ (Visual Basic)
Obsahuje hodnoty, které mohou být pouze `True` nebo `False`. Klíčová slova `True` a `False` odpovídají dvěma stavy `Boolean` proměnné.  
  
## <a name="remarks"></a>Poznámky  
 Použití [datový typ Boolean (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) tak, aby obsahovala hodnoty dvou stavů, jako je true nebo false, Ano/Ne, nebo zapnuto/vypnuto.  
  
 Výchozí hodnota `Boolean` je `False`.  
  
 `Boolean` hodnoty nejsou uložené jako čísla a uložené hodnoty nejsou určeny jako ekvivalentní čísla. Nikdy by měl napsat kód, který závisí na ekvivalentní číselné hodnoty pro `True` a `False`. Kdykoli je to možné, byste měli omezit využití `Boolean` proměnné logické hodnoty, které jsou určeny.  
  
## <a name="type-conversions"></a>Převody typu  
 Když Visual Basic převede číselný datový typ hodnoty na `Boolean`, stane 0 `False` a Staňte se všechny ostatní hodnoty `True`. Když Visual Basic převede `Boolean` hodnoty pro číselné typy `False` stane 0 a `True` stane hodnota -1.  
  
 Při převodu mezi `Boolean` hodnoty a číselné datové typy, mějte na paměti, že převod metod rozhraní .NET Framework vždy neposkytují stejné výsledky jako klíčová slova převodu jazyka Visual Basic. Je to proto, že převod jazyka Visual Basic zachovává chování, které jsou kompatibilní s předchozími verzemi. Další informace najdete v tématu "Logická typ nemá není převést na číselný typ přesně" v [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Záporná čísla.** `Boolean` není číselného typu a nemůže představovat záporné hodnoty. V každém případě byste neměli používat `Boolean` pro uložení číselné hodnoty.  
  
-   **Znaky typu.** `Boolean` nemá žádný – znak typu literálu nebo – znak typu identifikátoru.  
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Boolean?displayProperty=nameWithType> struktury.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `runningVB` je `Boolean` proměnnou, která ukládá jednoduché nastavení Ano/Ne.  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)
