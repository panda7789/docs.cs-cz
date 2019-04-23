---
title: Použití kontraktů v pracovním postupu
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: dd35766011c412acc937eed75d523a0574f6b9cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150056"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="5f752-102">Použití kontraktů v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="5f752-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="5f752-103">Při implementaci služby definovat několik smluv, které popisují služby a data, která odesílá a přijímá.</span><span class="sxs-lookup"><span data-stu-id="5f752-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="5f752-104">Data je vyjádřena jako data kontraktů a kontraktů zpráv; služby WCF a pracovního postupu pomocí definice kontraktu dat kontrakt a zprávy jako součást služby popisy.</span><span class="sxs-lookup"><span data-stu-id="5f752-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="5f752-105">Samotné služby zveřejňuje metadata (ve formě WSDL) aby bylo možné popisují operace služby.</span><span class="sxs-lookup"><span data-stu-id="5f752-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="5f752-106">Ve službě WCF definování kontraktů služby a operace kontraktů služby a operace, které podporuje.</span><span class="sxs-lookup"><span data-stu-id="5f752-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="5f752-107">Ale ve službě pracovního postupu, těchto smluv jsou součástí samotným obchodního procesu pomocí procesu nazývaného smlouvy odvození jsou vystaveny v metadatech.</span><span class="sxs-lookup"><span data-stu-id="5f752-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="5f752-108">Odvození kontraktu</span><span class="sxs-lookup"><span data-stu-id="5f752-108">Contract Inference</span></span>  
 <span data-ttu-id="5f752-109">Když je hostované služby pracovních postupů, pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, definice pracovního postupu je zkontrolován a kontrakt je generován a základě sadu zasílání zpráv aktivity v pracovním postupu nalezen.</span><span class="sxs-lookup"><span data-stu-id="5f752-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="5f752-110">Zejména následující aktivity a vlastnosti slouží ke generování kontraktu:</span><span class="sxs-lookup"><span data-stu-id="5f752-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="5f752-111"><xref:System.ServiceModel.Activities.Receive> Aktivita</span><span class="sxs-lookup"><span data-stu-id="5f752-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <span data-ttu-id="5f752-112"><xref:System.ServiceModel.Activities.SendReply> Aktivita</span><span class="sxs-lookup"><span data-stu-id="5f752-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="5f752-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivita</span><span class="sxs-lookup"><span data-stu-id="5f752-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="5f752-114">Konečný výsledek odvození smlouvy je popis služby pomocí stejné datové struktury jako smlouvy WCF služby a operace.</span><span class="sxs-lookup"><span data-stu-id="5f752-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="5f752-115">Potom tyto informace slouží k vystavení WSDL pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5f752-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f752-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f752-116">See also</span></span>

- [<span data-ttu-id="5f752-117">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5f752-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="5f752-118">Aktivity zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="5f752-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="5f752-119">Postupy: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="5f752-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="5f752-120">Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby</span><span class="sxs-lookup"><span data-stu-id="5f752-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
