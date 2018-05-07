---
title: Vlastní sledování záznamů
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 6c68c08e5beacee30b517bf0c2bad3e83785409b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="custom-tracking-records"></a>Vlastní sledování záznamů
Toto téma ukazuje, jak vytvořit vlastní sledování záznamy a naplnit daty pro vypuštění společně s záznamy.  
  
## <a name="emitting-custom-tracking-records"></a>Emitování záznamy vlastní sledování  
 Vlastní sledování záznamů můžete vygenerované z kódu aktivity, jak je znázorněno v následujícím příkladu.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 A <xref:System.Activities.Tracking.CustomTrackingRecord> je vygenerované v kódu aktivity vyvoláním <xref:System.Activities.NativeActivityContext.Track%2A> metodu `ActvityContext`.  
  
## <a name="see-also"></a>Viz také  
 [Windows Server App Fabric monitorování](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
