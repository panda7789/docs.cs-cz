---
title: typeof – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 7962a3d0a5885e64701cb9d9a4d689cd982b9830
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422550"
---
# <a name="typeof-c-reference"></a>typeof (Referenční dokumentace jazyka C#)

Používá k získání <xref:System.Type?displayProperty=nameWithType> pro typ objektu. A `typeof` výrazu má následující podobu:

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a>Poznámky

Pokud chcete získat run-time typu výrazu, můžete použít metodu rozhraní .NET Framework <xref:System.Object.GetType%2A>, jako v následujícím příkladu:

```csharp
int i = 0;
System.Type type = i.GetType();
```

`typeof` Operátor nelze přetížit.

`typeof` Operátor můžete použít také u otevřených obecných typů. Typy s více než jeden parametr typu musí mít odpovídající počet čárek ve specifikaci. Například <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> má dva argumenty typu, proto použijete jednu čárku:

```csharp
Type t = typeof(System.Collection.Generic.Dictionary<,>);
```

Následující příklad ukazuje, jak zjistit, jestli návratový typ metody je obecný <xref:System.Collections.Generic.IEnumerable%601>. <xref:System.Type.GetInterface%2A?displayProperty=nameWithType> Vrátí `null` návratový typ není-li <xref:System.Collections.Generic.IEnumerable%601> obecného typu.

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a>Příklad

Tento příklad používá <xref:System.Object.GetType%2A> metodu pro určení typu, který se používá pro jiné výsledek číselné výpočtu. To závisí na požadavky na úložiště z výsledné číslo.

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [operátor typeof](~/_csharplang/spec/expressions.md#the-typeof-operator) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- <xref:System.Type?displayProperty=nameWithType>
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
- [is](../../../csharp/language-reference/keywords/is.md)
