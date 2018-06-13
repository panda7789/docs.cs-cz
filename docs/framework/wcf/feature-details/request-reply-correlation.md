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
# <a name="request-reply-correlation"></a><span data-ttu-id="e40ed-102">Korelace požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="e40ed-102">Request-Reply Correlation</span></span>
<span data-ttu-id="e40ed-103">Korelace požadavku a odpovědi se používá s <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár implementovat obousměrný operace ve službě pracovního postupu a s <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vyvolá obousměrný operaci v jiný Web Služba.</span><span class="sxs-lookup"><span data-stu-id="e40ed-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="e40ed-104">Při vyvolání obousměrný operace ve službě WCF, služba může být buď tradiční imperativní založené na kódu služby Windows Communication Foundation (WCF), nebo může být služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="e40ed-104">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based Windows Communication Foundation (WCF) service or it can be a workflow service.</span></span> <span data-ttu-id="e40ed-105">Použít korelace požadavku a odpovědi vazba obousměrná musí být použita, jako například <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="e40ed-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="e40ed-106">Ať už vyvolání nebo implementace obousměrné operaci, jsou podobné kroků inicializace korelace a jsou popsané v této části.</span><span class="sxs-lookup"><span data-stu-id="e40ed-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="e40ed-107">Použití v obousměrný operaci s přijímat nebo SendReply korelace</span><span class="sxs-lookup"><span data-stu-id="e40ed-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="e40ed-108">A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár slouží k implementaci obousměrný operace ve službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e40ed-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="e40ed-109">Modul runtime používá k zajištění, že je správný volajícího odeslaných odpovědi korelace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e40ed-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="e40ed-110">Pokud je pracovní postup je hostováno pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, což je případ pro pracovní postup služby a pak stačí výchozí korelace inicializace.</span><span class="sxs-lookup"><span data-stu-id="e40ed-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="e40ed-111">V tomto scénáři <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pracovní postup používá pár a není nutná žádná konfigurace konkrétní korelace.</span><span class="sxs-lookup"><span data-stu-id="e40ed-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="e40ed-112">Explicitně inicializace korelace požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="e40ed-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="e40ed-113">Pokud jsou jiné obousměrný operace paralelně, pak korelace musí být explicitně nakonfigurovaný.</span><span class="sxs-lookup"><span data-stu-id="e40ed-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="e40ed-114">To lze provést zadáním <xref:System.ServiceModel.Activities.CorrelationHandle> a <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, nebo tím, že <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> uvnitř <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="e40ed-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="e40ed-115">V tomto příkladu je nakonfigurované korelace požadavku a odpovědi na <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár.</span><span class="sxs-lookup"><span data-stu-id="e40ed-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
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
  
 <span data-ttu-id="e40ed-116">Namísto výslovně konfigurace korelace, <xref:System.ServiceModel.Activities.CorrelationScope> lze aktivity.</span><span class="sxs-lookup"><span data-stu-id="e40ed-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="e40ed-117"><xref:System.ServiceModel.Activities.CorrelationScope> poskytuje implicitní <xref:System.ServiceModel.Activities.CorrelationHandle> pro zasílání zpráv aktivity, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="e40ed-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="e40ed-118">V tomto příkladu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> je součástí páru <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="e40ed-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="e40ed-119">Není nutná žádná konfigurace explicitní korelace.</span><span class="sxs-lookup"><span data-stu-id="e40ed-119">No explicit correlation configuration is required.</span></span>  
  
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
  
 <span data-ttu-id="e40ed-120">Pokud jsou vyžadovány další korelací, pak se dá nakonfigurovat pomocí <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> vlastnost příslušné aktivity zasílání zpráv pomocí požadovanou `CorrelationInitializer` typy.</span><span class="sxs-lookup"><span data-stu-id="e40ed-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="e40ed-121">Použití v obousměrný operaci s odeslání nebo ReceiveReply korelace</span><span class="sxs-lookup"><span data-stu-id="e40ed-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="e40ed-122">Při <xref:System.ServiceModel.Activities.Receive> aktivity lze použít pouze v pracovním postupu služba hostovaná společností <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár mohou být používány žádné pracovní postup, který musí vyvolání metody webové služby.</span><span class="sxs-lookup"><span data-stu-id="e40ed-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="e40ed-123">Pokud hostovaný pracovní postup pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost> pak použije korelace výchozí popisuje v předchozí části, ale pokud ne, pak korelace musí být nakonfigurovaný buď explicitně pomocí požadovanou <xref:System.ServiceModel.Activities.CorrelationInitializer> a <xref:System.ServiceModel.Activities.CorrelationHandle>, nebo pomocí implicitní zpracování správu <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="e40ed-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="e40ed-124">Při použití **přidat odkaz na službu** službu s obousměrný operacemi, jsou generovány aktivity tohoto wrap <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> explicitně spárujte aktivitu interně korelace požadavku/odpovědi zadat.</span><span class="sxs-lookup"><span data-stu-id="e40ed-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
