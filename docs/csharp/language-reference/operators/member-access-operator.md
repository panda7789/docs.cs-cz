---
title: . – Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 088f1991cafa92a69e11ca14bd2d983b36c0e3ca
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244696"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1468e-103">.</span><span class="sxs-lookup"><span data-stu-id="1468e-103">.</span></span> <span data-ttu-id="1468e-104">– Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1468e-104">Operator (C# Reference)</span></span>
<span data-ttu-id="1468e-105">Tečka – operátor (`.`) se používá pro přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="1468e-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="1468e-106">Operátor tečky Určuje typ nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="1468e-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="1468e-107">Například operátor tečky slouží k přístupu k určité metody v rámci knihovny tříd rozhraní .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1468e-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="1468e-108">Představte si třeba následující třídy:</span><span class="sxs-lookup"><span data-stu-id="1468e-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="1468e-109">Proměnná `s` se dvěma členy `a` a `b`; pokud ho chcete přistupovat k nim, použijte operátor tečky:</span><span class="sxs-lookup"><span data-stu-id="1468e-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="1468e-110">Tečka slouží také k vytvoření kvalifikované názvy, které jsou názvy, které určují obor názvů nebo rozhraní, například, ke kterému patří.</span><span class="sxs-lookup"><span data-stu-id="1468e-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="1468e-111">Using – direktiva provádí některé kvalifikace názvu volitelné:</span><span class="sxs-lookup"><span data-stu-id="1468e-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="1468e-112">Ale pokud identifikátor je dvojznačný, musí být kvalifikován:</span><span class="sxs-lookup"><span data-stu-id="1468e-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1468e-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1468e-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1468e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1468e-114">See Also</span></span>  
 [<span data-ttu-id="1468e-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1468e-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1468e-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1468e-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1468e-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1468e-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
