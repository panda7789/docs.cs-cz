---
title: "Async – přehled"
description: "Zjistěte, jak je asynchronní programování klíče techniku, která usnadňuje přehledné zpracování blokování vstupně-výstupních operací a souběžných operací na víc jader."
keywords: "Rozhraní .NET, .NET core"
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: bf0cc4ed21c92a57f3f5b2cfa27ac1f054e15172
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="async-overview"></a><span data-ttu-id="43076-104">Async – přehled</span><span class="sxs-lookup"><span data-stu-id="43076-104">Async Overview</span></span>

<span data-ttu-id="43076-105">Není to tak dávno aplikace získali rychlejší jednoduše si novější počítač nebo server a pak tento trend zastavena.</span><span class="sxs-lookup"><span data-stu-id="43076-105">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="43076-106">Ve skutečnosti obrácený.</span><span class="sxs-lookup"><span data-stu-id="43076-106">In fact, it reversed.</span></span> <span data-ttu-id="43076-107">Mobilní telefon zobrazovaly s jedním jádrem 1ghz ARM čipy a úlohy serveru přešla do virtuálních počítačů.</span><span class="sxs-lookup"><span data-stu-id="43076-107">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="43076-108">Uživatelé stále chcete citlivé uživatelské rozhraní a vlastníci společnosti budou chtít, aby servery, které škálovat s jejich podnikání.</span><span class="sxs-lookup"><span data-stu-id="43076-108">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="43076-109">Přechod mobilních a cloudu a připojené k Internetu naplnění > uživatelé 3B má za následek novou sadu vzory softwaru.</span><span class="sxs-lookup"><span data-stu-id="43076-109">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="43076-110">Klientské aplikace se měl stále aktivní, vždy připojené a neustále reaguje na interakce uživatele (například touch) s vysokou app store hodnocení!</span><span class="sxs-lookup"><span data-stu-id="43076-110">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="43076-111">Očekává se, že služby zpracování špičky v provozu řádně škálování nahoru a dolů.</span><span class="sxs-lookup"><span data-stu-id="43076-111">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="43076-112">Asynchronní programování je klíče technika, která usnadňuje přehledné zpracování blokování vstupně-výstupních operací a souběžných operací na víc jader.</span><span class="sxs-lookup"><span data-stu-id="43076-112">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="43076-113">Rozhraní .NET poskytuje možnost pro aplikace a služby reakce a elastické s snadné použití, úroveň jazyka asynchronní programovací modely v C#, VB a F #.</span><span class="sxs-lookup"><span data-stu-id="43076-113">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="43076-114">Proč psát kód asynchronní?</span><span class="sxs-lookup"><span data-stu-id="43076-114">Why Write Async Code?</span></span>

<span data-ttu-id="43076-115">Moderní aplikace využívají rozsáhlé vstupně-výstupní soubor a sítě.</span><span class="sxs-lookup"><span data-stu-id="43076-115">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="43076-116">Vstupně-výstupních operací rozhraní API tradičně bloku ve výchozím nastavení, výsledkem nízký uživatelského prostředí a využití hardwaru, pokud chcete další informace a využít náročné vzory.</span><span class="sxs-lookup"><span data-stu-id="43076-116">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="43076-117">Založený na úlohách async rozhraní API a úroveň jazyka asynchronní programovací model Invertovat tento model vytváření asynchronních provádění výchozí s několik nových konceptů Další.</span><span class="sxs-lookup"><span data-stu-id="43076-117">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="43076-118">Asynchronní kódu má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="43076-118">Async code has the following characteristics:</span></span>

* <span data-ttu-id="43076-119">Zpracovává požadavky na další server podle je vláken zpracovat další požadavky při čekání na vstupně-výstupní požadavky vrátit.</span><span class="sxs-lookup"><span data-stu-id="43076-119">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="43076-120">Umožňuje uživatelská být rychlejšího je vláken uživatelského rozhraní interakce při čekání na vstupně-výstupní požadavky a přechod pracovní dlouho běžící na jiné jader procesoru.</span><span class="sxs-lookup"><span data-stu-id="43076-120">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="43076-121">Mnoho novější rozhraní API .NET je asynchronní.</span><span class="sxs-lookup"><span data-stu-id="43076-121">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="43076-122">Je snadné napsat kód asynchronní v rozhraní .NET!</span><span class="sxs-lookup"><span data-stu-id="43076-122">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="43076-123">Co je další?</span><span class="sxs-lookup"><span data-stu-id="43076-123">What's next?</span></span>

<span data-ttu-id="43076-124">Podrobné informace o asynchronní koncepty a programování, najdete v části [asynchronní podrobněji](async-in-depth.md) a [založený na úlohách asynchronní programování](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span><span class="sxs-lookup"><span data-stu-id="43076-124">For a deep dive into async concepts and programming, see [Async in depth](async-in-depth.md) and [Task-based asynchronous programming](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span></span>
