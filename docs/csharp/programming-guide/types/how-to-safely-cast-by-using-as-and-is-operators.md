---
title: "Postupy: Bezpečné přetypování pomocí operátorů as a is (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 733b67408997feb0e518db327e3eedd42f286a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Postupy: Bezpečné přetypování pomocí operátorů as a is (Průvodce programováním v C#)
Protože jsou polymorfní objekty, je možné proměnnou typu základní třídy pro odvozený typ. Přístup odvozený typ metodě, je potřeba hodnota zpět do odvozený typ přetypování. Však k pokusu o jednoduchou cast v těchto případech vytvoří riziko vyvolání <xref:System.InvalidCastException>. To znamená proč C# poskytuje [je](../../../csharp/language-reference/keywords/is.md) a [jako](../../../csharp/language-reference/keywords/as.md) operátory. Tyto operátory můžete použít k ověření, zda přetypování bude úspěšné, aniž by docházelo vyvolání výjimky. Obecně `as` operátor je efektivnější, protože pokud přetypování můžete provedeny úspěšně ve skutečnosti vrátí hodnotu přetypování. `is` Operátor vrací pouze logickou hodnotu. Je proto dá právě chcete určit typ objektu, ale nemají ve skutečnosti vysílat.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak používat `is` a `as` zadejte operátory přetypovat z jeden odkaz na jiný bez riziko došlo k výjimce. Příklad také ukazuje způsob použití `as` operátor s typy hodnot s povolenou hodnotou Null.  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)
