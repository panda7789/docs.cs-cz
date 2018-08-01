---
title: Události a zpětná volání
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90cc40024de627f151a4d0df879a65e5900004b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573630"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="550ab-102">Události a zpětná volání</span><span class="sxs-lookup"><span data-stu-id="550ab-102">Events and Callbacks</span></span>
<span data-ttu-id="550ab-103">Zpětná volání jsou body rozšiřitelnosti, které umožňují rozhraní pro zpětné volání do kódu uživatele prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="550ab-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="550ab-104">Tyto Delegáti jsou obvykle předaný rozhraní prostřednictvím parametru metody.</span><span class="sxs-lookup"><span data-stu-id="550ab-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="550ab-105">Události jsou ve speciálním případě zpětná volání, který podporuje pohodlný a konzistentní syntaxe pro zadávání delegáta (obslužné rutiny události).</span><span class="sxs-lookup"><span data-stu-id="550ab-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="550ab-106">Kromě toho Visual Studio dokončování a návrháři poskytnutí nápovědy v pomocí rozhraní API založené na události.</span><span class="sxs-lookup"><span data-stu-id="550ab-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="550ab-107">(Viz [událostí návrhu](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="550ab-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="550ab-108">**✓ CONSIDER** pomocí zpětná volání umožníte uživatelům poskytnout vlastní kód, který bude proveden podle rozhraní.</span><span class="sxs-lookup"><span data-stu-id="550ab-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="550ab-109">**✓ CONSIDER** pomocí události umožníte uživatelům přizpůsobit chování prostředí bez nutnosti Princip objektově orientované návrhu.</span><span class="sxs-lookup"><span data-stu-id="550ab-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="550ab-110">**✓ DO** raději události přes prostý zpětná volání, protože jsou známější pro širší vývojářů a jsou integrované s dokončování Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="550ab-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="550ab-111">**X AVOID** pomocí zpětná volání rozhraní API náročné na výkon.</span><span class="sxs-lookup"><span data-stu-id="550ab-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="550ab-112">**✓ DO** pomocí nové `Func<...>`, `Action<...>`, nebo `Expression<...>` typy místo vlastní delegáty, při definování rozhraní API s zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="550ab-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="550ab-113">`Func<...>` a `Action<...>` představují obecní delegáti.</span><span class="sxs-lookup"><span data-stu-id="550ab-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="550ab-114">`Expression<...>` Definice představuje funkcí, které můžete zkompilovat a následně vyvolat za běhu, ale mohou také být serializované a předaný vzdálených procesů.</span><span class="sxs-lookup"><span data-stu-id="550ab-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="550ab-115">**✓ DO** měřit a chápat výkonu důsledky použití `Expression<...>`, místo použití `Func<...>` a `Action<...>` delegáti.</span><span class="sxs-lookup"><span data-stu-id="550ab-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="550ab-116">`Expression<...>` typy jsou ve většině případů logicky ekvivalentní `Func<...>` a `Action<...>` delegáti.</span><span class="sxs-lookup"><span data-stu-id="550ab-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="550ab-117">Hlavní rozdíl mezi nimi je, že delegáty jsou určena pro použití ve scénářích místní proces. výrazy jsou určeny k případech, kdy je výhodné a možných při vyhodnocování výrazu v vzdáleného procesu nebo počítači.</span><span class="sxs-lookup"><span data-stu-id="550ab-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="550ab-118">**✓ DO** pochopit, jsou prováděny voláním delegáta libovolný kód a který může mít dopad na zabezpečení, správnost a kompatibility.</span><span class="sxs-lookup"><span data-stu-id="550ab-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="550ab-119">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="550ab-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="550ab-120">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="550ab-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="550ab-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="550ab-121">See Also</span></span>  
 [<span data-ttu-id="550ab-122">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="550ab-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="550ab-123">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="550ab-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
