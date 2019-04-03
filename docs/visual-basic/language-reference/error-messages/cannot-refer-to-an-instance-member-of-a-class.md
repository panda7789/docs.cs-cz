---
title: V rámci sdílené metody nebo inicializační procedury sdíleného člena nelze odkazovat na instanci členu, aniž by byla k dispozici explicitní instance třídy.
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: fc54bbf8053c07cc3b48a762b6f1c60344de9921
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822567"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>V rámci sdílené metody nebo inicializační procedury sdíleného člena nelze odkazovat na instanci členu, aniž by byla k dispozici explicitní instance třídy.
Pokusili jste se odkazovat na nesdílený člen třídy z v rámci sdílené procedury. Následující příklad ukazuje takovou situaci.  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 V předchozím příkladu přiřazovací příkaz `x = 10` tuto chybovou zprávu. Je to proto, sdílený postup se pokouší o přístup k proměnné instance.  
  
 Proměnná `x` je členem instance, protože není deklarován jako [Shared](../../../visual-basic/language-reference/modifiers/shared.md). Každá instance třídy `sample` obsahuje vlastní jednotlivých proměnnou `x`. Když jedna instance nastavuje nebo mění hodnotu `x`, nemá vliv na hodnotu `x` v jiné instanci.  
  
 Nicméně postup `setX` je `Shared` mezi všemi instancemi třídy `sample`. To znamená, že není spojen s jakoukoli jednu instanci třídy, ale místo toho pracuje nezávisle jednotlivých instancí. Protože nemá žádné připojení s konkrétní instancí `setX` nelze přistupovat k proměnné instance. Musíte pouze na provoz `Shared` proměnné. Když `setX` nastavuje nebo mění hodnotu sdíleného proměnné, nová hodnota je k dispozici pro všechny instance třídy.  
  
 **ID chyby:** BC30369  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Rozhodněte, jestli chcete, aby člen sdílí mezi všemi instancemi třídy, nebo se uchovávají jednotlivé pro každou instanci.  
  
2.  Pokud chcete jednu kopii členu, který chcete sdílet mezi všemi instancemi, přidejte `Shared` – klíčové slovo do deklarace člena. Zachovat `Shared` – klíčové slovo v deklaraci procedury.  
  
3.  Pokud chcete, aby každá instance má svůj vlastní jednotlivá kopie člena, nezadávejte `Shared` pro deklarace člena. Odeberte `Shared` – klíčové slovo z deklarace procedury.  
  
## <a name="see-also"></a>Viz také:

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
