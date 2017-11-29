---
title: "Zpracování zpráv mimo pořadí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ffd220babe99661d8b6aaf271a566d415af5eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="edf94-102">Zpracování zpráv mimo pořadí</span><span class="sxs-lookup"><span data-stu-id="edf94-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="edf94-103">Služby pracovních postupů může záviset na zprávy odesílané v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="edf94-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="edf94-104">Služba pracovní postup obsahuje jeden nebo více <xref:System.ServiceModel.Activities.Receive> aktivity a každý <xref:System.ServiceModel.Activities.Receive> aktivity očekává konkrétní zprávou.</span><span class="sxs-lookup"><span data-stu-id="edf94-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="edf94-105">Zprávy odeslané klienti mohou bez záruky doručení konkrétní přenos, odložené a proto doručit v pořadí, které nemusí očekávat služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="edf94-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="edf94-106">Implementace služby pracovního postupu, který nevyžaduje zprávy odeslané v určitém pořadí se obvykle provádí pomocí paralelní aktivity.</span><span class="sxs-lookup"><span data-stu-id="edf94-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="edf94-107">Složitější aplikační protokol pracovní postup by být velice komplexní velmi rychle.</span><span class="sxs-lookup"><span data-stu-id="edf94-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="edf94-108">Funkci zpracování zpráv mimo pořadí v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vám umožní vytvořit takový pracovní postup bez všechny složitosti vnořené paralelní aktivity.</span><span class="sxs-lookup"><span data-stu-id="edf94-108">The out-of-order message processing feature in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="edf94-109">Zpracování zpráv mimo pořadí je podporován pouze na kanály, které podporují <xref:System.ServiceModel.Channels.ReceiveContext> , jako [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="edf94-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="edf94-110">Povolení zpracování zpráv mimo pořadí</span><span class="sxs-lookup"><span data-stu-id="edf94-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="edf94-111">Zpracování zpráv mimo pořadí povolíte nastavením <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> vlastnost `true` na WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="edf94-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="edf94-112">Následující příklad ukazuje, jak nastavit <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> vlastností v kódu.</span><span class="sxs-lookup"><span data-stu-id="edf94-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="edf94-113">Můžete taky použít `AllowBufferedReceive` atribut služby pracovních postupů v jazyce XAML, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="edf94-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="edf94-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="edf94-114">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [<span data-ttu-id="edf94-115">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="edf94-115">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="edf94-116">Fronty a spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="edf94-116">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
