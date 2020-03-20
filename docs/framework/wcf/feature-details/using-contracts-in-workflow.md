---
title: Použití kontraktů v pracovním postupu
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 9f967d75a8e9d24fcfac8b7376a3d4840fba52f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184277"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="d10fa-102">Použití kontraktů v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="d10fa-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="d10fa-103">Při implementaci služby definujete řadu smluv, které popisují službu a data, která odesílá a přijímá.</span><span class="sxs-lookup"><span data-stu-id="d10fa-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="d10fa-104">Data jsou reprezentována jako kontrakty dat a zprávy; WCF a workflow služby používají data smlouvy a definice smlouvy zprávy jako součást popisů služeb.</span><span class="sxs-lookup"><span data-stu-id="d10fa-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="d10fa-105">Samotná služba zveřejňuje metadata (ve formě WSDL) k popisu operací služby.</span><span class="sxs-lookup"><span data-stu-id="d10fa-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="d10fa-106">V WCF služby smlouvy a provozní smlouvy definovat služby a operace, které podporuje.</span><span class="sxs-lookup"><span data-stu-id="d10fa-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="d10fa-107">Ve službě pracovního postupu jsou však tyto smlouvy součástí samotného obchodního procesu. jsou vystaveny v metadatech procesem nazývaným odvození smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d10fa-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="d10fa-108">Odvození smlouvy</span><span class="sxs-lookup"><span data-stu-id="d10fa-108">Contract Inference</span></span>  
 <span data-ttu-id="d10fa-109">Pokud je služba pracovního <xref:System.ServiceModel.Activities.WorkflowServiceHost>postupu hostována pomocí , je zkontrolována definice pracovního postupu a smlouva je generována na základě sady aktivit zasílání zpráv nalezených v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="d10fa-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="d10fa-110">Ke generování smlouvy se používají zejména následující činnosti a vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d10fa-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="d10fa-111"><xref:System.ServiceModel.Activities.Receive>Činnosti</span><span class="sxs-lookup"><span data-stu-id="d10fa-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <span data-ttu-id="d10fa-112"><xref:System.ServiceModel.Activities.SendReply>Činnosti</span><span class="sxs-lookup"><span data-stu-id="d10fa-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="d10fa-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Činnosti</span><span class="sxs-lookup"><span data-stu-id="d10fa-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="d10fa-114">Konečný výsledek odvození smlouvy je popis služby pomocí stejné datové struktury jako WCF smlouvy o službách a operacích.</span><span class="sxs-lookup"><span data-stu-id="d10fa-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="d10fa-115">Tyto informace se pak používají k vystavení WSDL pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d10fa-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d10fa-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d10fa-116">See also</span></span>

- [<span data-ttu-id="d10fa-117">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d10fa-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="d10fa-118">Aktivity zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="d10fa-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="d10fa-119">Postupy: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="d10fa-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="d10fa-120">Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby</span><span class="sxs-lookup"><span data-stu-id="d10fa-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
