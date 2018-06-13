---
title: Delegovat třída &#39; &lt;classname&gt; &#39; má metodu Invoke, takže výrazu tohoto typu nemůže být cílem volání metody
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: cc1abba46224772e733780800dd104dfc7ebe9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588827"
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Delegovat třída &#39; &lt;classname&gt; &#39; má metodu Invoke, takže výrazu tohoto typu nemůže být cílem volání metody
Volání `Invoke` prostřednictvím delegáta se nezdařil, protože `Invoke` není implementována ve třídě delegáta.  
  
 **ID chyby:** BC30220  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že instance třídy delegáta byl vytvořen s `Dim` prohlášení a zda procedury byla přiřazena instance delegáta s `AddressOf` operátor.  
  
2.  Vyhledejte kód, který implementuje třídu delegáta a zajistěte, aby se implementuje `Invoke` postupu.  
  
## <a name="see-also"></a>Viz také  
 [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
