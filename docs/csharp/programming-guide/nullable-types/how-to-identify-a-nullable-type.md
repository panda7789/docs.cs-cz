---
title: 'Postupy: Identifikace typu s možnou hodnotou Null – C# Průvodce programováním pro službu'
ms.custom: seodec18
description: Zjistěte, jak určit, zda typ je typ připouštějící hodnotu null nebo je instance typu s možnou hodnotou Null
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 33169315f8bef45aba52f0696d4acac031584817
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582627"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="52172-103">Postupy: Identifikace typu s možnou hodnotou Null (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="52172-103">How to: Identify a nullable type (C# Programming Guide)</span></span>

<span data-ttu-id="52172-104">Následující příklad ukazuje, jak určit, jestli <xref:System.Type?displayProperty=nameWithType> instance představuje uzavřený obecný typ s možnou hodnotou Null, to znamená, <xref:System.Nullable%601?displayProperty=nameWithType> typ pomocí zadaného typu parametru `T`:</span><span class="sxs-lookup"><span data-stu-id="52172-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="52172-105">Jak ukazuje příklad, je použít [typeof](../../language-reference/keywords/typeof.md) operátoru pro vytvoření <xref:System.Type?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="52172-105">As the example shows, you use the [typeof](../../language-reference/keywords/typeof.md) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
<span data-ttu-id="52172-106">Pokud chcete zjistit, jestli je instance typu s možnou hodnotou Null, nepoužívejte <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodu k získání <xref:System.Type> instance má být testována s předchozím kódu.</span><span class="sxs-lookup"><span data-stu-id="52172-106">If you want to determine whether an instance is of a nullable type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="52172-107">Při volání <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodu na instanci typu s možnou hodnotou Null, je instance [boxed](using-nullable-types.md#boxing-and-unboxing) k <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="52172-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="52172-108">Je ekvivalentní k zabalení hodnota základního typu boxing nenulovou instanci typu s možnou hodnotou Null <xref:System.Object.GetType%2A> vrátí <xref:System.Type> objekt, který představuje základní typ typu s možnou hodnotou NULL:</span><span class="sxs-lookup"><span data-stu-id="52172-108">As boxing of a non-null instance of a nullable type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="52172-109">Nepoužívejte [je](../../language-reference/keywords/is.md) operátor zjistit, zda instanci typu s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="52172-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable type.</span></span> <span data-ttu-id="52172-110">Jak ukazuje následující příklad, nelze rozlišit typy instancí typu s možnou hodnotou Null a jeho nadřízeného typu s použitím `is` operátor:</span><span class="sxs-lookup"><span data-stu-id="52172-110">As the following example shows, you cannot distinguish types of instances of a nullable type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="52172-111">Kód uvedený v následujícím příkladu můžete použít k určení, zda je instance typu s možnou hodnotou NULL:</span><span class="sxs-lookup"><span data-stu-id="52172-111">You can use the code presented in the following example to determine whether an instance is of a nullable type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a><span data-ttu-id="52172-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52172-112">See also</span></span>

- [<span data-ttu-id="52172-113">Typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="52172-113">Nullable types</span></span>](index.md)
- [<span data-ttu-id="52172-114">Použití typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="52172-114">Using nullable types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
