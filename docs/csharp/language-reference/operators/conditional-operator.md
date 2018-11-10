---
title: '?: – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 3e45ff6eaaefa5829c3ed9415abe1a12b7a1d069
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980619"
---
# <a name="-operator-c-reference"></a>?: – operátor (Referenční dokumentace jazyka C#)

Podmíněný operátor (`?:`), obvykle označovaný jako Ternární podmiňovací operátor vrátí jednu ze dvou hodnot v závislosti na hodnotě logického výrazu. Následuje syntaxe pro podmiňovací operátor.  

```csharp
condition ? first_expression : second_expression;  
```

Počínaje C# 7.2, `first_expression` a `second_expression` Moje být [ `ref` výrazy](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):

```csharp
ref condition ? ref first_expression : ref second_expression;  
```

Výsledkem může být přiřazen `ref` nebo `ref readonly` proměnných, nebo proměnné ani modifikátorem.

## <a name="remarks"></a>Poznámky

`condition` Se musí vyhodnotit na `true` nebo `false`. Pokud `condition` je `true`, `first_expression` jsou vyhodnoceny a výsledek. Pokud `condition` je `false`, `second_expression` jsou vyhodnoceny a výsledek. Je vyhodnocen pouze jeden ze dvou výrazů. To je zvlášť důležité pro výrazy, ve kterém je výsledek `ref`, protože platí následující:

```csharp
ref (storage != null) ? ref storage[3] : ref defaultValue;
```

Odkaz na `storage` není vyhodnocen, když `storage` má hodnotu null.

Když výsledkem je hodnota, typ `first_expression` a `second_expression` musí být musí být stejné nebo existovat implicitní převod z jednoho typu na druhý. Pokud je výsledek `ref`, typ `first_expression` a `second_expression` se musí shodovat.

Můžete vyjádřit výpočty, které by jinak vyžadovaly `if-else` konstrukce více stručně a výstižně pomocí podmíněného operátoru. Například následující kód používá nejprve `if` příkaz a poté podmiňovací operátor pro klasifikaci celého čísla jako kladné nebo záporné.

```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```

Podmiňovací operátor je asociativní zprava. Výraz `a ? b : c ? d : e` se vyhodnotí jako `a ? b : (c ? d : e)`, nikoli jako `(a ? b : c) ? d : e`.  
  
Podmiňovací operátor nelze přetížit.
  
## <a name="example"></a>Příklad

Následující příklad ukazuje, jehož výsledkem je hodnota podmíněný operátor:

[!code-csharp[csRefOperators?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

Následující alternativní ukazuje podmíněného operátoru, kde výsledkem je odkaz:

[!code-csharp[csRefOperatorsRef?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
- [if-else](../../../csharp/language-reference/keywords/if-else.md)  
- [Operátory ?. a ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)  
- [?? – operátor](../../../csharp/language-reference/operators/null-coalescing-operator.md)
