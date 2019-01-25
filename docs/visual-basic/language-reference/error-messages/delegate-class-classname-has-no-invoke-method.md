---
title: Třída delegáta &#39; &lt;classname&gt; &#39; neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: d5421ea05968a221bbbf8f52a575550d1bca3cb2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653154"
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Třída delegáta &#39; &lt;classname&gt; &#39; neobsahuje metodu Invoke, a proto výraz tohoto typu nemůže být cílem volání metody
Volání `Invoke` prostřednictvím delegáta se nezdařila, protože `Invoke` není implementované u třídy delegáta.  
  
 **ID chyby:** BC30220  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že byla vytvořena instance třídy delegáta s `Dim` příkazu a, postup byl přiřazen k instanci delegáta s `AddressOf` operátor.  
  
2.  Vyhledejte kód, který implementuje třídu delegáta a ujistěte se, že implementuje `Invoke` postup.  
  
## <a name="see-also"></a>Viz také:
- [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
