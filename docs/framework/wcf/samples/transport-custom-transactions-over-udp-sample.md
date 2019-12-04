---
title: 'Přenos: Ukázka vlastních transakcí přes UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: 09ce715da4cf4d4fb4c959f63af3bb2c8c68b841
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712006"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="637ec-102">Přenos: Ukázka vlastních transakcí přes UDP</span><span class="sxs-lookup"><span data-stu-id="637ec-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="637ec-103">Tato ukázka je založena na ukázce [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) v[rozšíření přenosu](../../../../docs/framework/wcf/samples/transport-extensibility.md)služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="637ec-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="637ec-104">Rozšiřuje ukázku přenosu UDP pro podporu toku vlastní transakce a demonstruje použití vlastnosti <xref:System.ServiceModel.Channels.TransactionMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="637ec-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="637ec-105">Změny kódu v ukázce přenosu UDP</span><span class="sxs-lookup"><span data-stu-id="637ec-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="637ec-106">Pro ukázku toku transakce ukázka mění kontrakt služby pro `ICalculatorContract` tak, aby vyžadoval obor transakce pro `CalculatorService.Add()`.</span><span class="sxs-lookup"><span data-stu-id="637ec-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="637ec-107">Ukázka také přidá další `System.Guid` parametr pro kontrakt operace `Add`.</span><span class="sxs-lookup"><span data-stu-id="637ec-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="637ec-108">Tento parametr slouží k předání identifikátoru transakce klienta službě.</span><span class="sxs-lookup"><span data-stu-id="637ec-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="637ec-109">Ukázka [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) používá k předávání zpráv mezi klientem a službou pakety UDP.</span><span class="sxs-lookup"><span data-stu-id="637ec-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="637ec-110">[Přenos: Ukázka vlastního přenosu](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) používá stejný mechanismus pro přenos zpráv, ale při přetečení transakce je vložena do paketu UDP spolu s kódovanými zprávami.</span><span class="sxs-lookup"><span data-stu-id="637ec-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="637ec-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` je pomocná metoda, která obsahuje nové funkce pro sloučení tokenu šíření pro aktuální transakci s entitou zprávy a její umístění do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="637ec-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="637ec-112">V případě přenosu vlastního toku transakce musí implementace klientů znát, jaké operace služeb vyžadují tok transakcí a předávat tyto informace do WCF.</span><span class="sxs-lookup"><span data-stu-id="637ec-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="637ec-113">Měl by existovat i mechanismus pro přenos uživatelské transakce do transportní vrstvy.</span><span class="sxs-lookup"><span data-stu-id="637ec-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="637ec-114">V této ukázce se k získání těchto informací používá "kontroloři zpráv WCF".</span><span class="sxs-lookup"><span data-stu-id="637ec-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="637ec-115">Inspektor zprávy klienta implementovaný zde, který se nazývá `TransactionFlowInspector`, provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="637ec-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="637ec-116">Určuje, zda musí být transakce předávána pro danou akci zprávy (k tomu dochází v `IsTxFlowRequiredForThisOperation()`).</span><span class="sxs-lookup"><span data-stu-id="637ec-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="637ec-117">Připojí aktuální ambientní transakci ke zprávě pomocí `TransactionFlowProperty`, pokud je nutné transakci přesměrovat (to se provádí v `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="637ec-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="637ec-118">`TransactionFlowInspector` sám se předává do architektury pomocí vlastního chování: `TransactionFlowBehavior`.</span><span class="sxs-lookup"><span data-stu-id="637ec-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="637ec-119">Před započetím předchozího mechanismu uživatelský kód vytvoří `TransactionScope` před voláním operace služby.</span><span class="sxs-lookup"><span data-stu-id="637ec-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="637ec-120">Kontrola zprávy zajišťuje, aby transakce byla předána do přepravy v případě, že je nutné ji přesměrovat na operaci služby.</span><span class="sxs-lookup"><span data-stu-id="637ec-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="637ec-121">Po přijetí paketu UDP od klienta služba ho deserializace extrahuje a případně transakci.</span><span class="sxs-lookup"><span data-stu-id="637ec-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="637ec-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` je pomocná metoda, která vrátí proces serializace prováděný `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span><span class="sxs-lookup"><span data-stu-id="637ec-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="637ec-123">Pokud byla transakce převedena do, připojí se ke zprávě v `TransactionMessageProperty`.</span><span class="sxs-lookup"><span data-stu-id="637ec-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="637ec-124">Tím je zajištěno, že dispečer vezme transakci v době odeslání a použije ji při volání operace služby řešené zprávou.</span><span class="sxs-lookup"><span data-stu-id="637ec-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="637ec-125">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="637ec-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="637ec-126">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="637ec-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="637ec-127">Aktuální vzorek by měl být spuštěn podobně jako ukázka [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="637ec-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="637ec-128">Pokud ho chcete spustit, spusťte službu pomocí UdpTestService. exe.</span><span class="sxs-lookup"><span data-stu-id="637ec-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="637ec-129">Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], musíte službu spustit se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="637ec-129">If you are running [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must start the service with elevated privileges.</span></span> <span data-ttu-id="637ec-130">Provedete to tak, že kliknete pravým tlačítkem na UdpTestService. exe v Průzkumníkovi souborů a kliknete na **Spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="637ec-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="637ec-131">Tím se vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="637ec-131">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="637ec-132">V tuto chvíli můžete spustit klienta spuštěním UdpTestClient. exe.</span><span class="sxs-lookup"><span data-stu-id="637ec-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="637ec-133">Výstup vytvářený klientem je následující.</span><span class="sxs-lookup"><span data-stu-id="637ec-133">The output produced by the client is as follows.</span></span>  
  
    ```console 
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="637ec-134">Výstup služby je následující.</span><span class="sxs-lookup"><span data-stu-id="637ec-134">The service output is as follows.</span></span>  
  
    ```console 
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
  
6. <span data-ttu-id="637ec-135">Aplikace služby zobrazí `The client transaction has flowed to the service` zprávy, pokud se může shodovat s identifikátorem transakce odeslaným klientem, v parametru `clientTransactionId` operace `CalculatorService.Add()` na identifikátor transakce služby.</span><span class="sxs-lookup"><span data-stu-id="637ec-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="637ec-136">Shoda se získá jenom v případě, že transakce klienta přechází do služby.</span><span class="sxs-lookup"><span data-stu-id="637ec-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="637ec-137">Chcete-li spustit klientskou aplikaci proti koncovým bodům publikovaným pomocí konfigurace, stiskněte klávesu ENTER v okně aplikace služby a spusťte testovacího klienta znovu.</span><span class="sxs-lookup"><span data-stu-id="637ec-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="637ec-138">Ve službě by se měl zobrazit následující výstup.</span><span class="sxs-lookup"><span data-stu-id="637ec-138">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="637ec-139">Spuštění klienta proti službě teď vytvoří podobný výstup jako dřív.</span><span class="sxs-lookup"><span data-stu-id="637ec-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="637ec-140">Chcete-li znovu vygenerovat kód klienta a konfiguraci pomocí nástroje Svcutil. exe, spusťte aplikaci služby a spusťte následující příkaz Svcutil. exe z kořenového adresáře ukázky.</span><span class="sxs-lookup"><span data-stu-id="637ec-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="637ec-141">Všimněte si, že Svcutil. exe negeneruje konfiguraci rozšíření vazby pro `sampleProfileUdpBinding`; musíte ho přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="637ec-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
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
> <span data-ttu-id="637ec-142">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="637ec-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="637ec-143">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="637ec-143">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="637ec-144">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="637ec-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="637ec-145">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="637ec-145">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="637ec-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="637ec-146">See also</span></span>

- [<span data-ttu-id="637ec-147">Přenos: UDP</span><span class="sxs-lookup"><span data-stu-id="637ec-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)
