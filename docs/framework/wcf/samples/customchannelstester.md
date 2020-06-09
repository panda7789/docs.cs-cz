---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: 9123167e0f97592592765f7b4a4aa768064fc173
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596601"
---
# <a name="customchannelstester"></a>CustomChannelsTester
`CustomChannelsTester`Je nástroj, který můžete použít k otestování vlastních implementací kanálu na základě sady předdefinovaných kontraktů služeb. Můžete vybrat sadu kontraktů služby a předat ji nástroji pomocí souboru XML. Nástroj pak vygeneruje službu a klienta, které během výměny zpráv vykonává implementace vlastních kanálů.  
  
### <a name="to-build-the-tool"></a>Sestavení nástroje  
  
1. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
2. Sestavení řešení generuje tři soubory: CustomChannelsTester. exe, TestSpec. XML a SampleRun. cmd. Soubor SampleRun. cmd obsahuje vzorový příkazový řádek, který ukazuje, jak tento nástroj použít k otestování příkladu [Transport: UDP](transport-udp.md) .  
  
### <a name="to-run-the-tool"></a>Spuštění nástroje  
  
- Na příkazovém řádku zadejte následující příkaz:  
  
    ```console  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Použití `/binding` Možnosti je povinné.  
  
     `/dll`je vyžadováno, pokud "Binding" není vazba poskytnutá systémem, kterou poskytuje Windows Communication Foundation (WCF).  
  
     Parametr `/testspec` je volitelný.  
  
     Tím se vytvoří server a klienti na základě specifikací testu a vazby.  
  
     Spustí klienta a Server a vrátí výsledky.  
  
     Následuje ukázkový soubor XML pro popis specifikací testu (TestSpec. XML):  
  
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
