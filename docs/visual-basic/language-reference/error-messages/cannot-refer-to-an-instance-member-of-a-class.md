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
ms.openlocfilehash: 368539ed24d9819c8d1ddbbb9e3e0dff21d27c32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590180"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>V rámci sdílené metody nebo inicializační procedury sdíleného člena nelze odkazovat na instanci členu, aniž by byla k dispozici explicitní instance třídy.
Pokusili jste se k odkazování na člena nesdílené třídy z v rámci sdílené procedury. Následující příklad ukazuje taková situace.  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 V předchozím příkladu příkaz přiřazení `x = 10` tuto chybovou zprávu. Je to proto, že sdílený postup se pokouší o přístup k proměnné instance.  
  
 Proměnná `x` je členem instance, protože není deklarovaný jako [sdílené](../../../visual-basic/language-reference/modifiers/shared.md). Každá instance třídy `sample` obsahuje vlastní jednotlivé proměnné `x`. Když jedna instance Nastaví nebo změní hodnotu `x`, nemá vliv na hodnotu `x` v jeho ostatní instance.  
  
 Však postup `setX` je `Shared` mezi všechny instance třídy `sample`. To znamená, že není přidružen k žádné jedna instance třídy, ale spíš funguje nezávisle na jednotlivých instancí. Protože nemá žádné připojení s konkrétní instanci `setX` nelze přistupovat k proměnné instance. Ho musí fungovat jenom na `Shared` proměnné. Když `setX` nastaví změny nebo změny hodnoty sdílené proměnné, nová hodnota je k dispozici pro všechny instance třídy.  
  
 **ID chyby:** BC30369  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Rozhodněte, zda chcete, aby člen sdílen všech instancí třídy, nebo zachovány jednotlivých pro každou instanci.  
  
2.  Pokud chcete, aby jedna kopie člena na všechny instance, přidejte `Shared` – klíčové slovo k deklarace členů. Zachovat `Shared` – klíčové slovo v postupu deklaraci.  
  
3.  Pokud chcete, aby každá instance mít svůj vlastní jednotlivá kopie člena, nezadávejte `Shared` pro deklarace členů. Odeberte `Shared` – klíčové slovo z deklarace procedury.  
  
## <a name="see-also"></a>Viz také  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
