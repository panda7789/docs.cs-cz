---
title: Přehled asynchronizací
description: Zjistěte, jak je asynchronní programování klíčovou technikou, která usnadňuje zpracování blokování vstupně-va a souběžných operací na více jádrech.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: d649bc3a92d3bb834b3bc4f7d3c1bcb0f9417375
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159725"
---
# <a name="async-overview"></a><span data-ttu-id="d2bab-103">Přehled asynchronizací</span><span class="sxs-lookup"><span data-stu-id="d2bab-103">Async Overview</span></span>

<span data-ttu-id="d2bab-104">Není to tak dávno, aplikace dostal rychleji jednoduše tím, že koupí novější PC nebo server a pak se tento trend zastavil.</span><span class="sxs-lookup"><span data-stu-id="d2bab-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="d2bab-105">Ve skutečnosti se to obrátilo.</span><span class="sxs-lookup"><span data-stu-id="d2bab-105">In fact, it reversed.</span></span> <span data-ttu-id="d2bab-106">Mobilní telefony se objevily s jednojádrovými čipy ARM o 1ghz a serverovými úlohami převedenými na virtuální zařízení.</span><span class="sxs-lookup"><span data-stu-id="d2bab-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="d2bab-107">Uživatelé stále chtějí responzivní uživatelské rozhraní a vlastníci firem chtějí servery, které se škálují podle svého podnikání.</span><span class="sxs-lookup"><span data-stu-id="d2bab-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="d2bab-108">Přechod na mobilní a cloud a počet uživatelů >3B připojených k internetu vyústil v novou sadu softwarových vzorců.</span><span class="sxs-lookup"><span data-stu-id="d2bab-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span>

- <span data-ttu-id="d2bab-109">Očekává se, že klientské aplikace budou vždy zapnuté, vždy připojené a neustále reagují na interakci s uživatelem (například dotykové ovládání) s vysokým hodnocením obchodu s aplikacemi!</span><span class="sxs-lookup"><span data-stu-id="d2bab-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
- <span data-ttu-id="d2bab-110">Služby se očekává, že zpracování špičky v provozu řádně škálování nahoru a dolů.</span><span class="sxs-lookup"><span data-stu-id="d2bab-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span>

<span data-ttu-id="d2bab-111">Asynchronní programování je klíčová technika, která usnadňuje zpracování blokování vstupně-v a o a souběžných operací na více jádrech.</span><span class="sxs-lookup"><span data-stu-id="d2bab-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="d2bab-112">Rozhraní .NET poskytuje možnost, aby aplikace a služby reagovaly a byly elastické díky snadno použitelným asynchronním programovacím modelům na jazykové úrovni v jazyce C#, Visual Basic a F#.</span><span class="sxs-lookup"><span data-stu-id="d2bab-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, Visual Basic, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="d2bab-113">Proč psát asynchronní kód?</span><span class="sxs-lookup"><span data-stu-id="d2bab-113">Why Write Async Code?</span></span>

<span data-ttu-id="d2bab-114">Moderní aplikace využívají rozsáhlé vstupně-to-do souboru a síťové vstupně-up.</span><span class="sxs-lookup"><span data-stu-id="d2bab-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="d2bab-115">Vstupně-blouskározhraní tradičně blokují ve výchozím nastavení, což má za následek špatné uživatelské prostředí a využití hardwaru, pokud se nechcete učit a používat náročné vzory.</span><span class="sxs-lookup"><span data-stu-id="d2bab-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="d2bab-116">Asynchronní rozhraní API založená na úlohách a asynchronní programovací model na úrovni jazyka invertují tento model, takže asynchronní spuštění je výchozí s několika novými koncepty, které se mají naučit.</span><span class="sxs-lookup"><span data-stu-id="d2bab-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="d2bab-117">Asynchronní kód má následující charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="d2bab-117">Async code has the following characteristics:</span></span>

- <span data-ttu-id="d2bab-118">Zpracovává další požadavky serveru tím, že poskytuje podprocesy pro zpracování více požadavků při čekání na vstupně-va požadavky na vrácení.</span><span class="sxs-lookup"><span data-stu-id="d2bab-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
- <span data-ttu-id="d2bab-119">Umožňuje uživatelské rozhraní, které mají být citlivější tím, že dává podprocesů interakce uživatelského rozhraní při čekání na vstupně-va požadavky a přechodem dlouhotrvající práce na jiné jádra procesoru.</span><span class="sxs-lookup"><span data-stu-id="d2bab-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
- <span data-ttu-id="d2bab-120">Mnoho novějších rozhraní API ROZHRANÍ .NET je asynchronních.</span><span class="sxs-lookup"><span data-stu-id="d2bab-120">Many of the newer .NET APIs are asynchronous.</span></span>
- <span data-ttu-id="d2bab-121">Je snadné napsat asynchronní kód v rozhraní .NET!</span><span class="sxs-lookup"><span data-stu-id="d2bab-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="d2bab-122">Co dále?</span><span class="sxs-lookup"><span data-stu-id="d2bab-122">What's next?</span></span>

<span data-ttu-id="d2bab-123">Další informace naleznete v tématu [Async in depth.](async-in-depth.md)</span><span class="sxs-lookup"><span data-stu-id="d2bab-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="d2bab-124">Téma [Asynchronní programovací vzory](asynchronous-programming-patterns/index.md) poskytuje přehled tří asynchronních programovacích vzorů podporovaných v rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="d2bab-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="d2bab-125">[Asynchronní programovací model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starší verze)</span><span class="sxs-lookup"><span data-stu-id="d2bab-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="d2bab-126">[Asynchronní vzor založený na událostech (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starší verze)</span><span class="sxs-lookup"><span data-stu-id="d2bab-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="d2bab-127">[Asynchronní vzor založený na úlohách (TAP) (doporučeno](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) pro nový vývoj)</span><span class="sxs-lookup"><span data-stu-id="d2bab-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="d2bab-128">Další informace o doporučeném programovacím modelu založeném na úlohách naleznete v tématu [asynchronního programování na základě úloh.](parallel-programming/task-based-asynchronous-programming.md)</span><span class="sxs-lookup"><span data-stu-id="d2bab-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
