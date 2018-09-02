---
title: Vlastní sledování záznamů
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: ef3c20890f33f3ffd07a9c88de863e1ebe24851f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401248"
---
# <a name="custom-tracking-records"></a>Vlastní sledování záznamů
Toto téma ukazuje, jak vytvořit vlastní záznamy sledování a naplníte je s daty, aby byly vypuštěny spolu s záznamy.  
  
## <a name="emitting-custom-tracking-records"></a>Generování vlastní záznamy sledování  
 Vlastní sledování záznamů může být generována z aktivitě s kódem, jak je znázorněno v následujícím příkladu.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 A <xref:System.Activities.Tracking.CustomTrackingRecord> je vygenerován v aktivitě s kódem vyvoláním <xref:System.Activities.NativeActivityContext.Track%2A> metodu `ActvityContext`.  
  
## <a name="see-also"></a>Viz také  
 [Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=201275)
