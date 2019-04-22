---
title: Kopírování hodnoty parametru '<parametername> 'ByRef' zpět na odpovídající argument způsobí zúžení z typu '<typename1>' na typ '<typename2>'.
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: fa8607bf72dfb344048ec82514182dcb6810274d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817151"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a>Kopírování hodnoty 'ByRef' parametru '\<parametername >' zpět na odpovídající argument způsobí zúžení z typu '\<NázevTypu1 >' na typ '\<NázevTypu2 > "
Procedura je volána s argumentem, který rozšiřuje na odpovídající typ parametru, a je zužující převod z parametru do argumentu.  
  
 Při definování třídy nebo struktury, můžete definovat jeden nebo více operátorů převodu k převedení typu třídy nebo struktury na jiné typy. Můžete také definovat operátory reverzní převodu k převedení těchto typů zpět do vaší třídy nebo typ struktury. Když použijete typ třídy nebo struktury ve volání procedury, Visual Basic můžete použít tyto operátory převodu k převedení typu argumentu na jeho odpovídající parametr typu.  
  
 Pokud předáte argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic někdy kopíruje hodnotu argumentu do místní proměnné v postupu namísto předávání odkazem. V takovém případě se po návratu podle postupu Visual Basic musí potom zkopírujte hodnotu lokální proměnné zpět do argumentu ve volajícím kódu.  
  
 Pokud `ByRef` hodnota argumentu je zkopírován do procedury a argumentu a parametru jsou stejného typu, je nezbytné žádný převod. Ale pokud se typy liší, musíte převést jazyka Visual Basic v obou směrech. Pokud jeden z typů je typ třídy nebo struktury, musíte převést jazyka Visual Basic ji do i z jiného typu. Pokud je jeden z těchto převodů rozšiřující, může být zúžení zpětný převod.  
  
 **ID chyby:** BC32053  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud je to možné použijte volání argument stejného typu jako parametr procedury, proto není nutné provádět jakýkoli převod jazyka Visual Basic.  
  
-   Pokud je potřeba volání procedury s argumentem typu liší od typu parametru, ale není nutné vrátit hodnotu do volání argument, definujte parametr bude [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) místo `ByRef`.  
  
-   Pokud potřebujete vrátit hodnotu do volání argument, definovat operátor zpětný převod jako [Widening](../../../visual-basic/language-reference/modifiers/widening.md), pokud je to možné.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Parametry a argumenty procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Předávání argumentů podle hodnoty a reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Postupy: Definovat operátor](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Postupy: Definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
