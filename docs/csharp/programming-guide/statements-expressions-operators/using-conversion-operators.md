---
title: Použití operátorů převodu (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: 17a722f7160ae9cd03caa2dff9c4436fcf0f9d9e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139199"
---
# <a name="using-conversion-operators-c-programming-guide"></a>Použití operátorů převodu (Průvodce programováním v C#)
Je možné použít operátory převodů `implicit`, které jsou jednodušší, nebo operátory převodů `explicit`, které jasně označují každému, kdo čte kód, že převádíte typ. Toto téma ukazuje oba typy operátorů převodu.  
  
> [!NOTE]
>  Informace o převodech jednoduchého typu naleznete v tématu [postupy: převedení řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [postupy: převedení pole bajtů na typ int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [postupy: převod mezi hexadecimálními řetězci a číselné Typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), nebo <xref:System.Convert>.  
  
## <a name="example"></a>Příklad  
 Toto je příklad explicitního operátoru převodu. Tento operátor převede typ <xref:System.Byte> na hodnotu s názvem `Digit`. Vzhledem k tomu, že ne všechny bajty mohou být převedeny na číslice, je převod explicitní a znamená, že musí být použito přetypování, jak je znázorněno v metodě `Main`.  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje operátor implicitního převodu definováním operátoru převodu, který vrátí zpět, co předchozí příklad udělal: převede z hodnotové třídy s názvem `Digit` na integrál typu <xref:System.Byte>. Protože libovolná číslice může být převedena na <xref:System.Byte>, není potřeba přinutit uživatele k explicitnímu převodu.  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
- [is](../../../csharp/language-reference/keywords/is.md)
