---
title: jako - C# odkaz
ms.custom: seodec18
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: b87e75bd4866a191e84465e44d53850e6e2e9723
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169920"
---
# <a name="as-c-reference"></a><span data-ttu-id="35c2b-102">as (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="35c2b-102">as (C# Reference)</span></span>
<span data-ttu-id="35c2b-103">Můžete použít `as` operátor pro provádění určitých typů převody mezi typy kompatibilní odkazů nebo [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="35c2b-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="35c2b-104">Následující kód ukazuje příklad.</span><span class="sxs-lookup"><span data-stu-id="35c2b-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

<span data-ttu-id="35c2b-105">Jak ukazuje příklad, potřebujete porovnat výsledek `as` výraz s `null` ke kontrole, pokud je úspěšný převod.</span><span class="sxs-lookup"><span data-stu-id="35c2b-105">As the example shows, you need to compare the result of the `as` expression with `null` to check if a conversion is successful.</span></span> <span data-ttu-id="35c2b-106">Od verze C# 7.0, můžete použít [je](is.md) výraz pro testování, převod bude úspěšné a podmíněně přidělit proměnné v případě, že převod je úspěšný.</span><span class="sxs-lookup"><span data-stu-id="35c2b-106">Beginning with C# 7.0, you can use the [is](is.md) expression both to test that a conversion succeeds and conditionally assign a variable when the conversion succeeds.</span></span> <span data-ttu-id="35c2b-107">V mnoha případech je stručnější než při použití `as` operátor.</span><span class="sxs-lookup"><span data-stu-id="35c2b-107">In many scenarios, it's more concise than using the `as` operator.</span></span> <span data-ttu-id="35c2b-108">Další informace najdete v tématu [vzor typu](is.md#type) část [ `is` operátor](is.md) článku.</span><span class="sxs-lookup"><span data-stu-id="35c2b-108">For more information, see the [Type pattern](is.md#type) section of the [`is` operator](is.md) article.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="35c2b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35c2b-109">Remarks</span></span>  
 <span data-ttu-id="35c2b-110">`as` Operátor je jako operace přetypování.</span><span class="sxs-lookup"><span data-stu-id="35c2b-110">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="35c2b-111">Nicméně, pokud převod není možný, `as` vrátí `null` namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="35c2b-111">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="35c2b-112">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="35c2b-112">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="35c2b-113">Je ekvivalentem následujícího výrazu s výjimkou, že kód `expression` proměnná je vyhodnocen pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="35c2b-113">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="35c2b-114">Všimněte si, `as` operátor provádí pouze převody odkazů, s možnou hodnotou Null převody a převody zabalení.</span><span class="sxs-lookup"><span data-stu-id="35c2b-114">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="35c2b-115">`as` Operátor nelze provádět jiné převody, jako je například uživatelem definované převody, které by místo toho provádět pomocí výrazy přetypování.</span><span class="sxs-lookup"><span data-stu-id="35c2b-115">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35c2b-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="35c2b-116">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="35c2b-117">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35c2b-117">C# Language Specification</span></span>  

<span data-ttu-id="35c2b-118">Další informace najdete v tématu [operátor as](~/_csharplang/spec/expressions.md#the-as-operator) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="35c2b-118">For more information, see [The as operator](~/_csharplang/spec/expressions.md#the-as-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="35c2b-119">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="35c2b-119">The language specification is the definitive source for C# syntax and usage.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="35c2b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35c2b-120">See also</span></span>

- [<span data-ttu-id="35c2b-121">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35c2b-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="35c2b-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="35c2b-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="35c2b-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35c2b-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="35c2b-124">is</span><span class="sxs-lookup"><span data-stu-id="35c2b-124">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="35c2b-125">?: Operátor</span><span class="sxs-lookup"><span data-stu-id="35c2b-125">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)
- [<span data-ttu-id="35c2b-126">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="35c2b-126">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
