---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: c23bd3eddd49972b7083347fed88d4e70707ae58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183801"
---
# <a name="customchannelstester"></a>CustomChannelsTester
Jedná `CustomChannelsTester` se o nástroj, který můžete použít k testování implementace vlastního kanálu proti sadě předdefinovaných servisních smluv. Můžete vybrat sadu servisních smluv a předat ji nástroji pomocí souboru XML. Nástroj pak generuje službu a klienta, který vykonává implementace vlastního kanálu během výměny zpráv.  
  
### <a name="to-build-the-tool"></a>Vytvoření nástroje  
  
1. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Vytvoření řešení generuje tři soubory: CustomChannelsTester.exe, TestSpec.xml a SampleRun.cmd. Soubor SampleRun.cmd má ukázkový příkazový řádek, který ukazuje, jak pomocí tohoto nástroje otestovat ukázku [Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)  
  
### <a name="to-run-the-tool"></a>Spuštění nástroje  
  
- Na příkazovém řádku zadejte následující příkaz:  
  
    ```console  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Použití `/binding` možnosti je nutné.  
  
     `/dll`je vyžadována, pokud "vazba" není systémem poskytované vazby poskytované Windows Communication Foundation (WCF).  
  
     Parametr `/testspec` je volitelný.  
  
     Tím se vytvoří server a klienti na základě testovacíspecifikace a vazby.  
  
     Spustí klienta a server a vrátí výsledky.  
  
     Následuje ukázkový kód XML pro popis testovacích specifikací (testspec.xml):  
  
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
