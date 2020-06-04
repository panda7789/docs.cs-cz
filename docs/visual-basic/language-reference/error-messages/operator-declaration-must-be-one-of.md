---
title: 'Deklarace operátoru musí být jedna z těchto: +,-, *,-,-, ^, &amp; , like, mod, and, or, XOR, not,  <<,  >>, =,  <>, <, <=, >, >=, CType, true, false.'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 3fb2cf392611e5ca83818e3bf173513be031085d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409330"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>Deklarace operátoru musí být jedna z těchto: +,-, *, \, /, ^, &amp; , like, mod, and, or, XOR, not, \<\<, >>...
Můžete deklarovat pouze operátor, který má nárok na přetížení. V následující tabulce jsou uvedeny operátory, které můžete deklarovat.  
  
|Typ|Operátory|  
|----------|---------------|  
|Unární|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binární|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Převod (Unární)|`CType`|  
  
 Všimněte si, že `=` operátor v binárním seznamu je operátor porovnání, nikoli operátor přiřazení.  
  
 **ID chyby:** BC33000  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Vyberte operátor ze sady přetížených operátorů.  
  
2. Pokud potřebujete funkcionalitu přetížení operátoru, který nelze přímo přetížit, vytvořte `Function` proceduru, která přijímá příslušné parametry a vrátí příslušnou hodnotu.  
  
## <a name="see-also"></a>Viz také

- [Operator – příkaz](../statements/operator-statement.md)
- [Procedury operátoru](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Postupy: Definice operátoru](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Postupy: Definice operátoru převodu](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Function – příkaz](../statements/function-statement.md)
