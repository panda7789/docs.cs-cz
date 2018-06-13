---
title: Korelace požadavku a odpovědi
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497201"
---
# <a name="request-reply-correlation"></a>Korelace požadavku a odpovědi
Korelace požadavku a odpovědi se používá s <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár implementovat obousměrný operace ve službě pracovního postupu a s <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vyvolá obousměrný operaci v jiný Web Služba. Při vyvolání obousměrný operace ve službě WCF, služba může být buď tradiční imperativní založené na kódu služby Windows Communication Foundation (WCF), nebo může být služby pracovních postupů. Použít korelace požadavku a odpovědi vazba obousměrná musí být použita, jako například <xref:System.ServiceModel.BasicHttpBinding>. Ať už vyvolání nebo implementace obousměrné operaci, jsou podobné kroků inicializace korelace a jsou popsané v této části.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Použití v obousměrný operaci s přijímat nebo SendReply korelace  
 A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár slouží k implementaci obousměrný operace ve službě pracovního postupu. Modul runtime používá k zajištění, že je správný volajícího odeslaných odpovědi korelace požadavku a odpovědi. Pokud je pracovní postup je hostováno pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, což je případ pro pracovní postup služby a pak stačí výchozí korelace inicializace. V tomto scénáři <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pracovní postup používá pár a není nutná žádná konfigurace konkrétní korelace.  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Explicitně inicializace korelace požadavku a odpovědi  
 Pokud jsou jiné obousměrný operace paralelně, pak korelace musí být explicitně nakonfigurovaný. To lze provést zadáním <xref:System.ServiceModel.Activities.CorrelationHandle> a <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, nebo tím, že <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> uvnitř <xref:System.ServiceModel.Activities.CorrelationScope>. V tomto příkladu je nakonfigurované korelace požadavku a odpovědi na <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár.  
  
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
  
 Namísto výslovně konfigurace korelace, <xref:System.ServiceModel.Activities.CorrelationScope> lze aktivity. <xref:System.ServiceModel.Activities.CorrelationScope> poskytuje implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> pro zasílání zpráv aktivity, které obsahuje. V tomto příkladu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> je součástí páru <xref:System.ServiceModel.Activities.CorrelationScope>. Není nutná žádná konfigurace explicitní korelace.  
  
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
  
 Pokud jsou vyžadovány další korelací, pak se dá nakonfigurovat pomocí <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> vlastnost příslušné aktivity zasílání zpráv pomocí požadovanou `CorrelationInitializer` typy.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Použití v obousměrný operaci s odeslání nebo ReceiveReply korelace  
 Při <xref:System.ServiceModel.Activities.Receive> aktivity lze použít pouze v pracovním postupu služba hostovaná společností <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár mohou být používány žádné pracovní postup, který musí vyvolání metody webové služby. Pokud hostovaný pracovní postup pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost> pak použije korelace výchozí popisuje v předchozí části, ale pokud ne, pak korelace musí být nakonfigurovaný buď explicitně pomocí požadovanou <xref:System.ServiceModel.Activities.CorrelationInitializer> a <xref:System.ServiceModel.Activities.CorrelationHandle>, nebo pomocí implicitní zpracování správu <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Při použití **přidat odkaz na službu** službu s obousměrný operacemi, jsou generovány aktivity tohoto wrap <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> explicitně spárujte aktivitu interně korelace požadavku/odpovědi zadat.
