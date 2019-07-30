---
title: ':: operator- C# reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: c494e8dbb18f44ce5520b21800a21d3feb03da59
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631134"
---
# <a name="-operator-c-reference"></a>:: – operátorC# (Referenční dokumentace)

Kvalifikátor aliasu oboru názvů (`::`) se používá k vyhledání identifikátorů. Je vždy umístěn mezi dvěma identifikátory, jako v tomto příkladu:

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

Operátor lze také použít s *direktivou using alias:* `::`

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>Poznámky

Kvalifikátor aliasu oboru názvů může být `global`. Tím se vyvolá vyhledávání v globálním oboru názvů, nikoli obor názvů s aliasem.

## <a name="for-more-information"></a>Další informace

Příklad použití `::` operátoru naleznete v následující části:

- [Postupy: Použití aliasu globálního oboru názvů](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [. podnikatel](member-access-operators.md#member-access-operator-)
- [extern alias](../keywords/extern-alias.md)
