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
# <a name="-operator-c-reference"></a><span data-ttu-id="058c3-102">?: – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="058c3-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="058c3-103">Podmíněný operátor (`?:`), obvykle označovaný jako Ternární podmiňovací operátor vrátí jednu ze dvou hodnot v závislosti na hodnotě logického výrazu.</span><span class="sxs-lookup"><span data-stu-id="058c3-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="058c3-104">Následuje syntaxe pro podmiňovací operátor.</span><span class="sxs-lookup"><span data-stu-id="058c3-104">Following is the syntax for the conditional operator.</span></span>  

```csharp
condition ? first_expression : second_expression;  
```

<span data-ttu-id="058c3-105">Počínaje C# 7.2, `first_expression` a `second_expression` Moje být [ `ref` výrazy](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):</span><span class="sxs-lookup"><span data-stu-id="058c3-105">Beginning with C# 7.2, the `first_expression` and `second_expression` my be [`ref` expressions](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):</span></span>

```csharp
ref condition ? ref first_expression : ref second_expression;  
```

<span data-ttu-id="058c3-106">Výsledkem může být přiřazen `ref` nebo `ref readonly` proměnných, nebo proměnné ani modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="058c3-106">The result may be assigned to a `ref` or `ref readonly` variable, or to a variable with neither modifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="058c3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="058c3-107">Remarks</span></span>

<span data-ttu-id="058c3-108">`condition` Se musí vyhodnotit na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="058c3-108">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="058c3-109">Pokud `condition` je `true`, `first_expression` jsou vyhodnoceny a výsledek.</span><span class="sxs-lookup"><span data-stu-id="058c3-109">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="058c3-110">Pokud `condition` je `false`, `second_expression` jsou vyhodnoceny a výsledek.</span><span class="sxs-lookup"><span data-stu-id="058c3-110">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="058c3-111">Je vyhodnocen pouze jeden ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="058c3-111">Only one of the two expressions is evaluated.</span></span> <span data-ttu-id="058c3-112">To je zvlášť důležité pro výrazy, ve kterém je výsledek `ref`, protože platí následující:</span><span class="sxs-lookup"><span data-stu-id="058c3-112">This is particularly important for expressions where the result is a `ref`, as the following is valid:</span></span>

```csharp
ref (storage != null) ? ref storage[3] : ref defaultValue;
```

<span data-ttu-id="058c3-113">Odkaz na `storage` není vyhodnocen, když `storage` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="058c3-113">The reference to `storage` is not evaluated when `storage` is null.</span></span>

<span data-ttu-id="058c3-114">Když výsledkem je hodnota, typ `first_expression` a `second_expression` musí být musí být stejné nebo existovat implicitní převod z jednoho typu na druhý.</span><span class="sxs-lookup"><span data-stu-id="058c3-114">When the result is a value, the type of `first_expression` and `second_expression` must be the same, or there must be an implicit conversion from one type to the other.</span></span> <span data-ttu-id="058c3-115">Pokud je výsledek `ref`, typ `first_expression` a `second_expression` se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="058c3-115">When the result is a `ref`, the type of `first_expression` and `second_expression` must be the same.</span></span>

<span data-ttu-id="058c3-116">Můžete vyjádřit výpočty, které by jinak vyžadovaly `if-else` konstrukce více stručně a výstižně pomocí podmíněného operátoru.</span><span class="sxs-lookup"><span data-stu-id="058c3-116">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="058c3-117">Například následující kód používá nejprve `if` příkaz a poté podmiňovací operátor pro klasifikaci celého čísla jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="058c3-117">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>

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

<span data-ttu-id="058c3-118">Podmiňovací operátor je asociativní zprava.</span><span class="sxs-lookup"><span data-stu-id="058c3-118">The conditional operator is right-associative.</span></span> <span data-ttu-id="058c3-119">Výraz `a ? b : c ? d : e` se vyhodnotí jako `a ? b : (c ? d : e)`, nikoli jako `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="058c3-119">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
<span data-ttu-id="058c3-120">Podmiňovací operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="058c3-120">The conditional operator cannot be overloaded.</span></span>
  
## <a name="example"></a><span data-ttu-id="058c3-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="058c3-121">Example</span></span>

<span data-ttu-id="058c3-122">Následující příklad ukazuje, jehož výsledkem je hodnota podmíněný operátor:</span><span class="sxs-lookup"><span data-stu-id="058c3-122">The following example shows the conditional operator whose result is a value:</span></span>

[!code-csharp[csRefOperators?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

<span data-ttu-id="058c3-123">Následující alternativní ukazuje podmíněného operátoru, kde výsledkem je odkaz:</span><span class="sxs-lookup"><span data-stu-id="058c3-123">The following alternative shows the conditional operator where the result is a reference:</span></span>

[!code-csharp[csRefOperatorsRef?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

## <a name="see-also"></a><span data-ttu-id="058c3-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="058c3-124">See Also</span></span>

- [<span data-ttu-id="058c3-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="058c3-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="058c3-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="058c3-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="058c3-127">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="058c3-127">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="058c3-128">if-else</span><span class="sxs-lookup"><span data-stu-id="058c3-128">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
- <span data-ttu-id="058c3-129">[Operátory ?. a ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="058c3-129">[?. and ?[] Operators](../../../csharp/language-reference/operators/null-conditional-operators.md)</span></span>  
- [<span data-ttu-id="058c3-130">?? – operátor</span><span class="sxs-lookup"><span data-stu-id="058c3-130">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
