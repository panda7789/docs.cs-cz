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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a459e6df0e030f4e17bb73461d8fa790a61787e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="custom-tracking-records"></a><span data-ttu-id="6ceed-102">Vlastní sledování záznamů</span><span class="sxs-lookup"><span data-stu-id="6ceed-102">Custom Tracking Records</span></span>
<span data-ttu-id="6ceed-103">Toto téma ukazuje, jak vytvořit vlastní sledování záznamy a naplnit daty pro vypuštění společně s záznamy.</span><span class="sxs-lookup"><span data-stu-id="6ceed-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="6ceed-104">Emitování záznamy vlastní sledování</span><span class="sxs-lookup"><span data-stu-id="6ceed-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="6ceed-105">Vlastní sledování záznamů můžete vygenerované z kódu aktivity, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6ceed-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="6ceed-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> je vygenerované v kódu aktivity vyvoláním <xref:System.Activities.NativeActivityContext.Track%2A> metodu `ActvityContext`.</span><span class="sxs-lookup"><span data-stu-id="6ceed-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ceed-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ceed-107">See Also</span></span>  
 [<span data-ttu-id="6ceed-108">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="6ceed-108">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="6ceed-109">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="6ceed-109">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
