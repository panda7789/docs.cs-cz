---
title: ':: Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2e456be075f3487676228244e0119ff46ed9a538
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243475"
---
# <a name="-operator-c-reference"></a>:: – Operátor (referenční dokumentace jazyka C#)
Kvalifikátor aliasu oboru názvů (`::`) slouží k vyhledání identifikátory. Vždy je umístěný mezi dva identifikátory, jako v následujícím příkladu:  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

`::` Operátor můžete použít také s *alias direktiva using*:

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>Poznámky  
 Kvalifikátor aliasu oboru názvů může být `global`. Tím se spustí vyhledávání v globálním oboru názvů, ne obor názvů služby alias.  
  
## <a name="for-more-information"></a>Další informace  
 Příklad použití `::` operátoru, najdete v následující části:  
  
-   [Postupy: Použití aliasu globálního Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
- [Klíčová slova oboru názvů](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [. – operátor](../../../csharp/language-reference/operators/member-access-operator.md)  
- [extern alias](../../../csharp/language-reference/keywords/extern-alias.md)
