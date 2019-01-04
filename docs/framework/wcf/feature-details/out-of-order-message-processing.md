---
title: Zpracování zpráv mimo pořadí
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 3beca8d73788d177d07868d7169d8aea3ecd8e80
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029941"
---
# <a name="out-of-order-message-processing"></a>Zpracování zpráv mimo pořadí
Služby pracovních postupů může záviset na zprávy odesílané v určitém pořadí. Služba pracovního postupu obsahuje jeden nebo více <xref:System.ServiceModel.Activities.Receive> aktivity a každý <xref:System.ServiceModel.Activities.Receive> aktivity očekává konkrétní zprávu. Zprávy od klientů může bez záruky doručení konkrétní přenos, zpoždění a proto doručeny v pořadí, které nemusí očekávají služby pracovního postupu. Implementace služby pracovního postupu, který nevyžaduje zprávy odeslané v konkrétní pořadí se obvykle provádí pomocí paralelní aktivity. Pro složitější aplikační protokol pracovní postup by se mohla stát velmi složité velmi rychle.  Funkce ve Windows Communication Foundation (WCF) zpracování zpráv mimo pořadí umožňuje vytvořit pracovní postup, bez složitosti vnořené paralelní aktivity. Zpracování zpráv mimo pořadí je podporována pouze na kanály, které podporují <xref:System.ServiceModel.Channels.ReceiveContext> jako jsou třeba vazby služby MSMQ WCF.  
  
## <a name="enabling-out-of-order-message-processing"></a>Povolení zpracování zpráv mimo pořadí  
 Zpracování zpráv mimo pořadí se povoluje nastavením <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> vlastnost `true` na workflowservice hodnotu vlastnosti. Následující příklad ukazuje, jak nastavit <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> vlastností v kódu.  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 Můžete také použít `AllowBufferedReceive` atribut služby pracovních postupů v XAML, jak je znázorněno v následujícím příkladu.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Fronty a spolehlivé relace](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
