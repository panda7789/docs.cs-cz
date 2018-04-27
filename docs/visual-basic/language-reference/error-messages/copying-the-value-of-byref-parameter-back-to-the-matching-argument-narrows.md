---
title: Kopírování hodnotu &#39;ByRef&#39; parametr &#39; &lt;parametername&gt; &#39; zpět na odpovídající argument zúží z typu &#39; &lt;NázevTypu1&gt; &#39; na typ &#39; &lt;NázevTypu2&gt;&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18c72e56e4b2cc9c2251de2417a9f12a6688323f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>Kopírování hodnotu &#39;ByRef&#39; parametr &#39; &lt;parametername&gt; &#39; zpět na odpovídající argument zúží z typu &#39; &lt;NázevTypu1&gt; &#39; na typ &#39; &lt;NázevTypu2&gt;&#39;
Postup je volána s argumentem, která rozšiřuje na s typem parametru odpovídající a je zužující převod parametr argument.  
  
 Když definujete třídu nebo strukturu, můžete definovat jeden nebo více operátorů převodu typu třídu nebo strukturu převést na jiné typy. Můžete také definovat zpětný převod operátory převést tyto typy zpět do vaší třídy nebo typ struktury. Pokud použijete typ vašeho třídu nebo strukturu ve volání procedury, Visual Basic můžete použít tyto operátory převodu typ argumentu převést na typ jeho odpovídající parametr.  
  
 Pokud předáte argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), hodnota argumentu jazyka Visual Basic někdy zkopíruje do místní proměnné v postupu neprochází odkaz. V takovém případě po návratu postup jazyka Visual Basic musí pak zkopírujte místní hodnotu proměnné zpět do argument ve volání kódu.  
  
 Pokud `ByRef` hodnota argumentu se zkopíruje do procesu a argumentů a parametrů jsou stejného typu, je nutné žádný převod. Ale pokud se typy liší, musíte převést jazyka Visual Basic v obou směrech. Pokud jeden z typů typ vašeho třídu nebo strukturu, Visual Basic musí ji převést do a z jiných typu. Pokud jeden z těchto převody je rozšíření, může být zužující zpětný převod.  
  
 **ID chyby:** BC32053  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud je to možné použijte volání argument stejného typu jako parametr postupu, není nutné provádět jakékoli převody jazyka Visual Basic.  
  
-   Pokud potřebujete volání procedury s argumentem, zadejte odlišný od typu parametru ale nemusíte vrátit hodnotu do volání argument, definujte parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) místo `ByRef`.  
  
-   Pokud budete potřebovat vrátit hodnotu do volání argument, definice operátora zpětný převod jako [Widening](../../../visual-basic/language-reference/modifiers/widening.md), pokud je to možné.  
  
## <a name="see-also"></a>Viz také  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametry a argumenty procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Předávání argumentů podle hodnoty a reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Postupy: Definice operátoru převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
