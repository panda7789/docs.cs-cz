---
title: Korelace požadavku a odpovědi
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991130"
---
# <a name="request-reply-correlation"></a>Korelace požadavku a odpovědi
Korelace požadavku a odpovědi se používá s <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár pro implementaci obousměrný operace ve službě pracovních postupů a se <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vyvolá obousměrný operaci na jiném webu Služba. Při vyvolání obousměrný operace ve službě WCF, služba může být buď tradiční imperativní založený na kódu služby Windows Communication Foundation (WCF), nebo může být služba pracovního postupu. Použití korelace požadavku a odpovědi Obousměrná vazba musí být použita, jako například <xref:System.ServiceModel.BasicHttpBinding>. Ať už vyvolání nebo implementace obousměrné operace, kroků inicializace korelace jsou podobné a jsou popsané v této části.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Pomocí korelace v obousměrný operaci s příjem nebo odeslání odpovědi SendReply  
 A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár slouží k implementaci obousměrný operace ve službě pracovních postupů. Modul runtime používá k zajištění, že odpověď je odeslána volajícímu správné korelace požadavku a odpovědi. Když pracovní postup je hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, které se v případě služby pracovního postupu a pak stačí výchozí inicializace korelace. V tomto scénáři <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pracovní postup používá pár a není nutná žádná konfigurace konkrétní korelace.  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Explicitní inicializace korelace požadavku a odpovědi  
 Pokud jsou ostatní obousměrný operace paralelně, pak korelace musí být explicitně nakonfigurovaný. To můžete udělat tak, že zadáte <xref:System.ServiceModel.Activities.CorrelationHandle> a <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, nebo tak, že <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> uvnitř <xref:System.ServiceModel.Activities.CorrelationScope>. V tomto příkladu je hodnocen korelace požadavku a odpovědi <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár.  
  
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
  
 Místo explicitně konfigurace korelace, <xref:System.ServiceModel.Activities.CorrelationScope> aktivita se dá použít. <xref:System.ServiceModel.Activities.CorrelationScope> poskytuje implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> pro zasílání zpráv aktivity, které obsahuje. V tomto příkladu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> dvojice je obsaženo uvnitř <xref:System.ServiceModel.Activities.CorrelationScope>. Není nutná žádná konfigurace explicitní korelace.  
  
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
  
 Pokud požadujete dalších korelacích, pak se dají konfigurovat pomocí <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> vlastnost odpovídajících aktivit zasílání zpráv pomocí požadovaný `CorrelationInitializer` typy.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Pomocí korelace v obousměrný operaci s odeslat/ReceiveReply  
 Zatímco <xref:System.ServiceModel.Activities.Receive> aktivita se dá použít jenom v hostované službě pracovního postupu <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár lze použít v jakékoli pracovní postup, který musí vyvolat metodu na webovou službu. Pokud pracovní postup je hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost> pak použije výchozí korelace je popsáno v předchozí části, ale pokud ne, pak korelace musí konfigurovat buď explicitně pomocí požadovaný <xref:System.ServiceModel.Activities.CorrelationInitializer> a <xref:System.ServiceModel.Activities.CorrelationHandle>, nebo s použitím implicitního správu <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Při použití **přidat odkaz na službu** službu s operacemi obousměrný, vygenerují se aktivity tohoto zalamování řádků <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> explicitně spárovat aktivitu interně pomocí korelace požadavku/odpovědi zadat.
