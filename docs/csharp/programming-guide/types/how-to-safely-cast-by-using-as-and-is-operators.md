---
title: 'Postupy: Bezpečné přetypování pomocí operátorů as a is (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: 6e02675a2a895add245d3c2e40305a0417fdf429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Postupy: Bezpečné přetypování pomocí operátorů as a is (Průvodce programováním v C#)
Protože jsou polymorfní objekty, je možné proměnnou typu základní třídy pro odvozený typ. Přístup odvozený typ metodě, je potřeba hodnota zpět do odvozený typ přetypování. Však k pokusu o jednoduchou cast v těchto případech vytvoří riziko vyvolání <xref:System.InvalidCastException>. To znamená proč C# poskytuje [je](../../../csharp/language-reference/keywords/is.md) a [jako](../../../csharp/language-reference/keywords/as.md) operátory. Tyto operátory můžete použít k ověření, zda přetypování bude úspěšné, aniž by docházelo vyvolání výjimky. Obecně `as` operátor je efektivnější, protože pokud přetypování můžete provedeny úspěšně ve skutečnosti vrátí hodnotu přetypování. `is` Operátor vrací pouze logickou hodnotu. Je proto dá právě chcete určit typ objektu, ale nemají ve skutečnosti vysílat.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak používat `is` a `as` zadejte operátory přetypovat z jeden odkaz na jiný bez riziko došlo k výjimce. Příklad také ukazuje způsob použití `as` operátor s typy hodnot s povolenou hodnotou Null.  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Typy s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)
