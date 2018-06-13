---
title: Async – přehled
description: Zjistěte, jak je asynchronní programování klíče techniku, která usnadňuje přehledné zpracování blokování vstupně-výstupních operací a souběžných operací na víc jader.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: b9d612186e1051644e8d4ae9476b8fafd811deb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567338"
---
# <a name="async-overview"></a><span data-ttu-id="c2156-103">Async – přehled</span><span class="sxs-lookup"><span data-stu-id="c2156-103">Async Overview</span></span>

<span data-ttu-id="c2156-104">Není to tak dávno aplikace získali rychlejší jednoduše si novější počítač nebo server a pak tento trend zastavena.</span><span class="sxs-lookup"><span data-stu-id="c2156-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="c2156-105">Ve skutečnosti obrácený.</span><span class="sxs-lookup"><span data-stu-id="c2156-105">In fact, it reversed.</span></span> <span data-ttu-id="c2156-106">Mobilní telefon zobrazovaly s jedním jádrem 1ghz ARM čipy a úlohy serveru přešla do virtuálních počítačů.</span><span class="sxs-lookup"><span data-stu-id="c2156-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="c2156-107">Uživatelé stále chcete citlivé uživatelské rozhraní a vlastníci společnosti budou chtít, aby servery, které škálovat s jejich podnikání.</span><span class="sxs-lookup"><span data-stu-id="c2156-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="c2156-108">Přechod mobilních a cloudu a připojené k Internetu naplnění > uživatelé 3B má za následek novou sadu vzory softwaru.</span><span class="sxs-lookup"><span data-stu-id="c2156-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="c2156-109">Klientské aplikace se měl stále aktivní, vždy připojené a neustále reaguje na interakce uživatele (například touch) s vysokou app store hodnocení!</span><span class="sxs-lookup"><span data-stu-id="c2156-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="c2156-110">Očekává se, že služby zpracování špičky v provozu řádně škálování nahoru a dolů.</span><span class="sxs-lookup"><span data-stu-id="c2156-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="c2156-111">Asynchronní programování je klíče technika, která usnadňuje přehledné zpracování blokování vstupně-výstupních operací a souběžných operací na víc jader.</span><span class="sxs-lookup"><span data-stu-id="c2156-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="c2156-112">Rozhraní .NET poskytuje možnost pro aplikace a služby reakce a elastické s snadné použití, úroveň jazyka asynchronní programovací modely v C#, VB a F #.</span><span class="sxs-lookup"><span data-stu-id="c2156-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="c2156-113">Proč psát kód asynchronní?</span><span class="sxs-lookup"><span data-stu-id="c2156-113">Why Write Async Code?</span></span>

<span data-ttu-id="c2156-114">Moderní aplikace využívají rozsáhlé vstupně-výstupní soubor a sítě.</span><span class="sxs-lookup"><span data-stu-id="c2156-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="c2156-115">Vstupně-výstupních operací rozhraní API tradičně bloku ve výchozím nastavení, výsledkem nízký uživatelského prostředí a využití hardwaru, pokud chcete další informace a využít náročné vzory.</span><span class="sxs-lookup"><span data-stu-id="c2156-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="c2156-116">Založený na úlohách async rozhraní API a úroveň jazyka asynchronní programovací model Invertovat tento model vytváření asynchronních provádění výchozí s několik nových konceptů Další.</span><span class="sxs-lookup"><span data-stu-id="c2156-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="c2156-117">Asynchronní kódu má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c2156-117">Async code has the following characteristics:</span></span>

* <span data-ttu-id="c2156-118">Zpracovává požadavky na další server podle je vláken zpracovat další požadavky při čekání na vstupně-výstupní požadavky vrátit.</span><span class="sxs-lookup"><span data-stu-id="c2156-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="c2156-119">Umožňuje uživatelská být rychlejšího je vláken uživatelského rozhraní interakce při čekání na vstupně-výstupní požadavky a přechod pracovní dlouho běžící na jiné jader procesoru.</span><span class="sxs-lookup"><span data-stu-id="c2156-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="c2156-120">Mnoho novější rozhraní API .NET je asynchronní.</span><span class="sxs-lookup"><span data-stu-id="c2156-120">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="c2156-121">Je snadné napsat kód asynchronní v rozhraní .NET!</span><span class="sxs-lookup"><span data-stu-id="c2156-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="c2156-122">Co je další?</span><span class="sxs-lookup"><span data-stu-id="c2156-122">What's next?</span></span>

<span data-ttu-id="c2156-123">Další informace najdete v tématu [asynchronní podrobněji](async-in-depth.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="c2156-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="c2156-124">[Vzory asynchronního programování](/asynchronous-programming-patterns/index.md) téma obsahuje přehled ze tří asynchronní programování vzorů v rozhraní .NET podporovány:</span><span class="sxs-lookup"><span data-stu-id="c2156-124">The [Asynchronous Programming Patterns](/asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
-   <span data-ttu-id="c2156-125">[Asynchronní programování modelu (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starší)</span><span class="sxs-lookup"><span data-stu-id="c2156-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
-   <span data-ttu-id="c2156-126">[Na základě událostí asynchronní vzor (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starší)</span><span class="sxs-lookup"><span data-stu-id="c2156-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
-   <span data-ttu-id="c2156-127">[Založený na úlohách asynchronní vzor (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (doporučeno pro nový vývoj)</span><span class="sxs-lookup"><span data-stu-id="c2156-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="c2156-128">Další informace o doporučených založený na úlohách programovací model najdete v tématu [založený na úlohách asynchronní programování](parallel-programming/task-based-asynchronous-programming.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="c2156-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
