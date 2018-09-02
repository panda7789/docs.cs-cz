---
title: 'Přenos: Ukázka vlastních transakcí přes UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: b3a105194ceef9d9091dfbc9521fd47978517f89
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452713"
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Přenos: Ukázka vlastních transakcí přes UDP
Tato ukázka je založena na [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázku ve Windows Communication Foundation (WCF)[rozšiřitelnost přenosů](../../../../docs/framework/wcf/samples/transport-extensibility.md). Rozšiřuje podporu toku transakcí vlastní ukázku přenos UDP a demonstruje použití <xref:System.ServiceModel.Channels.TransactionMessageProperty> vlastnost.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Změny kódu v ukázce přenosu UDP  
 Abychom si předvedli tok transakcí, ukázka změní kontrakt služby pro `ICalculatorContract` tak, aby vyžadovala oboru transakce pro `CalculatorService.Add()`. Ukázka přidá také speciální `System.Guid` parametr kontraktu `Add` operace. Tento parametr se používá k předání identifikátor transakce klienta ke službě.  
  
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
  
 [Přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Ukázka používá k předávání zpráv mezi klientem a službou UDP paketů. [Přenos: Ukázka přenosu vlastní](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) používá stejný mechanismus pro přenos zpráv, ale když je počet plynoucích transakcí, je vložen do UDP paketů spolu s kódováním zpráv.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer` je pomocná metoda, která obsahuje novou funkci pro sloučení token šíření hodnoty pro aktuální transakce s entitou zprávy a umístěte ho do vyrovnávací paměti.  
  
 Pro tok transport vlastní transakce, musíte znát implementace klienta, jaké operace služby vyžaduje tok transakce a předávat tyto informace WCF. Měla by existovat i mechanismus pro předávání uživatelské transakce do přenosové vrstvy. Tato ukázka používá "Inspektoři zpráv WCF" pro získání těchto informací. Klienta zpráva inspektor implementované tady, která se nazývá `TransactionFlowInspector`, provede následující úlohy:  
  
-   Určuje, zda musí počet plynoucích transakcí pro danou zprávu akci (Tato akce se provede `IsTxFlowRequiredForThisOperation()`).  
  
-   Připojí aktuální okolí transakce do zprávy pomocí `TransactionFlowProperty`, pokud se vyžaduje tok transakce (to se provádí v `BeforeSendRequest()`).  
  
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
  
 `TransactionFlowInspector` Samotného je předán rozhraní framework pomocí vlastního chování: `TransactionFlowBehavior`.  
  
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
  
 S předchozím mechanismus v místě, vytvoří kód uživatele `TransactionScope` před voláním operace služby. Inspektor zpráv zajišťuje, že transakce je předán do přenosu v případě, že je potřeba být převedena do operace služby.  
  
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
  
 Při přijetí UDP paketů z klienta, služba ho deserializuje extrahovat zprávy a případně transakce.  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()` je pomocná metoda, která obrací procesu serializace provádí `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.  
  
 Pokud v byla převedena do transakce, je připojen na tuto zprávu najdete v `TransactionMessageProperty`.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Tím se zajistí, že dispečer vybere transakce v okamžiku odeslání a při volání operace služby řešený zprávy ji používá.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Aktuální ukázky by měl být spuštěn, podobně jako [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku. K jeho spuštění spusťte službu s UdpTestService.exe. Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], musíte spustit službu se zvýšenými oprávněními. Chcete-li to provést, klikněte pravým tlačítkem na UdpTestService.exe v [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a klikněte na tlačítko **spustit jako správce**.  
  
3.  To vytvoří následující výstup.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  V současné době může spuštění klienta spuštěním UdpTestClient.exe. Výstup vytvořený klienta vypadá takto.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  Služba výstup vypadá takto.  
  
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
  
6.  Aplikace služby zobrazí zprávu `The client transaction has flowed to the service` Pokud by odpovídat v odesílaném klientem, identifikátor transakce `clientTransactionId` parametr `CalculatorService.Add()` operace, identifikátor transakce služby. Shoda se získá jenom v případě, že klientská transakce prochází ke službě.  
  
7.  Ke spuštění klientské aplikace publikované pomocí konfigurace koncových bodů, stiskněte klávesu ENTER na okno aplikace služby a poté znovu spusťte testovací klient. Ve službě byste měli vidět následující výstup.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  Podobný výstup jako spuštění klienta na službu nyní vytvoří stejně jako předtím.  
  
9. Znovu vygenerovat kód klienta a konfigurace pomocí Svcutil.exe, spusťte aplikaci služby a pak spusťte následující příkaz Svcutil.exe z kořenového adresáře vzorku.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Všimněte si, že Svcutil.exe negeneruje pro konfiguraci rozšíření vazby `sampleProfileUdpBinding`; je třeba přidat ji ručně.  
  
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
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Viz také  
 [Přenos: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
