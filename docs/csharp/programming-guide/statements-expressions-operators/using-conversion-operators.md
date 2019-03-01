---
title: Použití operátorů převodu - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: 888339661ba1cb2e0b702f284d9f27b3217e74c1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973155"
---
# <a name="using-conversion-operators-c-programming-guide"></a>Použití operátorů převodu (Průvodce programováním v C#)
Je možné použít operátory převodů `implicit`, které jsou jednodušší, nebo operátory převodů `explicit`, které jasně označují každému, kdo čte kód, že převádíte typ. Toto téma ukazuje oba typy operátorů převodu.  
  
> [!NOTE]
>  Informace o převodech jednoduchého typu naleznete v tématu [jak: Převod řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [jak: Převedení pole bajtů na typ int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [jak: Převod mezi hexadecimálními řetězci a číselnými typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), nebo <xref:System.Convert>.  
  
## <a name="example"></a>Příklad  
 Toto je příklad explicitního operátoru převodu. Tento operátor převede typ <xref:System.Byte> na hodnotu s názvem `Digit`. Vzhledem k tomu, že ne všechny bajty mohou být převedeny na číslice, je převod explicitní a znamená, že musí být použito přetypování, jak je znázorněno v metodě `Main`.  
  
 [!code-csharp[csProgGuideStatements#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#11)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje operátor implicitního převodu definováním operátoru převodu, který vrátí zpět, co předchozí příklad udělal: převede z hodnotové třídy s názvem `Digit` na integrál typu <xref:System.Byte>. Protože libovolná číslice může být převedena na <xref:System.Byte>, není potřeba přinutit uživatele k explicitnímu převodu.  
  
 [!code-csharp[csProgGuideStatements#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#12)]  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
- [is](../../../csharp/language-reference/keywords/is.md)
