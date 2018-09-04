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
# <a name="context-exchange-correlation"></a><span data-ttu-id="a35b2-102">Korelace kontextové výměny</span><span class="sxs-lookup"><span data-stu-id="a35b2-102">Context Exchange Correlation</span></span>
<span data-ttu-id="a35b2-103">Korelace kontextové je založena na mechanismu exchange kontext je popsáno v [specifikace protokolu serveru Exchange kontextu .NET](https://go.microsoft.com/fwlink/?LinkId=166059).</span><span class="sxs-lookup"><span data-stu-id="a35b2-103">Context correlation is based on the context exchange mechanism described in the [.NET Context Exchange Protocol Specification](https://go.microsoft.com/fwlink/?LinkId=166059).</span></span> <span data-ttu-id="a35b2-104">Korelace kontextové pomocí hlavičku známého kontextu nebo soubor cookie týkají zprávy správné instanci.</span><span class="sxs-lookup"><span data-stu-id="a35b2-104">Context correlation uses a well-known context header or cookie to relate messages to the correct instance.</span></span> <span data-ttu-id="a35b2-105">Použití kontextu korelace, základě kontextu vazby, jako <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, nebo <xref:System.ServiceModel.NetTcpContextBinding> musí využívat v koncovém bodě k dispozici na <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a35b2-105">To use context correlation, a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, or <xref:System.ServiceModel.NetTcpContextBinding> must be used on the endpoint provided to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="a35b2-106">Toto téma vysvětluje, jak pomocí aktivit zasílání zpráv ve službě pracovních postupů korelace kontextu.</span><span class="sxs-lookup"><span data-stu-id="a35b2-106">This topic explains how to use context correlation with messaging activities in a workflow service.</span></span>  
  
## <a name="using-context-correlation"></a><span data-ttu-id="a35b2-107">Pomocí kontextu korelace</span><span class="sxs-lookup"><span data-stu-id="a35b2-107">Using Context Correlation</span></span>  
 <span data-ttu-id="a35b2-108">Korelace kontextové se používá, když klient musí provést opakované volání do služby pracovních postupů a služba je hostována pomocí jedné z kontextu vazby.</span><span class="sxs-lookup"><span data-stu-id="a35b2-108">Context correlation is used when a client must make repeated calls into a workflow service and the service is hosted using one of the context bindings.</span></span> <span data-ttu-id="a35b2-109">Tento typ korelace je inicializován pomocí <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a35b2-109">This type of correlation is initialized by a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair in the workflow service.</span></span> <span data-ttu-id="a35b2-110">Kontext budou odeslána zpět do klienta společně s odpověď, a pak klient připojí tento kontext v následných voláních na službu.</span><span class="sxs-lookup"><span data-stu-id="a35b2-110">The context is sent back to the client together with the reply, and then the client attaches this context on subsequent calls to the service.</span></span>  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a><span data-ttu-id="a35b2-111">Konfigurace korelace kontextové ve službě pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a35b2-111">Configuring Context Correlation in a Workflow Service</span></span>  
 <span data-ttu-id="a35b2-112">Korelace kontextové je inicializována pomocí <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> , který je přidružený <xref:System.ServiceModel.Activities.SendReply> aktivitu, která reaguje na počáteční příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="a35b2-112">Context correlation is initialized by using a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> that is associated with the <xref:System.ServiceModel.Activities.SendReply> activity that replies to the initial incoming message.</span></span> <span data-ttu-id="a35b2-113">V následujícím příkladu <xref:System.ServiceModel.Activities.SendReply> konfigurován tak, aby incializovat korelaci kontextu.</span><span class="sxs-lookup"><span data-stu-id="a35b2-113">In the following example, the <xref:System.ServiceModel.Activities.SendReply> is configured to initialize a context correlation.</span></span>  
  
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
>  <span data-ttu-id="a35b2-114">V tomto příkladu jsou ve skutečnosti korelace používá dva typy: korelační kontextu a korelace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a35b2-114">In this example, there are actually two types of correlation being used: context correlation and request-reply correlation.</span></span> <span data-ttu-id="a35b2-115">Korelace kontextu se používá tak, aby volání od klientů jsou směrovány na správné instanci.</span><span class="sxs-lookup"><span data-stu-id="a35b2-115">The context correlation is used so that calls from clients are routed to the correct instance.</span></span> <span data-ttu-id="a35b2-116">Používá korelace požadavku a odpovědi <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity společně k implementaci obousměrný operace modelovány pomocí těchto činností.</span><span class="sxs-lookup"><span data-stu-id="a35b2-116">The request-reply correlation is used by the <xref:System.ServiceModel.Activities.Receive> and the <xref:System.ServiceModel.Activities.SendReply> activities together to implement the two-way operation modeled by these activities.</span></span> <span data-ttu-id="a35b2-117">V tomto příkladu je explicitně nakonfigurované pouze korelace kontextu a <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> dvojici využívá korelaci výchozí požadavek odpověď, která je poskytována implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> správu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a35b2-117">In this example, only the context correlation is explicitly configured, and the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is using the default request-reply correlation that is provided by the implicit <xref:System.ServiceModel.Activities.CorrelationHandle> management of <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="a35b2-118">Při použití **ReceiveAndSendReply** šablona aktivity do pracovního postupu návrháře, korelace požadavku a odpovědi explicitně nastaven.</span><span class="sxs-lookup"><span data-stu-id="a35b2-118">When using the **ReceiveAndSendReply** activity template in the workflow designer, request-reply correlation is explicitly configured.</span></span> <span data-ttu-id="a35b2-119">Další informace o korelace požadavku a odpovědi a správa popisovačů implicitní korelace, najdete v části [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) a [korelace – přehled](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a35b2-119">For more information about request-reply correlation and implicit correlation handle management, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) and [Correlation Overview](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span></span> <span data-ttu-id="a35b2-120">Další informace o **ReceiveAndSendReply** šablony aktivit najdete v článku [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span><span class="sxs-lookup"><span data-stu-id="a35b2-120">For more information about the **ReceiveAndSendReply** activity template, see [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span></span>  
  
 <span data-ttu-id="a35b2-121">Následné <xref:System.ServiceModel.Activities.Receive> aktivity ve službě pracovního postupu můžete odkazovat <xref:System.ServiceModel.Activities.CorrelationHandle> , který byl inicializován pomocí <xref:System.ServiceModel.Activities.SendReply> v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a35b2-121">Subsequent <xref:System.ServiceModel.Activities.Receive> activities in the workflow service can reference the <xref:System.ServiceModel.Activities.CorrelationHandle> that was initialized by the <xref:System.ServiceModel.Activities.SendReply> in the previous example.</span></span>  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 <span data-ttu-id="a35b2-122">Koncový bod je nakonfigurovaný na <xref:System.ServiceModel.Activities.WorkflowServiceHost> použít, na základě kontextu vazby, jako například <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="a35b2-122">The endpoint is then configured on the <xref:System.ServiceModel.Activities.WorkflowServiceHost> to use a context-based binding, such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span>  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a><span data-ttu-id="a35b2-123">Konfigurace korelace kontextu v klientovi pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a35b2-123">Configuring Context Correlation in a Workflow Client</span></span>  
 <span data-ttu-id="a35b2-124">Nacházející se jiný pracovní postup, korelace kontextu musí být nakonfigurovaná na straně klienta i.</span><span class="sxs-lookup"><span data-stu-id="a35b2-124">When the client is another workflow, context correlation must be configured on the client as well.</span></span> <span data-ttu-id="a35b2-125">V pracovním postupu klienta <xref:System.ServiceModel.Activities.ReceiveReply> z <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vytvoří počáteční volání služby pracovního postupu musí mít nakonfigurovanou <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="a35b2-125">On the client workflow, the <xref:System.ServiceModel.Activities.ReceiveReply> of the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that makes the initial call to the workflow service must be configured with a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span></span>  
  
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
  
 <span data-ttu-id="a35b2-126">Po korelace je inicializovaný, následné <xref:System.ServiceModel.Activities.Send> aktivity mohou používat <xref:System.ServiceModel.Activities.CorrelationHandle> volat metody ve stejné instanci služby.</span><span class="sxs-lookup"><span data-stu-id="a35b2-126">After the correlation is initialized, subsequent <xref:System.ServiceModel.Activities.Send> activities can use the <xref:System.ServiceModel.Activities.CorrelationHandle> to invoke methods on the same service instance.</span></span>  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 <span data-ttu-id="a35b2-127">Všimněte si, že v těchto příkladech, kontext korelace není explicitně nakonfigurovaná.</span><span class="sxs-lookup"><span data-stu-id="a35b2-127">Note that in these examples, the context correlation has been explicitly configured.</span></span> <span data-ttu-id="a35b2-128">Pokud klienta pracovní postup také nehostovala ve <xref:System.ServiceModel.Activities.WorkflowServiceHost>, korelace musí být explicitně nakonfigurován, pokud činnosti, které jsou obsaženy v rámci <xref:System.ServiceModel.Activities.CorrelationScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="a35b2-128">If the client workflow is not also hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, then correlation must be explicitly configured, unless the activities are contained within a <xref:System.ServiceModel.Activities.CorrelationScope> activity.</span></span> <span data-ttu-id="a35b2-129">Další informace o kontextu korelace, najdete v článku [NetContextExchangeCorrelation](https://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) vzorku.</span><span class="sxs-lookup"><span data-stu-id="a35b2-129">For more information about context correlation, see the [NetContextExchangeCorrelation](https://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) sample.</span></span>  
  
 <span data-ttu-id="a35b2-130">Jestli klient, který provádí volání služby pracovního postupu není pracovního postupu, pak může i nadále provádět opakovaná volání tak dlouho, dokud ho explicitně předá zpět kontext, který je vrácen z prvního volání služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a35b2-130">If the client that is making calls to the workflow service is not a workflow, then it can still make repeated calls as long as it explicitly passes back the context that is returned from the first call to the workflow service.</span></span> <span data-ttu-id="a35b2-131">Proxy servery vygenerovat tak, že přidáte odkaz na službu v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ukládat a předávat kontext ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="a35b2-131">Proxies generated by adding a service reference in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] store and pass this context by default.</span></span>
