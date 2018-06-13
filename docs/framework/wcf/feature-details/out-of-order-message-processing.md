---
title: Zpracování zpráv mimo pořadí
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: a7839b60dbad7919a644c196a1c63f6bc46fb5d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492942"
---
# <a name="out-of-order-message-processing"></a>Zpracování zpráv mimo pořadí
Služby pracovních postupů může záviset na zprávy odesílané v určitém pořadí. Služba pracovní postup obsahuje jeden nebo více <xref:System.ServiceModel.Activities.Receive> aktivity a každý <xref:System.ServiceModel.Activities.Receive> aktivity očekává konkrétní zprávou. Zprávy odeslané klienti mohou bez záruky doručení konkrétní přenos, odložené a proto doručit v pořadí, které nemusí očekávat služby pracovního postupu. Implementace služby pracovního postupu, který nevyžaduje zprávy odeslané v určitém pořadí se obvykle provádí pomocí paralelní aktivity. Složitější aplikační protokol pracovní postup by být velice komplexní velmi rychle.  Funkce ve Windows Communication Foundation (WCF) zpracování zpráv mimo pořadí umožňuje vytvořit takový pracovní postup bez všechny složitosti vnořené paralelní aktivity. Zpracování zpráv mimo pořadí je podporován pouze na kanály, které podporují <xref:System.ServiceModel.Channels.ReceiveContext> jako jsou třeba vazby služby MSMQ WCF.  
  
## <a name="enabling-out-of-order-message-processing"></a>Povolení zpracování zpráv mimo pořadí  
 Zpracování zpráv mimo pořadí povolíte nastavením <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> vlastnost `true` na WorkflowService. Následující příklad ukazuje, jak nastavit <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> vlastností v kódu.  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 Můžete taky použít `AllowBufferedReceive` atribut služby pracovních postupů v jazyce XAML, jak je znázorněno v následujícím příkladu.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Fronty a spolehlivé relace](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
