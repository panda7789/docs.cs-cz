---
title: Nelze volat spřátelenou funkci pro objekt, který není instancí definující třídy
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c65bbb5028cf042b702bb2b8336d40512c980790
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912688"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Nelze volat spřátelenou funkci pro objekt, který není instancí definující třídy
Buď se snažíte volat `Friend` postup třídy, nebo jste se pokusili získat přístup `Friend` vlastnosti nebo metody procesy nebo mezi vlákny. A `Friend` procedury lze volat z modulu vně třídy, ale je součástí projektu, ve kterém je třída definovaná.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že jsou volání nebo přístupu k postupu z modulu, který je součástí projektu, ve kterém je třída definovaná.  
  
## <a name="see-also"></a>Viz také:

- [Friend](../../visual-basic/language-reference/modifiers/friend.md)
