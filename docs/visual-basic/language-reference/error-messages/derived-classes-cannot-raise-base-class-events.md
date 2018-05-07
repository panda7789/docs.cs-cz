---
title: Odvozené třídy nemohou vyvolat události třídy Base.
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 365ce6ece1d964d3fac2a44f7ed4c1e16f44c95d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Odvozené třídy nemohou vyvolat události třídy Base.
Událost může být vyvolána pouze z deklarace místa, ve kterém je deklarovaná. Proto třídy nemohou vyvolat události z jiné třídě, i jeden, ze kterého je odvozený.  
  
 **ID chyby:** BC30029  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přesunout `Event` příkaz nebo `RaiseEvent` příkaz tak, aby byly ve stejné třídě.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Příkaz RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
