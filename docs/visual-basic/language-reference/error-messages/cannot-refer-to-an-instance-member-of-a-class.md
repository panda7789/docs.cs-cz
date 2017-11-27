---
title: "V rámci sdílené metody nebo inicializační procedury sdíleného člena nelze odkazovat na instanci členu, aniž by byla k dispozici explicitní instance třídy."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a15d36c0b3a4d6b1657d583de0dc61621da960d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
 [Sdílené](../../../visual-basic/language-reference/modifiers/shared.md)
