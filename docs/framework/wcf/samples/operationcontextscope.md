---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: 581f75ece1a601b3baf590c1923a17a353de1ff1
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714609"
---
# <a name="operationcontextscope"></a>OperationContextScope
Ukázka OperationContextScope ukazuje, jak odeslat dodatečné informace o volání Windows Communication Foundation (WCF) pomocí hlaviček. V této ukázce jsou server i klient konzolové aplikace.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Ukázka předvádí, jak může klient odeslat další informace jako <xref:System.ServiceModel.Channels.MessageHeader> pomocí <xref:System.ServiceModel.OperationContextScope>. Objekt <xref:System.ServiceModel.OperationContextScope> se vytvoří jeho rozsahem na kanál. Hlavičky, které musí být přeloženy do vzdálené služby, lze přidat do kolekce <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A>. Hlavičky přidané do této kolekce se dají načíst do služby přístupem <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>. Jeho volání se provádí ve více kanálech a hlavičky přidané do klienta se použijí jenom na kanál, který se použil k vytvoření <xref:System.ServiceModel.OperationContextScope>.  
  
## <a name="messageheaderreader"></a>MessageHeaderReader  
 Toto je ukázková služba, která obdrží zprávu od klienta a pokusí se vyhledat hlavičku v kolekci <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>. Klient předá identifikátor GUID, který se odeslal v hlavičce, a služba načte vlastní hlavičku a pokud je k dispozici, porovná ji s identifikátorem GUID předaným jako argument klienta.  
  
```csharp
public bool RetrieveHeader(string guid)  
{  
     MessageHeaders messageHeaderCollection =   
             OperationContext.Current.IncomingMessageHeaders;  
     String guidHeader = null;  
  
     Console.WriteLine("Trying to check if IncomingMessageHeader " +  
               " collection contains header with value {0}", guid);  
     if (messageHeaderCollection.FindHeader(  
                       CustomHeader.HeaderName,   
                       CustomHeader.HeaderNamespace) != -1)  
     {  
          guidHeader = messageHeaderCollection.GetHeader<String>(  
           CustomHeader.HeaderName, CustomHeader.HeaderNamespace);  
     }  
     else  
     {  
          Console.WriteLine("No header was found");  
     }  
     if (guidHeader != null)  
     {  
          Console.WriteLine("Found header with value {0}. "+   
         "Does it match with GUID sent as parameter: {1}",   
          guidHeader, guidHeader.Equals(guid));  
      }  
  
      Console.WriteLine();  
      //Return true if header is present and equals the guid sent by  
      // client as argument  
      return (guidHeader != null && guidHeader.Equals(guid));  
}  
```  
  
## <a name="messageheaderclient"></a>MessageHeaderClient  
 Toto je implementace klienta, která pro komunikaci se vzdálenou službou používá proxy generovaný nástrojem [ServiceModel Metadata Utility (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) . Nejprve vytvoří dva objekty proxy `MessageHeaderReaderClient`.  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 Klient potom vytvoří OperationContextScope a rozsahy, které `client1`. Přidá <xref:System.ServiceModel.Channels.MessageHeader> k <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> a vyvolá jedno volání na obou klientech. Zajišťuje, že hlavička bude odeslána pouze v `client1` a nikoli na `client2` kontrolou návratové hodnoty z volání `RetrieveHeader`.  
  
```csharp
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetrieveHeader on both the proxies. Since the OperationContextScope is tied to   
    //client1's InnerChannel, the header should only be added to calls made on that client.  
    //Calls made on client2 should not be sending the header across even though the call  
    //is made in the same OperationContextScope.  
    Console.WriteLine("Using client1 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: True", client1.RetrieveHeader(guid));  
  
    Console.WriteLine();  
    Console.WriteLine("Using client2 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: False", client2.RetrieveHeader(guid));  
}  
```  
  
 Tato ukázka je v místním prostředí hostovaná. Následující vzorový výstup z běhu ukázky je k dispozici:  
  
```console  
Prompt> Service.exe  
The service is ready.  
Press <ENTER> to terminate service.  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
Found header with value 2239da67-546f-42d4-89dc-8eb3c06215d8. Does it match with GUID sent as parameter: True  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
No header was found  
  
Prompt>Client.exe  
Using client1 to send message  
Did server retrieve the header? : Actual: True, Expected: True  
  
Using client2 to send message  
Did server retrieve the header? : Actual: False, Expected: False  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
