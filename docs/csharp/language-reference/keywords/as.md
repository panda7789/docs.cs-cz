---
title: as (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 092c30a858df7baeb35bdf28bae53802fb0916d4
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172016"
---
# <a name="as-c-reference"></a><span data-ttu-id="313dd-102">as (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="313dd-102">as (C# Reference)</span></span>
<span data-ttu-id="313dd-103">Můžete použít `as` operátor provést určité typy převody mezi kompatibilní odkazové typy nebo [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="313dd-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="313dd-104">Následující kód ukazuje příklad.</span><span class="sxs-lookup"><span data-stu-id="313dd-104">The following code shows an example.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="313dd-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="313dd-105">Remarks</span></span>  
 <span data-ttu-id="313dd-106">`as` Operátor je jako operaci přetypování.</span><span class="sxs-lookup"><span data-stu-id="313dd-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="313dd-107">Nicméně, pokud není možné, převod `as` vrátí `null` místo vyvolání k výjimce.</span><span class="sxs-lookup"><span data-stu-id="313dd-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="313dd-108">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="313dd-108">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="313dd-109">Kód je ekvivalentní výrazu následující vyjma toho, že `expression` proměnná vyhodnotí pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="313dd-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="313dd-110">Všimněte si, že `as` operátor provádí pouze převody odkazů, s možnou hodnotou Null převody a zabalení převody.</span><span class="sxs-lookup"><span data-stu-id="313dd-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="313dd-111">`as` Operátor nelze provádět jiné převody, jako je například uživatelem definované převody, které by měli místo toho provádět pomocí výrazů přetypování.</span><span class="sxs-lookup"><span data-stu-id="313dd-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="313dd-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="313dd-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="313dd-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="313dd-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="313dd-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="313dd-114">See Also</span></span>  
 [<span data-ttu-id="313dd-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="313dd-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="313dd-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="313dd-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="313dd-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="313dd-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="313dd-118">is</span><span class="sxs-lookup"><span data-stu-id="313dd-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="313dd-119">?: – operátor</span><span class="sxs-lookup"><span data-stu-id="313dd-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="313dd-120">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="313dd-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
