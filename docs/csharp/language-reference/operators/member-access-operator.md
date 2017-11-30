---
title: ". Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2bb636bc110f57ace9a824a43afdd86246ed0a5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bb7e1-103">.</span><span class="sxs-lookup"><span data-stu-id="bb7e1-103">.</span></span> <span data-ttu-id="bb7e1-104">Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bb7e1-104">Operator (C# Reference)</span></span>
<span data-ttu-id="bb7e1-105">Operátor tečky (`.`) se používá pro přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="bb7e1-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="bb7e1-106">Operátor tečky určuje člena typu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bb7e1-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="bb7e1-107">Například operátor tečky slouží k přístupu konkrétním metod v rámci knihovny tříd rozhraní .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="bb7e1-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="bb7e1-108">Zvažte například následující třídy:</span><span class="sxs-lookup"><span data-stu-id="bb7e1-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="bb7e1-109">Proměnná `s` má dva členy `a` a `b`; chcete přistupovat k nim, použijte operátor tečky:</span><span class="sxs-lookup"><span data-stu-id="bb7e1-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="bb7e1-110">Tečky slouží také k formuláři kvalifikované názvy, které jsou názvy, které určují obor názvů nebo rozhraní, například, do které patří.</span><span class="sxs-lookup"><span data-stu-id="bb7e1-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="bb7e1-111">Using – direktiva umožňuje některé kvalifikace názvu volitelné:</span><span class="sxs-lookup"><span data-stu-id="bb7e1-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="bb7e1-112">Ale když identifikátor je nejednoznačné, musí být kvalifikovaný:</span><span class="sxs-lookup"><span data-stu-id="bb7e1-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="bb7e1-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bb7e1-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb7e1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb7e1-114">See Also</span></span>  
 [<span data-ttu-id="bb7e1-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bb7e1-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bb7e1-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="bb7e1-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bb7e1-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bb7e1-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
