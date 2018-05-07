---
title: 'Operátor musí být jeden z: +,-, *,-, -, ^, &amp;, jako Mod a, nebo Xor, ne, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;= IsFalse CType, IsTrue –'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: eb1e7e8088ec8661be2469aff043c0f1a96e4d01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a>Operátor musí být jeden z: +,-, *,\,/, ^, &amp;, jako Mod a, nebo Xor, ne, &lt; &lt;, &gt; &gt;...
Lze deklarovat pouze operátor, který je vhodné pro přetížení. Následující tabulka uvádí operátory, které můžou deklarovat.  
  
|Typ|Operátory|  
|----------|---------------|  
|Unární|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|binární|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Převod (unární)|`CType`|  
  
 Všimněte si, že `=` operátor v seznamu binární je relační operátor, operátor přiřazení.  
  
 **ID chyby:** BC33000  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Vyberte operátor ze sady přetížitelné operátory.  
  
2.  Pokud potřebujete funkci přetížení operátor, který nelze přímo přetížení, vytvořte `Function` postup, který mají příslušné parametry a vrátí odpovídající hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Postupy: Definice operátoru převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
