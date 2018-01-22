---
title: "Zadaný v EventLogSource název zdroje je registrován protokolu stanovené v EventLogName"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0a100789486dda403f483489e73accbf219374c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="db038-102">Zadaný v EventLogSource název zdroje je registrován protokolu stanovené v EventLogName</span><span class="sxs-lookup"><span data-stu-id="db038-102">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>
<span data-ttu-id="db038-103">`EventLog` Se pokouší o odkazovat na zdroj, který je zaregistrován jiný protokol.</span><span class="sxs-lookup"><span data-stu-id="db038-103">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="db038-104">Pokud píšete položky do protokolu událostí, je nutné zadat <xref:System.Diagnostics.EventLog.Source%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="db038-104">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="db038-105"><xref:System.Diagnostics.EventLog.Source%2A> Vlastnost zaregistruje příslušné součásti se v protokolu událostí jako platný zdroj položek.</span><span class="sxs-lookup"><span data-stu-id="db038-105">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="db038-106">Jednoho zdroje může být přidružen k (a tedy zapisovat položky k) jenom jeden protokol událostí v čase.</span><span class="sxs-lookup"><span data-stu-id="db038-106">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="db038-107">Ve výchozím nastavení, pokud se pokusíte zapsat záznam bez nejprve nutnosti zaregistrovat příslušné součásti jako platný zdroj, systém automaticky registruje zdroj protokolu událostí, pomocí hodnoty <xref:System.Diagnostics.EventLog.Source%2A> vlastnost jako zdrojový řetězec.</span><span class="sxs-lookup"><span data-stu-id="db038-107">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="db038-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="db038-108">To correct this error</span></span>  
  
-   <span data-ttu-id="db038-109">Zkontrolujte, zda že zdroj je zaregistrován v správné protokolu.</span><span class="sxs-lookup"><span data-stu-id="db038-109">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="db038-110">Chcete-li to provést, použijte <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metoda nebo jednoho z jeho přetížení pro zadejte řetězec, který jednoznačně identifikuje příslušné součásti do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="db038-110">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db038-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="db038-111">See Also</span></span>  
 [<span data-ttu-id="db038-112">Správa protokolů událostí</span><span class="sxs-lookup"><span data-stu-id="db038-112">Administering Event Logs</span></span>](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [<span data-ttu-id="db038-113">Odkazy v protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="db038-113">Event Log References</span></span>](http://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [<span data-ttu-id="db038-114">Postupy: Přidání aplikace jako zdroj položek protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="db038-114">How to: Add Your Application as a Source of Event Log Entries</span></span>](http://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)  
 [<span data-ttu-id="db038-115">Postupy: odebrání zdroje událostí</span><span class="sxs-lookup"><span data-stu-id="db038-115">How to: Remove an Event Source</span></span>](http://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
