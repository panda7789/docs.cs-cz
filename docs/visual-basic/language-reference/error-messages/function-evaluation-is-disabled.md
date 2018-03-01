---
title: "Vyhodnocení funkce je zakázáno, protože při vyhodnocování předchozí verze vypršel časový limit."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05067e730486b443b7a508adb499f34c060d5093
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>Vyhodnocení funkce je zakázáno, protože při vyhodnocování předchozí verze vypršel časový limit.
Vyhodnocení funkce je zakázáno, protože vypršel časový limit předchozího vyhodnocení funkce. Znovu povolit vyhodnocení funkce, krok opakujte nebo restartujte ladění.  
  
 Výraz v ladicím programu sady Visual Studio určuje volání procedury, ale vypršel limit jiného vyhodnocení.  
  
 Možné příčiny vypršení časového limitu volání procedury patří nekonečné smyčce nebo *nekonečná smyčka*. Další informace najdete v tématu [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 Je ve speciálním případě nekonečné smyčce *rekurze*. Další informace najdete v tématu [rekurzivní procedury](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **ID chyby:** BC30957  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Je-li to možné, určete, o jaké dřívější vyhodnocení funkce se jedná a co způsobilo vypršení jejího časového limitu. Jinak může k této chybě dojít znovu.  
  
2.  Proveďte krok ladicího programu znovu nebo ladění ukončete a znovu spusťte.  
  
## <a name="see-also"></a>Viz také  
 [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
 [Procházení kódu s ladicím programem](/visualstudio/debugger/navigating-through-code-with-the-debugger)
