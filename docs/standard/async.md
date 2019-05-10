---
title: Přehled asynchronních
description: Zjistěte, jak je asynchronní programování představuje klíčovou techniku, která umožňuje jednoduché blokování vstupně-výstupní operace a souběžné operace s více jádry.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: aa08389d896fa81dbed8a63bb22a97e151016392
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628797"
---
# <a name="async-overview"></a><span data-ttu-id="363c5-103">Přehled asynchronních</span><span class="sxs-lookup"><span data-stu-id="363c5-103">Async Overview</span></span>

<span data-ttu-id="363c5-104">Není to tak dávno aplikace rychleji jednoduše si koupíte novější počítač nebo server a potom tento trend se zastavilo.</span><span class="sxs-lookup"><span data-stu-id="363c5-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="363c5-105">Ve skutečnosti obrácený.</span><span class="sxs-lookup"><span data-stu-id="363c5-105">In fact, it reversed.</span></span> <span data-ttu-id="363c5-106">Mobilní telefony zobrazovaly s jedním jádrem frekvenci 1ghz ARM čipy a jiné úlohy serveru přešla do virtuálních počítačů.</span><span class="sxs-lookup"><span data-stu-id="363c5-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="363c5-107">Uživatelé stále chtějí responzivní uživatelské rozhraní a vlastníkům obchodních chtít, aby servery, které se škálují podle jejich společnosti.</span><span class="sxs-lookup"><span data-stu-id="363c5-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="363c5-108">Přechod na mobilní a cloudové a naplnění připojeného k Internetu z > uživatelé 3B má za následek novou sadu vzorů softwaru.</span><span class="sxs-lookup"><span data-stu-id="363c5-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="363c5-109">Klientské aplikace se očekává, že byly vždy na, vždy připojen a neustále responzivní na interakci uživatele (například touch) s hodnocením vysokou app storu!</span><span class="sxs-lookup"><span data-stu-id="363c5-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="363c5-110">Očekává se, že služby zpracovávat řádně vertikální navýšení a snížení špičkami v provozu.</span><span class="sxs-lookup"><span data-stu-id="363c5-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="363c5-111">Představuje klíčovou techniku, která umožňuje jednoduché blokování vstupně-výstupní operace a souběžné operace s více jádry je asynchronní programování.</span><span class="sxs-lookup"><span data-stu-id="363c5-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="363c5-112">.NET poskytuje možnosti pro aplikace a služby jako responzivního a elastické se snadným ovládáním, úroveň jazyka asynchronní programovací modely v C#, VB, a F#.</span><span class="sxs-lookup"><span data-stu-id="363c5-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="363c5-113">Proč psát asynchronní kód?</span><span class="sxs-lookup"><span data-stu-id="363c5-113">Why Write Async Code?</span></span>

<span data-ttu-id="363c5-114">Moderní aplikace využívat rozsáhlé vstupně-výstupní operace souboru a sítě.</span><span class="sxs-lookup"><span data-stu-id="363c5-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="363c5-115">Vstupně-výstupní operace rozhraní API tradičně bloku ve výchozím nastavení, výsledkem je špatné uživatelských prostředí a využití hardwaru Pokud nechcete učí a používají složité vzorce.</span><span class="sxs-lookup"><span data-stu-id="363c5-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="363c5-116">Úkolově orientovanou asynchronní rozhraní API a úrovni jazyka asynchronní programovací model Invertovat tento model, provádění asynchronní provádění výchozím nastavení se několik nových konceptů a další.</span><span class="sxs-lookup"><span data-stu-id="363c5-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="363c5-117">Asynchronní kód má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="363c5-117">Async code has the following characteristics:</span></span>

* <span data-ttu-id="363c5-118">Další požadavky na server zpracovává pomocí čekajících vláken zpracovávat další požadavky při čekání na vstupně-výstupních požadavků k vrácení.</span><span class="sxs-lookup"><span data-stu-id="363c5-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="363c5-119">Umožňuje UI se více přizpůsobovat čekajících vláken interakce s uživatelským rozhraním při čekání na vstupně-výstupních požadavků a přechod dlouhotrvající práci do jiné jader procesoru.</span><span class="sxs-lookup"><span data-stu-id="363c5-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="363c5-120">Řadu novějších rozhraní API .NET jsou asynchronní.</span><span class="sxs-lookup"><span data-stu-id="363c5-120">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="363c5-121">Je snadné napsat asynchronní kód v .NET!</span><span class="sxs-lookup"><span data-stu-id="363c5-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="363c5-122">Co dále?</span><span class="sxs-lookup"><span data-stu-id="363c5-122">What's next?</span></span>

<span data-ttu-id="363c5-123">Další informace najdete v tématu [asynchronní do hloubky](async-in-depth.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="363c5-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="363c5-124">[Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) téma poskytuje přehled o tři asynchronních programovacích vzorech podporovány v rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="363c5-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="363c5-125">[Asynchronní Programovací Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starší verze)</span><span class="sxs-lookup"><span data-stu-id="363c5-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="363c5-126">[Událost asynchronní vzor založený (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starší verze)</span><span class="sxs-lookup"><span data-stu-id="363c5-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="363c5-127">[Založený na úlohách asynchronního vzoru (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (doporučeno pro vývoj nových projektů)</span><span class="sxs-lookup"><span data-stu-id="363c5-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="363c5-128">Další informace o doporučených programovací model založený na úlohách najdete v článku [asynchronní programování založené na úlohách](parallel-programming/task-based-asynchronous-programming.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="363c5-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
