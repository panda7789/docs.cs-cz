---
title: "'<typename>' nemůže dědit ze třídy <type> '<basetypename>', protože rozšiřuje přístup třídy Base <type> mimo sestavení."
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: aa04c558abbcc4259c2821cdcbdc1669b91ffee0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402769"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>'\<typename>' nemůže dědit ze třídy \<type> '\<basetypename>', protože rozšiřuje přístup třídy Base \<type> mimo sestavení.
Třída nebo rozhraní dědí ze základní třídy nebo rozhraní, ale má méně omezující úroveň přístupu.  
  
 Například `Public` rozhraní dědí z `Friend` rozhraní nebo `Protected` Třída dědí z `Private` třídy. Tím se zpřístupňuje základní třída nebo rozhraní pro přístup mimo zamýšlenou úroveň.  
  
 **ID chyby:** BC30910  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Změňte úroveň přístupu odvozené třídy nebo rozhraní tak, aby byla alespoň stejná jako omezení základní třídy nebo rozhraní.  
  
     -nebo-  
  
- Pokud požadujete úroveň přístupu méně omezující, odeberte `Inherits` příkaz. Nemůžete dědit z více než omezené základní třídy nebo rozhraní.  
  
## <a name="see-also"></a>Viz také

- [Class – příkaz](../statements/class-statement.md)
- [Interface – příkaz](../statements/interface-statement.md)
- [Inherits – příkaz](../statements/inherits-statement.md)
- [Úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
