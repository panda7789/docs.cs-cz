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
# <a name="request-reply-correlation"></a><span data-ttu-id="b099e-102">Korelace požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="b099e-102">Request-Reply Correlation</span></span>
<span data-ttu-id="b099e-103">Korelace požadavku a odpovědi <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> se používá s dvojicí k implementaci obousměrné operace ve službě pracovního postupu a s <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> dvojicí, která vyvolá obousměrnou operaci v jiné webové službě.</span><span class="sxs-lookup"><span data-stu-id="b099e-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="b099e-104">Při vyvolání obousměrné operace ve službě WCF, služba může být buď tradiční imperativní kód založený Windows Communication Foundation (WCF) služby nebo může být služba pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b099e-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="b099e-105">Chcete-li použít korelaci požadavek odpověď obousměrné <xref:System.ServiceModel.BasicHttpBinding>vazby musí být použity, například .</span><span class="sxs-lookup"><span data-stu-id="b099e-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="b099e-106">Ať už vyvoláte nebo implementujete obousměrnou operaci, kroky inicializace korelace jsou podobné a jsou popsány v této části.</span><span class="sxs-lookup"><span data-stu-id="b099e-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="b099e-107">Použití korelace v obousměrné operaci s receive/SendReply</span><span class="sxs-lookup"><span data-stu-id="b099e-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="b099e-108"><xref:System.ServiceModel.Activities.Receive> / Dvojice <xref:System.ServiceModel.Activities.SendReply> se používá k implementaci obousměrné operace ve službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b099e-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="b099e-109">Runtime používá korelace požadavek odpověď k zajištění, že odpověď je odeslána správnému volajícímu.</span><span class="sxs-lookup"><span data-stu-id="b099e-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="b099e-110">Pokud je pracovní postup <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostován pomocí , což je případ služeb pracovního postupu, je výchozí inicializace korelace dostatečná.</span><span class="sxs-lookup"><span data-stu-id="b099e-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="b099e-111">V tomto scénáři <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> je dvojice používá pracovní postup a není vyžadována žádná konkrétní konfigurace korelace.</span><span class="sxs-lookup"><span data-stu-id="b099e-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="b099e-112">Explicitně inicializovat korelaci požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="b099e-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="b099e-113">Pokud jsou souběžně další obousměrné operace, měla by být korelace explicitně nakonfigurována.</span><span class="sxs-lookup"><span data-stu-id="b099e-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="b099e-114">To lze provést zadáním <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>a , nebo <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> umístěním <xref:System.ServiceModel.Activities.CorrelationScope>vnitřku .</span><span class="sxs-lookup"><span data-stu-id="b099e-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="b099e-115">V tomto příkladu je na <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> páru konfigurována korelace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b099e-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
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
  
 <span data-ttu-id="b099e-116">Namísto explicitní konfigurace korelace <xref:System.ServiceModel.Activities.CorrelationScope> lze použít aktivitu.</span><span class="sxs-lookup"><span data-stu-id="b099e-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="b099e-117"><xref:System.ServiceModel.Activities.CorrelationScope>poskytuje implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> zasílání zpráv aktivity, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="b099e-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="b099e-118">V tomto příkladu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> je pár <xref:System.ServiceModel.Activities.CorrelationScope>obsažen uvnitř .</span><span class="sxs-lookup"><span data-stu-id="b099e-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="b099e-119">Není vyžadována žádná explicitní konfigurace korelace.</span><span class="sxs-lookup"><span data-stu-id="b099e-119">No explicit correlation configuration is required.</span></span>  
  
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
  
 <span data-ttu-id="b099e-120">Pokud jsou požadovány další korelace pak <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> mohou být nakonfigurovány pomocí `CorrelationInitializer` vlastnosti příslušné zasílání zpráv aktivity pomocí požadovaných typů.</span><span class="sxs-lookup"><span data-stu-id="b099e-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="b099e-121">Použití korelace v obousměrné operaci s odesíláním a přijímáním odpovědi</span><span class="sxs-lookup"><span data-stu-id="b099e-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="b099e-122">Zatímco <xref:System.ServiceModel.Activities.Receive> aktivitu lze použít pouze ve službě <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> pracovního <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> postupu hostované aplikací a dvojici lze použít v libovolném pracovním postupu, který musí vyvolat metodu webové služby.</span><span class="sxs-lookup"><span data-stu-id="b099e-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="b099e-123">Pokud je pracovní postup <xref:System.ServiceModel.Activities.WorkflowServiceHost> hostován pomocí výchozí korelace popsané v předchozí části, ale pokud ne, <xref:System.ServiceModel.Activities.CorrelationInitializer> <xref:System.ServiceModel.Activities.CorrelationHandle>musí být korelace nakonfigurována <xref:System.ServiceModel.Activities.CorrelationScope>buď explicitně pomocí požadovaného a , nebo pomocí správy implicitního popisovače .</span><span class="sxs-lookup"><span data-stu-id="b099e-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="b099e-124">Při použití **přidat odkaz na službu** s obousměrné operace, <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> jsou generovány aktivity, které zabalit pár aktivity interně s Požadavek/Odpověď korelace explicitně zadána.</span><span class="sxs-lookup"><span data-stu-id="b099e-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
