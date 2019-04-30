---
title: Vlastní záznamy sledování
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: d4733b4ffc0d866cf90fd5a5e7d649de261c45fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945831"
---
# <a name="custom-tracking-records"></a>Vlastní záznamy sledování

Toto téma ukazuje, jak vytvořit vlastní záznamy sledování a naplníte je s daty, aby byly vypuštěny spolu s záznamy.

## <a name="emitting-custom-tracking-records"></a>Generování vlastní záznamy sledování

Vlastní sledování záznamů může být generována z aktivitě s kódem, jak je znázorněno v následujícím příkladu.

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

A <xref:System.Activities.Tracking.CustomTrackingRecord> je vygenerován v aktivitě s kódem vyvoláním <xref:System.Activities.NativeActivityContext.Track%2A> metodu `ActivityContext`.

## <a name="see-also"></a>Viz také:

- [Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorování aplikací pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=201275)
