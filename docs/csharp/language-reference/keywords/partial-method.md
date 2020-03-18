---
title: částečná metoda - Odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 62efd8b47fb565316b417a65e1b0fe37e40786c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713219"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="ec0f9-102">částečná metoda (Odkaz na C#</span><span class="sxs-lookup"><span data-stu-id="ec0f9-102">partial method (C# Reference)</span></span>

<span data-ttu-id="ec0f9-103">Částečná metoda má svou signaturu definovanou v jedné části částečného typu a implementaci definovanou v jiné části typu.</span><span class="sxs-lookup"><span data-stu-id="ec0f9-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="ec0f9-104">Částečné metody umožňují návrhářům tříd poskytovat háky metod, podobně jako obslužné rutiny událostí, u kterých se mohou vývojáři rozhodnout, zda je chtějí implementovat nebo ne.</span><span class="sxs-lookup"><span data-stu-id="ec0f9-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="ec0f9-105">Pokud vývojář neposkytne implementaci, kompilátor v době kompilace odebere signaturu.</span><span class="sxs-lookup"><span data-stu-id="ec0f9-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="ec0f9-106">Na částečné metody se uplatňují tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="ec0f9-106">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="ec0f9-107">Podpisy v obou částech částečného typu se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="ec0f9-107">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="ec0f9-108">Metoda musí vracet typ void.</span><span class="sxs-lookup"><span data-stu-id="ec0f9-108">The method must return void.</span></span>

- <span data-ttu-id="ec0f9-109">Nejsou povoleny žádné modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="ec0f9-109">No access modifiers are allowed.</span></span> <span data-ttu-id="ec0f9-110">Částečné metody jsou implicitně soukromé.</span><span class="sxs-lookup"><span data-stu-id="ec0f9-110">Partial methods are implicitly private.</span></span>

<span data-ttu-id="ec0f9-111">Následující příklad ukazuje částečnou metodu definovanou ve dvou částech částečné třídy:</span><span class="sxs-lookup"><span data-stu-id="ec0f9-111">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="ec0f9-112">Další informace naleznete [v tématu Částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ec0f9-112">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec0f9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec0f9-113">See also</span></span>

- [<span data-ttu-id="ec0f9-114">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ec0f9-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ec0f9-115">částečný typ</span><span class="sxs-lookup"><span data-stu-id="ec0f9-115">partial type</span></span>](partial-type.md)
