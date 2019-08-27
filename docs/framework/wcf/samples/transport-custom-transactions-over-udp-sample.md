---
title: 'Přenos: Ukázka vlastních transakcí přes UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: aeab56c122cff4c8a1ee87cb067f03ee0c2f3227
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044706"
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Přenos: Ukázka vlastních transakcí přes UDP
Tato ukázka je založena na [přenosu: Ukázka](../../../../docs/framework/wcf/samples/transport-udp.md) UDP v[rozšíření přenosu](../../../../docs/framework/wcf/samples/transport-extensibility.md)Windows Communication Foundation (WCF). Rozšiřuje ukázku přenosu UDP pro podporu toku vlastní transakce a demonstruje použití <xref:System.ServiceModel.Channels.TransactionMessageProperty> vlastnosti.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Změny kódu v ukázce přenosu UDP  
 Pro ukázku toku transakce ukázka mění kontrakt `ICalculatorContract` služby, aby vyžadovala rozsah transakce pro. `CalculatorService.Add()` Ukázka také přidá k kontraktu `System.Guid` `Add` operace další parametr. Tento parametr slouží k předání identifikátoru transakce klienta službě.  
  
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
  
 [Přenos: Ukázka](../../../../docs/framework/wcf/samples/transport-udp.md) UDP používá k předávání zpráv mezi klientem a službou pakety UDP. [Přenos: Ukázka](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) vlastního přenosu používá stejný mechanismus pro přenos zpráv, ale při přetečení transakce je vložena do paketu UDP spolu s kódovanými zprávami.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`je pomocná metoda, která obsahuje nové funkce pro sloučení tokenu šíření pro aktuální transakci s entitou zprávy a její umístění do vyrovnávací paměti.  
  
 V případě přenosu vlastního toku transakce musí implementace klientů znát, jaké operace služeb vyžadují tok transakcí a předávat tyto informace do WCF. Měl by existovat i mechanismus pro přenos uživatelské transakce do transportní vrstvy. V této ukázce se k získání těchto informací používá "kontroloři zpráv WCF". Inspektor zprávy klienta, který je `TransactionFlowInspector`implementován zde, provádí následující úlohy:  
  
- Určuje, zda musí být transakce předána do toku pro danou akci zprávy (k tomu dojde `IsTxFlowRequiredForThisOperation()`v rámci).  
  
- Připojí aktuální ambientní transakci ke zprávě pomocí `TransactionFlowProperty`, pokud je nutné transakci přesměrovat (to je provedeno v `BeforeSendRequest()`).  
  
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
  
 Samotný je předán do rozhraní pomocí vlastního chování `TransactionFlowBehavior`:. `TransactionFlowInspector`  
  
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
  
 `TransactionScope` Před tím, než se zahájí předchozí mechanismus, kód uživatele vytvoří před voláním operace služby. Kontrola zprávy zajišťuje, aby transakce byla předána do přepravy v případě, že je nutné ji přesměrovat na operaci služby.  
  
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
  
 Po přijetí paketu UDP od klienta služba ho deserializace extrahuje a případně transakci.  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()`je pomocná metoda, která vrátí proces serializace, kterou `TransactionMessageBuffer.WriteTransactionMessageBuffer()`provádí.  
  
 Pokud byla transakce převedena do, připojí se ke zprávě v `TransactionMessageProperty`.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Tím je zajištěno, že dispečer vezme transakci v době odeslání a použije ji při volání operace služby řešené zprávou.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Aktuální vzorek by měl běžet podobně [jako přenos: Ukázka](../../../../docs/framework/wcf/samples/transport-udp.md) UDP Pokud ho chcete spustit, spusťte službu pomocí UdpTestService. exe. Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], musíte službu spustit se zvýšenými oprávněními. Provedete to tak, že kliknete pravým tlačítkem na UdpTestService. exe v Průzkumníkovi souborů a kliknete na **Spustit jako správce**.  
  
3. Tím se vytvoří následující výstup.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. V tuto chvíli můžete spustit klienta spuštěním UdpTestClient. exe. Výstup vytvářený klientem je následující.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. Výstup služby je následující.  
  
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
  
6. Aplikace služby zobrazí zprávu `The client transaction has flowed to the service` , pokud se může shodovat s identifikátorem transakce odeslaným klientem `clientTransactionId` v parametru `CalculatorService.Add()` operace na identifikátor transakce služby. Shoda se získá jenom v případě, že transakce klienta přechází do služby.  
  
7. Chcete-li spustit klientskou aplikaci proti koncovým bodům publikovaným pomocí konfigurace, stiskněte klávesu ENTER v okně aplikace služby a spusťte testovacího klienta znovu. Ve službě by se měl zobrazit následující výstup.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. Spuštění klienta proti službě teď vytvoří podobný výstup jako dřív.  
  
9. Chcete-li znovu vygenerovat kód klienta a konfiguraci pomocí nástroje Svcutil. exe, spusťte aplikaci služby a spusťte následující příkaz Svcutil. exe z kořenového adresáře ukázky.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Všimněte si, že Svcutil. exe negeneruje konfiguraci rozšíření vazby pro `sampleProfileUdpBinding`. je nutné ho přidat ručně.  
  
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
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Viz také:

- [Přepravu UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
