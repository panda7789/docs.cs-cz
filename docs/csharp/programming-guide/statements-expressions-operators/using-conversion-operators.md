---
title: "Použití operátorů převodu (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5a43332df795d853c3060a604360adeaea5e3fd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-conversion-operators-c-programming-guide"></a>Použití operátorů převodu (Průvodce programováním v C#)
Je možné použít operátory převodů `implicit`, které jsou jednodušší, nebo operátory převodů `explicit`, které jasně označují každému, kdo čte kód, že převádíte typ. Toto téma ukazuje oba typy operátorů převodu.  
  
> [!NOTE]
>  Informace o jednoduchý typ převody najdete v tématu [postupy: převedení řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [postupy: převedení pole bajtů na typ int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [postupy: převod mezi hexadecimálními řetězci a číselné Typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), nebo <xref:System.Convert>.  
  
## <a name="example"></a>Příklad  
 Toto je příklad explicitního operátoru převodu. Tento operátor převede typ <xref:System.Byte> na hodnotu s názvem `Digit`. Vzhledem k tomu, že ne všechny bajty mohou být převedeny na číslice, je převod explicitní a znamená, že musí být použito přetypování, jak je znázorněno v metodě `Main`.  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje operátor implicitního převodu definováním operátoru převodu, který vrátí zpět, co předchozí příklad udělal: převede z hodnotové třídy s názvem `Digit` na integrál typu <xref:System.Byte>. Protože libovolná číslice může být převedena na <xref:System.Byte>, není potřeba přinutit uživatele k explicitnímu převodu.  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [je](../../../csharp/language-reference/keywords/is.md)
