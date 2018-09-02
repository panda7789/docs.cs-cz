---
title: Transakční dávkování
ms.date: 03/30/2017
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
ms.openlocfilehash: abada9aaf5fac8f05599467f385e708e1898832f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416645"
---
# <a name="transacted-batching"></a><span data-ttu-id="c6e16-102">Transakční dávkování</span><span class="sxs-lookup"><span data-stu-id="c6e16-102">Transacted Batching</span></span>
<span data-ttu-id="c6e16-103">Tento příklad ukazuje, jak dávkové transakce čtení pomocí služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="c6e16-103">This sample demonstrates how to batch transacted reads by using Message Queuing (MSMQ).</span></span> <span data-ttu-id="c6e16-104">Transakční dávkování je funkce optimalizace výkonu pro transakční operace čtení v komunikaci ve frontě.</span><span class="sxs-lookup"><span data-stu-id="c6e16-104">Transacted Batching is a performance optimization feature for transacted reads in queued communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6e16-105">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c6e16-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c6e16-106">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="c6e16-107">Přesněji řečeno klient odešle zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="c6e16-108">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-108">The service receives messages from the queue.</span></span> <span data-ttu-id="c6e16-109">Klienta a služby, proto není potřeba běžet současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-109">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="c6e16-110">V této ukázce provedené dávkování.</span><span class="sxs-lookup"><span data-stu-id="c6e16-110">This sample demonstrates transacted batching.</span></span> <span data-ttu-id="c6e16-111">Provedené dávkování je chování, které umožňuje použití jedné transakce při čtení počet zpráv ve frontě a jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="c6e16-111">Transacted batching is a behavior that enables the use of a single transaction when reading many messages in the queue and processing them.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c6e16-112">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="c6e16-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c6e16-113">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6e16-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c6e16-114">Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c6e16-114">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="c6e16-115">Pokud fronta neexistuje, služba ho vytvoří.</span><span class="sxs-lookup"><span data-stu-id="c6e16-115">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="c6e16-116">Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c6e16-116">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="c6e16-117">Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="c6e16-117">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="c6e16-118">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6e16-118">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="c6e16-119">Rozbalte **funkce** kartu.</span><span class="sxs-lookup"><span data-stu-id="c6e16-119">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="c6e16-120">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="c6e16-120">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="c6e16-121">Zkontrolujte, **transakční** pole.</span><span class="sxs-lookup"><span data-stu-id="c6e16-121">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="c6e16-122">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-122">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c6e16-123">V této ukázce klient odešle stovky zprávy jako součást služby batch.</span><span class="sxs-lookup"><span data-stu-id="c6e16-123">In this sample the client sends hundreds of messages as part of the batch.</span></span> <span data-ttu-id="c6e16-124">Je běžné pro aplikaci služby pro zpracování těchto nějakou dobu trvat.</span><span class="sxs-lookup"><span data-stu-id="c6e16-124">It is normal for the service application to take some time to process these.</span></span>  
  
3.  <span data-ttu-id="c6e16-125">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6e16-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="c6e16-126">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6e16-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="c6e16-127">Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby active directory</span><span class="sxs-lookup"><span data-stu-id="c6e16-127">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="c6e16-128">Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="c6e16-128">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="c6e16-129">Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` výchozí režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="c6e16-129">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="c6e16-130">Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby active directory pro službu MSMQ musí být nainstalována.</span><span class="sxs-lookup"><span data-stu-id="c6e16-130">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="c6e16-131">Pokud tuto ukázku spustit na počítači, který nevyhovuje těmto kritériím zobrazí chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="c6e16-131">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
2.  <span data-ttu-id="c6e16-132">Pokud počítač není součástí domény nebo nemá nainstalované integrace služby active directory, vypněte zabezpečení přenosu nastavením úroveň ověření režimu a ochrany na `None` jak je znázorněno v následující ukázková konfigurace:</span><span class="sxs-lookup"><span data-stu-id="c6e16-132">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
3.  <span data-ttu-id="c6e16-133">Ujistěte se, že změníte konfiguraci na serveru a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="c6e16-133">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c6e16-134">Nastavení `security``mode` k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="c6e16-134">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
4.  <span data-ttu-id="c6e16-135">Ke spuštění databáze ve vzdáleném počítači, změňte připojovací řetězec tak, aby odkazoval na počítač, na kterém je umístěna databáze.</span><span class="sxs-lookup"><span data-stu-id="c6e16-135">To run the database on a remote computer, change the connection string to point to the computer on which the database resides.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6e16-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6e16-136">Requirements</span></span>  
 <span data-ttu-id="c6e16-137">Tuto ukázku spustit, musí být služba MSMQ nainstalovaná a je potřeba SQL nebo systém SQL Express.</span><span class="sxs-lookup"><span data-stu-id="c6e16-137">To run this sample, MSMQ must be installed and SQL or SQL Express is required.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c6e16-138">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="c6e16-138">Demonstrates</span></span>  
 <span data-ttu-id="c6e16-139">Vzorek ukazuje chování dávkového zpracování.</span><span class="sxs-lookup"><span data-stu-id="c6e16-139">The sample demonstrates transacted batching behavior.</span></span> <span data-ttu-id="c6e16-140">Provedené dávkování je funkce optimalizace výkonu součástí služby MSMQ zařazených do fronty přenosu.</span><span class="sxs-lookup"><span data-stu-id="c6e16-140">Transacted batching is a performance optimization feature provided with MSMQ queued transport.</span></span>  
  
 <span data-ttu-id="c6e16-141">Pokud transakce se používají k odesílání a příjem zpráv, které nejsou ve skutečnosti 2 oddělte transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-141">When transactions are used to send and receive messages there are actually 2 separate transactions.</span></span> <span data-ttu-id="c6e16-142">Když klient odešle zprávy v rámci oboru transakce, transakce je místní pro klienta a klient správce fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-142">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="c6e16-143">Když služba přijímá zprávy v rámci oboru transakce, transakce je místní pro službu a využívá správce fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-143">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="c6e16-144">Je velmi dobré si uvědomit, že klient a služba nenachází v rámci jedné transakce; Místo toho stále používá jinou transakcí při provádění operací (například odesílání a příjem) s frontou.</span><span class="sxs-lookup"><span data-stu-id="c6e16-144">It is very important to remember that the client and the service are not participating in the same transaction; rather they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="c6e16-145">V ukázce používáme k provádění více operací služby jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-145">In the sample we use a single transaction for the execution of multiple service operations.</span></span> <span data-ttu-id="c6e16-146">To slouží pouze jako funkce optimalizace výkonu a nemá vliv na sémantiku aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6e16-146">This is used only as a performance optimization feature and does not impact the semantics of the application.</span></span> <span data-ttu-id="c6e16-147">Vzorek je založen na [nepodporuje transakce vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="c6e16-147">The sample is based on [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="c6e16-148">Komentáře</span><span class="sxs-lookup"><span data-stu-id="c6e16-148">Comments</span></span>  
 <span data-ttu-id="c6e16-149">V této ukázce klient odešle dávku zpráv ke službě z v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-149">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="c6e16-150">Chcete-li zobrazit optimalizace výkonu, pošleme velkého počtu zpráv; v takovém případě až 2500 zpráv.</span><span class="sxs-lookup"><span data-stu-id="c6e16-150">To show the performance optimization, we send a large number of messages; in this case, up to 2500 messages.</span></span>  
  
 <span data-ttu-id="c6e16-151">Služby v rámci oboru transakce definovány službou pak přijme zprávy odeslané do fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-151">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span> <span data-ttu-id="c6e16-152">Bez dávkování, výsledkem 2500 transakce pro každé vyvolání operace služby.</span><span class="sxs-lookup"><span data-stu-id="c6e16-152">Without batching, this results in 2500 transactions for each invocation of the service operation.</span></span> <span data-ttu-id="c6e16-153">To má vliv na výkon systému.</span><span class="sxs-lookup"><span data-stu-id="c6e16-153">This impacts performance of the system.</span></span> <span data-ttu-id="c6e16-154">Vzhledem k tomu, že dvě správce prostředků se využívá řada – fronta MSMQ a `Orders` databáze-každou transakci DTC je takový transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-154">Because two resource managers are involved -the MSMQ queue and the `Orders` database- each such transaction is a DTC transaction.</span></span> <span data-ttu-id="c6e16-155">Jsme optimalizovat pomocí mnohem menším počtu transakcí tím, že zajišťuje, který dávku zpráv a vyvolání operace služby dojít v rámci jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-155">We optimize this by using a much smaller number of transactions by ensuring that a batch of messages and service operation invocations happen in a single transaction.</span></span>  
  
 <span data-ttu-id="c6e16-156">Můžeme použít funkci dávkování podle:</span><span class="sxs-lookup"><span data-stu-id="c6e16-156">We use the batching feature by:</span></span>  
  
-   <span data-ttu-id="c6e16-157">Určení chování dávkového zpracování v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c6e16-157">Specifying transacted batching behavior in configuration.</span></span>  
  
-   <span data-ttu-id="c6e16-158">Určení velikosti dávky z hlediska počtu zpráv ke čtení pomocí jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-158">Specifying a batch size in terms of number of messages to be read using a single transaction.</span></span>  
  
-   <span data-ttu-id="c6e16-159">Zadání maximální počet souběžných dávek, pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="c6e16-159">Specifying the maximum number of concurrent batches to run.</span></span>  
  
 <span data-ttu-id="c6e16-160">V tomto příkladu vám ukážeme, zvýšení výkonu snížením počtu transakcí tím, že zajišťuje, že v rámci jedné transakce před potvrzením transakce jsou vyvolány 100 operací služby.</span><span class="sxs-lookup"><span data-stu-id="c6e16-160">In this example, we show performance gains by reducing the number of transactions by ensuring that 100 service operations are invoked in a single transaction before committing the transaction.</span></span>  
  
 <span data-ttu-id="c6e16-161">Definuje chování služby na chování operace s `TransactionScopeRequired` nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="c6e16-161">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="c6e16-162">Tím se zajistí, že všechny správce prostředků přistupovat pomocí metody používají stejný obor transakcí, která se používá k načtení zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-162">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="c6e16-163">V tomto příkladu používáme základní databáze k ukládání informací o pořadí nákupní obsažené ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="c6e16-163">In this example, we use a basic database to store the purchase order information contained in the message.</span></span> <span data-ttu-id="c6e16-164">Obor transakce také zaručuje, že pokud metoda vyvolá výjimku, se vrátí zprávu do fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-164">The transaction scope also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="c6e16-165">Bez nastavení tohoto chování operace kanálu ve frontě vytvoří transakce čtení zprávy z fronty a potvrdí ji automaticky, předtím, než je odeslána, takže pokud se operace nezdaří, dojde ke ztrátě zprávy.</span><span class="sxs-lookup"><span data-stu-id="c6e16-165">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before it is dispatched so that if the operation fails, the message is lost.</span></span> <span data-ttu-id="c6e16-166">Nejběžnější scénář je pro operace služby k zařazení v transakci, která slouží k načtení zprávy z fronty, jak je ukázáno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c6e16-166">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue as demonstrated in the following code.</span></span>  
  
 <span data-ttu-id="c6e16-167">Všimněte si, že `ReleaseServiceInstanceOnTransactionComplete` je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="c6e16-167">Note that `ReleaseServiceInstanceOnTransactionComplete` is set to `false`.</span></span> <span data-ttu-id="c6e16-168">Toto je důležité požadavek pro dávkové zpracování.</span><span class="sxs-lookup"><span data-stu-id="c6e16-168">This is an important requirement for batching.</span></span> <span data-ttu-id="c6e16-169">Vlastnost `ReleaseServiceInstanceOnTransactionComplete` na `ServiceBehaviorAttribute` indikuje, co dělat s instancí služby, po dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-169">The property `ReleaseServiceInstanceOnTransactionComplete` on `ServiceBehaviorAttribute` indicates what to do with the service instance once the transaction is completed.</span></span> <span data-ttu-id="c6e16-170">Ve výchozím nastavení instance služby je uvolněn po dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-170">By default, the service instance is released upon completing the transaction.</span></span> <span data-ttu-id="c6e16-171">Základní aspekt pro dávkové zpracování je použití jedné transakce pro čtení a odesílání počet zpráv ve frontě.</span><span class="sxs-lookup"><span data-stu-id="c6e16-171">The core aspect to batching is the use of a single transaction for reading and dispatching many messages in the queue.</span></span> <span data-ttu-id="c6e16-172">Proto uvolňování instance služby končí dokončení transakce předčasně negace velmi použití dávkování.</span><span class="sxs-lookup"><span data-stu-id="c6e16-172">Therefore releasing the service instance ends up completing the transaction prematurely negating the very use of batching.</span></span> <span data-ttu-id="c6e16-173">Pokud je tato vlastnost nastavená na `true` a chování dávkového zpracování je přidán do koncového bodu, vyvolá výjimku, dávkování chování ověřování.</span><span class="sxs-lookup"><span data-stu-id="c6e16-173">If this property is set to `true` and transacted batching behavior is added to the endpoint, the batching validation behavior throws an exception.</span></span>  

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

 <span data-ttu-id="c6e16-174">`Orders` Třída zapouzdří zpracování objednávky.</span><span class="sxs-lookup"><span data-stu-id="c6e16-174">The `Orders` class encapsulates the processing of the order.</span></span> <span data-ttu-id="c6e16-175">V ukázce databáze se aktualizuje informace o objednávce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-175">In the sample, it updates the database with purchase order information.</span></span>  

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

 <span data-ttu-id="c6e16-176">Dávkování chování a jeho konfigurace jsou uvedeny v konfiguraci aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="c6e16-176">The batching behavior and its configuration are specified in the service application configuration.</span></span>  
  
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
>  <span data-ttu-id="c6e16-177">Velikost dávky se o nápovědu k systému.</span><span class="sxs-lookup"><span data-stu-id="c6e16-177">The batch size is a hint to the system.</span></span> <span data-ttu-id="c6e16-178">Například pokud chcete zadat velikost dávky 20, pak 20 zpráv četla a pomocí jedné transakce a pak je transakce potvrzena.</span><span class="sxs-lookup"><span data-stu-id="c6e16-178">For example, if you specify a batch size of 20, then 20 messages would be read and dispatched using a single transaction and then the transaction is committed.</span></span> <span data-ttu-id="c6e16-179">Ale existují případy, kde může transakci potvrdit dávku předtím, než je dosaženo velikost dávky.</span><span class="sxs-lookup"><span data-stu-id="c6e16-179">But there are cases where the transaction may commit the batch before the batch size is reached.</span></span>  
>   
>  <span data-ttu-id="c6e16-180">Spojené s každou transakci je časový limit, který se spustí tikání po vytvoření transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-180">Associated with every transaction is a timeout that starts ticking once the transaction is created.</span></span> <span data-ttu-id="c6e16-181">Když vyprší platnost tento časový limit transakce byla přerušena.</span><span class="sxs-lookup"><span data-stu-id="c6e16-181">When this timeout expires the transaction is aborted.</span></span> <span data-ttu-id="c6e16-182">Je možné pro tento časový limit vyprší ještě předtím, než je dosaženo velikost dávky.</span><span class="sxs-lookup"><span data-stu-id="c6e16-182">It is possible for this timeout to expire even before the batch size is reached.</span></span> <span data-ttu-id="c6e16-183">Aby se zabránilo znovu dávku práce z důvodu přerušení, `TransactedBatchingBehavior` kontroluje, jak dlouho zůstane v transakci.</span><span class="sxs-lookup"><span data-stu-id="c6e16-183">To avoid re-working the batch because of the abort, the `TransactedBatchingBehavior` checks to see how much time is left on the transaction.</span></span> <span data-ttu-id="c6e16-184">Pokud se využilo 80 % limitu transakcí, je transakce potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="c6e16-184">If 80% of the transaction timeout is used up, then the transaction is committed.</span></span>  
>   
>  <span data-ttu-id="c6e16-185">Pokud nejsou žádné další zprávy ve frontě a místo abyste čekali, plnění velikost dávky <xref:System.ServiceModel.Description.TransactedBatchingBehavior> potvrzení transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-185">If there are no more messages in the queue then instead of waiting for the fulfillment of the batch size the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> commits the transaction.</span></span>  
>   
>  <span data-ttu-id="c6e16-186">Volba velikosti dávky je závislá na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c6e16-186">The choice of the batch size is dependent on your application.</span></span> <span data-ttu-id="c6e16-187">Pokud velikost dávky je příliš malá, nelze získat požadovaný výkon.</span><span class="sxs-lookup"><span data-stu-id="c6e16-187">If the batch size is too small, you may not get the desired performance.</span></span> <span data-ttu-id="c6e16-188">Na druhé straně Pokud velikost dávky je příliš velká, může zhoršit výkon.</span><span class="sxs-lookup"><span data-stu-id="c6e16-188">On the other hand if the batch size is too big, it may deteriorate performance.</span></span> <span data-ttu-id="c6e16-189">Například transakce může již live a podržte zámky ve vaší databázi nebo transakce může stát dead uzamčen, které by mohly způsobit batch k získání vrátit zpět a vrátit ke svému práce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-189">For example, your transaction could live longer and hold locks on your database or your transaction could become dead locked, which could cause the batch to get rolled back and to redo the work.</span></span>  
  
 <span data-ttu-id="c6e16-190">Klient vytvoří obor transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-190">The client creates a transaction scope.</span></span> <span data-ttu-id="c6e16-191">Komunikace s frontou probíhá v rámci oboru transakcí, vyvolá zacházet jako atomickou jednotku, kde jsou všechny zprávy odeslané do fronty nebo jsou žádné zprávy odeslané do fronty.</span><span class="sxs-lookup"><span data-stu-id="c6e16-191">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="c6e16-192">Transakce se potvrdí při volání <xref:System.Transactions.TransactionScope.Complete%2A> v oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="c6e16-192">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  

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

 <span data-ttu-id="c6e16-193">Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="c6e16-193">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="c6e16-194">Můžete zobrazit přijetí zprávy služby z klienta.</span><span class="sxs-lookup"><span data-stu-id="c6e16-194">You can see the service receive messages from the client.</span></span> <span data-ttu-id="c6e16-195">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="c6e16-195">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="c6e16-196">Mějte na paměti, protože služba Řízení front se používá, klient a služba nemusí být zprovoznit ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="c6e16-196">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="c6e16-197">Můžete spustit klienta, vypněte ho a spusťte službu a stále přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="c6e16-197">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="c6e16-198">Postupné výstup můžete prohlédnout, jak číst v dávce a zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="c6e16-198">You can see a rolling output as messages are read in a batch and processed.</span></span>  
  
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
>  <span data-ttu-id="c6e16-199">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="c6e16-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c6e16-200">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c6e16-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c6e16-201">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c6e16-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6e16-202">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c6e16-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a><span data-ttu-id="c6e16-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6e16-203">See Also</span></span>
