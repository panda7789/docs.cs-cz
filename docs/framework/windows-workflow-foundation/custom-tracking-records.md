---
title: Vlastní sledování záznamů
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: d4733b4ffc0d866cf90fd5a5e7d649de261c45fb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499118"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="9f567-102">Vlastní sledování záznamů</span><span class="sxs-lookup"><span data-stu-id="9f567-102">Custom Tracking Records</span></span>

<span data-ttu-id="9f567-103">Toto téma ukazuje, jak vytvořit vlastní záznamy sledování a naplníte je s daty, aby byly vypuštěny spolu s záznamy.</span><span class="sxs-lookup"><span data-stu-id="9f567-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="9f567-104">Generování vlastní záznamy sledování</span><span class="sxs-lookup"><span data-stu-id="9f567-104">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="9f567-105">Vlastní sledování záznamů může být generována z aktivitě s kódem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f567-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="9f567-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> je vygenerován v aktivitě s kódem vyvoláním <xref:System.Activities.NativeActivityContext.Track%2A> metodu `ActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="9f567-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f567-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f567-107">See also</span></span>

- [<span data-ttu-id="9f567-108">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="9f567-108">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="9f567-109">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="9f567-109">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
