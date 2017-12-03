---
title: CustomChannelsTester
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 802d501dabbf14d30a26cd682afb366f0a83a17a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="customchannelstester"></a>CustomChannelsTester
`CustomChannelsTester` Je nástroj, který můžete použít k testování vaší implementace vlastní kanál oproti sadě kontrakty předdefinovaných služeb. Můžete vybrat sadu kontraktů služby a předejte ji do nástroje pomocí souboru XML. Nástroj potom generuje službu a klienta, který vykonává vaší implementace vlastní kanál při výměně zpráv.  
  
### <a name="to-build-the-tool"></a>K sestavení nástroje  
  
1.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Sestavování řešení generuje tři soubory: CustomChannelsTester.exe, TestSpec.xml a SampleRun.cmd. Soubor SampleRun.cmd má ukázka příkazového řádku, který ukazuje, jak tento nástroj použijte k testování [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.  
  
### <a name="to-run-the-tool"></a>Chcete-li spustit nástroj  
  
-   Na příkazovém řádku zadejte následující příkaz:  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Pomocí `/binding` možnost je povinná.  
  
     `/dll`je nutný, pokud "vazba" není vazby poskytované systémem poskytované [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
     `/testspec`je volitelný.  
  
     Tím se vytvoří serverem a klienty na základě specifikace test a vazby.  
  
     Provede klient a server a vrátí výsledky.  
  
     Zde je ukázka XML pro popis specifikace testu (testspec.xml):  
  
    ```xml  
    <TestSpec xmlns="http://WCF/TestSpec" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" >  
    <ServiceContract>  
    <!-- Test a contract which has oneway / twoway operations. If you set ExpandAll = true, both types of contracts are tested -->    <IsOneWay ExpandAll="true">true</IsOneWay>  
    <!-- Test a contract with Asynchronous / Synchronous Operations-->  
        <IsAsync>false</IsAsync>   
    <!-- Test a sessionful / sessionless contract-->      
        <IsSession ExpandAll="true">true</IsSession>  
    <!-- If the Service Contract includes a CallBack Contract-->      
        <IsCallBack ExpandAll="true">true</IsCallBack>  
    </ServiceContract>  
    <TestDetails>  
    <!-- Name of the machine that runs the server - required if you want to run the test crossmachine-->  
        <ServerName>ReplaceThisWithTheServerMachineName</ServerName>  
    <!-- Port Number - Optional-->  
        <Port>8000</Port>  
    <!--URI for the callBack address for the CLient. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
        <ClientCallBackAddress/>      
    <!-- Duration (in sec) after the server has started, it times out - optional(default = 300sec) -->  
        <ServerTimeout>300</ServerTimeout>  
    <!-- Duration (in sec) before the Client initializes -optional(default = 60sec) -->  
        <ClientTimeout>60</ClientTimeout>  
    <!-- Number of clients for each service - optional(default = 1) -->  
        <NumberOfClients>1</NumberOfClients>  
    <!-- Number of messages each client sends to the service - optional(default = 1) -->  
        <MessagesPerClient>1</MessagesPerClient>  
    </TestDetails>  
    </TestSpec>  
    ```  
  
## <a name="see-also"></a>Viz také
