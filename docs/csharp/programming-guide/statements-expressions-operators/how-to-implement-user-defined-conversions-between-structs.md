---
title: "Postupy: Implementace uživatelem definovaných převodů mezi strukturami (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d86cbd48347e6951f6b6883a385d80d68697c9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="aeb56-102">Postupy: Implementace uživatelem definovaných převodů mezi strukturami (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="aeb56-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="aeb56-103">Tento příklad definuje dvě struktury `RomanNumeral` a `BinaryNumeral`a předvádí převody mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="aeb56-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeb56-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="aeb56-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="aeb56-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="aeb56-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="aeb56-106">V předchozím příkladu, příkaz:</span><span class="sxs-lookup"><span data-stu-id="aeb56-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     <span data-ttu-id="aeb56-107">provede převod z `RomanNumeral` k `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="aeb56-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="aeb56-108">Protože není k dispozici žádný přímý převod z `RomanNumeral` k `BinaryNumeral`, přetypování slouží k převodu z `RomanNumeral` k `int`a jiné přetypování převést z `int` k `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="aeb56-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="aeb56-109">Také příkaz</span><span class="sxs-lookup"><span data-stu-id="aeb56-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     <span data-ttu-id="aeb56-110">provede převod z `BinaryNumeral` k `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="aeb56-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="aeb56-111">Protože `RomanNumeral` definuje implicitní převod z `BinaryNumeral`, není třeba žádné přetypování.</span><span class="sxs-lookup"><span data-stu-id="aeb56-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb56-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="aeb56-112">See Also</span></span>  
 [<span data-ttu-id="aeb56-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aeb56-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="aeb56-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="aeb56-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aeb56-115">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="aeb56-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
