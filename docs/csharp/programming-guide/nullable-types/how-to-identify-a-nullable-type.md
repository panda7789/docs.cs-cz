---
title: 'Postupy: Identifikace typu hodnoty s možnou hodnotou C# null – Průvodce programováním'
ms.custom: seodec18
description: Naučte se, jak určit, jestli typ je typ hodnoty s možnou hodnotou null nebo instance je typu s možnou hodnotou null.
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 15b1ffedf57648955ee5a004514841a5d140292b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392604"
---
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a><span data-ttu-id="ee850-103">Postupy: určení typu hodnoty s možnou hodnotouC# null (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ee850-103">How to: identify a nullable value type (C# Programming Guide)</span></span>

<span data-ttu-id="ee850-104">Následující příklad ukazuje, jak určit, zda instance <xref:System.Type?displayProperty=nameWithType> představuje uzavřený obecný typ hodnoty s možnou hodnotou null, tj. typ <xref:System.Nullable%601?displayProperty=nameWithType> s určeným parametrem typu `T`:</span><span class="sxs-lookup"><span data-stu-id="ee850-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="ee850-105">Jak ukazuje příklad, použijte operátor [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) k vytvoření objektu <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ee850-105">As the example shows, you use the [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="ee850-106">Chcete-li určit, zda je instance typu hodnoty s možnou hodnotou null, nepoužívejte metodu <xref:System.Object.GetType%2A?displayProperty=nameWithType> pro získání instance <xref:System.Type> pro otestování pomocí předchozího kódu.</span><span class="sxs-lookup"><span data-stu-id="ee850-106">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="ee850-107">Když zavoláte metodu <xref:System.Object.GetType%2A?displayProperty=nameWithType> u instance typu hodnoty s možnou hodnotou null, je instance [zabalená](using-nullable-types.md#boxing-and-unboxing) na <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="ee850-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="ee850-108">Jako zabalení instance typu s možnou hodnotou null, která není null, je ekvivalentem zabalení hodnoty nadřízeného typu, <xref:System.Object.GetType%2A> vrátí objekt <xref:System.Type>, který představuje nadřízený typ hodnoty s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="ee850-108">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="ee850-109">Nepoužívejte operátor [is](../../language-reference/keywords/is.md) k určení, zda je instance typu hodnot s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ee850-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="ee850-110">Jak ukazuje následující příklad, nelze odlišit typy instancí typu hodnoty s možnou hodnotou null a jeho nadřízený typ pomocí operátoru `is`:</span><span class="sxs-lookup"><span data-stu-id="ee850-110">As the following example shows, you cannot distinguish types of instances of a nullable value type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="ee850-111">K určení, zda je instance typu s možnou hodnotou null, lze použít kód prezentovaný v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ee850-111">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a><span data-ttu-id="ee850-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee850-112">See also</span></span>

- [<span data-ttu-id="ee850-113">Typy hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="ee850-113">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="ee850-114">Použití typů hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="ee850-114">Using nullable value types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
