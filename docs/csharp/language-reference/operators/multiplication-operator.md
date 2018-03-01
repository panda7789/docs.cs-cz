---
title: "* Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 64c32def0935f4347f9aaccc2865b9cd33dd8a70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="14b07-102">\* – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="14b07-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="14b07-103">Operátor násobení (`*`), která vypočítá produktu jejími operandy.</span><span class="sxs-lookup"><span data-stu-id="14b07-103">The multiplication operator (`*`), which computes the product of its operands.</span></span>  <span data-ttu-id="14b07-104">Navíc dereference operátor, který umožňuje čtení a zápis do ukazatel.</span><span class="sxs-lookup"><span data-stu-id="14b07-104">Also, the dereference operator, which allows reading and writing to a pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14b07-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14b07-105">Remarks</span></span>  
 <span data-ttu-id="14b07-106">Všechny číselné typy obsahuje předdefinované operátory násobení.</span><span class="sxs-lookup"><span data-stu-id="14b07-106">All numeric types have predefined multiplication operators.</span></span>  
  
 <span data-ttu-id="14b07-107">`*` Operátor slouží také k deklaraci typy ukazatelů a dereference ukazatele.</span><span class="sxs-lookup"><span data-stu-id="14b07-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="14b07-108">Tento operátor lze použít pouze v kontextu unsafe, odlišené použití [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo a vyžadující [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="14b07-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="14b07-109">Operátor dereference se taky říká deferenční operátor.</span><span class="sxs-lookup"><span data-stu-id="14b07-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="14b07-110">Uživatelem definované typy může přetížit binárního souboru `*` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="14b07-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="14b07-111">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="14b07-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14b07-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="14b07-112">Example</span></span>  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="14b07-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="14b07-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="14b07-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="14b07-114">See Also</span></span>  
 [<span data-ttu-id="14b07-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="14b07-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="14b07-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="14b07-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="14b07-117">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="14b07-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="14b07-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="14b07-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
