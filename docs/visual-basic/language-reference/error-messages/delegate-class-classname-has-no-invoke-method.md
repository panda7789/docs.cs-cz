---
title: "Delegát třídy & č. 39; &lt;classname&gt;& č. 39; obsahuje metodu Invoke, takže výrazu tohoto typu nemůže být cílem volání metody"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55d0e2442807e25737d90ac4b45a59b9d3e73037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Delegát třídy & č. 39; &lt;classname&gt;& č. 39; obsahuje metodu Invoke, takže výrazu tohoto typu nemůže být cílem volání metody
Volání `Invoke` prostřednictvím delegáta se nezdařil, protože `Invoke` není implementována ve třídě delegáta.  
  
 **ID chyby:** BC30220  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že instance třídy delegáta byl vytvořen s `Dim` prohlášení a zda procedury byla přiřazena instance delegáta s `AddressOf` operátor.  
  
2.  Vyhledejte kód, který implementuje třídu delegáta a zajistěte, aby se implementuje `Invoke` postupu.  
  
## <a name="see-also"></a>Viz také  
 [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [AddressOf – operátor](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)
