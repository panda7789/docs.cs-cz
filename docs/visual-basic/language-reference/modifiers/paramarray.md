---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: b9dee0fc876c6e7a02d085db7db4bf1c5dd2c68d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053909"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Určuje, že parametr procedury přijímá volitelné pole prvků zadaného typu. `ParamArray` lze použít pouze v posledním parametru seznam parametrů.  
  
## <a name="remarks"></a>Poznámky  
 `ParamArray` umožňuje předat libovolný počet argumentů postup. A `ParamArray` parametr je vždy deklarovány pomocí [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Můžete zadat jednu nebo více argumentů `ParamArray` předáním pole odpovídající datový typ parametru, seznam hodnot, nebo nic vůbec. Podrobnosti najdete v tématu "Volání ParamArray" [pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
>  Pokaždé, když budete pracovat s polem, které mohou být po neomezenou dobu velké, existuje riziko přetečení vnitřní nějakým vaší aplikace. Pokud souhlasíte s polem parametrů z volající kód, by měl test jeho délka a proveďte příslušné kroky, pokud je příliš velký pro vaši aplikaci.  
  
 `ParamArray` Modifikátor lze použít v těchto kontextech:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
