---
title: "Souhrn typů trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c1570832e5f179b6d2685ad33fad743c9530bb16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="trace-type-summary"></a><span data-ttu-id="4dd4e-102">Souhrn typů trasování</span><span class="sxs-lookup"><span data-stu-id="4dd4e-102">Trace Type Summary</span></span>
<span data-ttu-id="4dd4e-103">[Zdroj úrovně](http://go.microsoft.com/fwlink/?LinkID=94943) definuje různé úrovně trasování: kritická, chyba, upozornění, informace a podrobné, stejně jako obsahuje popis `ActivityTracing` příznak, které přepíná výstup trasování událostí pro přenos hranice a aktivity.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-103">[Source Levels](http://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="4dd4e-104">Můžete také zkontrolovat [typ TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) pro typy trasování, které můžou být vygenerované z <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-104">You can also review [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="4dd4e-105">Následující tabulka uvádí nejdůležitější ty.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="4dd4e-106">Typ trasování</span><span class="sxs-lookup"><span data-stu-id="4dd4e-106">Trace Type</span></span>|<span data-ttu-id="4dd4e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4dd4e-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="4dd4e-108">Kritická</span><span class="sxs-lookup"><span data-stu-id="4dd4e-108">Critical</span></span>|<span data-ttu-id="4dd4e-109">Závažná chyba nebo aplikaci k chybě.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="4dd4e-110">Chyba</span><span class="sxs-lookup"><span data-stu-id="4dd4e-110">Error</span></span>|<span data-ttu-id="4dd4e-111">Nezotavitelnou chybu.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-111">Recoverable error.</span></span>|  
|<span data-ttu-id="4dd4e-112">Upozornění</span><span class="sxs-lookup"><span data-stu-id="4dd4e-112">Warning</span></span>|<span data-ttu-id="4dd4e-113">Informační zpráva.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-113">Informational message.</span></span>|  
|<span data-ttu-id="4dd4e-114">Informace o</span><span class="sxs-lookup"><span data-stu-id="4dd4e-114">Information</span></span>|<span data-ttu-id="4dd4e-115">Nekritická problém.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="4dd4e-116">Verbose</span><span class="sxs-lookup"><span data-stu-id="4dd4e-116">Verbose</span></span>|<span data-ttu-id="4dd4e-117">Ladění trasování.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-117">Debugging trace.</span></span>|  
|<span data-ttu-id="4dd4e-118">Spustit</span><span class="sxs-lookup"><span data-stu-id="4dd4e-118">Start</span></span>|<span data-ttu-id="4dd4e-119">Spouštění logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="4dd4e-120">Pozastavit</span><span class="sxs-lookup"><span data-stu-id="4dd4e-120">Suspend</span></span>|<span data-ttu-id="4dd4e-121">Pozastavení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="4dd4e-122">Resume</span><span class="sxs-lookup"><span data-stu-id="4dd4e-122">Resume</span></span>|<span data-ttu-id="4dd4e-123">Obnovení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="4dd4e-124">Zastavit</span><span class="sxs-lookup"><span data-stu-id="4dd4e-124">Stop</span></span>|<span data-ttu-id="4dd4e-125">Zastavování logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="4dd4e-126">Přenos</span><span class="sxs-lookup"><span data-stu-id="4dd4e-126">Transfer</span></span>|<span data-ttu-id="4dd4e-127">Změna identity korelace.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="4dd4e-128">Aktivita je definován jako kombinace výše uvedených typů trasování.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="4dd4e-129">Toto je regulární výraz, který definuje ideální aktivitu v oboru místní (Zdroj trasování)</span><span class="sxs-lookup"><span data-stu-id="4dd4e-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="4dd4e-130">To znamená, že aktivita musí splňovat následující podmínky.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="4dd4e-131">Musí začínat a zastavte v uvedeném pořadí spouštění a zastavování trasování</span><span class="sxs-lookup"><span data-stu-id="4dd4e-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="4dd4e-132">Musí mít přenos trasování bezprostředně předcházející pozastavit nebo obnovit trasování</span><span class="sxs-lookup"><span data-stu-id="4dd4e-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="4dd4e-133">Nesmí obsahovat žádné trasování mezi pozastavení a obnovení trasování, pokud existují takové trasování</span><span class="sxs-lookup"><span data-stu-id="4dd4e-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="4dd4e-134">Také je možné vysledovat předchozích podmínek může mít všechny a libovolný počet trasování kritické/chyby nebo upozornění nebo informace nebo Verbose/přenos</span><span class="sxs-lookup"><span data-stu-id="4dd4e-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="4dd4e-135">Toto je regulární výraz, který definuje ideální aktivitu v globálním oboru</span><span class="sxs-lookup"><span data-stu-id="4dd4e-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="4dd4e-136">s R se regulární výraz pro aktivitu v místní rozsah.</span><span class="sxs-lookup"><span data-stu-id="4dd4e-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="4dd4e-137">To znamená, že</span><span class="sxs-lookup"><span data-stu-id="4dd4e-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
