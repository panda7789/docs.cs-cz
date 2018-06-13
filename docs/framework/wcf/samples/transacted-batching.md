---
title: Transakční dávkování
ms.date: 03/30/2017
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
ms.openlocfilehash: 7df65b8f3f149deac841010e392f3919b24506b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508875"
---
# <a name="transacted-batching"></a><span data-ttu-id="e1aa0-102">Transakční dávkování</span><span class="sxs-lookup"><span data-stu-id="e1aa0-102">Transacted Batching</span></span>
<span data-ttu-id="e1aa0-103">Tento příklad ukazuje, jak dávky zpracovaných čtení pomocí služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="e1aa0-103">This sample demonstrates how to batch transacted reads by using Message Queuing (MSMQ).</span></span> <span data-ttu-id="e1aa0-104">Zpracovaných Batching je funkce optimalizace výkonu pro zpracovaných čtení v komunikaci ve frontě.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-104">Transacted Batching is a performance optimization feature for transacted reads in queued communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1aa0-105">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e1aa0-106">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="e1aa0-107">Přesněji řečeno klient odešle zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="e1aa0-108">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-108">The service receives messages from the queue.</span></span> <span data-ttu-id="e1aa0-109">Služba a klient proto nemusíte používat současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-109">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="e1aa0-110">Tento příklad znázorňuje zpracovaných dávkování.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-110">This sample demonstrates transacted batching.</span></span> <span data-ttu-id="e1aa0-111">Dávkové je chování, které umožňuje použití jedné transakci při čtení mnoho zpráv ve frontě a jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-111">Transacted batching is a behavior that enables the use of a single transaction when reading many messages in the queue and processing them.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e1aa0-112">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="e1aa0-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e1aa0-113">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1aa0-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e1aa0-114">Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-114">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="e1aa0-115">Pokud fronta neexistuje, vytvoří služba jeden.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-115">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="e1aa0-116">Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-116">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="e1aa0-117">Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-117">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="e1aa0-118">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e1aa0-118">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="e1aa0-119">Rozbalte **funkce** kartě.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-119">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="e1aa0-120">Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-120">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="e1aa0-121">Zkontrolujte **transakcí** pole.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-121">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="e1aa0-122">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-122">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e1aa0-123">V této ukázce klient odešle stovky zprávy jako část dávky.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-123">In this sample the client sends hundreds of messages as part of the batch.</span></span> <span data-ttu-id="e1aa0-124">Je normální, pro aplikaci služby pro zpracování těchto chvíli trvat.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-124">It is normal for the service application to take some time to process these.</span></span>  
  
3.  <span data-ttu-id="e1aa0-125">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1aa0-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="e1aa0-126">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1aa0-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="e1aa0-127">Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby active directory</span><span class="sxs-lookup"><span data-stu-id="e1aa0-127">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="e1aa0-128">Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-128">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="e1aa0-129">Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-129">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="e1aa0-130">Pro služby MSMQ k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby active directory pro službu MSMQ musí být nainstalován.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-130">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="e1aa0-131">Pokud tuto ukázku spustit na počítači, který nesplňuje tato kritéria obdržíte chybu.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-131">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
2.  <span data-ttu-id="e1aa0-132">Pokud počítač není součástí domény nebo nemá nainstalované integrační služby active directory, vypněte zabezpečení přenosu podle nastavení úrovně režim a ochrany ověřování na `None` jak je znázorněno v následující ukázka konfigurace:</span><span class="sxs-lookup"><span data-stu-id="e1aa0-132">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
    </system.serviceModel>  
    ```  
  
3.  <span data-ttu-id="e1aa0-133">Ujistěte se, změnit konfiguraci na serveru a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-133">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e1aa0-134">Nastavení `security``mode` k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-134">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
4.  <span data-ttu-id="e1aa0-135">Pokud chcete spustit databáze ve vzdáleném počítači, změňte připojovací řetězec tak, aby odkazoval na počítač, na kterém je umístěna databáze.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-135">To run the database on a remote computer, change the connection string to point to the computer on which the database resides.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1aa0-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1aa0-136">Requirements</span></span>  
 <span data-ttu-id="e1aa0-137">Chcete-li tuto ukázku spustit, musí být nainstalované služby MSMQ a je zapotřebí SQL nebo SQL Express.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-137">To run this sample, MSMQ must be installed and SQL or SQL Express is required.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e1aa0-138">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="e1aa0-138">Demonstrates</span></span>  
 <span data-ttu-id="e1aa0-139">Ukázka ukazuje chování dávkového zpracování.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-139">The sample demonstrates transacted batching behavior.</span></span> <span data-ttu-id="e1aa0-140">Dávkové je funkce optimalizace výkonu součástí služby MSMQ zařazených do fronty přenosu.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-140">Transacted batching is a performance optimization feature provided with MSMQ queued transport.</span></span>  
  
 <span data-ttu-id="e1aa0-141">Pokud transakce se používají k odesílání a přijímání zpráv, které jsou ve skutečnosti 2 oddělte transakce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-141">When transactions are used to send and receive messages there are actually 2 separate transactions.</span></span> <span data-ttu-id="e1aa0-142">Když klient odešle zprávy v rámci oboru transakce, transakce je místní pro klienta a fronty správce klienta.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-142">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="e1aa0-143">Když služba přijímá zprávy v rámci oboru transakce, transakce je místní služby a využívá správce fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-143">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="e1aa0-144">Je důležité si pamatovat, klient a služba nejsou součástí stejné transakci; různé transakce místo používají při provádění operací (například odesílat a přijímat) s fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-144">It is very important to remember that the client and the service are not participating in the same transaction; rather they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="e1aa0-145">V ukázce používáme pro provádění více operací služby jedné transakci.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-145">In the sample we use a single transaction for the execution of multiple service operations.</span></span> <span data-ttu-id="e1aa0-146">To se používají pouze jako funkce optimalizace výkonu a nemá negativní vliv na sémantiku aplikace.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-146">This is used only as a performance optimization feature and does not impact the semantics of the application.</span></span> <span data-ttu-id="e1aa0-147">Ukázka je založena na [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="e1aa0-147">The sample is based on [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="e1aa0-148">Komentáře</span><span class="sxs-lookup"><span data-stu-id="e1aa0-148">Comments</span></span>  
 <span data-ttu-id="e1aa0-149">V této ukázce klient odešle dávku zpráv do služby z v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-149">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="e1aa0-150">Chcete-li zobrazit optimalizace výkonu, odešleme velkého počtu zpráv; v takovém případě až 2 500 zprávy.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-150">To show the performance optimization, we send a large number of messages; in this case, up to 2500 messages.</span></span>  
  
 <span data-ttu-id="e1aa0-151">Služba v rámci oboru transakce definované ve službě jsou pak přijímá zprávy odeslané do fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-151">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span> <span data-ttu-id="e1aa0-152">Bez dávkování, výsledkem 2 500 transakce pro každé vyvolání operace služby.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-152">Without batching, this results in 2500 transactions for each invocation of the service operation.</span></span> <span data-ttu-id="e1aa0-153">Má to dopad na výkon systému.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-153">This impacts performance of the system.</span></span> <span data-ttu-id="e1aa0-154">Protože se účastní - dvěma správci prostředků frontu MSMQ a `Orders` databáze-každé takové transakce je transakcí koordinátoru DTC.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-154">Because two resource managers are involved -the MSMQ queue and the `Orders` database- each such transaction is a DTC transaction.</span></span> <span data-ttu-id="e1aa0-155">Jsme optimalizovat pomocí mnohem menší počet transakcí zajištěním toho docílit dávku zpráv a volání operace služby v rámci jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-155">We optimize this by using a much smaller number of transactions by ensuring that a batch of messages and service operation invocations happen in a single transaction.</span></span>  
  
 <span data-ttu-id="e1aa0-156">Můžeme použít funkci dávkování podle:</span><span class="sxs-lookup"><span data-stu-id="e1aa0-156">We use the batching feature by:</span></span>  
  
-   <span data-ttu-id="e1aa0-157">Určení chování dávkového zpracování v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-157">Specifying transacted batching behavior in configuration.</span></span>  
  
-   <span data-ttu-id="e1aa0-158">Zadání velikost dávky z hlediska počet zpráv ke čtení pomocí jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-158">Specifying a batch size in terms of number of messages to be read using a single transaction.</span></span>  
  
-   <span data-ttu-id="e1aa0-159">Zadání maximální počet souběžných balíků ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-159">Specifying the maximum number of concurrent batches to run.</span></span>  
  
 <span data-ttu-id="e1aa0-160">V tomto příkladu ukážeme zvýšení výkonu snížením počtu transakcí tím, že zajistí, že v rámci jedné transakce před potvrzením transakce jsou vyvolány 100 operací služby.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-160">In this example, we show performance gains by reducing the number of transactions by ensuring that 100 service operations are invoked in a single transaction before committing the transaction.</span></span>  
  
 <span data-ttu-id="e1aa0-161">Chování služby definuje chování operaci s `TransactionScopeRequired` nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-161">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="e1aa0-162">To zajistí, že je žádné správci prostředků přístup metodu použít stejný obor transakce, který se používá k načtení zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-162">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="e1aa0-163">V tomto příkladu používáme databáze basic uložit informace o nákupu pořadí obsažené ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-163">In this example, we use a basic database to store the purchase order information contained in the message.</span></span> <span data-ttu-id="e1aa0-164">Oboru transakce také zaručuje, že pokud metoda vyvolá výjimku, bude vráceno do fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-164">The transaction scope also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="e1aa0-165">Bez nastavení toto chování operace, zařazených do fronty kanál, který vytvoří transakci čtení zprávy ve frontě a potvrdí automaticky předtím, než je odeslán, takže pokud se operace nezdaří, dojde ke ztrátě zprávy.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-165">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before it is dispatched so that if the operation fails, the message is lost.</span></span> <span data-ttu-id="e1aa0-166">Nejběžnější scénáře je pro operace služby zařazení v transakci, která slouží k načtení zprávy z fronty, jak je ukázáno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-166">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue as demonstrated in the following code.</span></span>  
  
 <span data-ttu-id="e1aa0-167">Všimněte si, že `ReleaseServiceInstanceOnTransactionComplete` je nastaven na `false`.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-167">Note that `ReleaseServiceInstanceOnTransactionComplete` is set to `false`.</span></span> <span data-ttu-id="e1aa0-168">Toto je důležité požadavek pro dávkové zpracování.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-168">This is an important requirement for batching.</span></span> <span data-ttu-id="e1aa0-169">Vlastnost `ReleaseServiceInstanceOnTransactionComplete` na `ServiceBehaviorAttribute` označuje, co dělat s instancí služby po dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-169">The property `ReleaseServiceInstanceOnTransactionComplete` on `ServiceBehaviorAttribute` indicates what to do with the service instance once the transaction is completed.</span></span> <span data-ttu-id="e1aa0-170">Ve výchozím nastavení je instance služby vydala po dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-170">By default, the service instance is released upon completing the transaction.</span></span> <span data-ttu-id="e1aa0-171">Základní aspekt pro dávkování je použití jedné transakci pro čtení a odeslání mnoho zpráv ve frontě.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-171">The core aspect to batching is the use of a single transaction for reading and dispatching many messages in the queue.</span></span> <span data-ttu-id="e1aa0-172">Proto uvolnění instance služby skončilo dokončení transakce předčasně negace velmi použití dávkování.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-172">Therefore releasing the service instance ends up completing the transaction prematurely negating the very use of batching.</span></span> <span data-ttu-id="e1aa0-173">Pokud je tato vlastnost nastavena na `true` a chování dávkového zpracování se přidá do koncového bodu, dávkování chování vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-173">If this property is set to `true` and transacted batching behavior is added to the endpoint, the batching validation behavior throws an exception.</span></span>  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```

 <span data-ttu-id="e1aa0-174">`Orders` Třída zapouzdří zpracování pořadí.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-174">The `Orders` class encapsulates the processing of the order.</span></span> <span data-ttu-id="e1aa0-175">V ukázce databáze se aktualizuje informace o objednávce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-175">In the sample, it updates the database with purchase order information.</span></span>  

```csharp
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```

 <span data-ttu-id="e1aa0-176">Dávkování chování a jeho konfigurace jsou určené v konfiguraci aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-176">The batching behavior and its configuration are specified in the service application configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="e1aa0-177">Velikost dávky je nápovědu k systému.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-177">The batch size is a hint to the system.</span></span> <span data-ttu-id="e1aa0-178">Například pokud zadáte velikost dávky 20, pak 20 zpráv by se přečíst a odeslat pomocí jedné transakce a pak je transakce potvrzena.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-178">For example, if you specify a batch size of 20, then 20 messages would be read and dispatched using a single transaction and then the transaction is committed.</span></span> <span data-ttu-id="e1aa0-179">Ale existují případy, kdy může transakce potvrdit dávku před dosažením velikost dávky.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-179">But there are cases where the transaction may commit the batch before the batch size is reached.</span></span>  
>   
>  <span data-ttu-id="e1aa0-180">Přidružený ke každé transakci je vypršení časového limitu, která se spouští tikání po vytvoření transakce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-180">Associated with every transaction is a timeout that starts ticking once the transaction is created.</span></span> <span data-ttu-id="e1aa0-181">Transakce byla přerušena, když vyprší platnost tento časový limit.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-181">When this timeout expires the transaction is aborted.</span></span> <span data-ttu-id="e1aa0-182">Je možné pro tento časový limit vyprší, ještě před dosažením velikosti dávky.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-182">It is possible for this timeout to expire even before the batch size is reached.</span></span> <span data-ttu-id="e1aa0-183">Aby se zabránilo znovu práce dávky z důvodu přerušení, `TransactedBatchingBehavior` kontroluje, jak dlouho je ponechán v transakci.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-183">To avoid re-working the batch because of the abort, the `TransactedBatchingBehavior` checks to see how much time is left on the transaction.</span></span> <span data-ttu-id="e1aa0-184">Pokud 80 % časový limit transakcí slouží, je transakce potvrzena.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-184">If 80% of the transaction timeout is used up, then the transaction is committed.</span></span>  
>   
>  <span data-ttu-id="e1aa0-185">Pokud neexistují žádné další zprávy ve frontě a nemusí se čekat splnění velikost dávky <xref:System.ServiceModel.Description.TransactedBatchingBehavior> potvrdí transakce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-185">If there are no more messages in the queue then instead of waiting for the fulfillment of the batch size the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> commits the transaction.</span></span>  
>   
>  <span data-ttu-id="e1aa0-186">Vybraná velikost dávky je závisí na vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-186">The choice of the batch size is dependent on your application.</span></span> <span data-ttu-id="e1aa0-187">Pokud velikost dávky je příliš malá, nelze získat požadovaný výkon.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-187">If the batch size is too small, you may not get the desired performance.</span></span> <span data-ttu-id="e1aa0-188">Na druhé straně Pokud velikost dávky je příliš velký, může zhoršit výkon.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-188">On the other hand if the batch size is too big, it may deteriorate performance.</span></span> <span data-ttu-id="e1aa0-189">Například může vaší transakce a za provozu již a podržením zámky ve vaší databázi nebo vaší transakce a může přestat mrtvých uzamčené, které by mohly způsobit dávky k získání vrácena zpět a vrátit práce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-189">For example, your transaction could live longer and hold locks on your database or your transaction could become dead locked, which could cause the batch to get rolled back and to redo the work.</span></span>  
  
 <span data-ttu-id="e1aa0-190">Klient vytvoří oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-190">The client creates a transaction scope.</span></span> <span data-ttu-id="e1aa0-191">Komunikace s fronty probíhá v rámci oboru transakce, příčinou je považován za atomické jednotky, kde jsou všechny zprávy odeslané do fronty nebo žádné zprávy jsou odesílány do fronty.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-191">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="e1aa0-192">Transakce se potvrdí voláním <xref:System.Transactions.TransactionScope.Complete%2A> v oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-192">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  

```csharp
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
            PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
            lineItem2.ProductId = "Red Widget";  
            lineItem2.Quantity = 890;  
            lineItem2.UnitCost = 45.89F;  
  
            po.orderLineItems = new PurchaseOrderLineItem[2];  
            po.orderLineItems[0] = lineItem1;  
            po.orderLineItems[1] = lineItem2;  
  
            //Create a transaction scope.  
            using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
            {  
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```

 <span data-ttu-id="e1aa0-193">Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-193">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="e1aa0-194">Uvidíte služby přijmout zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-194">You can see the service receive messages from the client.</span></span> <span data-ttu-id="e1aa0-195">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-195">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="e1aa0-196">Všimněte si, že vzhledem k tomu, že služby Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-196">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="e1aa0-197">Spuštění klienta, vypněte ho a potom spuštění služby a stále přijímá jeho zprávy.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-197">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="e1aa0-198">Uvidíte postupného výstup jako přečtená v dávce a zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-198">You can see a rolling output as messages are read in a batch and processed.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="e1aa0-199">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e1aa0-200">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e1aa0-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e1aa0-201">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1aa0-202">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a><span data-ttu-id="e1aa0-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1aa0-203">See Also</span></span>
