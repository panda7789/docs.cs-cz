---
title: Souhrn typů trasování
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 73777df2b58b14947c416ce409bcb42d439499ec
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403840"
---
# <a name="trace-type-summary"></a><span data-ttu-id="72ce2-102">Souhrn typů trasování</span><span class="sxs-lookup"><span data-stu-id="72ce2-102">Trace Type Summary</span></span>
<span data-ttu-id="72ce2-103">[Zdrojové úrovně](https://go.microsoft.com/fwlink/?LinkID=94943) definuje různé úrovně trasování: kritické, chyba, upozornění, informace a podrobné, stejně jako obsahuje popis `ActivityTracing` příznak, které přepíná výstup trasování událostí pro přenos hranice a aktivity.</span><span class="sxs-lookup"><span data-stu-id="72ce2-103">[Source Levels](https://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="72ce2-104">Můžete také zkontrolovat [parametrem TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) pro typy trasování, které může být generována z <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="72ce2-104">You can also review [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="72ce2-105">V následující tabulce jsou uvedeny nejdůležitější ty.</span><span class="sxs-lookup"><span data-stu-id="72ce2-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="72ce2-106">Typ sledování</span><span class="sxs-lookup"><span data-stu-id="72ce2-106">Trace Type</span></span>|<span data-ttu-id="72ce2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="72ce2-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="72ce2-108">Kritická</span><span class="sxs-lookup"><span data-stu-id="72ce2-108">Critical</span></span>|<span data-ttu-id="72ce2-109">Závažná chyba nebo aplikaci k chybě.</span><span class="sxs-lookup"><span data-stu-id="72ce2-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="72ce2-110">Chyba</span><span class="sxs-lookup"><span data-stu-id="72ce2-110">Error</span></span>|<span data-ttu-id="72ce2-111">Došlo k opravitelné chybě.</span><span class="sxs-lookup"><span data-stu-id="72ce2-111">Recoverable error.</span></span>|  
|<span data-ttu-id="72ce2-112">Upozornění</span><span class="sxs-lookup"><span data-stu-id="72ce2-112">Warning</span></span>|<span data-ttu-id="72ce2-113">Informační zpráva.</span><span class="sxs-lookup"><span data-stu-id="72ce2-113">Informational message.</span></span>|  
|<span data-ttu-id="72ce2-114">Informace o</span><span class="sxs-lookup"><span data-stu-id="72ce2-114">Information</span></span>|<span data-ttu-id="72ce2-115">Nekritická problém.</span><span class="sxs-lookup"><span data-stu-id="72ce2-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="72ce2-116">verbose</span><span class="sxs-lookup"><span data-stu-id="72ce2-116">Verbose</span></span>|<span data-ttu-id="72ce2-117">Ladění trasování.</span><span class="sxs-lookup"><span data-stu-id="72ce2-117">Debugging trace.</span></span>|  
|<span data-ttu-id="72ce2-118">Spustit</span><span class="sxs-lookup"><span data-stu-id="72ce2-118">Start</span></span>|<span data-ttu-id="72ce2-119">Spouští se zpracování logické jednotky.</span><span class="sxs-lookup"><span data-stu-id="72ce2-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="72ce2-120">Pozastavit</span><span class="sxs-lookup"><span data-stu-id="72ce2-120">Suspend</span></span>|<span data-ttu-id="72ce2-121">Pozastavení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="72ce2-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="72ce2-122">Resume</span><span class="sxs-lookup"><span data-stu-id="72ce2-122">Resume</span></span>|<span data-ttu-id="72ce2-123">Obnovení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="72ce2-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="72ce2-124">Zastavit</span><span class="sxs-lookup"><span data-stu-id="72ce2-124">Stop</span></span>|<span data-ttu-id="72ce2-125">Zastavuje se logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="72ce2-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="72ce2-126">Přenos</span><span class="sxs-lookup"><span data-stu-id="72ce2-126">Transfer</span></span>|<span data-ttu-id="72ce2-127">Změna identity korelace.</span><span class="sxs-lookup"><span data-stu-id="72ce2-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="72ce2-128">Aktivita je definován jako kombinace výše uvedených typů trasování.</span><span class="sxs-lookup"><span data-stu-id="72ce2-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="72ce2-129">Tady je regulární výraz, který definuje ideální aktivitu v oboru místní (Zdroj trasování)</span><span class="sxs-lookup"><span data-stu-id="72ce2-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="72ce2-130">To znamená, že aktivita musí splňovat následující podmínky.</span><span class="sxs-lookup"><span data-stu-id="72ce2-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="72ce2-131">Musí začínat a zastavte v uvedeném pořadí spouštění a zastavování trasování</span><span class="sxs-lookup"><span data-stu-id="72ce2-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="72ce2-132">Musí mít přenos trasování bezprostředně před pozastavení nebo obnovení činnosti trasování</span><span class="sxs-lookup"><span data-stu-id="72ce2-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="72ce2-133">Nesmí mít žádné trasování mezi pozastavit a obnovit trasování, pokud existují tato trasování</span><span class="sxs-lookup"><span data-stu-id="72ce2-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="72ce2-134">Tak dlouho, dokud jsou dodržovány předchozích podmínek může mít libovolný a libovolný počet kritických/Chyba/upozornění / / Verbose/přenosu informací trasování</span><span class="sxs-lookup"><span data-stu-id="72ce2-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="72ce2-135">Tady je regulární výraz, který definuje ideální aktivitu v globálním oboru</span><span class="sxs-lookup"><span data-stu-id="72ce2-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="72ce2-136">s R se regulární výraz pro aktivitu v místním oboru.</span><span class="sxs-lookup"><span data-stu-id="72ce2-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="72ce2-137">Výsledkem je,</span><span class="sxs-lookup"><span data-stu-id="72ce2-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
