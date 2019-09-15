---
title: 'Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 09b21c9483b4f2716409b560dbbb478fe5a6badd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972225"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="fda14-102">Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF</span><span class="sxs-lookup"><span data-stu-id="fda14-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="fda14-103">Fronty zajišťují, že spolehlivé zasílání zpráv může nastat mezi klientem a službou Windows Communication Foundation (WCF), a to i v případě, že služba není k dispozici v době komunikace.</span><span class="sxs-lookup"><span data-stu-id="fda14-103">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="fda14-104">Následující postupy ukazují, jak zajistit trvalou komunikaci mezi klientem a službou pomocí standardní vazby ve frontě při implementaci služby WCF.</span><span class="sxs-lookup"><span data-stu-id="fda14-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="fda14-105">V této části se dozvíte <xref:System.ServiceModel.NetMsmqBinding> , jak použít pro komunikaci ve frontě mezi klientem WCF a službou WCF.</span><span class="sxs-lookup"><span data-stu-id="fda14-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="fda14-106">Používání služby Řízení front zpráv ve službě WCF</span><span class="sxs-lookup"><span data-stu-id="fda14-106">To use queuing in a WCF service</span></span>  
  
1. <span data-ttu-id="fda14-107">Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fda14-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="fda14-108">Označte operace v rozhraní, které jsou součástí kontraktu <xref:System.ServiceModel.OperationContractAttribute> služby, a zadejte je jako jednosměrné, protože se nevrátí žádná odpověď na metodu.</span><span class="sxs-lookup"><span data-stu-id="fda14-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="fda14-109">Následující kód poskytuje příklad kontraktu služby a jeho definice operace.</span><span class="sxs-lookup"><span data-stu-id="fda14-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. <span data-ttu-id="fda14-110">Pokud kontrakt služby předává uživatelsky definované typy, je nutné pro tyto typy definovat kontrakty dat.</span><span class="sxs-lookup"><span data-stu-id="fda14-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="fda14-111">Následující kód ukazuje dvě kontrakty dat, `PurchaseOrder` a `PurchaseOrderLineItem`.</span><span class="sxs-lookup"><span data-stu-id="fda14-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="fda14-112">Tyto dva typy definují data, která jsou odeslána do služby.</span><span class="sxs-lookup"><span data-stu-id="fda14-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="fda14-113">(Všimněte si, že třídy, které definují tento datový kontrakt, definují také počet metod.</span><span class="sxs-lookup"><span data-stu-id="fda14-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="fda14-114">Tyto metody nejsou považovány za součást kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="fda14-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="fda14-115">Pouze členové, kteří jsou deklarováni s <xref:System.Runtime.Serialization.DataMemberAttribute> atributem, jsou součástí kontraktu dat.)</span><span class="sxs-lookup"><span data-stu-id="fda14-115">Only those members that are declared with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. <span data-ttu-id="fda14-116">Implementujte metody kontraktu služby definovaného v rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="fda14-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="fda14-117">Všimněte si <xref:System.ServiceModel.OperationBehaviorAttribute> , že se `SubmitPurchaseOrder` nachází na metodě.</span><span class="sxs-lookup"><span data-stu-id="fda14-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="fda14-118">To určuje, že tuto operaci je nutné volat v rámci transakce a že transakce se automaticky dokončí po dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="fda14-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4. <span data-ttu-id="fda14-119">Vytvořte transakční frontu pomocí <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="fda14-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="fda14-120">Místo toho můžete vytvořit frontu pomocí konzoly Microsoft Management Console (MSMQ) společnosti Microsoft (MMC).</span><span class="sxs-lookup"><span data-stu-id="fda14-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="fda14-121">Pokud ano, ujistěte se, že jste vytvořili transakční frontu.</span><span class="sxs-lookup"><span data-stu-id="fda14-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. <span data-ttu-id="fda14-122">Definujte v konfiguraci, která určuje adresu služby a používá standardní <xref:System.ServiceModel.NetMsmqBinding> vazbu. <xref:System.ServiceModel.Description.ServiceEndpoint></span><span class="sxs-lookup"><span data-stu-id="fda14-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="fda14-123">Další informace o použití konfigurace WCF najdete v tématu [Konfigurace služeb WCF](../configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="fda14-123">For more information about using WCF configuration, see [Configuring WCF services](../configuring-services.md).</span></span>  

6. <span data-ttu-id="fda14-124">Vytvořte hostitele pro `OrderProcessing` službu pomocí nástroje <xref:System.ServiceModel.ServiceHost> , který načte zprávy z fronty a zpracuje je.</span><span class="sxs-lookup"><span data-stu-id="fda14-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="fda14-125">Otevřete hostitele služby, aby služba byla dostupná.</span><span class="sxs-lookup"><span data-stu-id="fda14-125">Open the service host to make the service available.</span></span> <span data-ttu-id="fda14-126">Zobrazí zprávu s oznámením, že uživatel stiskne libovolnou klávesu a ukončí službu.</span><span class="sxs-lookup"><span data-stu-id="fda14-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="fda14-127">Zavolejte `ReadLine` na čekání na stisknutí klávesy a potom službu zavřete.</span><span class="sxs-lookup"><span data-stu-id="fda14-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="fda14-128">Vytvoření klienta pro službu ve frontě</span><span class="sxs-lookup"><span data-stu-id="fda14-128">To create a client for the queued service</span></span>  
  
1. <span data-ttu-id="fda14-129">Následující příklad ukazuje, jak spustit hostitelskou aplikaci a použít nástroj Svcutil. exe k vytvoření klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="fda14-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. <span data-ttu-id="fda14-130">Definujte v konfiguraci, která určuje adresu a používá standardní <xref:System.ServiceModel.NetMsmqBinding> vazbu, jak je znázorněno v následujícím příkladu. <xref:System.ServiceModel.Description.ServiceEndpoint></span><span class="sxs-lookup"><span data-stu-id="fda14-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  

3. <span data-ttu-id="fda14-131">Vytvořte obor transakce pro zápis do transakční fronty, zavolejte `SubmitPurchaseOrder` operaci a zavřete klienta služby WCF, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fda14-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="fda14-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="fda14-132">Example</span></span>  
 <span data-ttu-id="fda14-133">Následující příklady znázorňují kód služby, hostující aplikaci, soubor App. config a klientský kód, který je součástí tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="fda14-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a><span data-ttu-id="fda14-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fda14-134">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- [<span data-ttu-id="fda14-135">Zpracované vazby služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="fda14-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)
- [<span data-ttu-id="fda14-136">Zařazování do front ve WCF</span><span class="sxs-lookup"><span data-stu-id="fda14-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="fda14-137">Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="fda14-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="fda14-138">Z Windows Communication Foundation do služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="fda14-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="fda14-139">Instalace služby Řízení front zpráv (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="fda14-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="fda14-140">Ze služby Řízení front zpráv do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fda14-140">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="fda14-141">Zabezpečení zprávy pomocí služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="fda14-141">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
