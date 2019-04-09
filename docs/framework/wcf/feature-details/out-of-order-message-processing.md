---
title: Zpracování zpráv mimo pořadí
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 4e1864b25a4dbe8192cd5c692c75645bebbb92d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141398"
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="5b02e-102">Zpracování zpráv mimo pořadí</span><span class="sxs-lookup"><span data-stu-id="5b02e-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="5b02e-103">Služby pracovních postupů může záviset na zprávy odesílané v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="5b02e-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="5b02e-104">Služba pracovního postupu obsahuje jeden nebo více <xref:System.ServiceModel.Activities.Receive> aktivity a každý <xref:System.ServiceModel.Activities.Receive> aktivity očekává konkrétní zprávu.</span><span class="sxs-lookup"><span data-stu-id="5b02e-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="5b02e-105">Zprávy od klientů může bez záruky doručení konkrétní přenos, zpoždění a proto doručeny v pořadí, které nemusí očekávají služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5b02e-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="5b02e-106">Implementace služby pracovního postupu, který nevyžaduje zprávy odeslané v konkrétní pořadí se obvykle provádí pomocí paralelní aktivity.</span><span class="sxs-lookup"><span data-stu-id="5b02e-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="5b02e-107">Pro složitější aplikační protokol pracovní postup by se mohla stát velmi složité velmi rychle.</span><span class="sxs-lookup"><span data-stu-id="5b02e-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="5b02e-108">Funkce ve Windows Communication Foundation (WCF) zpracování zpráv mimo pořadí umožňuje vytvořit pracovní postup, bez složitosti vnořené paralelní aktivity.</span><span class="sxs-lookup"><span data-stu-id="5b02e-108">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="5b02e-109">Zpracování zpráv mimo pořadí je podporována pouze na kanály, které podporují <xref:System.ServiceModel.Channels.ReceiveContext> jako jsou třeba vazby služby MSMQ WCF.</span><span class="sxs-lookup"><span data-stu-id="5b02e-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="5b02e-110">Povolení zpracování zpráv mimo pořadí</span><span class="sxs-lookup"><span data-stu-id="5b02e-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="5b02e-111">Zpracování zpráv mimo pořadí se povoluje nastavením <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> vlastnost `true` na workflowservice hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5b02e-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="5b02e-112">Následující příklad ukazuje, jak nastavit <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> vlastností v kódu.</span><span class="sxs-lookup"><span data-stu-id="5b02e-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="5b02e-113">Můžete také použít `AllowBufferedReceive` atribut služby pracovních postupů v XAML, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5b02e-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b02e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b02e-114">See also</span></span>

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [<span data-ttu-id="5b02e-115">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5b02e-115">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="5b02e-116">Fronty a spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="5b02e-116">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
