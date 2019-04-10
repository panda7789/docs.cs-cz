---
title: Třída delegáta '<classname>' neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody.
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 3fe164d868ee7bde0e687e1d592f4d5a17565aea
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321299"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Třída delegáta\<classname >' neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody
Volání `Invoke` prostřednictvím delegáta se nezdařila, protože `Invoke` není implementované u třídy delegáta.  
  
 **ID chyby:** BC30220  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že byla vytvořena instance třídy delegáta s `Dim` příkazu a, postup byl přiřazen k instanci delegáta s `AddressOf` operátor.  
  
2. Vyhledejte kód, který implementuje třídu delegáta a ujistěte se, že implementuje `Invoke` postup.  
  
## <a name="see-also"></a>Viz také:

- [Delegáty](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [AddressOf – operátor](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)
