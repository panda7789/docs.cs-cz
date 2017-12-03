---
title: "Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6c50d9c6740b0c680e349a71bf4b3bdece2b34f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="04e7f-102">Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF</span><span class="sxs-lookup"><span data-stu-id="04e7f-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="04e7f-103">Fronty Ujistěte se, že spolehlivé zasílání zpráv může dojít mezi klientem a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby, i když služba není k dispozici v době komunikace.</span><span class="sxs-lookup"><span data-stu-id="04e7f-103">Queues ensure that reliable messaging can occur between a client and a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="04e7f-104">Následující postupy ukazují, jak zajistit trvanlivý komunikace mezi klientem a služby pomocí standardní zařazených do fronty závazný při implementaci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="04e7f-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="04e7f-105">Tato část vysvětluje, jak používat <xref:System.ServiceModel.NetMsmqBinding> pro komunikaci mezi ve frontě [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="04e7f-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="04e7f-106">Použití služby Řízení front služby WCF</span><span class="sxs-lookup"><span data-stu-id="04e7f-106">To use queuing in a WCF service</span></span>  
  
1.  <span data-ttu-id="04e7f-107">Definování kontraktu služby pomocí rozhraní označené jako <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="04e7f-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="04e7f-108">Označit operace v rozhraní, které jsou součástí na kontrakt služby s <xref:System.ServiceModel.OperationContractAttribute> a zadejte je jako jednosměrný, protože je vrácena žádná odezva na metodu.</span><span class="sxs-lookup"><span data-stu-id="04e7f-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="04e7f-109">Následující kód obsahuje kontrakt služby příklad a jeho definice operace.</span><span class="sxs-lookup"><span data-stu-id="04e7f-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  <span data-ttu-id="04e7f-110">Když je kontrakt služby úspěšné uživatelem definované typy, je nutné zadat kontrakty dat pro tyto typy.</span><span class="sxs-lookup"><span data-stu-id="04e7f-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="04e7f-111">Následující kód ukazuje dva datové kontrakty, `PurchaseOrder` a `PurchaseOrderLineItem`.</span><span class="sxs-lookup"><span data-stu-id="04e7f-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="04e7f-112">Tyto dva typy zadat data, která je odeslána do služby.</span><span class="sxs-lookup"><span data-stu-id="04e7f-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="04e7f-113">(Všimněte si, že třídy, které definují tento kontrakt dat také definovat několik metod.</span><span class="sxs-lookup"><span data-stu-id="04e7f-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="04e7f-114">Tyto metody nejsou považovány za součást kontrakt dat.</span><span class="sxs-lookup"><span data-stu-id="04e7f-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="04e7f-115">Pouze členové, které jsou deklarovány s `DataMember` atribut jsou součástí kontrakt dat.)</span><span class="sxs-lookup"><span data-stu-id="04e7f-115">Only those members that are declared with the `DataMember` attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  <span data-ttu-id="04e7f-116">Implementace metody kontraktu služby, které jsou definované v rozhraní v třídě.</span><span class="sxs-lookup"><span data-stu-id="04e7f-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="04e7f-117">Upozornění <xref:System.ServiceModel.OperationBehaviorAttribute> umístit na `SubmitPurchaseOrder` metoda.</span><span class="sxs-lookup"><span data-stu-id="04e7f-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="04e7f-118">Toto nastavení určuje, že tato operace je nutné volat v transakci a transakce automaticky dokončí při dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="04e7f-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4.  <span data-ttu-id="04e7f-119">Vytvoření transakční fronty pomocí <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="04e7f-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="04e7f-120">Můžete vytvořit frontu, místo toho použít Microsoft služby Řízení front zpráv (MSMQ) Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="04e7f-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="04e7f-121">Pokud ano, ujistěte se, že vytvoříte transakční fronty.</span><span class="sxs-lookup"><span data-stu-id="04e7f-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  <span data-ttu-id="04e7f-122">Definování <xref:System.ServiceModel.Description.ServiceEndpoint> v konfiguraci, kterou určuje adresu služby a používá standardní <xref:System.ServiceModel.NetMsmqBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="04e7f-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="04e7f-123">pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfigurace, najdete v části [konfigurace Windows Communication Foundation aplikací](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="04e7f-123"> using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration, see [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
  
  
6.  <span data-ttu-id="04e7f-124">Vytvořte pro hostitele, který `OrderProcessing` služby pomocí <xref:System.ServiceModel.ServiceHost> která čte zprávy z fronty a zpracovává je.</span><span class="sxs-lookup"><span data-stu-id="04e7f-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="04e7f-125">Otevření hostitele služby chcete zpřístupnit službu.</span><span class="sxs-lookup"><span data-stu-id="04e7f-125">Open the service host to make the service available.</span></span> <span data-ttu-id="04e7f-126">Zobrazí zprávu, která uživateli říká, aby stisknutím libovolné klávesy ukončit službu.</span><span class="sxs-lookup"><span data-stu-id="04e7f-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="04e7f-127">Volání `ReadLine` čekat pro klíč stisknout a pak zavřete službu.</span><span class="sxs-lookup"><span data-stu-id="04e7f-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="04e7f-128">Vytvoření klienta pro službu ve frontě</span><span class="sxs-lookup"><span data-stu-id="04e7f-128">To create a client for the queued service</span></span>  
  
1.  <span data-ttu-id="04e7f-129">Následující příklad ukazuje, jak spouštět hostitelskou aplikaci a pomocí nástroje Svcutil.exe vytvořit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="04e7f-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  <span data-ttu-id="04e7f-130">Definování <xref:System.ServiceModel.Description.ServiceEndpoint> v konfiguraci, kterou určuje adresu a používá standardní <xref:System.ServiceModel.NetMsmqBinding> vazby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="04e7f-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  
  
  
  
3.  <span data-ttu-id="04e7f-131">Vytvoření oboru transakce k zápisu do transakční fronty, volání `SubmitPurchaseOrder` operaci a zavřete [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="04e7f-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="04e7f-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="04e7f-132">Example</span></span>  
 <span data-ttu-id="04e7f-133">Následující příklady ukazují kódu služby, hostování aplikace, soubor App.config a kód klienta, které jsou zahrnuté v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="04e7f-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="04e7f-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="04e7f-134">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [<span data-ttu-id="04e7f-135">Zpracované vazby služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="04e7f-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [<span data-ttu-id="04e7f-136">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="04e7f-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="04e7f-137">Postupy: výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="04e7f-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="04e7f-138">Windows Communication Foundation do řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="04e7f-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="04e7f-139">Instalace služby Řízení front zpráv (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="04e7f-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="04e7f-140">Ukázky vazby integrace služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="04e7f-140">Message Queuing Integration Binding Samples</span></span>](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [<span data-ttu-id="04e7f-141">Řízení front zpráv do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="04e7f-141">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="04e7f-142">Zabezpečení zprávy pomocí služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="04e7f-142">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
