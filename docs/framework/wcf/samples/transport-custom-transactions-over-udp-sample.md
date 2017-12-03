---
title: "Přenos: Ukázka vlastních transakcí přes UDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b17cb737533f1542b5f702097da4592df8e17eac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Přenos: Ukázka vlastních transakcí přes UDP
Tato ukázka je založena na [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázku v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] [rozšiřitelnost přenosů](../../../../docs/framework/wcf/samples/transport-extensibility.md). Ji rozšiřuje ukázka přenosu UDP pro podporu toku vlastní transakcí a demonstruje použití <xref:System.ServiceModel.Channels.TransactionMessageProperty> vlastnost.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Změny kódu v ukázce přenosu UDP  
 K předvedení toku transakcí, ukázky změní kontrakt služby pro `ICalculatorContract` tak, aby vyžadovala oboru transakce pro `CalculatorService.Add()`. Ukázka také přidá další `System.Guid` parametr smlouvy o `Add` operaci. Tento parametr slouží k předávání identifikátor transakce klienta ke službě.  
  
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
  
 [Přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Ukázka používá pakety UDP pro předávání zpráv mezi klientem a služby. [Přenos: Ukázka přenosu vlastní](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) používá stejný mechanismus pro přenos zpráv, ale pokud je počet plynoucích transakcí, je vložen do UDP paketů společně s kódované zprávy.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`je pomocná metoda, která obsahuje novou funkci pro sloučení šíření token pro aktuální transakci s entitou, zprávu a umístěte ji do vyrovnávací paměti.  
  
 Pro vlastní transakce tok přenosu, musíte znát implementace klienta, jaké operace služby vyžadují toku transakcí a předávat tyto informace k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Měla by být mechanismus pro přenos uživatelská transakce do přenosové vrstvy. V tomto příkladu "[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy inspektoři" pro získání těchto informací. Klient zpráva kontrolor implementována tady, se nazývá `TransactionFlowInspector`, provede následující úlohy:  
  
-   Určuje, zda transakce musí být plynoucích pro akci s danou zprávou (to probíhá `IsTxFlowRequiredForThisOperation()`).  
  
-   Připojí aktuální vedlejším transakce na zprávu pomocí `TransactionFlowProperty`, pokud je požadována zalomen transakce (to se provádí v `BeforeSendRequest()`).  
  
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
  
 `TransactionFlowInspector` Samotné předaný framework pomocí vlastní chování: `TransactionFlowBehavior`.  
  
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
  
 U předchozích mechanismus na místě, vytvoří kód uživatele `TransactionScope` před voláním operace služby. Zpráva inspector zajistí, že transakce je předán do přenosu v případě, že je potřeba být předávány operaci služby.  
  
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
  
 Po přijetí UDP paketů z klienta, službu deserializuje ho k extrakci zprávu a případně transakce.  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()`je pomocná metoda, která obrátí proces serializace provádí `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.  
  
 Pokud transakce byla plynoucích v, je připojen ke zprávě v `TransactionMessageProperty`.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 To zajišťuje, že dispečera převezme transakce během odesílání a použije při volání operace služby řešit zprávy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Aktuální ukázka by měl být spuštěn podobně jako [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka. Chcete-li jej spustit, spusťte službu s UdpTestService.exe. Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], je nutné spustit službu se zvýšenými oprávněními. Chcete-li to provést, klikněte pravým tlačítkem UdpTestService.exe v [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a klikněte na tlačítko **spustit jako správce**.  
  
3.  To vytvoří následující výstup.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  V tomto okamžiku můžete spustit klienta spuštěním UdpTestClient.exe. Výstup vytvořený klientem je následující.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  Výstup služby je následující.  
  
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
  
6.  Aplikace služby zobrazí zprávu `The client transaction has flowed to the service` pokud ho může odpovídat identifikátor transakce odeslaných klientem v `clientTransactionId` parametr `CalculatorService.Add()` operace, identifikátor transakce služby. Shoda se získávají pouze v případě, že klientská transakce prochází ke službě.  
  
7.  Ke spouštění klientskou aplikaci publikovat pomocí konfigurace koncových bodů, stiskněte klávesu ENTER v okně aplikace služby a poté znovu spusťte testovacího klienta. Měli byste vidět následující výstup ve službě.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  Podobný výstup spuštěným klienta pro službu nyní vytvoří jako předtím.  
  
9. Znovu vygenerovat kód klienta a konfigurace pomocí Svcutil.exe, spusťte aplikaci služby a potom spusťte následující příkaz Svcutil.exe z kořenového adresáře vzorku.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Všimněte si, že Svcutil.exe negeneruje vazby konfigurace rozšíření pro `sampleProfileUdpBinding`; je třeba přidat ji ručně.  
  
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
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Viz také  
 [Přenos: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
