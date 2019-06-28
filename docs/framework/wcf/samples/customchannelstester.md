---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: 1517a2eb73da778c9b84ff857f4b8ad2b4334498
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425009"
---
# <a name="customchannelstester"></a>CustomChannelsTester
`CustomChannelsTester` Je nástroj, který můžete použít k otestování implementace vaší vlastní kanál s pomocí sady předdefinovaných servisní smlouvy. Můžete vybrat sadu kontrakty služeb a předat nástroji pomocí souboru XML. Nástroj poté vygeneruje službu a klienta, která zpracovává vaše implementace vlastního kanálu při výměně zpráv.  
  
### <a name="to-build-the-tool"></a>K sestavení nástroj  
  
1. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Sestavování řešení se vytvoří tři soubory: CustomChannelsTester.exe TestSpec.xml a SampleRun.cmd. Ukázka příkazového řádku, který ukazuje, jak tento nástroj použijte k testování má soubor SampleRun.cmd [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.  
  
### <a name="to-run-the-tool"></a>Chcete-li spustit nástroj  
  
- Na příkazovém řádku zadejte následující příkaz:  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Použití `/binding` možnost je vyžadována.  
  
     `/dll` Pokud "vazba" není k dispozici ve Windows Communication Foundation (WCF) vazeb poskytovaných systémem je povinný.  
  
     `/testspec` je volitelný.  
  
     Tím se vytvoří serverem a klienty na základě specifikací testu a vazby.  
  
     Spustí klienta a serveru a vrátí výsledky.  
  
     Následuje ukázkový soubor XML pro popis testu specifikace (testspec.xml):  
  
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
    <!--URI for the callBack address for the client. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
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
