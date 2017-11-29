---
title: "Jiné protokolu událostí už zaregistrovaný zdroj s tímto názvem"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8beea344d233794ddc36d7fc53db1c01be84399f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="66094-102">Jiné protokolu událostí už zaregistrovaný zdroj s tímto názvem</span><span class="sxs-lookup"><span data-stu-id="66094-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="66094-103">Pokus o byl proveden pro zápis záznamu do protokolu událostí, kde je zadaný zdroj registrovaná s jinou protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="66094-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="66094-104">Je nutné nastavit <xref:System.Diagnostics.EventLog.Source%2A> vlastnost vaší <xref:System.Diagnostics.EventLog> instance komponenty před příslušné součásti zapíše položku do protokolu.</span><span class="sxs-lookup"><span data-stu-id="66094-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="66094-105">V takovém případě systém kontroluje, zda je zadaný zdroj není zaregistrována v protokolu událostí, ke kterému je součást zápisu a volání <xref:System.Diagnostics.EventLog.CreateEventSource%2A> v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="66094-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="66094-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="66094-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="66094-107">Odebere přidružení zdroje první pomocí protokolu <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> nebo <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="66094-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="66094-108">Zaregistrujte zdroj se nový protokol.</span><span class="sxs-lookup"><span data-stu-id="66094-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66094-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="66094-109">See Also</span></span>  
 [<span data-ttu-id="66094-110">My.Application.Log – objekt</span><span class="sxs-lookup"><span data-stu-id="66094-110">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="66094-111">Postupy: odebrání zdroje událostí</span><span class="sxs-lookup"><span data-stu-id="66094-111">How to: Remove an Event Source</span></span>](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)  
 [<span data-ttu-id="66094-112">Postupy: Přidání aplikace jako zdroj položek protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="66094-112">How to: Add Your Application as a Source of Event Log Entries</span></span>](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)
