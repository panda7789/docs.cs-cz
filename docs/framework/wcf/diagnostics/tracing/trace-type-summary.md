---
title: Souhrn typů trasování
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8f54f71ef63338708a29fac5557c7c7e8f257f58
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856010"
---
# <a name="trace-type-summary"></a><span data-ttu-id="a03bf-102">Souhrn typů trasování</span><span class="sxs-lookup"><span data-stu-id="a03bf-102">Trace Type Summary</span></span>
<span data-ttu-id="a03bf-103">[Zdrojové úrovně](https://go.microsoft.com/fwlink/?LinkID=94943) definují různé úrovně trasování: Kritická, chyba, upozornění, informace a podrobné a také poskytuje popis `ActivityTracing` příznaku, který přepíná výstup událostí pro trasování a přenos aktivity.</span><span class="sxs-lookup"><span data-stu-id="a03bf-103">[Source Levels](https://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="a03bf-104">Můžete také zkontrolovat [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) pro typy trasování, ze <xref:System.Diagnostics>kterých lze generovat.</span><span class="sxs-lookup"><span data-stu-id="a03bf-104">You can also review [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="a03bf-105">V následující tabulce jsou uvedeny nejdůležitější ty.</span><span class="sxs-lookup"><span data-stu-id="a03bf-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="a03bf-106">Typ trasování</span><span class="sxs-lookup"><span data-stu-id="a03bf-106">Trace Type</span></span>|<span data-ttu-id="a03bf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a03bf-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="a03bf-108">Kritická</span><span class="sxs-lookup"><span data-stu-id="a03bf-108">Critical</span></span>|<span data-ttu-id="a03bf-109">Závažná chyba nebo selhání aplikace</span><span class="sxs-lookup"><span data-stu-id="a03bf-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="a03bf-110">Chyba</span><span class="sxs-lookup"><span data-stu-id="a03bf-110">Error</span></span>|<span data-ttu-id="a03bf-111">Obnovitelná chyba.</span><span class="sxs-lookup"><span data-stu-id="a03bf-111">Recoverable error.</span></span>|  
|<span data-ttu-id="a03bf-112">Upozornění</span><span class="sxs-lookup"><span data-stu-id="a03bf-112">Warning</span></span>|<span data-ttu-id="a03bf-113">Informační zpráva.</span><span class="sxs-lookup"><span data-stu-id="a03bf-113">Informational message.</span></span>|  
|<span data-ttu-id="a03bf-114">Informace o</span><span class="sxs-lookup"><span data-stu-id="a03bf-114">Information</span></span>|<span data-ttu-id="a03bf-115">Nekritický problém.</span><span class="sxs-lookup"><span data-stu-id="a03bf-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="a03bf-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a03bf-116">Verbose</span></span>|<span data-ttu-id="a03bf-117">Trasování ladění.</span><span class="sxs-lookup"><span data-stu-id="a03bf-117">Debugging trace.</span></span>|  
|<span data-ttu-id="a03bf-118">Spustit</span><span class="sxs-lookup"><span data-stu-id="a03bf-118">Start</span></span>|<span data-ttu-id="a03bf-119">Spuštění logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="a03bf-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="a03bf-120">Pozastavit</span><span class="sxs-lookup"><span data-stu-id="a03bf-120">Suspend</span></span>|<span data-ttu-id="a03bf-121">Pozastavení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="a03bf-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="a03bf-122">Resume</span><span class="sxs-lookup"><span data-stu-id="a03bf-122">Resume</span></span>|<span data-ttu-id="a03bf-123">Obnovení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="a03bf-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="a03bf-124">Zastavit</span><span class="sxs-lookup"><span data-stu-id="a03bf-124">Stop</span></span>|<span data-ttu-id="a03bf-125">Zastavuje se logická jednotka zpracování.</span><span class="sxs-lookup"><span data-stu-id="a03bf-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="a03bf-126">Přenos</span><span class="sxs-lookup"><span data-stu-id="a03bf-126">Transfer</span></span>|<span data-ttu-id="a03bf-127">Změna identity korelace.</span><span class="sxs-lookup"><span data-stu-id="a03bf-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="a03bf-128">Aktivita je definována jako kombinace typů trasování výše.</span><span class="sxs-lookup"><span data-stu-id="a03bf-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="a03bf-129">Následuje regulární výraz, který definuje ideální aktivitu v oboru místního (zdroje trasování),</span><span class="sxs-lookup"><span data-stu-id="a03bf-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="a03bf-130">To znamená, že aktivita musí splňovat následující podmínky.</span><span class="sxs-lookup"><span data-stu-id="a03bf-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="a03bf-131">Musí začínat a zastavovat trasování spuštění a zastavení.</span><span class="sxs-lookup"><span data-stu-id="a03bf-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="a03bf-132">Musí mít trasování přenosu hned před přerušením nebo obnovením trasování.</span><span class="sxs-lookup"><span data-stu-id="a03bf-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="a03bf-133">Nesmí obsahovat žádné trasování mezi trasováním pozastavení a obnovení, pokud taková trasování existují.</span><span class="sxs-lookup"><span data-stu-id="a03bf-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="a03bf-134">Může mít libovolné a tolik kritických/chyb/upozornění/informací/podrobných trasování/přenosů, pokud jsou splněny předchozí podmínky.</span><span class="sxs-lookup"><span data-stu-id="a03bf-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="a03bf-135">Následuje regulární výraz, který definuje ideální aktivitu v globálním oboru.</span><span class="sxs-lookup"><span data-stu-id="a03bf-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="a03bf-136">v jazyce R je regulární výraz aktivity v místním oboru.</span><span class="sxs-lookup"><span data-stu-id="a03bf-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="a03bf-137">To se týká,</span><span class="sxs-lookup"><span data-stu-id="a03bf-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
