---
title: "Operátor musí být jeden z: +,-, *,-, -, ^, &amp;, jako Mod a, nebo Xor, ne, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;= IsFalse CType, IsTrue –"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Postupy: definice operátora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Postupy: definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)
