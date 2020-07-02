---
title: Události a zpětná volání
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 4000944c3b913f71bc18462cea9062e9237ae53f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619530"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="3bd76-102">Události a zpětná volání</span><span class="sxs-lookup"><span data-stu-id="3bd76-102">Events and Callbacks</span></span>
<span data-ttu-id="3bd76-103">Zpětná volání jsou body rozšiřitelnosti, které umožňují rozhraní volat zpět do uživatelského kódu prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="3bd76-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="3bd76-104">Tyto delegáty jsou obvykle předávány rozhraní prostřednictvím parametru metody.</span><span class="sxs-lookup"><span data-stu-id="3bd76-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>

 <span data-ttu-id="3bd76-105">Události jsou zvláštním případem zpětných volání, která podporují praktické a konzistentní syntaxi pro poskytnutí delegáta (obslužná rutina události).</span><span class="sxs-lookup"><span data-stu-id="3bd76-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="3bd76-106">Kromě toho dokončování příkazů sady Visual Studio a návrháři poskytují podporu pro používání rozhraní API založených na událostech.</span><span class="sxs-lookup"><span data-stu-id="3bd76-106">In addition, Visual Studio's statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="3bd76-107">(Viz [návrh události](event.md).)</span><span class="sxs-lookup"><span data-stu-id="3bd76-107">(See [Event Design](event.md).)</span></span>

 <span data-ttu-id="3bd76-108">✔️ Zvažte použití zpětných volání k umožnění uživatelům poskytnout vlastní kód, který má být spuštěn rozhraním.</span><span class="sxs-lookup"><span data-stu-id="3bd76-108">✔️ CONSIDER using callbacks to allow users to provide custom code to be executed by the framework.</span></span>

 <span data-ttu-id="3bd76-109">✔️ Zvažte použití událostí, aby uživatelé mohli přizpůsobit chování architektury bez nutnosti porozumění objektově orientovanému návrhu.</span><span class="sxs-lookup"><span data-stu-id="3bd76-109">✔️ CONSIDER using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>

 <span data-ttu-id="3bd76-110">✔️ preferovat události proti prostým zpětným voláním, protože jsou více obeznámené s širší škálou vývojářů a jsou integrovány s dokončováním příkazů sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3bd76-110">✔️ DO prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>

 <span data-ttu-id="3bd76-111">❌Vyhněte se použití zpětných volání v rozhraních API citlivých na výkon.</span><span class="sxs-lookup"><span data-stu-id="3bd76-111">❌ AVOID using callbacks in performance-sensitive APIs.</span></span>

 <span data-ttu-id="3bd76-112">`Func<...>` `Action<...>` `Expression<...>` při definování rozhraní API pomocí zpětných volání ne✔️ použít nové typy, nebo namísto vlastních delegátů.</span><span class="sxs-lookup"><span data-stu-id="3bd76-112">✔️ DO use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>

 <span data-ttu-id="3bd76-113">`Func<...>`a `Action<...>` představuje Obecné delegáty.</span><span class="sxs-lookup"><span data-stu-id="3bd76-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="3bd76-114">`Expression<...>`představuje definice funkcí, které lze zkompilovat a následně vyvolávat za běhu, ale lze je také serializovat a předat vzdáleným procesům.</span><span class="sxs-lookup"><span data-stu-id="3bd76-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>

 <span data-ttu-id="3bd76-115">✔️ měření a pochopení dopadu na výkon použití `Expression<...>` , místo použití `Func<...>` a `Action<...>` delegátů.</span><span class="sxs-lookup"><span data-stu-id="3bd76-115">✔️ DO measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>

 <span data-ttu-id="3bd76-116">`Expression<...>`typy jsou ve většině případů logicky ekvivalentní `Func<...>` a `Action<...>` delegáty.</span><span class="sxs-lookup"><span data-stu-id="3bd76-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="3bd76-117">Hlavním rozdílem mezi nimi je to, že Delegáti mají být použiti v rámci scénářů místních procesů; výrazy jsou určené pro případy, kdy je výhodné a možné vyhodnotit výraz ve vzdáleném procesu nebo počítači.</span><span class="sxs-lookup"><span data-stu-id="3bd76-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it's beneficial and possible to evaluate the expression in a remote process or machine.</span></span>

 <span data-ttu-id="3bd76-118">✔️ pochopit, že voláním delegáta spouštíte libovolný kód, který by mohl mít zabezpečení, správnost a vliv na kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="3bd76-118">✔️ DO understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>

 <span data-ttu-id="3bd76-119">*Částečně &copy; 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="3bd76-119">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="3bd76-120">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="3bd76-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="3bd76-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3bd76-121">See also</span></span>

- [<span data-ttu-id="3bd76-122">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="3bd76-122">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="3bd76-123">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="3bd76-123">Framework Design Guidelines</span></span>](index.md)
