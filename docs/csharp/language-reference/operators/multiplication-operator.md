---
title: '* Operátor (referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 6c5d4de587b67e5ade158c163a87e8dea6bece5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275838"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e849b-102">\* – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e849b-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="e849b-103">Operátor násobení (`*`) vypočítá produktu jejími operandy.</span><span class="sxs-lookup"><span data-stu-id="e849b-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="e849b-104">Všechny číselné typy obsahuje předdefinované operátory násobení.</span><span class="sxs-lookup"><span data-stu-id="e849b-104">All numeric types have predefined multiplication operators.</span></span>  

<span data-ttu-id="e849b-105">`*` slouží také jako dereference operátor, který umožňuje čtení a zápis do ukazatel.</span><span class="sxs-lookup"><span data-stu-id="e849b-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="e849b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e849b-106">Remarks</span></span>  
 <span data-ttu-id="e849b-107">`*` Operátor slouží také k deklaraci typy ukazatelů a dereference ukazatele.</span><span class="sxs-lookup"><span data-stu-id="e849b-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="e849b-108">Tento operátor lze použít pouze v kontextu unsafe, odlišené použití [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo a vyžadující [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="e849b-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="e849b-109">Operátor dereference se taky říká deferenční operátor.</span><span class="sxs-lookup"><span data-stu-id="e849b-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="e849b-110">Uživatelem definované typy může přetížit binárního souboru `*` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e849b-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="e849b-111">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="e849b-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e849b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e849b-112">Example</span></span>  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="e849b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e849b-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e849b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e849b-114">See Also</span></span>  
 [<span data-ttu-id="e849b-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e849b-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e849b-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e849b-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e849b-117">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="e849b-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="e849b-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e849b-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
