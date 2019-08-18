---
title: 'Postupy: Identifikace typu s možnou C# hodnotou null – Průvodce programováním'
ms.custom: seodec18
description: Naučte se určit, jestli typ je typ s možnou hodnotou null nebo instance je typu s možnou hodnotou null.
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 43a35874b8c9f52c4b98a93e1217994980e1b223
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567376"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="343ef-103">Postupy: Identifikace typu s možnouC# hodnotou null (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="343ef-103">How to: Identify a nullable type (C# Programming Guide)</span></span>

<span data-ttu-id="343ef-104">Následující příklad ukazuje, jak určit, zda <xref:System.Type?displayProperty=nameWithType> instance představuje uzavřený obecný typ s možnou hodnotou null, to znamená <xref:System.Nullable%601?displayProperty=nameWithType> typ s parametrem `T`zadaného typu:</span><span class="sxs-lookup"><span data-stu-id="343ef-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="343ef-105">Jak ukazuje příklad, použijte operátor [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) k vytvoření <xref:System.Type?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="343ef-105">As the example shows, you use the [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
<span data-ttu-id="343ef-106">Pokud chcete zjistit, zda je instance typu s možnou hodnotou null, nepoužívejte <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodu k <xref:System.Type> získání instance, která má být testována pomocí předchozího kódu.</span><span class="sxs-lookup"><span data-stu-id="343ef-106">If you want to determine whether an instance is of a nullable type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="343ef-107">Při volání <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody na instanci typu s možnou hodnotou null je instance zabalena do [](using-nullable-types.md#boxing-and-unboxing) <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="343ef-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="343ef-108">Jako zabalení instance typu s možnou hodnotou null, která není null, je ekvivalentem zabalení hodnoty nadřazeného typu, <xref:System.Object.GetType%2A> <xref:System.Type> vrátí objekt, který představuje nadřízený typ typu s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="343ef-108">As boxing of a non-null instance of a nullable type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="343ef-109">Nepoužívejte operátor [is](../../language-reference/keywords/is.md) k určení, zda je instance typu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="343ef-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable type.</span></span> <span data-ttu-id="343ef-110">Jak ukazuje následující příklad, nelze odlišit typy instancí typu s možnou hodnotou null a jeho nadřízený typ pomocí `is` operátoru:</span><span class="sxs-lookup"><span data-stu-id="343ef-110">As the following example shows, you cannot distinguish types of instances of a nullable type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="343ef-111">K určení, jestli je instance typu s možnou hodnotou null, můžete použít kód prezentovaný v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="343ef-111">You can use the code presented in the following example to determine whether an instance is of a nullable type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a><span data-ttu-id="343ef-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="343ef-112">See also</span></span>

- [<span data-ttu-id="343ef-113">Typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="343ef-113">Nullable types</span></span>](index.md)
- [<span data-ttu-id="343ef-114">Použití typů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="343ef-114">Using nullable types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
