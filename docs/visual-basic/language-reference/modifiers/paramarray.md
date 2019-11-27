---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: fbc87bffebc265e6062512e96fc29a64334b3c65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351376"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Určuje, že parametr procedury přijímá volitelné pole prvků zadaného typu. `ParamArray` lze použít pouze pro poslední parametr seznamu parametrů.  
  
## <a name="remarks"></a>Poznámky  
 `ParamArray` umožňuje předat libovolnému počtu argumentů proceduru. Parametr `ParamArray` je vždy deklarován pomocí [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Jednomu nebo více argumentům `ParamArray` parametr můžete zadat předáním pole vhodného datového typu, seznamu hodnot oddělených čárkami nebo nic vůbec. Podrobnosti naleznete v tématu "volání ParamArray" v [polích parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
> Kdykoli budete pracovat s polem, které může být neomezeně velké, existuje riziko, že dojde k přeběhu některé interní kapacity vaší aplikace. Pokud přijímáte pole parametrů z volajícího kódu, měli byste otestovat jeho délku a provést příslušné kroky, pokud je pro vaši aplikaci příliš velká.  
  
 V těchto kontextech lze použít modifikátor `ParamArray`:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
