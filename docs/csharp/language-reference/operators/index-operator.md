---
title: '[] – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 948ce238058307631cf0e5a7a5e3d72664233052
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333392"
---
# <a name="-operator-c-reference"></a>[] – operátor (C# odkaz)

Hranaté závorky, `[]`, se obvykle používají pro přístup k prvkům pole, indexovací člen nebo ukazatel.

Další informace o přístup k prvkům ukazatel, naleznete v tématu [postupy: přístup k elementu pole pomocí ukazatele](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).

Můžete také použít hranaté závorky k určení [atributy](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a>Přístup k poli

Následující příklad ukazuje, jak přistupovat k prvkům pole:

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

Pokud pole indexu je mimo hranice odpovídající dimenze v poli, <xref:System.IndexOutOfRangeException> je vyvolána výjimka.

Jak ukazuje předchozí příklad, také použít hranaté závorky v deklaraci typu pole a vytvoření instance pole instance.

Další informace o polích naleznete v tématu [pole](../../programming-guide/arrays/index.md).

## <a name="indexer-access"></a>Přístup indexeru

Následující příklad používá .NET <xref:System.Collections.Generic.Dictionary%602> typu k předvedení přístup indexeru:

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

Indexery umožňují index instance typu uživatelem definované v podobným způsobem jako indexování pole. Na rozdíl od indexy pole, které musí být celé číslo, mohou být deklarovány argumenty indexeru být libovolného typu.

Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

Přístup k prvkům `[]` není považováno za očekával se přetěžovatelný operátor. Použití [indexery](../../programming-guide/indexers/index.md) pro podporu indexování pomocí uživatelem definovaných typů.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [přístup k prvkům](~/_csharplang/spec/expressions.md#element-access) a [přístup k prvkům ukazatel](~/_csharplang/spec/unsafe-code.md#pointer-element-access) oddíly [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Pole](../../programming-guide/arrays/index.md)
- [Indexery](../../programming-guide/indexers/index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Atributy](../../programming-guide/concepts/attributes/index.md)