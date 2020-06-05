---
title: Vyhodnocení funkce je zakázáno, protože při vyhodnocování předchozí verze vypršel časový limit.
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 7b0113e9c1018772da6dc180f7fc5beb0e922917
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402950"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>Vyhodnocení funkce je zakázáno, protože při vyhodnocování předchozí verze vypršel časový limit.
Vyhodnocení funkce je zakázáno, protože vypršel časový limit pro předchozí vyhodnocení funkce. Chcete-li znovu povolit vyhodnocení funkce, proveďte krok znovu nebo znovu spusťte ladění.  
  
 Výraz v ladicím programu sady Visual Studio určuje volání procedury, ale vypršel limit jiného vyhodnocení.  
  
 Možné příčiny vypršení časového limitu volání procedury zahrnují nekonečnou smyčku nebo *nekonečné smyčky*. Další informace najdete v tématu [... Další příkaz](../statements/for-next-statement.md).  
  
 Zvláštní případ nekonečné smyčky je *rekurze*. Další informace naleznete v tématu [rekurzivní procedury](../../programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **ID chyby:** BC30957  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Pokud je to možné, určete, co bylo předchozí vyhodnocení funkce a co způsobilo vypršení časového limitu. V opačném případě se tato chyba může zobrazit znovu.  
  
2. Proveďte krok ladicího programu znovu nebo ladění ukončete a znovu spusťte.  
  
## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Procházení kódu s ladicím programem](/visualstudio/debugger/navigating-through-code-with-the-debugger)
