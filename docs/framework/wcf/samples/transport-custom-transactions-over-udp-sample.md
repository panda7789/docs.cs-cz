---
title: 'Přenos: Ukázka vlastních transakcí přes UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: ba9fb91623606d3aaba5ba56784b20bb92d343a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143795"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="34139-102">Přenos: Ukázka vlastních transakcí přes UDP</span><span class="sxs-lookup"><span data-stu-id="34139-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="34139-103">Tato ukázka je založena na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka v Windows Communication Foundation (WCF)[transport rozšiřitelnost](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="34139-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="34139-104">Rozšiřuje ukázku Přenosu UDP pro podporu vlastní transakce toku <xref:System.ServiceModel.Channels.TransactionMessageProperty> a ukazuje použití vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="34139-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="34139-105">Změny kódu v ukázce přenosu UDP</span><span class="sxs-lookup"><span data-stu-id="34139-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="34139-106">Chcete-li prokázat tok transakce, `ICalculatorContract` ukázka změní `CalculatorService.Add()`servisní smlouvy pro vyžadovat rozsah transakce pro .</span><span class="sxs-lookup"><span data-stu-id="34139-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="34139-107">Ukázka také přidá `System.Guid` další parametr smlouvy `Add` operace.</span><span class="sxs-lookup"><span data-stu-id="34139-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="34139-108">Tento parametr se používá k předání identifikátoru transakce klienta službě.</span><span class="sxs-lookup"><span data-stu-id="34139-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
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
  
 <span data-ttu-id="34139-109">[Transport: Ukázka UDP](../../../../docs/framework/wcf/samples/transport-udp.md) používá pakety UDP k předání zpráv mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="34139-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="34139-110">[Přenos: Vlastní transport ukázka](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) používá stejný mechanismus k přenosu zpráv, ale při toku transakce, je vložen do paketu UDP spolu s kódované zprávy.</span><span class="sxs-lookup"><span data-stu-id="34139-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="34139-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer`je pomocná metoda, která obsahuje nové funkce pro sloučení tokenu šíření pro aktuální transakci s entitou zprávy a umístěte ji do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="34139-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="34139-112">Pro vlastní přenos toku transakcí implementace klienta musí vědět, jaké operace služby vyžadují tok transakcí a předat tyto informace WCF.</span><span class="sxs-lookup"><span data-stu-id="34139-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="34139-113">Měl by také existovat mechanismus pro přenos transakce uživatele do transportní vrstvy.</span><span class="sxs-lookup"><span data-stu-id="34139-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="34139-114">Tato ukázka používá "WCF zprávy inspektoři" získat tyto informace.</span><span class="sxs-lookup"><span data-stu-id="34139-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="34139-115">Inspektor zpráv klienta implementovaný `TransactionFlowInspector`zde, který se nazývá , provádí následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="34139-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="34139-116">Určuje, zda transakce musí být tok pro danou akci `IsTxFlowRequiredForThisOperation()`zprávy (to probíhá v ).</span><span class="sxs-lookup"><span data-stu-id="34139-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="34139-117">Připojí aktuální okolí transakce ke `TransactionFlowProperty`zprávě pomocí , pokud transakce je nutné tok (to se provádí v `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="34139-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
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
  
 <span data-ttu-id="34139-118">Sám `TransactionFlowInspector` je předán do rámce pomocí vlastní `TransactionFlowBehavior`chování: .</span><span class="sxs-lookup"><span data-stu-id="34139-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
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
  
 <span data-ttu-id="34139-119">S předchozí mechanismus na místě, uživatelský `TransactionScope` kód vytvoří před voláním operace služby.</span><span class="sxs-lookup"><span data-stu-id="34139-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="34139-120">Inspektor zprávy zajišťuje, že transakce je předána do přenosu v případě, že je nutné, aby tok do operace služby.</span><span class="sxs-lookup"><span data-stu-id="34139-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
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
  
 <span data-ttu-id="34139-121">Po obdržení paketu UDP od klienta služba deserializuje extrahovat zprávu a případně transakce.</span><span class="sxs-lookup"><span data-stu-id="34139-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="34139-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()`je pomocná metoda, která stornuje `TransactionMessageBuffer.WriteTransactionMessageBuffer()`proces serializace prováděný společností .</span><span class="sxs-lookup"><span data-stu-id="34139-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="34139-123">Pokud transakce byla tok v, je připojen ke `TransactionMessageProperty`zprávě v .</span><span class="sxs-lookup"><span data-stu-id="34139-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="34139-124">Tím zajistíte, že dispečer vyzvedne transakci v době odeslání a použije ji při volání operace služby adresované zprávou.</span><span class="sxs-lookup"><span data-stu-id="34139-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="34139-125">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="34139-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="34139-126">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="34139-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="34139-127">Aktuální vzorek by měl být spuštěn podobně jako [transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="34139-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="34139-128">Chcete-li spustit, spusťte službu s UdpTestService.exe.</span><span class="sxs-lookup"><span data-stu-id="34139-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="34139-129">Pokud používáte systém Windows Vista, je nutné spustit službu se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="34139-129">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="34139-130">Chcete-li tak učinit, klepněte v Průzkumníkovi souborů pravým tlačítkem myši na soubor UdpTestService.exe a klepněte na příkaz **Spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="34139-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="34139-131">Výsledkem je následující výstup.</span><span class="sxs-lookup"><span data-stu-id="34139-131">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="34139-132">V tomto okamžiku můžete spustit klienta spuštěním UdpTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="34139-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="34139-133">Výstup vytvořený klientem je následující.</span><span class="sxs-lookup"><span data-stu-id="34139-133">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="34139-134">Výstup služby je následující.</span><span class="sxs-lookup"><span data-stu-id="34139-134">The service output is as follows.</span></span>  
  
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
  
6. <span data-ttu-id="34139-135">Aplikace služby zobrazí `The client transaction has flowed to the service` zprávu, pokud může odpovídat identifikátor u `clientTransactionId` transakce `CalculatorService.Add()` odeslaný klientem v parametru operace s identifikátorem transakce služby.</span><span class="sxs-lookup"><span data-stu-id="34139-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="34139-136">Shoda je získána pouze v případě, že transakce klienta tekla do služby.</span><span class="sxs-lookup"><span data-stu-id="34139-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="34139-137">Chcete-li spustit klientskou aplikaci proti koncovým bodům publikovaným pomocí konfigurace, stiskněte klávesu ENTER v okně aplikace služby a spusťte testovacího klienta znovu.</span><span class="sxs-lookup"><span data-stu-id="34139-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="34139-138">Měli byste vidět následující výstup na službu.</span><span class="sxs-lookup"><span data-stu-id="34139-138">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="34139-139">Spuštění klienta proti službě nyní vytváří podobný výstup jako dříve.</span><span class="sxs-lookup"><span data-stu-id="34139-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="34139-140">Chcete-li znovu vygenerovat klientský kód a konfiguraci pomocí programu Svcutil.exe, spusťte aplikaci služby a spusťte následující příkaz Svcutil.exe z kořenového adresáře ukázky.</span><span class="sxs-lookup"><span data-stu-id="34139-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="34139-141">Všimněte si, že Svcutil.exe negeneruje `sampleProfileUdpBinding`konfiguraci rozšíření vazby pro ; je nutné jej přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="34139-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
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
> <span data-ttu-id="34139-142">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="34139-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="34139-143">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="34139-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="34139-144">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="34139-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34139-145">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="34139-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="34139-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="34139-146">See also</span></span>

- [<span data-ttu-id="34139-147">Přenos: UDP</span><span class="sxs-lookup"><span data-stu-id="34139-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)
