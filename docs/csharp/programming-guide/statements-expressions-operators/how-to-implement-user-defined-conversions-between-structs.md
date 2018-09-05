---
title: 'Postupy: Implementace uživatelem definovaných převodů mezi strukturami (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: cff85d60c1b59f4d1ca028f8fc02fee5728fa3d6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746701"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="72311-102">Postupy: Implementace uživatelem definovaných převodů mezi strukturami (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="72311-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="72311-103">Tento příklad definuje dvě struktury `RomanNumeral` a `BinaryNumeral`a ukazuje převody mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="72311-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72311-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="72311-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="72311-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="72311-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="72311-106">V předchozím příkladu, příkaz:</span><span class="sxs-lookup"><span data-stu-id="72311-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     <span data-ttu-id="72311-107">provede konverzi `RomanNumeral` k `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="72311-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="72311-108">Protože neexistuje žádný přímý převod z `RomanNumeral` k `BinaryNumeral`, přetypování se používá k převodu z `RomanNumeral` do `int`a jiné přetypování pro převod z `int` k `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="72311-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="72311-109">Také – příkaz</span><span class="sxs-lookup"><span data-stu-id="72311-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     <span data-ttu-id="72311-110">provede konverzi `BinaryNumeral` k `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="72311-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="72311-111">Protože `RomanNumeral` definuje implicitní převod z `BinaryNumeral`, žádné přetypování je povinný.</span><span class="sxs-lookup"><span data-stu-id="72311-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72311-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="72311-112">See Also</span></span>

- [<span data-ttu-id="72311-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="72311-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="72311-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="72311-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="72311-115">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="72311-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
