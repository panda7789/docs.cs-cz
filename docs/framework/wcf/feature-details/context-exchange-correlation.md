---
title: "Korelace kontextové výměny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ab311974b1fe8cbc2707ee0818806d6264a1573
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="context-exchange-correlation"></a>Korelace kontextové výměny
Korelace kontextu je založené na mechanismu exchange kontext, který je popsané v [Exchange kontextu .NET – specifikace protokolu](http://go.microsoft.com/fwlink/?LinkId=166059). Korelace kontextové používá dobře známé kontextu hlavičky nebo soubor cookie k úpravě zprávy na správnou instanci. Použít korelace kontextu, na základě kontextu vazby, jako <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, nebo <xref:System.ServiceModel.NetTcpContextBinding> na zadaný pro koncový bod se musí použít <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Toto téma vysvětluje, jak používat kontextu korelace aktivitách zasílání zpráv ve službě pracovního postupu.  
  
## <a name="using-context-correlation"></a>Pomocí kontextu korelace  
 Korelace kontextové se používá při klienta, musí opakovaná volání do služby pracovního postupu a služba je hostovaná pomocí jedné z kontextu vazby. Tento typ korelace se inicializuje pomocí <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár v rámci služby pracovního postupu. Kontext budou odeslána zpět do klienta společně s odpověď, a potom klient připojí tento kontext na následující volání do služby.  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a>Konfigurace korelace kontextu v služby pracovních postupů  
 Korelace kontextové se inicializuje pomocí <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> přidružená <xref:System.ServiceModel.Activities.SendReply> aktivity, která reaguje na počáteční příchozí zprávy. V následujícím příkladu <xref:System.ServiceModel.Activities.SendReply> je nakonfigurovaný k chybě při inicializaci korelace kontextu.  
  
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
>  V tomto příkladu jsou ve skutečnosti korelace používá dva typy: korelace kontextu a korelace požadavku a odpovědi. Korelace kontextové se používá, aby volání od klientů, směrovaly na správnou instanci. Korelace požadavku a odpovědi je používán <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity společně k implementaci obousměrný operaci modelovány pomocí tyto aktivity. V tomto příkladu je explicitně nakonfigurovaný jenom korelace kontextu a <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár používá výchozí korelace požadavku a odpovědi, které poskytuje implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> správu <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Při použití **ReceiveAndSendReply** šablony aktivit v návrháře, korelace požadavku a odpovědi pracovního postupu explicitně nastaven. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]korelace požadavku a odpovědi a správa popisovačů implicitní korelace, najdete v části [požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) a [korelace – přehled](../../../../docs/framework/wcf/feature-details/correlation-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]**ReceiveAndSendReply** šabloně aktivit, najdete v části [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).  
  
 Následné <xref:System.ServiceModel.Activities.Receive> aktivit ve službě pracovní postup může odkazovat <xref:System.ServiceModel.Activities.CorrelationHandle> který byl inicializován nástrojem <xref:System.ServiceModel.Activities.SendReply> v předchozím příkladu.  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 Koncový bod je nakonfigurovaný na <xref:System.ServiceModel.Activities.WorkflowServiceHost> používat, na základě kontextu vazby, jako například <xref:System.ServiceModel.BasicHttpContextBinding>.  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a>Konfigurace korelace kontextu v klientovi pracovního postupu  
 Když se klient nachází jiného pracovního postupu, kontext korelace musí být nakonfigurované na klientovi i. Pro pracovní postup klienta <xref:System.ServiceModel.Activities.ReceiveReply> z <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vytvoří počáteční volání služby pracovního postupu musí být nakonfigurované <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.  
  
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
  
 Po korelaci inicializovaného, následných <xref:System.ServiceModel.Activities.Send> aktivity mohou používat <xref:System.ServiceModel.Activities.CorrelationHandle> volat metody na stejnou instanci služby.  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 Všimněte si, že se v těchto příkladech, korelace kontextu explicitně nakonfigurovaný. Pokud pracovní postup klienta není hostují taky v <xref:System.ServiceModel.Activities.WorkflowServiceHost>, pak korelace musí být explicitně nakonfigurovaný, pokud aktivity jsou obsaženy v rámci <xref:System.ServiceModel.Activities.CorrelationScope> aktivity. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]korelace kontextu, najdete v článku [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) ukázka.  
  
 Pokud klienta, která volá služby pracovního postupu není pracovního postupu, poté ji opakovaných volání uskutečnit tak dlouho, dokud ji explicitně předá zpět kontext, který je vrácen z prvního volání služby pracovního postupu. Proxy vygenerovala přidáním odkazu na službu v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ukládat a předat ve výchozím nastavení tento kontext.
