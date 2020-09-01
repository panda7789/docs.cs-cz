---
description: částečný způsob – reference jazyka C#
title: částečný způsob – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: d6c433fd30f6ec51355bdefee90d815783487c1b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134377"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="67981-103">Partial – metoda (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="67981-103">partial method (C# Reference)</span></span>

<span data-ttu-id="67981-104">Částečná metoda má svou signaturu definovanou v jedné části částečného typu a implementaci definovanou v jiné části typu.</span><span class="sxs-lookup"><span data-stu-id="67981-104">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="67981-105">Částečné metody umožňují návrhářům tříd poskytovat háky metod, podobně jako obslužné rutiny událostí, u kterých se mohou vývojáři rozhodnout, zda je chtějí implementovat nebo ne.</span><span class="sxs-lookup"><span data-stu-id="67981-105">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="67981-106">Pokud vývojář neposkytne implementaci, kompilátor v době kompilace odebere signaturu.</span><span class="sxs-lookup"><span data-stu-id="67981-106">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="67981-107">Na částečné metody se uplatňují tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="67981-107">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="67981-108">Podpisy v obou částech částečného typu se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="67981-108">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="67981-109">Metoda musí vracet typ void.</span><span class="sxs-lookup"><span data-stu-id="67981-109">The method must return void.</span></span>

- <span data-ttu-id="67981-110">Nejsou povoleny žádné modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="67981-110">No access modifiers are allowed.</span></span> <span data-ttu-id="67981-111">Částečné metody jsou implicitně soukromé.</span><span class="sxs-lookup"><span data-stu-id="67981-111">Partial methods are implicitly private.</span></span>

<span data-ttu-id="67981-112">Následující příklad ukazuje částečnou metodu definovanou ve dvou částech částečné třídy:</span><span class="sxs-lookup"><span data-stu-id="67981-112">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="67981-113">Další informace naleznete v tématu [částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="67981-113">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67981-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="67981-114">See also</span></span>

- [<span data-ttu-id="67981-115">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67981-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="67981-116">částečný typ</span><span class="sxs-lookup"><span data-stu-id="67981-116">partial type</span></span>](partial-type.md)
