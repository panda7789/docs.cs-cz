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
ms.openlocfilehash: e3c24818ea87884a0dd9b42c604e13e16ca6d3d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391817"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Určuje, že parametr procedury přijímá volitelné pole prvků zadaného typu. `ParamArray`dá se použít jenom pro poslední parametr seznamu parametrů.  
  
## <a name="remarks"></a>Poznámky  
 `ParamArray`umožňuje předat libovolnému počtu argumentů proceduru. `ParamArray`Parametr je vždy deklarován pomocí [ByVal](byval.md).  
  
 Jednomu nebo více argumentům můžete zadat `ParamArray` parametr předáním pole vhodného datového typu, seznamu hodnot oddělených čárkami nebo nic vůbec. Podrobnosti naleznete v tématu "volání ParamArray" v [polích parametrů](../../programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
> Kdykoli budete pracovat s polem, které může být neomezeně velké, existuje riziko, že dojde k přeběhu některé interní kapacity vaší aplikace. Pokud přijímáte pole parametrů z volajícího kódu, měli byste otestovat jeho délku a provést příslušné kroky, pokud je pro vaši aplikaci příliš velká.  
  
 `ParamArray`V těchto kontextech lze použít modifikátor:  
  
 [Declare – příkaz](../statements/declare-statement.md)  
  
 [Function – příkaz](../statements/function-statement.md)  
  
 [Property – příkaz](../statements/property-statement.md)  
  
 [Sub – příkaz](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Klíčová slova](../keywords/index.md)
- [Pole parametrů](../../programming-guide/language-features/procedures/parameter-arrays.md)
