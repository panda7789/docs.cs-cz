---
title: "Kopírování hodnotu & č. 39; ByRef & č. 39; Parametr & č. 39; &lt;parametername&gt;& č. 39; zpět na odpovídající argument narrows z typu & č. 39;&lt; NázevTypu1&gt;& č. 39; na typ & č. 39;&lt; NázevTypu2&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords: BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4bf993639007162e2e17d4b8cb9dfe8d5316acaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>Kopírování hodnotu & č. 39; ByRef & č. 39; Parametr & č. 39; &lt;parametername&gt;& č. 39; zpět na odpovídající argument narrows z typu & č. 39;&lt; NázevTypu1&gt;& č. 39; na typ & č. 39;&lt; NázevTypu2&gt;& č. 39;
Postup je volána s argumentem, která rozšiřuje na s typem parametru odpovídající a je zužující převod parametr argument.  
  
 Když definujete třídu nebo strukturu, můžete definovat jeden nebo více operátorů převodu typu třídu nebo strukturu převést na jiné typy. Můžete také definovat zpětný převod operátory převést tyto typy zpět do vaší třídy nebo typ struktury. Pokud použijete typ vašeho třídu nebo strukturu ve volání procedury, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] můžete použít tyto operátory převodu typu argument převést na typ jeho odpovídající parametr.  
  
 Pokud předáte argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] někdy zkopíruje hodnota argumentu do místní proměnné v postupu neprochází odkaz. V takovém případě, když se proces vrátí [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zpět do argument ve volání kód musí zkopírujte místní hodnotu proměnné.  
  
 Pokud `ByRef` hodnota argumentu se zkopíruje do procesu a argumentů a parametrů jsou stejného typu, je nutné žádný převod. Pokud se typy liší, ale [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nutné převést v obou směrech. Pokud jeden z typů třídu nebo strukturu typu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] musí ho převést na a z jiných typu. Pokud jeden z těchto převody je rozšíření, může být zužující zpětný převod.  
  
 **ID chyby:** BC32053  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud je to možné, použijte volání argument stejného typu jako parametr postupu, takže [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] není nutné provádět jakékoli převody.  
  
-   Pokud potřebujete volání procedury s argumentem, zadejte odlišný od typu parametru ale nemusíte vrátit hodnotu do volání argument, definujte parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) místo `ByRef`.  
  
-   Pokud budete potřebovat vrátit hodnotu do volání argument, definice operátora zpětný převod jako [Widening](../../../visual-basic/language-reference/modifiers/widening.md), pokud je to možné.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametry a argumenty procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Předávání argumentů podle hodnoty a podle Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Postupy: definice operátora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Postupy: definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
