---
title: Asynchronní přehled
description: Přečtěte si, jak je asynchronní programování klíčovou technikou, která usnadňuje zpracování blokujících vstupně-výstupních operací a souběžných operací s více jádry.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: d649bc3a92d3bb834b3bc4f7d3c1bcb0f9417375
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159725"
---
# <a name="async-overview"></a><span data-ttu-id="c3f91-103">Asynchronní přehled</span><span class="sxs-lookup"><span data-stu-id="c3f91-103">Async Overview</span></span>

<span data-ttu-id="c3f91-104">Ještě nejste tak dlouho, ale aplikace jsou rychlejší, protože si koupíte novější počítač nebo server a tento trend se zastavil.</span><span class="sxs-lookup"><span data-stu-id="c3f91-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="c3f91-105">Ve skutečnosti se vrátila zpět.</span><span class="sxs-lookup"><span data-stu-id="c3f91-105">In fact, it reversed.</span></span> <span data-ttu-id="c3f91-106">Mobilní telefony se zobrazily s 1GHz s jedním jádrem ARM a úlohami serveru, které jsou převedené na virtuální počítače.</span><span class="sxs-lookup"><span data-stu-id="c3f91-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="c3f91-107">Uživatelé pořád chtějí reagovat na uživatelské rozhraní a obchodní vlastníci, kteří chtějí servery, které se škálují podle jejich podnikání.</span><span class="sxs-lookup"><span data-stu-id="c3f91-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="c3f91-108">Přechod do mobilního a cloudu a naplnění Internetu připojeného k Internetu z >ch verzí 3B uživatelů má za následek novou sadu vzorů softwaru.</span><span class="sxs-lookup"><span data-stu-id="c3f91-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span>

- <span data-ttu-id="c3f91-109">Očekává se, že klientské aplikace budou vždycky zapnuté, vždy se připojí a nepřetržitě reagují na interakci s uživatelem (například dotykové ovládání) s vysokým hodnocením v obchodě s aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="c3f91-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
- <span data-ttu-id="c3f91-110">U služeb se očekává, že budou zpracovávat špičky v provozu díky řádnému škálování směrem nahoru a dolů.</span><span class="sxs-lookup"><span data-stu-id="c3f91-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span>

<span data-ttu-id="c3f91-111">Asynchronní programování je klíčovou technikou, která usnadňuje zpracování blokujících vstupně-výstupních operací a souběžných operací s více jádry.</span><span class="sxs-lookup"><span data-stu-id="c3f91-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="c3f91-112">Rozhraní .NET poskytuje možnosti pro aplikace a služby, které je možné reagovat a elastický pomocí snadno použitelných a prostředí asynchronních programovacích modelů C#na úrovni jazyka v F#, Visual Basic a.</span><span class="sxs-lookup"><span data-stu-id="c3f91-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, Visual Basic, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="c3f91-113">Proč psát asynchronní kód?</span><span class="sxs-lookup"><span data-stu-id="c3f91-113">Why Write Async Code?</span></span>

<span data-ttu-id="c3f91-114">Moderní aplikace využívají v/v rozsáhlé soubory a síťové operace.</span><span class="sxs-lookup"><span data-stu-id="c3f91-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="c3f91-115">I/O rozhraní API tradičně standardně blokují, což má za následek špatné uživatelské prostředí a využití hardwaru, pokud se nechcete naučit a používat náročné vzory.</span><span class="sxs-lookup"><span data-stu-id="c3f91-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="c3f91-116">Asynchronní rozhraní API založené na úlohách a jejich modul asynchronního programování na úrovni jazyka invertují tento model, což provádí asynchronní spouštění ve výchozím nastavení s několika novými koncepty pro učení.</span><span class="sxs-lookup"><span data-stu-id="c3f91-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="c3f91-117">Asynchronní kód má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c3f91-117">Async code has the following characteristics:</span></span>

- <span data-ttu-id="c3f91-118">Zpracovává více požadavků serveru tím, že vrací vlákna pro zpracování více požadavků při čekání na vrácení vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="c3f91-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
- <span data-ttu-id="c3f91-119">Umožňuje, aby uživatelská rozhraní lépe reagovaly tím, že při čekání na požadavky na vstupně-výstupní operace vychází z vlákna na interakci uživatelského rozhraní a přechodem dlouhotrvající práce na jiné jádra procesoru.</span><span class="sxs-lookup"><span data-stu-id="c3f91-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
- <span data-ttu-id="c3f91-120">Mnohé z novějších rozhraní API .NET jsou asynchronní.</span><span class="sxs-lookup"><span data-stu-id="c3f91-120">Many of the newer .NET APIs are asynchronous.</span></span>
- <span data-ttu-id="c3f91-121">Psaní asynchronního kódu v rozhraní .NET je snadné.</span><span class="sxs-lookup"><span data-stu-id="c3f91-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="c3f91-122">Co dále?</span><span class="sxs-lookup"><span data-stu-id="c3f91-122">What's next?</span></span>

<span data-ttu-id="c3f91-123">Další informace naleznete [v tématu Async v rámci hloubky](async-in-depth.md) .</span><span class="sxs-lookup"><span data-stu-id="c3f91-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="c3f91-124">Téma o [asynchronních programovacích vzorcích](asynchronous-programming-patterns/index.md) poskytuje přehled tří asynchronních programovacích vzorů podporovaných v rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="c3f91-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="c3f91-125">[Asynchronní programovací model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starší verze)</span><span class="sxs-lookup"><span data-stu-id="c3f91-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="c3f91-126">[Asynchronní vzor založený na událostech (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starší verze)</span><span class="sxs-lookup"><span data-stu-id="c3f91-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="c3f91-127">[Asynchronní vzor založený na úlohách (klepněte na)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (doporučeno pro nový vývoj)</span><span class="sxs-lookup"><span data-stu-id="c3f91-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="c3f91-128">Další informace o doporučeném programovacím modelu založeném na úlohách naleznete v tématu věnovaném [asynchronnímu programování založenému](parallel-programming/task-based-asynchronous-programming.md) na úlohách.</span><span class="sxs-lookup"><span data-stu-id="c3f91-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
