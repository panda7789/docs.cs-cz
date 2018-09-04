---
title: Korelace kontextové výměny
ms.date: 03/30/2017
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
ms.openlocfilehash: d9de111fa08b4a398bba52bc903ea1fec8c7f298
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519729"
---
# <a name="context-exchange-correlation"></a>Korelace kontextové výměny
Korelace kontextové je založena na mechanismu exchange kontext je popsáno v [specifikace protokolu serveru Exchange kontextu .NET](https://go.microsoft.com/fwlink/?LinkId=166059). Korelace kontextové pomocí hlavičku známého kontextu nebo soubor cookie týkají zprávy správné instanci. Použití kontextu korelace, základě kontextu vazby, jako <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, nebo <xref:System.ServiceModel.NetTcpContextBinding> musí využívat v koncovém bodě k dispozici na <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Toto téma vysvětluje, jak pomocí aktivit zasílání zpráv ve službě pracovních postupů korelace kontextu.  
  
## <a name="using-context-correlation"></a>Pomocí kontextu korelace  
 Korelace kontextové se používá, když klient musí provést opakované volání do služby pracovních postupů a služba je hostována pomocí jedné z kontextu vazby. Tento typ korelace je inicializován pomocí <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár služby pracovního postupu. Kontext budou odeslána zpět do klienta společně s odpověď, a pak klient připojí tento kontext v následných voláních na službu.  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a>Konfigurace korelace kontextové ve službě pracovního postupu  
 Korelace kontextové je inicializována pomocí <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> , který je přidružený <xref:System.ServiceModel.Activities.SendReply> aktivitu, která reaguje na počáteční příchozí zprávy. V následujícím příkladu <xref:System.ServiceModel.Activities.SendReply> konfigurován tak, aby incializovat korelaci kontextu.  
  
```csharp  
Variable<string> Item = new Variable<string>();  
Variable<CorrelationHandle> OrderHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IOrderService",  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    CorrelationInitializers =  
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = OrderHandle  
        }  
    }  
};  
```  
  
> [!NOTE]
>  V tomto příkladu jsou ve skutečnosti korelace používá dva typy: korelační kontextu a korelace požadavku a odpovědi. Korelace kontextu se používá tak, aby volání od klientů jsou směrovány na správné instanci. Používá korelace požadavku a odpovědi <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity společně k implementaci obousměrný operace modelovány pomocí těchto činností. V tomto příkladu je explicitně nakonfigurované pouze korelace kontextu a <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> dvojici využívá korelaci výchozí požadavek odpověď, která je poskytována implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> správu <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Při použití **ReceiveAndSendReply** šablona aktivity do pracovního postupu návrháře, korelace požadavku a odpovědi explicitně nastaven. Další informace o korelace požadavku a odpovědi a správa popisovačů implicitní korelace, najdete v části [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) a [korelace – přehled](../../../../docs/framework/wcf/feature-details/correlation-overview.md). Další informace o **ReceiveAndSendReply** šablony aktivit najdete v článku [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).  
  
 Následné <xref:System.ServiceModel.Activities.Receive> aktivity ve službě pracovního postupu můžete odkazovat <xref:System.ServiceModel.Activities.CorrelationHandle> , který byl inicializován pomocí <xref:System.ServiceModel.Activities.SendReply> v předchozím příkladu.  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 Koncový bod je nakonfigurovaný na <xref:System.ServiceModel.Activities.WorkflowServiceHost> použít, na základě kontextu vazby, jako například <xref:System.ServiceModel.BasicHttpContextBinding>.  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a>Konfigurace korelace kontextu v klientovi pracovního postupu  
 Nacházející se jiný pracovní postup, korelace kontextu musí být nakonfigurovaná na straně klienta i. V pracovním postupu klienta <xref:System.ServiceModel.Activities.ReceiveReply> z <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vytvoří počáteční volání služby pracovního postupu musí mít nakonfigurovanou <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.  
  
```csharp  
Variable<CorrelationHandle> cchandle = new Variable<CorrelationHandle>();  
Send request = new Send  
{  
    // Activity configuration omitted.  
};  
  
ReceiveReply reply = new ReceiveReply  
{  
    Request = request,  
    CorrelationInitializers =   
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = cchandle  
        }  
    }  
};  
```  
  
 Po korelace je inicializovaný, následné <xref:System.ServiceModel.Activities.Send> aktivity mohou používat <xref:System.ServiceModel.Activities.CorrelationHandle> volat metody ve stejné instanci služby.  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 Všimněte si, že v těchto příkladech, kontext korelace není explicitně nakonfigurovaná. Pokud klienta pracovní postup také nehostovala ve <xref:System.ServiceModel.Activities.WorkflowServiceHost>, korelace musí být explicitně nakonfigurován, pokud činnosti, které jsou obsaženy v rámci <xref:System.ServiceModel.Activities.CorrelationScope> aktivity. Další informace o kontextu korelace, najdete v článku [NetContextExchangeCorrelation](https://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) vzorku.  
  
 Jestli klient, který provádí volání služby pracovního postupu není pracovního postupu, pak může i nadále provádět opakovaná volání tak dlouho, dokud ho explicitně předá zpět kontext, který je vrácen z prvního volání služby pracovního postupu. Proxy servery vygenerovat tak, že přidáte odkaz na službu v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ukládat a předávat kontext ve výchozím nastavení.
