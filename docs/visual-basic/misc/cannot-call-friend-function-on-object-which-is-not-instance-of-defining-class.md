---
title: Nejde volat funkci Friend u objektu, který není instancí definující třídy.
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c18c04470c4c49113e8195b92185326c5c4197c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400845"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Nejde volat funkci Friend u objektu, který není instancí definující třídy.
Buď jste se pokusili zavolat `Friend` proceduru třídy, nebo jste se pokusili získat přístup k `Friend` vlastnosti nebo metodě buď mezi procesy, nebo mezi vlákny. `Friend`Procedura se může volat z modulu mimo třídu, ale je součástí projektu, ve kterém je třída definovaná.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že zavoláte nebo přistupujete k proceduře z modulu, který je součástí projektu, ve kterém je třída definována.  
  
## <a name="see-also"></a>Viz také

- [Friend](../language-reference/modifiers/friend.md)
