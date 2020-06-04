---
title: Třída delegáta '<classname>' neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody.
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 27be97ba2930791bcb9012c824bc418a0089b037
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409709"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Třída delegáta '\<classname>' neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody.
Volání `Invoke` prostřednictvím delegáta se nezdařilo, protože není `Invoke` implementováno ve třídě Delegate.  
  
 **ID chyby:** BC30220  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zajistěte, aby byla instance třídy Delegate vytvořená `Dim` příkazem a aby byla procedura přiřazena k instanci delegáta s `AddressOf` operátorem.  
  
2. Vyhledejte kód, který implementuje třídu delegáta, a ujistěte se, že implementuje `Invoke` proceduru.  
  
## <a name="see-also"></a>Viz také

- [Delegáti](../../programming-guide/language-features/delegates/index.md)
- [Delegate – příkaz](../statements/delegate-statement.md)
- [AddressOf – operátor](../operators/addressof-operator.md)
- [Dim – příkaz](../statements/dim-statement.md)
