---
title: Použití výchozí instance třídy v konstruktoru třídy může vést k nekonečnému rekurzivnímu volání.
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cec3d3d462822ca571cab59a2e4d7e730d2aec46
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664371"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Použití výchozí instance třídy v konstruktoru třídy může vést k nekonečnému rekurzivnímu volání.
V konstruktoru třídy byla použita výchozí instance třídy. To může vést k nekonečnému rekurzivnímu volání, známému také jako nekonečné smyčky.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte výchozí instanci z konstruktoru třídy.  
  
## <a name="see-also"></a>Viz také:

- [Konstruktory](../programming-guide/concepts/object-oriented-programming.md#constructors)
