---
title: ':: – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 0b456ed3ce9965ef389d8ce40167afa4ac33da18
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422521"
---
# <a name="-operator-c-reference"></a>:: – operátor (C# odkaz)

Kvalifikátor aliasu oboru názvů (`::`) slouží k vyhledání identifikátory. Vždy je umístěný mezi dva identifikátory, jako v následujícím příkladu:

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

`::` Operátor můžete použít také s *alias direktiva using*:

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>Poznámky

Kvalifikátor aliasu oboru názvů může být `global`. Tím se spustí vyhledávání v globálním oboru názvů, ne obor názvů služby alias.

## <a name="for-more-information"></a>Další informace

Příklad použití `::` operátoru, najdete v následující části:

- [Postupy: Použití aliasu globálního Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [. – operátor](member-access-operators.md#member-access-operator-)
- [extern alias](../keywords/extern-alias.md)
