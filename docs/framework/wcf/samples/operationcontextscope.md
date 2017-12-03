---
title: OperationContextScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7cf84c30c5784de813f947d26b18816906ec6a7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="operationcontextscope"></a>OperationContextScope
Ukázka OperationContextScope ukazuje, jak odeslat na doplňující informace [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] volat pomocí hlavičky. V této ukázce se serverem a klientem konzolové aplikace.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Ukázka ukazuje, jak klient může odesílat jako další informace <xref:System.ServiceModel.Channels.MessageHeader> pomocí <xref:System.ServiceModel.OperationContextScope>. <xref:System.ServiceModel.OperationContextScope> Podle rozsahu pro kanál, který je vytvořen objekt. Hlavičky, které musí být převedeny na vzdálené služby mohou být přidány do <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> kolekce. Přidat do této kolekce hlavičky může načíst služby přístupu k <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>. Jeho volání na více typů komunikačních kanálů a pak záhlaví přidat do klienta se vztahují pouze na kanálu, který byl použit k vytvoření <xref:System.ServiceModel.OperationContextScope>.  
  
## <a name="messageheaderreader"></a>MessageHeaderReader  
 Toto je ukázkový služba, která přijme zprávu od klienta a pokusí se vyhledat záhlaví má v <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> kolekce. Klient předá identifikátor GUID, který ho odeslal v hlavičce a službu načte vlastní hlavičky a pokud je k dispozici, porovná ho s identifikátorem GUID jako argument předaný klientem.  
  
```  
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
 Toto je implementace klienta, který používá proxy server generované [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke komunikaci s vzdálené služby. Nejprve vytvoří dva objekty proxy `MessageHeaderReaderClient`.  
  
```  
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 Klient pak vytvoří OperationContextScope a rozsahy, aby `client1`. Přidá <xref:System.ServiceModel.Channels.MessageHeader> k <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> a vyvolá jedno volání na obou klientských počítačích. Zajišťuje, že hlavičku se odesílají pouze na `client1` a ne v `client2` kontrolou návratovou hodnotou z `RetrieveHeader` volání.  
  
```  
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetreieveHeader on both the proxies. Since the OperationContextScope is tied to   
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
  
 Tato ukázka se hostuje sama. Následující ukázkový výstup ve spuštění ukázce je k dispozici:  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
  
## <a name="see-also"></a>Viz také
