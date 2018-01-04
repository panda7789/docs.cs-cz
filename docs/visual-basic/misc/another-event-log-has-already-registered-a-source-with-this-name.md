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
ms.openlocfilehash: 0f04afd5d061a44f572d95abfb0173ad6fa2ac27
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="2c9a4-102">Jiné protokolu událostí už zaregistrovaný zdroj s tímto názvem</span><span class="sxs-lookup"><span data-stu-id="2c9a4-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="2c9a4-103">Pokus o byl proveden pro zápis záznamu do protokolu událostí, kde je zadaný zdroj registrovaná s jinou protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="2c9a4-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="2c9a4-104">Je nutné nastavit <xref:System.Diagnostics.EventLog.Source%2A> vlastnost vaší <xref:System.Diagnostics.EventLog> instance komponenty před příslušné součásti zapíše položku do protokolu.</span><span class="sxs-lookup"><span data-stu-id="2c9a4-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="2c9a4-105">V takovém případě systém kontroluje, zda je zadaný zdroj není zaregistrována v protokolu událostí, ke kterému je součást zápisu a volání <xref:System.Diagnostics.EventLog.CreateEventSource%2A> v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="2c9a4-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c9a4-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2c9a4-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="2c9a4-107">Odebere přidružení zdroje první pomocí protokolu <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> nebo <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2c9a4-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="2c9a4-108">Zaregistrujte zdroj se nový protokol.</span><span class="sxs-lookup"><span data-stu-id="2c9a4-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c9a4-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c9a4-109">See Also</span></span>  
 [<span data-ttu-id="2c9a4-110">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="2c9a4-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

