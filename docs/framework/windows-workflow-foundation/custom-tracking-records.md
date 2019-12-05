---
title: Vlastní záznamy sledování
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 986f0350c24414d0ff960474445adf6ac3f39734
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802619"
---
# <a name="custom-tracking-records"></a>Vlastní záznamy sledování

Toto téma ukazuje, jak vytvořit vlastní záznamy sledování a naplnit je daty, která se mají vygenerovat společně se záznamy.

## <a name="emitting-custom-tracking-records"></a>Emitování vlastních záznamů sledování

Vlastní záznamy sledování je možné vygenerovat z aktivity kódu, jak je znázorněno v následujícím příkladu.

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<xref:System.Activities.Tracking.CustomTrackingRecord> je vygenerována v aktivitě kódu vyvoláním metody <xref:System.Activities.NativeActivityContext.Track%2A> na `ActivityContext`.

## <a name="see-also"></a>Viz také:

- [Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
