---
title: 'Operátor musí být jeden z: +,-, *,-, -, ^, &amp;, Like, Mod a, Or, Xor, Not, <<>>,, =, <>, <, < =, >, > =, CType, IsTrue nebo IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 7acec56be60f88147bac1ba4179ad0234ea1c6e1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270053"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>Operátor musí být jeden z: +,-, *,\,/, ^, &amp;, Like, Mod a, Or, Xor, Not, \< \<, >>...
Je možné deklarovat pouze operátor, který opravňuje k přetížení. V následující tabulce jsou uvedeny operátory, které je možné deklarovat.  
  
|Typ|Operátory|  
|----------|---------------|  
|Unární|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|binární|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Převod (unární)|`CType`|  
  
 Všimněte si, že `=` operátor v binárním seznamu je relační operátor, operátor přiřazení.  
  
 **ID chyby:** BC33000  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Vyberte operátor ze sady přetížitelné operátory.  
  
2.  Pokud potřebujete funkce přetížení operátor nelze přetížit přímo, vytvořte `Function` proceduru, která mají příslušné parametry a vrátí odpovídající hodnotu.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Postupy: Definovat operátor](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Postupy: Definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
