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
# <a name="transport-custom-transactions-over-udp-sample"></a>Přenos: Ukázka vlastních transakcí přes UDP
Tato ukázka je založena na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka v Windows Communication Foundation (WCF)[transport rozšiřitelnost](../../../../docs/framework/wcf/samples/transport-extensibility.md). Rozšiřuje ukázku Přenosu UDP pro podporu vlastní transakce toku <xref:System.ServiceModel.Channels.TransactionMessageProperty> a ukazuje použití vlastnosti.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Změny kódu v ukázce přenosu UDP  
 Chcete-li prokázat tok transakce, `ICalculatorContract` ukázka změní `CalculatorService.Add()`servisní smlouvy pro vyžadovat rozsah transakce pro . Ukázka také přidá `System.Guid` další parametr smlouvy `Add` operace. Tento parametr se používá k předání identifikátoru transakce klienta službě.  
  
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
  
 [Transport: Ukázka UDP](../../../../docs/framework/wcf/samples/transport-udp.md) používá pakety UDP k předání zpráv mezi klientem a službou. [Přenos: Vlastní transport ukázka](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) používá stejný mechanismus k přenosu zpráv, ale při toku transakce, je vložen do paketu UDP spolu s kódované zprávy.  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`je pomocná metoda, která obsahuje nové funkce pro sloučení tokenu šíření pro aktuální transakci s entitou zprávy a umístěte ji do vyrovnávací paměti.  
  
 Pro vlastní přenos toku transakcí implementace klienta musí vědět, jaké operace služby vyžadují tok transakcí a předat tyto informace WCF. Měl by také existovat mechanismus pro přenos transakce uživatele do transportní vrstvy. Tato ukázka používá "WCF zprávy inspektoři" získat tyto informace. Inspektor zpráv klienta implementovaný `TransactionFlowInspector`zde, který se nazývá , provádí následující úkoly:  
  
- Určuje, zda transakce musí být tok pro danou akci `IsTxFlowRequiredForThisOperation()`zprávy (to probíhá v ).  
  
- Připojí aktuální okolí transakce ke `TransactionFlowProperty`zprávě pomocí , pokud transakce je nutné tok (to se provádí v `BeforeSendRequest()`).  
  
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
  
 Sám `TransactionFlowInspector` je předán do rámce pomocí vlastní `TransactionFlowBehavior`chování: .  
  
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
  
 S předchozí mechanismus na místě, uživatelský `TransactionScope` kód vytvoří před voláním operace služby. Inspektor zprávy zajišťuje, že transakce je předána do přenosu v případě, že je nutné, aby tok do operace služby.  
  
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
  
 Po obdržení paketu UDP od klienta služba deserializuje extrahovat zprávu a případně transakce.  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()`je pomocná metoda, která stornuje `TransactionMessageBuffer.WriteTransactionMessageBuffer()`proces serializace prováděný společností .  
  
 Pokud transakce byla tok v, je připojen ke `TransactionMessageProperty`zprávě v .  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Tím zajistíte, že dispečer vyzvedne transakci v době odeslání a použije ji při volání operace služby adresované zprávou.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Aktuální vzorek by měl být spuštěn podobně jako [transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku. Chcete-li spustit, spusťte službu s UdpTestService.exe. Pokud používáte systém Windows Vista, je nutné spustit službu se zvýšenými oprávněními. Chcete-li tak učinit, klepněte v Průzkumníkovi souborů pravým tlačítkem myši na soubor UdpTestService.exe a klepněte na příkaz **Spustit jako správce**.  
  
3. Výsledkem je následující výstup.  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. V tomto okamžiku můžete spustit klienta spuštěním UdpTestClient.exe. Výstup vytvořený klientem je následující.  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. Výstup služby je následující.  
  
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
  
6. Aplikace služby zobrazí `The client transaction has flowed to the service` zprávu, pokud může odpovídat identifikátor u `clientTransactionId` transakce `CalculatorService.Add()` odeslaný klientem v parametru operace s identifikátorem transakce služby. Shoda je získána pouze v případě, že transakce klienta tekla do služby.  
  
7. Chcete-li spustit klientskou aplikaci proti koncovým bodům publikovaným pomocí konfigurace, stiskněte klávesu ENTER v okně aplikace služby a spusťte testovacího klienta znovu. Měli byste vidět následující výstup na službu.  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. Spuštění klienta proti službě nyní vytváří podobný výstup jako dříve.  
  
9. Chcete-li znovu vygenerovat klientský kód a konfiguraci pomocí programu Svcutil.exe, spusťte aplikaci služby a spusťte následující příkaz Svcutil.exe z kořenového adresáře ukázky.  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Všimněte si, že Svcutil.exe negeneruje `sampleProfileUdpBinding`konfiguraci rozšíření vazby pro ; je nutné jej přidat ručně.  
  
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
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Viz také

- [Přenos: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
