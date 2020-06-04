---
title: Odvozené třídy nemohou vyvolat události třídy Base.
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: c59212a28ba27123a7db9163ff7437c159a3d310
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409696"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Odvozené třídy nemohou vyvolat události třídy Base.
Událost lze vyvolat pouze z prostoru deklarací, ve kterém je deklarována. Třída proto nemůže vyvolat události z jakékoli jiné třídy, dokonce i z toho, ze které je odvozena.  
  
 **ID chyby:** BC30029  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přesuňte `Event` příkaz nebo `RaiseEvent` příkaz, aby byly ve stejné třídě.  
  
## <a name="see-also"></a>Viz také

- [Event – příkaz](../statements/event-statement.md)
- [RaiseEvent – příkaz](../statements/raiseevent-statement.md)
