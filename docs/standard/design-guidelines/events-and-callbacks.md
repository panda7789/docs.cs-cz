---
title: "Události a zpětná volání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 217e9eae3540e0a20afd0888d24803285d6352b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="events-and-callbacks"></a><span data-ttu-id="7ae35-102">Události a zpětná volání</span><span class="sxs-lookup"><span data-stu-id="7ae35-102">Events and Callbacks</span></span>
<span data-ttu-id="7ae35-103">Zpětná volání jsou body rozšiřitelnosti, které umožňují rozhraní pro zpětné volání do kódu uživatele prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="7ae35-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="7ae35-104">Tyto Delegáti jsou obvykle předaný rozhraní prostřednictvím parametru metody.</span><span class="sxs-lookup"><span data-stu-id="7ae35-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="7ae35-105">Události jsou ve speciálním případě zpětná volání, který podporuje pohodlný a konzistentní syntaxe pro zadávání delegáta (obslužné rutiny události).</span><span class="sxs-lookup"><span data-stu-id="7ae35-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="7ae35-106">Kromě toho Visual Studio dokončování a návrháři poskytnutí nápovědy v pomocí rozhraní API založené na události.</span><span class="sxs-lookup"><span data-stu-id="7ae35-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="7ae35-107">(Viz [událostí návrhu](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="7ae35-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="7ae35-108">**✓ ZVAŽTE** pomocí zpětná volání umožníte uživatelům poskytnout vlastní kód, který bude proveden podle rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7ae35-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="7ae35-109">**✓ ZVAŽTE** pomocí události umožníte uživatelům přizpůsobit chování prostředí bez nutnosti Princip objektově orientované návrhu.</span><span class="sxs-lookup"><span data-stu-id="7ae35-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="7ae35-110">**PROVEĎTE ✓** raději události přes prostý zpětná volání, protože jsou známější pro širší vývojářů a jsou integrované s dokončování Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7ae35-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="7ae35-111">**X nepoužívejte** pomocí zpětná volání rozhraní API náročné na výkon.</span><span class="sxs-lookup"><span data-stu-id="7ae35-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="7ae35-112">**PROVEĎTE ✓** pomocí nové `Func<...>`, `Action<...>`, nebo `Expression<...>` typy místo vlastní delegáty, při definování rozhraní API s zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="7ae35-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="7ae35-113">`Func<...>`a `Action<...>` představují obecní delegáti.</span><span class="sxs-lookup"><span data-stu-id="7ae35-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="7ae35-114">`Expression<...>`Definice představuje funkcí, které můžete zkompilovat a následně vyvolat za běhu, ale mohou také být serializované a předaný vzdálených procesů.</span><span class="sxs-lookup"><span data-stu-id="7ae35-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="7ae35-115">**PROVEĎTE ✓** měřit a chápat výkonu důsledky použití `Expression<...>`, místo použití `Func<...>` a `Action<...>` delegáti.</span><span class="sxs-lookup"><span data-stu-id="7ae35-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="7ae35-116">`Expression<...>`typy jsou ve většině případů logicky ekvivalentní `Func<...>` a `Action<...>` delegáti.</span><span class="sxs-lookup"><span data-stu-id="7ae35-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="7ae35-117">Hlavní rozdíl mezi nimi je, že delegáty jsou určena pro použití ve scénářích místní proces. výrazy jsou určeny k případech, kdy je výhodné a možných při vyhodnocování výrazu v vzdáleného procesu nebo počítači.</span><span class="sxs-lookup"><span data-stu-id="7ae35-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="7ae35-118">**PROVEĎTE ✓** pochopit, jsou prováděny voláním delegáta libovolný kód a který může mít dopad na zabezpečení, správnost a kompatibility.</span><span class="sxs-lookup"><span data-stu-id="7ae35-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="7ae35-119">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="7ae35-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7ae35-120">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="7ae35-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae35-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ae35-121">See Also</span></span>  
 [<span data-ttu-id="7ae35-122">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="7ae35-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="7ae35-123">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="7ae35-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
