---
title: Vlastní sledování záznamů
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: ef3c20890f33f3ffd07a9c88de863e1ebe24851f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520182"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="cff22-102">Vlastní sledování záznamů</span><span class="sxs-lookup"><span data-stu-id="cff22-102">Custom Tracking Records</span></span>
<span data-ttu-id="cff22-103">Toto téma ukazuje, jak vytvořit vlastní záznamy sledování a naplníte je s daty, aby byly vypuštěny spolu s záznamy.</span><span class="sxs-lookup"><span data-stu-id="cff22-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="cff22-104">Generování vlastní záznamy sledování</span><span class="sxs-lookup"><span data-stu-id="cff22-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="cff22-105">Vlastní sledování záznamů může být generována z aktivitě s kódem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cff22-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="cff22-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> je vygenerován v aktivitě s kódem vyvoláním <xref:System.Activities.NativeActivityContext.Track%2A> metodu `ActvityContext`.</span><span class="sxs-lookup"><span data-stu-id="cff22-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff22-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="cff22-107">See Also</span></span>  
 [<span data-ttu-id="cff22-108">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="cff22-108">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="cff22-109">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="cff22-109">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
