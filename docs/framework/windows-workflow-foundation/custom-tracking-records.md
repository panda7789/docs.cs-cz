---
title: "Vlastní sledování záznamů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51c47c3b11c912c1c67fe0d9ed4960de42f8a852
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-tracking-records"></a><span data-ttu-id="eb275-102">Vlastní sledování záznamů</span><span class="sxs-lookup"><span data-stu-id="eb275-102">Custom Tracking Records</span></span>
<span data-ttu-id="eb275-103">Toto téma ukazuje, jak vytvořit vlastní sledování záznamy a naplnit daty pro vypuštění společně s záznamy.</span><span class="sxs-lookup"><span data-stu-id="eb275-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="eb275-104">Emitování záznamy vlastní sledování</span><span class="sxs-lookup"><span data-stu-id="eb275-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="eb275-105">Vlastní sledování záznamů můžete vygenerované z kódu aktivity, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb275-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="eb275-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> je vygenerované v kódu aktivity vyvoláním <xref:System.Activities.NativeActivityContext.Track%2A> metodu `ActvityContext`.</span><span class="sxs-lookup"><span data-stu-id="eb275-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb275-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb275-107">See Also</span></span>  
 [<span data-ttu-id="eb275-108">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="eb275-108">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="eb275-109">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="eb275-109">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
