---
title: 'Postupy: Bezpečné přetypování pomocí operátorů as a is (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: de59fb49ca5dbe1282cd828f7d6995dda449d31b
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257298"
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Postupy: Bezpečné přetypování pomocí operátorů as a is (Průvodce programováním v C#)
Protože objekty jsou polymorfní, je možné pro proměnné typu základní třídy pro uložení odvozeného typu. Pro přístup k metodám instance odvozeného typu, je nezbytné převést hodnotu zpět na odvozeného typu. Však pokusu o jednoduchý přetypování v těchto případech vytvoří riziko vyvolání <xref:System.InvalidCastException>. To znamená proč C# poskytuje [je](../../../csharp/language-reference/keywords/is.md) a [jako](../../../csharp/language-reference/keywords/as.md) operátory. Tyto operátory můžete použít k ověření, zda přetypování proběhne úspěšně, aniž by to způsobilo vyvolání výjimky. Obecně platí `as` operátor je mnohem efektivnější, protože je ve skutečnosti vrací hodnotu přetypování, pokud přetypování lze provést úspěšně. `is` Operátor vrátí logickou hodnotu. Může být proto použita, když pouze k určení typu objektu, ale nemají skutečně přetypovat.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak používat `is` a `as` operátory přetypování z jednoho odkazu typu na jiný bez rizika došlo k výjimce. Tento příklad také ukazuje způsob použití `as` operátor s typy s možnou hodnotou Null.  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Typy s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)
