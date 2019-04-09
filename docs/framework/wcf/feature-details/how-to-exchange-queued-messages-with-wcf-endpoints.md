---
title: 'Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 98cb62c0d3f82a90ee96797a34600473dbe4dc11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179163"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="140e1-102">Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF</span><span class="sxs-lookup"><span data-stu-id="140e1-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="140e1-103">Fronty Ujistěte se, že může dojít spolehlivé zasílání zpráv, mezi klientem a službou Windows Communication Foundation (WCF), i v případě, že služba není k dispozici v době komunikace.</span><span class="sxs-lookup"><span data-stu-id="140e1-103">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="140e1-104">Následující postupy ukazují, jak zajistit ve frontě trvalý komunikace mezi klientem a službou pomocí standardní připojení, při implementaci služby WCF.</span><span class="sxs-lookup"><span data-stu-id="140e1-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="140e1-105">Tato část vysvětluje, jak používat <xref:System.ServiceModel.NetMsmqBinding> pro komunikaci mezi klienta WCF a služby WCF ve frontě.</span><span class="sxs-lookup"><span data-stu-id="140e1-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="140e1-106">Použití služby Řízení front ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="140e1-106">To use queuing in a WCF service</span></span>  
  
1.  <span data-ttu-id="140e1-107">Definování kontraktu služby pomocí rozhraní označené <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="140e1-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="140e1-108">Označit operace v rozhraní, které jsou součástí kontraktu služby se <xref:System.ServiceModel.OperationContractAttribute> a zadejte jako jednosměrná, protože není vrácena žádná odpověď na metodu.</span><span class="sxs-lookup"><span data-stu-id="140e1-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="140e1-109">Následující kód obsahuje kontrakt služby příklad a jeho definice operace.</span><span class="sxs-lookup"><span data-stu-id="140e1-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  <span data-ttu-id="140e1-110">Když je kontrakt služby úspěšné uživatelem definovaných typů, je nutné definovat kontraktů dat pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="140e1-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="140e1-111">Následující kód ukazuje dva kontrakty dat `PurchaseOrder` a `PurchaseOrderLineItem`.</span><span class="sxs-lookup"><span data-stu-id="140e1-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="140e1-112">Tyto dva typy definují data, která se odesílají do služby.</span><span class="sxs-lookup"><span data-stu-id="140e1-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="140e1-113">(Všimněte si, že třídy, které definují tento kontrakt dat také definovat několik metod.</span><span class="sxs-lookup"><span data-stu-id="140e1-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="140e1-114">Tyto metody nejsou považované za součást kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="140e1-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="140e1-115">Pouze ty členy, které jsou deklarovány pomocí <xref:System.Runtime.Serialization.DataMemberAttribute> atribut jsou součástí kontraktu dat.)</span><span class="sxs-lookup"><span data-stu-id="140e1-115">Only those members that are declared with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  <span data-ttu-id="140e1-116">Implementace metod definovaných v rozhraní ve třídě kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="140e1-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="140e1-117">Všimněte si, že <xref:System.ServiceModel.OperationBehaviorAttribute> umístit `SubmitPurchaseOrder` metody.</span><span class="sxs-lookup"><span data-stu-id="140e1-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="140e1-118">Toto nastavení určuje, že tuto operaci musí být volána v rámci transakce a transakce automaticky dokončí při dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="140e1-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4.  <span data-ttu-id="140e1-119">Vytvoření transakční fronty pomocí <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="140e1-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="140e1-120">Můžete vytvořit frontu, místo toho použít Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="140e1-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="140e1-121">Pokud ano, ujistěte se, že vytvoříte transakční frontu.</span><span class="sxs-lookup"><span data-stu-id="140e1-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  <span data-ttu-id="140e1-122">Definování <xref:System.ServiceModel.Description.ServiceEndpoint> v konfiguraci, která určuje adresu služby a využívá standardní <xref:System.ServiceModel.NetMsmqBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="140e1-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="140e1-123">Další informace o použití konfigurace WCF najdete v tématu [konfigurace WCF services](../configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="140e1-123">For more information about using WCF configuration, see [Configuring WCF services](../configuring-services.md).</span></span>  

6.  <span data-ttu-id="140e1-124">Vytvoření hostitele pro `OrderProcessing` služby pomocí <xref:System.ServiceModel.ServiceHost> , která čte zprávy z fronty a zpracovává je.</span><span class="sxs-lookup"><span data-stu-id="140e1-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="140e1-125">Otevření hostitele služby, aby tato služba k dispozici.</span><span class="sxs-lookup"><span data-stu-id="140e1-125">Open the service host to make the service available.</span></span> <span data-ttu-id="140e1-126">Zobrazte zprávu, která uživateli říká, aby stisknutím libovolné klávesy ukončete službu.</span><span class="sxs-lookup"><span data-stu-id="140e1-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="140e1-127">Volání `ReadLine` čekání na klávesu se aktivovala a potom zavřete okno služby.</span><span class="sxs-lookup"><span data-stu-id="140e1-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="140e1-128">K vytvoření klienta pro službu ve frontě</span><span class="sxs-lookup"><span data-stu-id="140e1-128">To create a client for the queued service</span></span>  
  
1.  <span data-ttu-id="140e1-129">Následující příklad ukazuje způsob použití nástroje Svcutil.exe k vytvoření klienta WCF a spouštění hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="140e1-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  <span data-ttu-id="140e1-130">Definování <xref:System.ServiceModel.Description.ServiceEndpoint> v konfiguraci, která určuje adresu a používá standardní <xref:System.ServiceModel.NetMsmqBinding> vazbu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="140e1-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  

3.  <span data-ttu-id="140e1-131">Vytvoření oboru transakce k zápisu transakční fronty, volání `SubmitPurchaseOrder` operace a zavřít klienta WCF, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="140e1-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="140e1-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="140e1-132">Example</span></span>  
 <span data-ttu-id="140e1-133">Následující příklady ukazují kód služby, hostitelské aplikace, soubor App.config a kód klienta, které jsou zahrnuté v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="140e1-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a><span data-ttu-id="140e1-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="140e1-134">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- [<span data-ttu-id="140e1-135">Zpracované vazby služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="140e1-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)
- [<span data-ttu-id="140e1-136">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="140e1-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="140e1-137">Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front</span><span class="sxs-lookup"><span data-stu-id="140e1-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="140e1-138">Z WCF do Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="140e1-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="140e1-139">Instalace služby Řízení front zpráv (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="140e1-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="140e1-140">Řízení front zpráv do WCF</span><span class="sxs-lookup"><span data-stu-id="140e1-140">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="140e1-141">Zabezpečení zprávy pomocí služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="140e1-141">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
