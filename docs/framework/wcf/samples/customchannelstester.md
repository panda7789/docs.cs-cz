---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: eebe4f15095c7cefbd32971fd2f3ee308e9916b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499385"
---
# <a name="customchannelstester"></a><span data-ttu-id="b26e0-102">CustomChannelsTester</span><span class="sxs-lookup"><span data-stu-id="b26e0-102">CustomChannelsTester</span></span>
<span data-ttu-id="b26e0-103">`CustomChannelsTester` Je nástroj, který můžete použít k testování vaší implementace vlastní kanál oproti sadě kontrakty předdefinovaných služeb.</span><span class="sxs-lookup"><span data-stu-id="b26e0-103">The `CustomChannelsTester` is a tool that you can use to test your custom channel implementations against a set of predefined service contracts.</span></span> <span data-ttu-id="b26e0-104">Můžete vybrat sadu kontraktů služby a předejte ji do nástroje pomocí souboru XML.</span><span class="sxs-lookup"><span data-stu-id="b26e0-104">You can select the set of service contracts and pass it to the tool using an XML file.</span></span> <span data-ttu-id="b26e0-105">Nástroj potom generuje službu a klienta, který vykonává vaší implementace vlastní kanál při výměně zpráv.</span><span class="sxs-lookup"><span data-stu-id="b26e0-105">The tool then generates the service and client that exercises your custom channel implementations during message exchange.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="b26e0-106">K sestavení nástroje</span><span class="sxs-lookup"><span data-stu-id="b26e0-106">To build the tool</span></span>  
  
1.  <span data-ttu-id="b26e0-107">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b26e0-107">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="b26e0-108">Sestavování řešení generuje tři soubory: CustomChannelsTester.exe, TestSpec.xml a SampleRun.cmd.</span><span class="sxs-lookup"><span data-stu-id="b26e0-108">Building the solution generates three files: CustomChannelsTester.exe, TestSpec.xml and SampleRun.cmd.</span></span> <span data-ttu-id="b26e0-109">Soubor SampleRun.cmd má ukázka příkazového řádku, který ukazuje, jak tento nástroj použijte k testování [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="b26e0-109">The file SampleRun.cmd has a sample command line that shows how to use this tool to test the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="b26e0-110">Chcete-li spustit nástroj</span><span class="sxs-lookup"><span data-stu-id="b26e0-110">To run the tool</span></span>  
  
-   <span data-ttu-id="b26e0-111">Na příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="b26e0-111">At the command prompt type the following command:</span></span>  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     <span data-ttu-id="b26e0-112">Pomocí `/binding` možnost je povinná.</span><span class="sxs-lookup"><span data-stu-id="b26e0-112">Using the `/binding` option is required.</span></span>  
  
     <span data-ttu-id="b26e0-113">`/dll` je vyžadován Pokud "vazba" není vazby poskytované systémem zadaný ve Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b26e0-113">`/dll` is required if "binding" is not a system-provided binding provided by Windows Communication Foundation (WCF).</span></span>  
  
     <span data-ttu-id="b26e0-114">`/testspec` je volitelný.</span><span class="sxs-lookup"><span data-stu-id="b26e0-114">`/testspec` is optional.</span></span>  
  
     <span data-ttu-id="b26e0-115">Tím se vytvoří serverem a klienty na základě specifikace test a vazby.</span><span class="sxs-lookup"><span data-stu-id="b26e0-115">This creates server and clients based on the test specifications and the binding.</span></span>  
  
     <span data-ttu-id="b26e0-116">Provede klient a server a vrátí výsledky.</span><span class="sxs-lookup"><span data-stu-id="b26e0-116">Executes the client and server and returns the results.</span></span>  
  
     <span data-ttu-id="b26e0-117">Zde je ukázka XML pro popis specifikace testu (testspec.xml):</span><span class="sxs-lookup"><span data-stu-id="b26e0-117">The following is the sample XML for the description of the test specifications (testspec.xml):</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b26e0-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b26e0-118">See Also</span></span>
