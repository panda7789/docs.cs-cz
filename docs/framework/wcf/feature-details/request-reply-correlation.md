---
title: Korelace požadavku a odpovědi
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: 34a41a149e740faf0f3816bba2c9bd9b47d4996e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184548"
---
# <a name="request-reply-correlation"></a>Korelace požadavku a odpovědi
Korelace požadavku a odpovědi <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> se používá s dvojicí k implementaci obousměrné operace ve službě pracovního postupu a s <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> dvojicí, která vyvolá obousměrnou operaci v jiné webové službě. Při vyvolání obousměrné operace ve službě WCF, služba může být buď tradiční imperativní kód založený Windows Communication Foundation (WCF) služby nebo může být služba pracovního postupu. Chcete-li použít korelaci požadavek odpověď obousměrné <xref:System.ServiceModel.BasicHttpBinding>vazby musí být použity, například . Ať už vyvoláte nebo implementujete obousměrnou operaci, kroky inicializace korelace jsou podobné a jsou popsány v této části.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Použití korelace v obousměrné operaci s receive/SendReply  
 <xref:System.ServiceModel.Activities.Receive> / Dvojice <xref:System.ServiceModel.Activities.SendReply> se používá k implementaci obousměrné operace ve službě pracovního postupu. Runtime používá korelace požadavek odpověď k zajištění, že odpověď je odeslána správnému volajícímu. Pokud je pracovní postup <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostován pomocí , což je případ služeb pracovního postupu, je výchozí inicializace korelace dostatečná. V tomto scénáři <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> je dvojice používá pracovní postup a není vyžadována žádná konkrétní konfigurace korelace.  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Explicitně inicializovat korelaci požadavku a odpovědi  
 Pokud jsou souběžně další obousměrné operace, měla by být korelace explicitně nakonfigurována. To lze provést zadáním <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>a , nebo <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> umístěním <xref:System.ServiceModel.Activities.CorrelationScope>vnitřku . V tomto příkladu je na <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> páru konfigurována korelace požadavku a odpovědi.  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 Namísto explicitní konfigurace korelace <xref:System.ServiceModel.Activities.CorrelationScope> lze použít aktivitu. <xref:System.ServiceModel.Activities.CorrelationScope>poskytuje implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> zasílání zpráv aktivity, které obsahuje. V tomto příkladu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> je pár <xref:System.ServiceModel.Activities.CorrelationScope>obsažen uvnitř . Není vyžadována žádná explicitní konfigurace korelace.  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 Pokud jsou požadovány další korelace pak <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> mohou být nakonfigurovány pomocí `CorrelationInitializer` vlastnosti příslušné zasílání zpráv aktivity pomocí požadovaných typů.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Použití korelace v obousměrné operaci s odesíláním a přijímáním odpovědi  
 Zatímco <xref:System.ServiceModel.Activities.Receive> aktivitu lze použít pouze ve službě <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> pracovního <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> postupu hostované aplikací a dvojici lze použít v libovolném pracovním postupu, který musí vyvolat metodu webové služby. Pokud je pracovní postup <xref:System.ServiceModel.Activities.WorkflowServiceHost> hostován pomocí výchozí korelace popsané v předchozí části, ale pokud ne, <xref:System.ServiceModel.Activities.CorrelationInitializer> <xref:System.ServiceModel.Activities.CorrelationHandle>musí být korelace nakonfigurována <xref:System.ServiceModel.Activities.CorrelationScope>buď explicitně pomocí požadovaného a , nebo pomocí správy implicitního popisovače .  
  
 Při použití **přidat odkaz na službu** s obousměrné operace, <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> jsou generovány aktivity, které zabalit pár aktivity interně s Požadavek/Odpověď korelace explicitně zadána.
