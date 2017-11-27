---
title: "as (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4f2964f32a4139ffeb6d51b761f1176a57c5be6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="as-c-reference"></a><span data-ttu-id="f2fcf-102">as (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f2fcf-102">as (C# Reference)</span></span>
<span data-ttu-id="f2fcf-103">Můžete použít `as` operátor provést určité typy převody mezi kompatibilní odkazové typy nebo [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2fcf-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="f2fcf-104">Následující kód ukazuje příklad.</span><span class="sxs-lookup"><span data-stu-id="f2fcf-104">The following code shows an example.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="f2fcf-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2fcf-105">Remarks</span></span>  
 <span data-ttu-id="f2fcf-106">`as` Operátor je jako operaci přetypování.</span><span class="sxs-lookup"><span data-stu-id="f2fcf-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="f2fcf-107">Nicméně, pokud není možné, převod `as` vrátí `null` místo vyvolání k výjimce.</span><span class="sxs-lookup"><span data-stu-id="f2fcf-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="f2fcf-108">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="f2fcf-108">Consider the following example:</span></span>  
  
```  
expression as type  
```  
  
 <span data-ttu-id="f2fcf-109">Kód je ekvivalentní výrazu následující vyjma toho, že `expression` proměnná vyhodnotí pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="f2fcf-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="f2fcf-110">Všimněte si, že `as` operátor provádí pouze převody odkazů, s možnou hodnotou Null převody a zabalení převody.</span><span class="sxs-lookup"><span data-stu-id="f2fcf-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="f2fcf-111">`as` Operátor nelze provádět jiné převody, jako je například uživatelem definované převody, které by měli místo toho provádět pomocí výrazů přetypování.</span><span class="sxs-lookup"><span data-stu-id="f2fcf-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2fcf-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2fcf-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f2fcf-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2fcf-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f2fcf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2fcf-114">See Also</span></span>  
 [<span data-ttu-id="f2fcf-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2fcf-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f2fcf-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f2fcf-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f2fcf-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2fcf-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f2fcf-118">je</span><span class="sxs-lookup"><span data-stu-id="f2fcf-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="f2fcf-119">?: – Operátor</span><span class="sxs-lookup"><span data-stu-id="f2fcf-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="f2fcf-120">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="f2fcf-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
