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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e21c6eb15e305584b86c35f8a3cb4a7e549b7cae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="context-exchange-correlation"></a><span data-ttu-id="a3386-102">Korelace kontextové výměny</span><span class="sxs-lookup"><span data-stu-id="a3386-102">Context Exchange Correlation</span></span>
<span data-ttu-id="a3386-103">Korelace kontextu je založené na mechanismu exchange kontext, který je popsané v [Exchange kontextu .NET – specifikace protokolu](http://go.microsoft.com/fwlink/?LinkId=166059).</span><span class="sxs-lookup"><span data-stu-id="a3386-103">Context correlation is based on the context exchange mechanism described in the [.NET Context Exchange Protocol Specification](http://go.microsoft.com/fwlink/?LinkId=166059).</span></span> <span data-ttu-id="a3386-104">Korelace kontextové používá dobře známé kontextu hlavičky nebo soubor cookie k úpravě zprávy na správnou instanci.</span><span class="sxs-lookup"><span data-stu-id="a3386-104">Context correlation uses a well-known context header or cookie to relate messages to the correct instance.</span></span> <span data-ttu-id="a3386-105">Použít korelace kontextu, na základě kontextu vazby, jako <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, nebo <xref:System.ServiceModel.NetTcpContextBinding> na zadaný pro koncový bod se musí použít <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a3386-105">To use context correlation, a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, or <xref:System.ServiceModel.NetTcpContextBinding> must be used on the endpoint provided to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="a3386-106">Toto téma vysvětluje, jak používat kontextu korelace aktivitách zasílání zpráv ve službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a3386-106">This topic explains how to use context correlation with messaging activities in a workflow service.</span></span>  
  
## <a name="using-context-correlation"></a><span data-ttu-id="a3386-107">Pomocí kontextu korelace</span><span class="sxs-lookup"><span data-stu-id="a3386-107">Using Context Correlation</span></span>  
 <span data-ttu-id="a3386-108">Korelace kontextové se používá při klienta, musí opakovaná volání do služby pracovního postupu a služba je hostovaná pomocí jedné z kontextu vazby.</span><span class="sxs-lookup"><span data-stu-id="a3386-108">Context correlation is used when a client must make repeated calls into a workflow service and the service is hosted using one of the context bindings.</span></span> <span data-ttu-id="a3386-109">Tento typ korelace se inicializuje pomocí <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár v rámci služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a3386-109">This type of correlation is initialized by a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair in the workflow service.</span></span> <span data-ttu-id="a3386-110">Kontext budou odeslána zpět do klienta společně s odpověď, a potom klient připojí tento kontext na následující volání do služby.</span><span class="sxs-lookup"><span data-stu-id="a3386-110">The context is sent back to the client together with the reply, and then the client attaches this context on subsequent calls to the service.</span></span>  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a><span data-ttu-id="a3386-111">Konfigurace korelace kontextu v služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a3386-111">Configuring Context Correlation in a Workflow Service</span></span>  
 <span data-ttu-id="a3386-112">Korelace kontextové se inicializuje pomocí <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> přidružená <xref:System.ServiceModel.Activities.SendReply> aktivity, která reaguje na počáteční příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="a3386-112">Context correlation is initialized by using a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> that is associated with the <xref:System.ServiceModel.Activities.SendReply> activity that replies to the initial incoming message.</span></span> <span data-ttu-id="a3386-113">V následujícím příkladu <xref:System.ServiceModel.Activities.SendReply> je nakonfigurovaný k chybě při inicializaci korelace kontextu.</span><span class="sxs-lookup"><span data-stu-id="a3386-113">In the following example, the <xref:System.ServiceModel.Activities.SendReply> is configured to initialize a context correlation.</span></span>  
  
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
>  <span data-ttu-id="a3386-114">V tomto příkladu jsou ve skutečnosti korelace používá dva typy: korelace kontextu a korelace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a3386-114">In this example, there are actually two types of correlation being used: context correlation and request-reply correlation.</span></span> <span data-ttu-id="a3386-115">Korelace kontextové se používá, aby volání od klientů, směrovaly na správnou instanci.</span><span class="sxs-lookup"><span data-stu-id="a3386-115">The context correlation is used so that calls from clients are routed to the correct instance.</span></span> <span data-ttu-id="a3386-116">Korelace požadavku a odpovědi je používán <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity společně k implementaci obousměrný operaci modelovány pomocí tyto aktivity.</span><span class="sxs-lookup"><span data-stu-id="a3386-116">The request-reply correlation is used by the <xref:System.ServiceModel.Activities.Receive> and the <xref:System.ServiceModel.Activities.SendReply> activities together to implement the two-way operation modeled by these activities.</span></span> <span data-ttu-id="a3386-117">V tomto příkladu je explicitně nakonfigurovaný jenom korelace kontextu a <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár používá výchozí korelace požadavku a odpovědi, které poskytuje implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> správu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a3386-117">In this example, only the context correlation is explicitly configured, and the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is using the default request-reply correlation that is provided by the implicit <xref:System.ServiceModel.Activities.CorrelationHandle> management of <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="a3386-118">Při použití **ReceiveAndSendReply** šablony aktivit v návrháře, korelace požadavku a odpovědi pracovního postupu explicitně nastaven.</span><span class="sxs-lookup"><span data-stu-id="a3386-118">When using the **ReceiveAndSendReply** activity template in the workflow designer, request-reply correlation is explicitly configured.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a3386-119">korelace požadavku a odpovědi a správa popisovačů implicitní korelace, najdete v části [požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) a [korelace – přehled](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a3386-119"> request-reply correlation and implicit correlation handle management, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) and [Correlation Overview](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a3386-120">**ReceiveAndSendReply** šabloně aktivit, najdete v části [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span><span class="sxs-lookup"><span data-stu-id="a3386-120"> the **ReceiveAndSendReply** activity template, see [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span></span>  
  
 <span data-ttu-id="a3386-121">Následné <xref:System.ServiceModel.Activities.Receive> aktivit ve službě pracovní postup může odkazovat <xref:System.ServiceModel.Activities.CorrelationHandle> který byl inicializován nástrojem <xref:System.ServiceModel.Activities.SendReply> v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3386-121">Subsequent <xref:System.ServiceModel.Activities.Receive> activities in the workflow service can reference the <xref:System.ServiceModel.Activities.CorrelationHandle> that was initialized by the <xref:System.ServiceModel.Activities.SendReply> in the previous example.</span></span>  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 <span data-ttu-id="a3386-122">Koncový bod je nakonfigurovaný na <xref:System.ServiceModel.Activities.WorkflowServiceHost> používat, na základě kontextu vazby, jako například <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="a3386-122">The endpoint is then configured on the <xref:System.ServiceModel.Activities.WorkflowServiceHost> to use a context-based binding, such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span>  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a><span data-ttu-id="a3386-123">Konfigurace korelace kontextu v klientovi pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a3386-123">Configuring Context Correlation in a Workflow Client</span></span>  
 <span data-ttu-id="a3386-124">Když se klient nachází jiného pracovního postupu, kontext korelace musí být nakonfigurované na klientovi i.</span><span class="sxs-lookup"><span data-stu-id="a3386-124">When the client is another workflow, context correlation must be configured on the client as well.</span></span> <span data-ttu-id="a3386-125">Pro pracovní postup klienta <xref:System.ServiceModel.Activities.ReceiveReply> z <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vytvoří počáteční volání služby pracovního postupu musí být nakonfigurované <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="a3386-125">On the client workflow, the <xref:System.ServiceModel.Activities.ReceiveReply> of the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that makes the initial call to the workflow service must be configured with a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span></span>  
  
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
  
 <span data-ttu-id="a3386-126">Po korelaci inicializovaného, následných <xref:System.ServiceModel.Activities.Send> aktivity mohou používat <xref:System.ServiceModel.Activities.CorrelationHandle> volat metody na stejnou instanci služby.</span><span class="sxs-lookup"><span data-stu-id="a3386-126">After the correlation is initialized, subsequent <xref:System.ServiceModel.Activities.Send> activities can use the <xref:System.ServiceModel.Activities.CorrelationHandle> to invoke methods on the same service instance.</span></span>  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 <span data-ttu-id="a3386-127">Všimněte si, že se v těchto příkladech, korelace kontextu explicitně nakonfigurovaný.</span><span class="sxs-lookup"><span data-stu-id="a3386-127">Note that in these examples, the context correlation has been explicitly configured.</span></span> <span data-ttu-id="a3386-128">Pokud pracovní postup klienta není hostují taky v <xref:System.ServiceModel.Activities.WorkflowServiceHost>, pak korelace musí být explicitně nakonfigurovaný, pokud aktivity jsou obsaženy v rámci <xref:System.ServiceModel.Activities.CorrelationScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="a3386-128">If the client workflow is not also hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, then correlation must be explicitly configured, unless the activities are contained within a <xref:System.ServiceModel.Activities.CorrelationScope> activity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a3386-129">korelace kontextu, najdete v článku [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) ukázka.</span><span class="sxs-lookup"><span data-stu-id="a3386-129"> context correlation, see the [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) sample.</span></span>  
  
 <span data-ttu-id="a3386-130">Pokud klienta, která volá služby pracovního postupu není pracovního postupu, poté ji opakovaných volání uskutečnit tak dlouho, dokud ji explicitně předá zpět kontext, který je vrácen z prvního volání služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a3386-130">If the client that is making calls to the workflow service is not a workflow, then it can still make repeated calls as long as it explicitly passes back the context that is returned from the first call to the workflow service.</span></span> <span data-ttu-id="a3386-131">Proxy vygenerovala přidáním odkazu na službu v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ukládat a předat ve výchozím nastavení tento kontext.</span><span class="sxs-lookup"><span data-stu-id="a3386-131">Proxies generated by adding a service reference in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] store and pass this context by default.</span></span>
