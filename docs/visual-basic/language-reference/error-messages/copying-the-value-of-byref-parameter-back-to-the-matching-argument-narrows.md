---
title: Kopírování hodnoty parametru '<parametername> 'ByRef' zpět na odpovídající argument způsobí zúžení z typu '<typename1>' na typ '<typename2>'.
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: bac5f9a88df719bc64a8b0541f65e5912275866e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409748"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a>Kopírování hodnoty parametru '\<parametername> 'ByRef' zpět na odpovídající argument způsobí zúžení z typu '\<typename1>' na typ '\<typename2>'.
Procedura je volána s argumentem, který rozšiřuje na odpovídající typ parametru a je zúžena konverze z parametru na argument.  
  
 Při definování třídy nebo struktury můžete definovat jeden nebo více operátorů převodu pro převod této třídy nebo typu struktury na jiné typy. Můžete také definovat operátory zpětného převodu pro převod těchto ostatních typů zpět na typ třídy nebo struktury. Použijete-li typ třídy nebo struktury ve volání procedury, Visual Basic mohou použít tyto operátory převodu pro převod typu argumentu na typ odpovídajícího parametru.  
  
 Pokud předáte argument [ByRef](../modifiers/byref.md), Visual Basic někdy zkopíruje hodnotu argumentu do místní proměnné v proceduře namísto předání odkazu. V takovém případě, když se procedura vrátí, Visual Basic nutné zkopírovat hodnotu lokální proměnné zpátky do argumentu v volajícím kódu.  
  
 Pokud `ByRef` je do procedury zkopírována hodnota argumentu a argument a parametr je stejného typu, není nutný žádný převod. Pokud se však typy liší, Visual Basic nutné převést v obou směrech. Pokud je jeden z typů vaší třídy nebo typu struktury, Visual Basic musí převést na i z druhého typu. Pokud jeden z těchto převodů rozšiřujete, může se zpětný převod zúžit.  
  
 **ID chyby:** BC32053  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud je to možné, použijte jako parametr procedury volající argument stejného typu, takže Visual Basic nemusí provádět žádné konverze.  
  
- Pokud potřebujete zavolat proceduru s typem argumentu odlišným od typu parametru, ale nemusíte vracet hodnotu do argumentu volání, definujte parametr jako [ByVal](../modifiers/byval.md) namísto `ByRef` .  
  
- Pokud potřebujete vrátit hodnotu do argumentu volání, definujte operátor zpětného převodu jako [rozšiřující](../modifiers/widening.md), pokud je to možné.  
  
## <a name="see-also"></a>Viz také

- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Parametry a argumenty procedury](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Předávání argumentů podle hodnoty a reference](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Procedury operátoru](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Operator – příkaz](../statements/operator-statement.md)
- [Postupy: Definice operátoru](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Postupy: Definice operátoru převodu](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Převody typů v jazyce Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
- [Rozšíření a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
