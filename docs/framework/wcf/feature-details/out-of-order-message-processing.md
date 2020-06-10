---
title: Zpracování zpráv mimo pořadí
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 7930f26cf5957158a16d65085267cf1bab2e4504
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598720"
---
# <a name="out-of-order-message-processing"></a>Zpracování zpráv mimo pořadí
Služby pracovních postupů můžou záviset na zprávách odesílaných v určitém pořadí. Služba pracovního postupu obsahuje jednu nebo více <xref:System.ServiceModel.Activities.Receive> aktivit a každá <xref:System.ServiceModel.Activities.Receive> aktivita očekává určitou zprávu. Bez jakýchkoli konkrétních záruk přenosů za provozu můžou být zprávy odesílané klienty zpožděné a proto se doručí v pořadí, ve kterém služba pracovního postupu nemusí očekávat. Implementace služby pracovního postupu, která nevyžaduje odeslání zprávy v určitém pořadí, se obvykle provádí pomocí paralelní aktivity. Pro složitější aplikační protokol by byl pracovní postup velmi složitý velmi rychle.  Funkce zpracování zpráv mimo pořadí v Windows Communication Foundation (WCF) umožňuje vytvořit takový pracovní postup bez nutnosti složitosti vnořených paralelních aktivit. Zpracování zpráv mimo pořadí je podporováno pouze na kanálech, které podporují <xref:System.ServiceModel.Channels.ReceiveContext> například vazby služby MSMQ WCF.  
  
## <a name="enabling-out-of-order-message-processing"></a>Povolení zpracování zpráv mimo pořadí  
 Zpracování zpráv mimo pořadí je povoleno nastavením vlastnosti na hodnotu <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> `true` implementace WorkflowService. Následující příklad ukazuje, jak nastavit <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> vlastnost v kódu.  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 Můžete také použít `AllowBufferedReceive` atribut pro službu pracovního postupu v jazyce XAML, jak je znázorněno v následujícím příkladu.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [Služby pracovních postupů](workflow-services.md)
- [Fronty a spolehlivé relace](queues-and-reliable-sessions.md)
