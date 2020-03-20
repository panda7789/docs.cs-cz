---
title: Souhrn typů trasování
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8ed6dceb19caa52f928f285064c60337e3f15a87
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674843"
---
# <a name="trace-type-summary"></a><span data-ttu-id="895e7-102">Souhrn typů trasování</span><span class="sxs-lookup"><span data-stu-id="895e7-102">Trace Type Summary</span></span>
<span data-ttu-id="895e7-103">[Úrovně zdrojového přenosu](xref:System.Diagnostics.SourceLevels) definuje různé úrovně trasování: Kritická, Chyba, Upozornění, Informace `ActivityTracing` a Verbose, stejně jako poskytuje popis příznaku, který přepíná výstup hranice trasování a události přenosu aktivity.</span><span class="sxs-lookup"><span data-stu-id="895e7-103">[Source Levels](xref:System.Diagnostics.SourceLevels) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides a description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="895e7-104">Můžete také <xref:System.Diagnostics.TraceEventType> zkontrolovat typy trasování, které mohou <xref:System.Diagnostics>být emitovány z .</span><span class="sxs-lookup"><span data-stu-id="895e7-104">You can also review <xref:System.Diagnostics.TraceEventType> for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="895e7-105">V následující tabulce jsou uvedeny nejdůležitější.</span><span class="sxs-lookup"><span data-stu-id="895e7-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="895e7-106">Typ trasování</span><span class="sxs-lookup"><span data-stu-id="895e7-106">Trace Type</span></span>|<span data-ttu-id="895e7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="895e7-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="895e7-108">Kritická</span><span class="sxs-lookup"><span data-stu-id="895e7-108">Critical</span></span>|<span data-ttu-id="895e7-109">Závažná chyba nebo selhání aplikace.</span><span class="sxs-lookup"><span data-stu-id="895e7-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="895e7-110">Chyba</span><span class="sxs-lookup"><span data-stu-id="895e7-110">Error</span></span>|<span data-ttu-id="895e7-111">Obnovitelná chyba.</span><span class="sxs-lookup"><span data-stu-id="895e7-111">Recoverable error.</span></span>|  
|<span data-ttu-id="895e7-112">Upozornění</span><span class="sxs-lookup"><span data-stu-id="895e7-112">Warning</span></span>|<span data-ttu-id="895e7-113">Informační zpráva.</span><span class="sxs-lookup"><span data-stu-id="895e7-113">Informational message.</span></span>|  
|<span data-ttu-id="895e7-114">Informace</span><span class="sxs-lookup"><span data-stu-id="895e7-114">Information</span></span>|<span data-ttu-id="895e7-115">Nekritický problém.</span><span class="sxs-lookup"><span data-stu-id="895e7-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="895e7-116">Verbose</span><span class="sxs-lookup"><span data-stu-id="895e7-116">Verbose</span></span>|<span data-ttu-id="895e7-117">Ladění trasování.</span><span class="sxs-lookup"><span data-stu-id="895e7-117">Debugging trace.</span></span>|  
|<span data-ttu-id="895e7-118">Start</span><span class="sxs-lookup"><span data-stu-id="895e7-118">Start</span></span>|<span data-ttu-id="895e7-119">Spuštění logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="895e7-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="895e7-120">Suspend</span><span class="sxs-lookup"><span data-stu-id="895e7-120">Suspend</span></span>|<span data-ttu-id="895e7-121">Pozastavení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="895e7-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="895e7-122">Obnovit</span><span class="sxs-lookup"><span data-stu-id="895e7-122">Resume</span></span>|<span data-ttu-id="895e7-123">Obnovení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="895e7-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="895e7-124">Zastavit</span><span class="sxs-lookup"><span data-stu-id="895e7-124">Stop</span></span>|<span data-ttu-id="895e7-125">Zastavení logické jednotky zpracování.</span><span class="sxs-lookup"><span data-stu-id="895e7-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="895e7-126">Přenos</span><span class="sxs-lookup"><span data-stu-id="895e7-126">Transfer</span></span>|<span data-ttu-id="895e7-127">Změna korelační identity.</span><span class="sxs-lookup"><span data-stu-id="895e7-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="895e7-128">Aktivita je definována jako kombinace výše uvedených typů trasování.</span><span class="sxs-lookup"><span data-stu-id="895e7-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="895e7-129">Následuje regulární výraz, který definuje ideální aktivitu v místním oboru (zdroj trasování),</span><span class="sxs-lookup"><span data-stu-id="895e7-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="895e7-130">To znamená, že činnost musí splňovat následující podmínky.</span><span class="sxs-lookup"><span data-stu-id="895e7-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="895e7-131">Musí se spustit a zastavit, respektive stopami Start a Stop</span><span class="sxs-lookup"><span data-stu-id="895e7-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="895e7-132">Musí mít trasování přenosu bezprostředně předcházející sledování pozastavit nebo pokračovat.</span><span class="sxs-lookup"><span data-stu-id="895e7-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="895e7-133">Nesmí mít žádné stopy mezi Stopy spánku a Pokračovat, pokud takové stopy existují</span><span class="sxs-lookup"><span data-stu-id="895e7-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="895e7-134">To může mít všechny a tolik kritických / Chyba / Varování / Informace / Verbose / Transfer stopy tak dlouho, dokud jsou dodrženy předchozí podmínky</span><span class="sxs-lookup"><span data-stu-id="895e7-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="895e7-135">Následuje regulární výraz, který definuje ideální aktivitu v globálním rozsahu,</span><span class="sxs-lookup"><span data-stu-id="895e7-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="895e7-136">r je regulární výraz pro aktivitu v místním oboru.</span><span class="sxs-lookup"><span data-stu-id="895e7-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="895e7-137">To se promítá do,</span><span class="sxs-lookup"><span data-stu-id="895e7-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
