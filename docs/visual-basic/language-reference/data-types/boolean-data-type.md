---
title: "Boolean – datový typ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdc106f1ec874c1a2165df069d5f3485fe5b2e43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-data-type-visual-basic"></a>Boolean – datový typ (Visual Basic)
Blokování hodnoty, které může být pouze `True` nebo `False`. Klíčová slova `True` a `False` odpovídají dva stavy `Boolean` proměnné.  
  
## <a name="remarks"></a>Poznámky  
 Použití [logický datový typ (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) tak, aby obsahovala hodnoty dvou stavů například true nebo false, Ano/Ne, nebo zapnutí nebo vypnutí.  
  
 Výchozí hodnota `Boolean` je `False`.  
  
 `Boolean`hodnoty nejsou uložené jako čísla a uložené hodnoty nejsou určeny jako ekvivalentní na čísla. Nikdy byste měli zapsat kód, který závisí na ekvivalentní číselné hodnoty pro `True` a `False`. Kdykoli je to možné, měli byste omezit využití `Boolean` proměnné logické hodnoty, pro které jsou navrženy.  
  
## <a name="type-conversions"></a>Převody typu  
 Když jazyka Visual Basic převádí hodnoty číselný datový typ pro `Boolean`, stane 0 `False` a všechny ostatní hodnoty přestat `True`. Když Visual Basic převede `Boolean` hodnot na číselné typy `False` se změní na 0 a `True` se změní na hodnotu -1.  
  
 Při převodu mezi `Boolean` hodnoty a číselné datové typy, mějte na paměti, že conversion metod rozhraní .NET Framework vždy nevedou stejné výsledky jako klíčová slova převodu jazyka Visual Basic. To je proto, že conversion jazyka Visual Basic uchovává chování, které jsou kompatibilní s předchozími verzemi. Další informace najdete v tématu "Logický typ nemá není převést na číselný typ přesně" v [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Záporná čísla.** `Boolean`není číselného typu a nesmí představovat zápornou hodnotu. V každém případě byste neměli používat `Boolean` pro uložení číselné hodnoty.  
  
-   **Znaky typu.** `Boolean`nemá žádnou – znak typu literálu nebo – znak typu identifikátoru.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.Boolean?displayProperty=nameWithType> struktura.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `runningVB` je `Boolean` proměnné, která ukládá jednoduché nastavení Ano/Ne.  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Řešení potíží s datové typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [CType – funkce](../../../visual-basic/language-reference/functions/ctype-function.md)
