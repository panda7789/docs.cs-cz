---
title: Implicitní převod z &#39; &lt;NázevTypu1&gt; &#39; k &#39; &lt;NázevTypu2&gt; &#39; v hodnotu z &#39;ByRef&#39; parametr &#39; &lt; Název parametru&gt; &#39; zpět na odpovídající argument.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: b1f772598b18f8edfe0198f62d78854d30f993ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Implicitní převod z &#39; &lt;NázevTypu1&gt; &#39; k &#39; &lt;NázevTypu2&gt; &#39; v hodnotu z &#39;ByRef&#39; parametr &#39; &lt; Název parametru&gt; &#39; zpět na odpovídající argument.
Postup je volán s [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument jiného typu než jeho odpovídající parametr.  
  
 Pokud předáte argument `ByRef`, hodnota argumentu jazyka Visual Basic někdy zkopíruje do místní proměnné v postupu neprochází odkaz. V takovém případě po návratu postup jazyka Visual Basic musí pak zkopírujte místní hodnotu proměnné zpět do argument ve volání kódu.  
  
 Pokud `ByRef` hodnota argumentu se zkopíruje do procesu a argumentů a parametrů jsou stejného typu, je nutné žádný převod. Ale pokud se typy liší, musíte převést jazyka Visual Basic v obou směrech. Vzhledem k tomu, že nemůžete použít `CType` nebo některý z dalších převod slov v argumentu procedury nebo parametr, takový převod je vždy implicitní.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC41999  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud je to možné použijte volání argument stejného typu jako parametr postupu, není nutné provádět jakékoli převody jazyka Visual Basic.  
  
-   Pokud potřebujete volání procedury s argumentem, zadejte odlišný od typu parametru ale nemusíte vrátit hodnotu do volání argument, definujte parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) místo `ByRef`.  
  
## <a name="see-also"></a>Viz také  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametry a argumenty procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Předávání argumentů podle hodnoty a reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
