---
title: "Nelze volat funkce friend objekt, který není instancí definice – třída"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f1ac1ea14efb0cdf0d8ca03257e4da33d35e368
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Nelze volat funkce friend objekt, který není instancí definice – třída
Buď jste se pokusili volání `Friend` postup třídy, nebo jste se pokusili získat přístup `Friend` vlastnosti nebo metody napříč procesy nebo mezi vlákny. A `Friend` postup lze volat z modulu mimo třídu, ale je součástí projektu, ve kterém je třída definovaná.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, že jsou volání nebo přístup k procesu z modul, který je součástí projektu, ve kterém je třída definovaná.  
  
## <a name="see-also"></a>Viz také  
 [Friend](../../visual-basic/language-reference/modifiers/friend.md)
