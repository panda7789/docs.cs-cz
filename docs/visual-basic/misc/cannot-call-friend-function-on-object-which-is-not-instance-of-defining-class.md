---
title: Nelze volat funkce friend objekt, který není instancí definice – třída
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a655207110d512805490b693e413b1d22b0367ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33634918"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Nelze volat funkce friend objekt, který není instancí definice – třída
Buď jste se pokusili volání `Friend` postup třídy, nebo jste se pokusili získat přístup `Friend` vlastnosti nebo metody napříč procesy nebo mezi vlákny. A `Friend` postup lze volat z modulu mimo třídu, ale je součástí projektu, ve kterém je třída definovaná.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, že jsou volání nebo přístup k procesu z modul, který je součástí projektu, ve kterém je třída definovaná.  
  
## <a name="see-also"></a>Viz také  
 [Friend](../../visual-basic/language-reference/modifiers/friend.md)
