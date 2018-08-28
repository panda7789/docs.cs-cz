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
ms.openlocfilehash: aee80b3262ccd9432d7c311dddec47185b66d05f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43003070"
---
# <a name="as-c-reference"></a><span data-ttu-id="07c37-102">as (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="07c37-102">as (C# Reference)</span></span>
<span data-ttu-id="07c37-103">Můžete použít `as` operátor pro provádění určitých typů převody mezi typy kompatibilní odkazů nebo [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="07c37-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="07c37-104">Následující kód ukazuje příklad.</span><span class="sxs-lookup"><span data-stu-id="07c37-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]
  
## <a name="remarks"></a><span data-ttu-id="07c37-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07c37-105">Remarks</span></span>  
 <span data-ttu-id="07c37-106">`as` Operátor je jako operace přetypování.</span><span class="sxs-lookup"><span data-stu-id="07c37-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="07c37-107">Nicméně, pokud převod není možný, `as` vrátí `null` namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="07c37-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="07c37-108">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="07c37-108">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="07c37-109">Je ekvivalentem následujícího výrazu s výjimkou, že kód `expression` proměnná je vyhodnocen pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="07c37-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="07c37-110">Všimněte si, `as` operátor provádí pouze převody odkazů, s možnou hodnotou Null převody a převody zabalení.</span><span class="sxs-lookup"><span data-stu-id="07c37-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="07c37-111">`as` Operátor nelze provádět jiné převody, jako je například uživatelem definované převody, které by místo toho provádět pomocí výrazy přetypování.</span><span class="sxs-lookup"><span data-stu-id="07c37-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07c37-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="07c37-112">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="07c37-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07c37-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="07c37-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="07c37-114">See Also</span></span>  
- [<span data-ttu-id="07c37-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07c37-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="07c37-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="07c37-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="07c37-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07c37-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="07c37-118">is</span><span class="sxs-lookup"><span data-stu-id="07c37-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="07c37-119">?: – operátor</span><span class="sxs-lookup"><span data-stu-id="07c37-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
- [<span data-ttu-id="07c37-120">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="07c37-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
