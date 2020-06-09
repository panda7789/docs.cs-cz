---
title: Použití kontraktů v pracovním postupu
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: def100f9483ea9ac8bf1aa3285d76edccffb030a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595008"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="320be-102">Použití kontraktů v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="320be-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="320be-103">Při implementaci služby definujete řadu kontraktů, které popisují službu a data, která odesílá a přijímá.</span><span class="sxs-lookup"><span data-stu-id="320be-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="320be-104">Data jsou reprezentována jako kontrakty dat a kontrakty zpráv. WCF i služba pracovních postupů používají jako součást popisů služeb kontrakt dat a definice kontraktů zpráv.</span><span class="sxs-lookup"><span data-stu-id="320be-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="320be-105">Služba sama zveřejňuje metadata (ve formě WSDL), aby bylo možné popsání operací služby.</span><span class="sxs-lookup"><span data-stu-id="320be-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="320be-106">V rámci WCF, kontrakty služeb a kontrakty operací definují službu a operace, které podporuje.</span><span class="sxs-lookup"><span data-stu-id="320be-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="320be-107">Ve službě pracovního postupu ale tyto smlouvy jsou součástí samotného obchodního procesu; jsou zpřístupněny v metadatech pomocí procesu nazývaného odvození kontraktu.</span><span class="sxs-lookup"><span data-stu-id="320be-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="320be-108">Odvození kontraktu</span><span class="sxs-lookup"><span data-stu-id="320be-108">Contract Inference</span></span>  
 <span data-ttu-id="320be-109">Je-li služba pracovního postupu hostována pomocí nástroje <xref:System.ServiceModel.Activities.WorkflowServiceHost> , je prověřena definice pracovního postupu a na základě sady aktivit zasílání zpráv, které jsou v pracovním postupu nalezeny, je vygenerován kontrakt.</span><span class="sxs-lookup"><span data-stu-id="320be-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="320be-110">Konkrétně se k vygenerování kontraktu použijí tyto aktivity a vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="320be-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="320be-111"><xref:System.ServiceModel.Activities.Receive>Akce</span><span class="sxs-lookup"><span data-stu-id="320be-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <span data-ttu-id="320be-112"><xref:System.ServiceModel.Activities.SendReply>Akce</span><span class="sxs-lookup"><span data-stu-id="320be-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="320be-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Akce</span><span class="sxs-lookup"><span data-stu-id="320be-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="320be-114">Konečný výsledek odvození smlouvy je popis služby, která používá stejné datové struktury jako služby WCF a kontrakty operací.</span><span class="sxs-lookup"><span data-stu-id="320be-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="320be-115">Tyto informace se pak použijí k vystavení WSDL pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="320be-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320be-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="320be-116">See also</span></span>

- [<span data-ttu-id="320be-117">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="320be-117">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="320be-118">Aktivity zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="320be-118">Messaging Activities</span></span>](messaging-activities.md)
- [<span data-ttu-id="320be-119">Postupy: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="320be-119">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="320be-120">Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby</span><span class="sxs-lookup"><span data-stu-id="320be-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
