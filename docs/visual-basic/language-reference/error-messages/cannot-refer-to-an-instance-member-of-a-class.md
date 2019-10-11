---
title: V rámci sdílené metody nebo inicializační procedury sdíleného členu nelze odkazovat na instanci členu bez explicitní instance třídy.
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: 9b388685299469d5865d57b698e3a66de912fa84
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250203"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>V rámci sdílené metody nebo inicializační procedury sdíleného členu nelze odkazovat na instanci členu bez explicitní instance třídy.

Pokusili jste se v rámci sdílené procedury odkazovat na nesdíleného člena třídy. Následující příklad znázorňuje takovou situaci:
  
```vb  
Class Sample
    Public x as Integer  
    Public Shared Sub SetX()
        x = 10  
    End Sub  
End Class  
```  
  
 V předchozím příkladu příkaz přiřazení `x = 10` vygeneruje tuto chybovou zprávu. Je to proto, že se sdílená procedura pokouší o přístup k proměnné instance.  
  
 Proměnná `x` je členem instance, protože není deklarována jako [Shared](../modifiers/shared.md). Každá instance třídy `Sample` obsahuje vlastní individuální proměnnou `x`. Když jedna instance nastaví nebo změní hodnotu `x`, neovlivní hodnotu `x` v jakékoli jiné instanci.
  
 Nicméně procedura `SetX` je `Shared` mezi všemi instancemi třídy `Sample`. To znamená, že není přidružena k žádné jedné instanci třídy, ale funguje spíše nezávisle na jednotlivých instancích. Protože nemá připojení s určitou instancí, `setX` nemůže získat přístup k proměnné instance. Musí pracovat pouze s proměnnými @no__t 0. Když `SetX` nastaví nebo změní hodnotu sdílené proměnné, je tato nová hodnota k dispozici všem instancím třídy.
  
 **ID chyby:** BC30369
  
## <a name="to-correct-this-error"></a>Oprava této chyby
  
1. Rozhodněte, zda chcete, aby byl člen sdílen mezi všemi instancemi třídy, nebo aby se pro každou instanci chovaly jednotlivě.

2. Pokud chcete jednu kopii člena sdílet mezi všemi instancemi, přidejte do deklarace členů klíčové slovo `Shared`. V deklaraci procedury zachovejte klíčové slovo `Shared`.

3. Chcete-li, aby každá instance měla svou vlastní jednotlivou kopii člena, nezadávejte pro deklaraci člena `Shared`. Odeberte klíčové slovo `Shared` z deklarace procedury.
  
## <a name="see-also"></a>Související témata

- [Sdíleného](../modifiers/shared.md)
