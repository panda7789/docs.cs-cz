---
title: "[] – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03664f5604bb7d7dce9e8ae2ff0ec045c6a203b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d192d-102">[] – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d192d-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="d192d-103">Hranaté závorky (`[]`) se používají pro pole, indexery a atributy.</span><span class="sxs-lookup"><span data-stu-id="d192d-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="d192d-104">Můžete také používají s ukazatele.</span><span class="sxs-lookup"><span data-stu-id="d192d-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d192d-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d192d-105">Remarks</span></span>  
 <span data-ttu-id="d192d-106">Typ pole je typu, za nímž následuje `[]`:</span><span class="sxs-lookup"><span data-stu-id="d192d-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="d192d-107">Pro přístup k elementu pole, je index požadovaný element uzavřený v závorkách:</span><span class="sxs-lookup"><span data-stu-id="d192d-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="d192d-108">Pokud pole indexu je mimo rozsah, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d192d-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="d192d-109">Pole indexu operátor nemohou být přetíženy; typy však můžete definovat, indexery a vlastnosti, které trvat jeden nebo více parametrů.</span><span class="sxs-lookup"><span data-stu-id="d192d-109">The array indexing operator cannot be overloaded; however, types can define indexers, and properties that take one or more parameters.</span></span> <span data-ttu-id="d192d-110">Indexer parametry jsou uzavřeny do hranatých závorek, stejně jako indexy pole, ale indexer parametry lze deklarovat být jakéhokoli typu, na rozdíl od indexy pole, které musí být celočíselné.</span><span class="sxs-lookup"><span data-stu-id="d192d-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="d192d-111">Například definuje rozhraní .NET Framework `Hashtable` typ, který přidruží klíče a hodnoty libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="d192d-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="d192d-112">Hranaté závorky se také používají k určení [atributy](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="d192d-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="d192d-113">Hranaté závorky můžete použít k indexu vypnout ukazatel:</span><span class="sxs-lookup"><span data-stu-id="d192d-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="d192d-114">Žádné hranice, kontrola probíhá.</span><span class="sxs-lookup"><span data-stu-id="d192d-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d192d-115">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d192d-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d192d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d192d-116">See Also</span></span>  
 [<span data-ttu-id="d192d-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d192d-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d192d-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d192d-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d192d-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d192d-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="d192d-120">Pole</span><span class="sxs-lookup"><span data-stu-id="d192d-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="d192d-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="d192d-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="d192d-122">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="d192d-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="d192d-123">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="d192d-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
