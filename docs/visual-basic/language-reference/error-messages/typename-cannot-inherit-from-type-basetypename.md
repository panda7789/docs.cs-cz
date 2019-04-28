---
title: "'<typename>' nemůže dědit ze třídy <type> '<basetypename>', protože rozšiřuje přístup třídy Base <type> mimo sestavení."
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764358"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>"\<typename >' nemůže dědit od třídy \<typu >"\<basetypename >' protože rozšiřuje přístup základní třídy \<typ > mimo sestavení
Třídy nebo rozhraní dědí ze základní třídy nebo rozhraní, ale má míň omezující úroveň přístupu.  
  
 Například `Public` rozhraní zdědí `Friend` rozhraní, nebo `Protected` třída dědí z `Private` třídy. Tato třída zveřejňuje základní třídu nebo rozhraní pro přístup k mimo určené úroveň.  
  
 **ID chyby:** BC30910  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Změníte úroveň přístupu odvozené třídy nebo rozhraní, které má být omezující jako základní třídu nebo rozhraní.  
  
     -nebo-  
  
- Pokud požadujete méně omezující úroveň přístupu, odeberte `Inherits` příkazu. Nemůže dědit z více omezený základní třídu nebo rozhraní.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
