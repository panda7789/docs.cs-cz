---
title: partial (metoda) (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 29b5d442a1aa33babc24aee987e749c93a5ec727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269038"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="11257-102">partial (metoda) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="11257-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="11257-103">Částečná metoda má svou signaturu definovanou v jedné části částečného typu a implementaci definovanou v jiné části typu.</span><span class="sxs-lookup"><span data-stu-id="11257-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="11257-104">Částečné metody umožňují návrhářům tříd poskytovat háky metod, podobně jako obslužné rutiny událostí, u kterých se mohou vývojáři rozhodnout, zda je chtějí implementovat nebo ne.</span><span class="sxs-lookup"><span data-stu-id="11257-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="11257-105">Pokud vývojář neposkytne implementaci, kompilátor v době kompilace odebere signaturu.</span><span class="sxs-lookup"><span data-stu-id="11257-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="11257-106">Na částečné metody se uplatňují tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="11257-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="11257-107">Podpisy v obou částech částečného typu se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="11257-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="11257-108">Metoda musí vracet typ void.</span><span class="sxs-lookup"><span data-stu-id="11257-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="11257-109">Nejsou povoleny žádné modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="11257-109">No access modifiers are allowed.</span></span> <span data-ttu-id="11257-110">Částečné metody jsou implicitně soukromé.</span><span class="sxs-lookup"><span data-stu-id="11257-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="11257-111">Následující příklad ukazuje částečnou metodu definovanou ve dvou částech částečné třídy:</span><span class="sxs-lookup"><span data-stu-id="11257-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 <span data-ttu-id="11257-112">Další informace najdete v tématu [částečné třídy a metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="11257-112">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11257-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="11257-113">See Also</span></span>  
 [<span data-ttu-id="11257-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="11257-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="11257-115">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="11257-115">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
