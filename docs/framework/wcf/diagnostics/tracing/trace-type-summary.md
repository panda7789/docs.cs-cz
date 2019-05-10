---
title: Souhrn typů trasování
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 44446b58510e58758934a5eb964efc8643854879
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647178"
---
# <a name="trace-type-summary"></a><span data-ttu-id="8947b-102">Souhrn typů trasování</span><span class="sxs-lookup"><span data-stu-id="8947b-102">Trace Type Summary</span></span>
<span data-ttu-id="8947b-103">[Zdrojové úrovně](https://go.microsoft.com/fwlink/?LinkID=94943) definuje různé úrovně trasování: Kritická chyba, upozornění, informace a Verbose, stejně jako obsahuje popis `ActivityTracing` příznak, které přepíná výstup trasování událostí pro přenos hranice a aktivity.</span><span class="sxs-lookup"><span data-stu-id="8947b-103">[Source Levels](https://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="8947b-104">Můžete také zkontrolovat [parametrem TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) pro typy trasování, které může být generována z <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="8947b-104">You can also review [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="8947b-105">V následující tabulce jsou uvedeny nejdůležitější ty.</span><span class="sxs-lookup"><span data-stu-id="8947b-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="8947b-106">Typ sledování</span><span class="sxs-lookup"><span data-stu-id="8947b-106">Trace Type</span></span>|<span data-ttu-id="8947b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8947b-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="8947b-108">Kritická</span><span class="sxs-lookup"><span data-stu-id="8947b-108">Critical</span></span>|<span data-ttu-id="8947b-109">Závažná chyba nebo aplikaci k chybě.</span><span class="sxs-lookup"><span data-stu-id="8947b-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="8947b-110">Chyba</span><span class="sxs-lookup"><span data-stu-id="8947b-110">Error</span></span>|<span data-ttu-id="8947b-111">Došlo k opravitelné chybě.</span><span class="sxs-lookup"><span data-stu-id="8947b-111">Recoverable error.</span></span>|  
|<span data-ttu-id="8947b-112">Upozornění</span><span class="sxs-lookup"><span data-stu-id="8947b-112">Warning</span></span>|<span data-ttu-id="8947b-113">Informační zpráva.</span><span class="sxs-lookup"><span data-stu-id="8947b-113">Informational message.</span></span>|  
|<span data-ttu-id="8947b-114">Informace o</span><span class="sxs-lookup"><span data-stu-id="8947b-114">Information</span></span>|<span data-ttu-id="8947b-115">Nekritická problém.</span><span class="sxs-lookup"><span data-stu-id="8947b-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="8947b-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8947b-116">Verbose</span></span>|<span data-ttu-id="8947b-117">Ladění trasování.</span><span class="sxs-lookup"><span data-stu-id="8947b-117">Debugging trace.</span></span>|  
|<span data-ttu-id="8947b-118">Spustit</span><span class="sxs-lookup"><span data-stu-id="8947b-118">Start</span></span>|<span data-ttu-id="8947b-119">Spouští se zpracování logické jednotky.</span><span class="sxs-lookup"><span data-stu-id="8947b-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="8947b-120">Pozastavit</span><span class="sxs-lookup"><span data-stu-id="8947b-120">Suspend</span></span>|<span data-ttu-id="8947b-121">Pozastavení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="8947b-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="8947b-122">Resume</span><span class="sxs-lookup"><span data-stu-id="8947b-122">Resume</span></span>|<span data-ttu-id="8947b-123">Obnovení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="8947b-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="8947b-124">Zastavit</span><span class="sxs-lookup"><span data-stu-id="8947b-124">Stop</span></span>|<span data-ttu-id="8947b-125">Zastavuje se logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="8947b-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="8947b-126">Přenos</span><span class="sxs-lookup"><span data-stu-id="8947b-126">Transfer</span></span>|<span data-ttu-id="8947b-127">Změna identity korelace.</span><span class="sxs-lookup"><span data-stu-id="8947b-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="8947b-128">Aktivita je definován jako kombinace výše uvedených typů trasování.</span><span class="sxs-lookup"><span data-stu-id="8947b-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="8947b-129">Tady je regulární výraz, který definuje ideální aktivitu v oboru místní (Zdroj trasování)</span><span class="sxs-lookup"><span data-stu-id="8947b-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="8947b-130">To znamená, že aktivita musí splňovat následující podmínky.</span><span class="sxs-lookup"><span data-stu-id="8947b-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="8947b-131">Musí začínat a zastavte v uvedeném pořadí spouštění a zastavování trasování</span><span class="sxs-lookup"><span data-stu-id="8947b-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="8947b-132">Musí mít přenos trasování bezprostředně před pozastavení nebo obnovení činnosti trasování</span><span class="sxs-lookup"><span data-stu-id="8947b-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="8947b-133">Nesmí mít žádné trasování mezi pozastavit a obnovit trasování, pokud existují tato trasování</span><span class="sxs-lookup"><span data-stu-id="8947b-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="8947b-134">Tak dlouho, dokud jsou dodržovány předchozích podmínek může mít libovolný a libovolný počet kritických/Chyba/upozornění / / Verbose/přenosu informací trasování</span><span class="sxs-lookup"><span data-stu-id="8947b-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="8947b-135">Tady je regulární výraz, který definuje ideální aktivitu v globálním oboru</span><span class="sxs-lookup"><span data-stu-id="8947b-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="8947b-136">s R se regulární výraz pro aktivitu v místním oboru.</span><span class="sxs-lookup"><span data-stu-id="8947b-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="8947b-137">Výsledkem je,</span><span class="sxs-lookup"><span data-stu-id="8947b-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
