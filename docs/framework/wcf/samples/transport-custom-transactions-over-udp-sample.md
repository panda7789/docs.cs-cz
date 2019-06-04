---
title: 'Přenos: Ukázka vlastních transakcí přes UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: 8a7b0c4e9ea73fa952710f2b415082b56062dad0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483098"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="021ff-102">Přenos: Ukázka vlastních transakcí přes UDP</span><span class="sxs-lookup"><span data-stu-id="021ff-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="021ff-103">Tato ukázka je založena na [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázku ve Windows Communication Foundation (WCF)[rozšiřitelnost přenosů](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="021ff-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="021ff-104">Rozšiřuje podporu toku transakcí vlastní ukázku přenos UDP a demonstruje použití <xref:System.ServiceModel.Channels.TransactionMessageProperty> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="021ff-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="021ff-105">Změny kódu v ukázce přenosu UDP</span><span class="sxs-lookup"><span data-stu-id="021ff-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="021ff-106">Abychom si předvedli tok transakcí, ukázka změní kontrakt služby pro `ICalculatorContract` tak, aby vyžadovala oboru transakce pro `CalculatorService.Add()`.</span><span class="sxs-lookup"><span data-stu-id="021ff-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="021ff-107">Ukázka přidá také speciální `System.Guid` parametr kontraktu `Add` operace.</span><span class="sxs-lookup"><span data-stu-id="021ff-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="021ff-108">Tento parametr se používá k předání identifikátor transakce klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="021ff-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);              
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="021ff-109">[Přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Ukázka používá k předávání zpráv mezi klientem a službou UDP paketů.</span><span class="sxs-lookup"><span data-stu-id="021ff-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="021ff-110">[Přenosu: Přenos ukázková](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) používá stejný mechanismus pro přenos zpráv, ale když je počet plynoucích transakcí, je vložen do UDP paketů spolu s kódováním zpráv.</span><span class="sxs-lookup"><span data-stu-id="021ff-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="021ff-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` je pomocná metoda, která obsahuje novou funkci pro sloučení token šíření hodnoty pro aktuální transakce s entitou zprávy a umístěte ho do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="021ff-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="021ff-112">Pro tok transport vlastní transakce, musíte znát implementace klienta, jaké operace služby vyžaduje tok transakce a předávat tyto informace WCF.</span><span class="sxs-lookup"><span data-stu-id="021ff-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="021ff-113">Měla by existovat i mechanismus pro předávání uživatelské transakce do přenosové vrstvy.</span><span class="sxs-lookup"><span data-stu-id="021ff-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="021ff-114">Tato ukázka používá "Inspektoři zpráv WCF" pro získání těchto informací.</span><span class="sxs-lookup"><span data-stu-id="021ff-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="021ff-115">Klienta zpráva inspektor implementované tady, která se nazývá `TransactionFlowInspector`, provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="021ff-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="021ff-116">Určuje, zda musí počet plynoucích transakcí pro danou zprávu akci (Tato akce se provede `IsTxFlowRequiredForThisOperation()`).</span><span class="sxs-lookup"><span data-stu-id="021ff-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="021ff-117">Připojí aktuální okolí transakce do zprávy pomocí `TransactionFlowProperty`, pokud se vyžaduje tok transakce (to se provádí v `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="021ff-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;             
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;              
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="021ff-118">`TransactionFlowInspector` Samotného je předán rozhraní framework pomocí vlastního chování: `TransactionFlowBehavior`.</span><span class="sxs-lookup"><span data-stu-id="021ff-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="021ff-119">S předchozím mechanismus v místě, vytvoří kód uživatele `TransactionScope` před voláním operace služby.</span><span class="sxs-lookup"><span data-stu-id="021ff-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="021ff-120">Inspektor zpráv zajišťuje, že transakce je předán do přenosu v případě, že je potřeba být převedena do operace služby.</span><span class="sxs-lookup"><span data-stu-id="021ff-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());               
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }               
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="021ff-121">Při přijetí UDP paketů z klienta, služba ho deserializuje extrahovat zprávy a případně transakce.</span><span class="sxs-lookup"><span data-stu-id="021ff-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="021ff-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` je pomocná metoda, která obrací procesu serializace provádí `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span><span class="sxs-lookup"><span data-stu-id="021ff-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="021ff-123">Pokud v byla převedena do transakce, je připojen na tuto zprávu najdete v `TransactionMessageProperty`.</span><span class="sxs-lookup"><span data-stu-id="021ff-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="021ff-124">Tím se zajistí, že dispečer vybere transakce v okamžiku odeslání a při volání operace služby řešený zprávy ji používá.</span><span class="sxs-lookup"><span data-stu-id="021ff-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="021ff-125">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="021ff-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="021ff-126">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="021ff-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="021ff-127">Aktuální ukázky by měl být spuštěn, podobně jako [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="021ff-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="021ff-128">K jeho spuštění spusťte službu s UdpTestService.exe.</span><span class="sxs-lookup"><span data-stu-id="021ff-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="021ff-129">Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], musíte spustit službu se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="021ff-129">If you are running [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must start the service with elevated privileges.</span></span> <span data-ttu-id="021ff-130">Uděláte to tak, UdpTestService.exe v Průzkumníku souborů klikněte pravým tlačítkem myši a klikněte na tlačítko **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="021ff-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="021ff-131">To vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="021ff-131">This produces the following output.</span></span>  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="021ff-132">V současné době může spuštění klienta spuštěním UdpTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="021ff-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="021ff-133">Výstup vytvořený klienta vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="021ff-133">The output produced by the client is as follows.</span></span>  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="021ff-134">Služba výstup vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="021ff-134">The service output is as follows.</span></span>  
  
    ```  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6. <span data-ttu-id="021ff-135">Aplikace služby zobrazí zprávu `The client transaction has flowed to the service` Pokud by odpovídat v odesílaném klientem, identifikátor transakce `clientTransactionId` parametr `CalculatorService.Add()` operace, identifikátor transakce služby.</span><span class="sxs-lookup"><span data-stu-id="021ff-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="021ff-136">Shoda se získá jenom v případě, že klientská transakce prochází ke službě.</span><span class="sxs-lookup"><span data-stu-id="021ff-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="021ff-137">Ke spuštění klientské aplikace publikované pomocí konfigurace koncových bodů, stiskněte klávesu ENTER na okno aplikace služby a poté znovu spusťte testovací klient.</span><span class="sxs-lookup"><span data-stu-id="021ff-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="021ff-138">Ve službě byste měli vidět následující výstup.</span><span class="sxs-lookup"><span data-stu-id="021ff-138">You should see the following output on the service.</span></span>  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="021ff-139">Podobný výstup jako spuštění klienta na službu nyní vytvoří stejně jako předtím.</span><span class="sxs-lookup"><span data-stu-id="021ff-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="021ff-140">Znovu vygenerovat kód klienta a konfigurace pomocí Svcutil.exe, spusťte aplikaci služby a pak spusťte následující příkaz Svcutil.exe z kořenového adresáře vzorku.</span><span class="sxs-lookup"><span data-stu-id="021ff-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="021ff-141">Všimněte si, že Svcutil.exe negeneruje pro konfiguraci rozšíření vazby `sampleProfileUdpBinding`; je třeba přidat ji ručně.</span><span class="sxs-lookup"><span data-stu-id="021ff-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>      
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="021ff-142">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="021ff-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="021ff-143">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="021ff-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="021ff-144">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="021ff-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="021ff-145">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="021ff-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="021ff-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="021ff-146">See also</span></span>

- [<span data-ttu-id="021ff-147">Přenos: UDP</span><span class="sxs-lookup"><span data-stu-id="021ff-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)
