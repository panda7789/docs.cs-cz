---
title: ++ – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: a52f614ce1bbfb8e9d9be686b277c1e69f6f9d35
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45593098"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="449cf-102">++ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="449cf-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="449cf-103">Operátor Inkrementace (`++`) svého operandu zvýší o hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="449cf-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="449cf-104">Operátor Inkrementace může objevit před nebo po jeho operandu: `++variable` a `variable++`.</span><span class="sxs-lookup"><span data-stu-id="449cf-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="449cf-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="449cf-105">Remarks</span></span>  
 <span data-ttu-id="449cf-106">První forma je operace Inkrementace předponu.</span><span class="sxs-lookup"><span data-stu-id="449cf-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="449cf-107">Výsledkem operace je hodnota operandu po byla zvýšena.</span><span class="sxs-lookup"><span data-stu-id="449cf-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="449cf-108">Druhá forma se operace Inkrementace přípony.</span><span class="sxs-lookup"><span data-stu-id="449cf-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="449cf-109">Výsledkem operace je hodnota operandu předtím, než byla zvýšena.</span><span class="sxs-lookup"><span data-stu-id="449cf-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="449cf-110">Operátory zvýšení obsahuje předdefinované číselné a výčet typů.</span><span class="sxs-lookup"><span data-stu-id="449cf-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="449cf-111">Lze přetěžovat uživatelsky definované typy `++` operátor.</span><span class="sxs-lookup"><span data-stu-id="449cf-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="449cf-112">Operace interních typů jsou obecně povoleny na výčet.</span><span class="sxs-lookup"><span data-stu-id="449cf-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="449cf-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="449cf-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="449cf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="449cf-114">See Also</span></span>

- [<span data-ttu-id="449cf-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="449cf-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="449cf-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="449cf-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="449cf-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="449cf-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
