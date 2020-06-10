---
title: Zpracování zpráv mimo pořadí
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 7930f26cf5957158a16d65085267cf1bab2e4504
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598720"
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="8be5d-102">Zpracování zpráv mimo pořadí</span><span class="sxs-lookup"><span data-stu-id="8be5d-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="8be5d-103">Služby pracovních postupů můžou záviset na zprávách odesílaných v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="8be5d-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="8be5d-104">Služba pracovního postupu obsahuje jednu nebo více <xref:System.ServiceModel.Activities.Receive> aktivit a každá <xref:System.ServiceModel.Activities.Receive> aktivita očekává určitou zprávu.</span><span class="sxs-lookup"><span data-stu-id="8be5d-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="8be5d-105">Bez jakýchkoli konkrétních záruk přenosů za provozu můžou být zprávy odesílané klienty zpožděné a proto se doručí v pořadí, ve kterém služba pracovního postupu nemusí očekávat.</span><span class="sxs-lookup"><span data-stu-id="8be5d-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="8be5d-106">Implementace služby pracovního postupu, která nevyžaduje odeslání zprávy v určitém pořadí, se obvykle provádí pomocí paralelní aktivity.</span><span class="sxs-lookup"><span data-stu-id="8be5d-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="8be5d-107">Pro složitější aplikační protokol by byl pracovní postup velmi složitý velmi rychle.</span><span class="sxs-lookup"><span data-stu-id="8be5d-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="8be5d-108">Funkce zpracování zpráv mimo pořadí v Windows Communication Foundation (WCF) umožňuje vytvořit takový pracovní postup bez nutnosti složitosti vnořených paralelních aktivit.</span><span class="sxs-lookup"><span data-stu-id="8be5d-108">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="8be5d-109">Zpracování zpráv mimo pořadí je podporováno pouze na kanálech, které podporují <xref:System.ServiceModel.Channels.ReceiveContext> například vazby služby MSMQ WCF.</span><span class="sxs-lookup"><span data-stu-id="8be5d-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="8be5d-110">Povolení zpracování zpráv mimo pořadí</span><span class="sxs-lookup"><span data-stu-id="8be5d-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="8be5d-111">Zpracování zpráv mimo pořadí je povoleno nastavením vlastnosti na hodnotu <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> `true` implementace WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="8be5d-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="8be5d-112">Následující příklad ukazuje, jak nastavit <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> vlastnost v kódu.</span><span class="sxs-lookup"><span data-stu-id="8be5d-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="8be5d-113">Můžete také použít `AllowBufferedReceive` atribut pro službu pracovního postupu v jazyce XAML, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8be5d-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8be5d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8be5d-114">See also</span></span>

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [<span data-ttu-id="8be5d-115">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8be5d-115">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="8be5d-116">Fronty a spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="8be5d-116">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
