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
ms.openlocfilehash: be8ddb7f9ba08535d12890d1c5c82a9b7b485f3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597357"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Určuje, že parametr postupu přebírá volitelné pole elementy zadaného typu. `ParamArray` lze použít pouze na poslední parametr seznam parametrů.  
  
## <a name="remarks"></a>Poznámky  
 `ParamArray` umožňuje předat libovolný počet argumentů procesu. A `ParamArray` parametr je vždy deklarováno s použitím [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Můžete zadat jednu nebo více argumentů `ParamArray` parametr předáním pole příslušná data typ, seznam hodnoty, nebo nic vůbec. Podrobnosti najdete v tématu "Volání ParamArray" v [pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
>  Vždy, když budete pracovat s pole to může být velký, bez omezení, existuje riziko překročení některé interní kapacitu vaší aplikace. Pokud přijmete pole parametrů z volání kódu, měli otestovat jeho délka a proveďte příslušné kroky, pokud je příliš velká pro vaši aplikaci.  
  
 `ParamArray` Modifikátor lze použít v těchto kontexty:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)  
 [Pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
