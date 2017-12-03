---
title: "Použití kontraktů v pracovním postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c13da32e304e54d1826c6dd4ad83d5fbb17702a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="9c2ff-102">Použití kontraktů v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="9c2ff-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="9c2ff-103">Při implementaci služby, definujete číslo smlouvy, které popisují služby a data, která se odesílá a přijímá.</span><span class="sxs-lookup"><span data-stu-id="9c2ff-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="9c2ff-104">Data je reprezentována jako kontrakty dat a kontrakty zpráv; obě [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a služby, pracovní postup definice kontraktu dat kontrakt a zprávy v rámci popis služby.</span><span class="sxs-lookup"><span data-stu-id="9c2ff-104">The data is represented as data contracts and message contracts; both [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="9c2ff-105">Službu samotnou zveřejňuje metadata (ve formě WSDL) Chcete-li popsali, jak službu.</span><span class="sxs-lookup"><span data-stu-id="9c2ff-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="9c2ff-106">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], služba kontraktů a kontraktů operaci definovat služby a činnosti podporuje.</span><span class="sxs-lookup"><span data-stu-id="9c2ff-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="9c2ff-107">Ale ve službě pracovního postupu, tyto smlouvy jsou součástí obchodní proces, sama o sobě; pomocí procesu nazývaného kontrakt odvození jsou vystaveny v metadatech.</span><span class="sxs-lookup"><span data-stu-id="9c2ff-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="9c2ff-108">Odvození kontraktu</span><span class="sxs-lookup"><span data-stu-id="9c2ff-108">Contract Inference</span></span>  
 <span data-ttu-id="9c2ff-109">Když je pracovní postup služby hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, je zkontrolován definice pracovního postupu a kontraktu se vygeneruje na základě sady zasílání zpráv aktivity nalezen v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="9c2ff-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="9c2ff-110">Zejména následující aktivity a vlastnosti jsou použita pro vytvoření kontraktu:</span><span class="sxs-lookup"><span data-stu-id="9c2ff-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="9c2ff-111"><xref:System.ServiceModel.Activities.Receive>Aktivity</span><span class="sxs-lookup"><span data-stu-id="9c2ff-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <span data-ttu-id="9c2ff-112"><xref:System.ServiceModel.Activities.SendReply>Aktivity</span><span class="sxs-lookup"><span data-stu-id="9c2ff-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="9c2ff-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Aktivity</span><span class="sxs-lookup"><span data-stu-id="9c2ff-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="9c2ff-114">Konečný výsledek kontrakt odvození je popis služby pomocí stejné datové struktury jako kontraktů služby a operace WCF.</span><span class="sxs-lookup"><span data-stu-id="9c2ff-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="9c2ff-115">Tyto informace se pak používá ke zveřejnění WSDL pro služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9c2ff-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c2ff-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c2ff-116">See Also</span></span>  
 [<span data-ttu-id="9c2ff-117">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9c2ff-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="9c2ff-118">Aktivity zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="9c2ff-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [<span data-ttu-id="9c2ff-119">Postupy: vytvoření služby pracovního postupu se aktivity zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="9c2ff-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [<span data-ttu-id="9c2ff-120">Postupy: vytvoření služby pracovního postupu, který využívá existující smlouvy služby</span><span class="sxs-lookup"><span data-stu-id="9c2ff-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
