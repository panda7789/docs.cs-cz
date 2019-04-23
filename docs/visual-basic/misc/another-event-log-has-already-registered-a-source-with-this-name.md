---
title: Jiný protokol událostí už zaregistrovaný zdroj s tímto názvem
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: d932869504b2d8a5f3a948b190e5528bfcfa664f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314669"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="4f76b-102">Jiný protokol událostí už zaregistrovaný zdroj s tímto názvem</span><span class="sxs-lookup"><span data-stu-id="4f76b-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="4f76b-103">Pokus o byla vytvořena pro zápis záznamu do protokolu událostí, kde zadaný zdroj je zaregistrován jiný protokol událostí.</span><span class="sxs-lookup"><span data-stu-id="4f76b-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="4f76b-104">Je nutné nastavit <xref:System.Diagnostics.EventLog.Source%2A> vlastnictví vaší <xref:System.Diagnostics.EventLog> instance komponenty předtím, než vaše komponenta zapíše položku do protokolu.</span><span class="sxs-lookup"><span data-stu-id="4f76b-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="4f76b-105">Pokud k tomu dojde, systém kontroluje, zda je zadaný zdroj je zaregistrován v protokolu událostí, ke kterému je součást zápisu a volání <xref:System.Diagnostics.EventLog.CreateEventSource%2A> v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="4f76b-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4f76b-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4f76b-106">To correct this error</span></span>  
  
1. <span data-ttu-id="4f76b-107">Odebere přidružení zdroje první pomocí protokolu <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> nebo <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4f76b-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2. <span data-ttu-id="4f76b-108">Zaregistrujte zdroj nový protokol.</span><span class="sxs-lookup"><span data-stu-id="4f76b-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f76b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f76b-109">See also</span></span>

- [<span data-ttu-id="4f76b-110">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="4f76b-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
