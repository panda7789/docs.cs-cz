---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: ce21d9d099d893015ea828bdc3b136ab83f6d8e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183423"
---
# <a name="operationcontextscope"></a><span data-ttu-id="93320-102">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="93320-102">OperationContextScope</span></span>
<span data-ttu-id="93320-103">OperationContextScope ukázka ukazuje, jak odeslat další informace o volání Windows Communication Foundation (WCF) pomocí záhlaví.</span><span class="sxs-lookup"><span data-stu-id="93320-103">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="93320-104">V této ukázce jsou server i klient konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="93320-104">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93320-105">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="93320-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="93320-106">Ukázka ukazuje, jak klient může odeslat další informace jako <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span><span class="sxs-lookup"><span data-stu-id="93320-106">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="93320-107">Objekt <xref:System.ServiceModel.OperationContextScope> je vytvořen oborem do kanálu.</span><span class="sxs-lookup"><span data-stu-id="93320-107">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="93320-108">Hlavičky, které musí být přeloženy do vzdálené <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> služby lze přidat do kolekce.</span><span class="sxs-lookup"><span data-stu-id="93320-108">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="93320-109">Záhlaví přidané do této kolekce lze načíst ve <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>službě přístupem .</span><span class="sxs-lookup"><span data-stu-id="93320-109">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="93320-110">Jeho volání jsou prováděny na více kanálech a potom záhlaví přidána do klienta platí pouze pro kanál, který byl použit k vytvoření <xref:System.ServiceModel.OperationContextScope>.</span><span class="sxs-lookup"><span data-stu-id="93320-110">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="93320-111">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="93320-111">MessageHeaderReader</span></span>  
 <span data-ttu-id="93320-112">Toto je ukázková služba, která obdrží zprávu od klienta <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> a pokusí se vyhledat záhlaví v kolekci.</span><span class="sxs-lookup"><span data-stu-id="93320-112">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="93320-113">Klient předá identifikátor GUID, který odeslal v záhlaví a služba načte vlastní hlavičku a pokud je k dispozici, porovná jej s identifikátorem GUID předaným jako argument klientem.</span><span class="sxs-lookup"><span data-stu-id="93320-113">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
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
  
## <a name="messageheaderclient"></a><span data-ttu-id="93320-114">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="93320-114">MessageHeaderClient</span></span>  
 <span data-ttu-id="93320-115">Toto je implementace klienta, který používá proxy generovaný [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke komunikaci se vzdálenou službou.</span><span class="sxs-lookup"><span data-stu-id="93320-115">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="93320-116">Nejprve vytvoří dva `MessageHeaderReaderClient`proxy objekty .</span><span class="sxs-lookup"><span data-stu-id="93320-116">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="93320-117">Klient pak vytvoří OperationContextScope a `client1`obory do .</span><span class="sxs-lookup"><span data-stu-id="93320-117">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="93320-118">Přidá <xref:System.ServiceModel.Channels.MessageHeader> <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> a a vyvolá jedno volání na obou klientů.</span><span class="sxs-lookup"><span data-stu-id="93320-118">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="93320-119">Zajišťuje, že záhlaví je odeslána pouze na `client1` a nikoli na `client2` kontrolou vrácená hodnota z `RetrieveHeader` volání.</span><span class="sxs-lookup"><span data-stu-id="93320-119">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
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
  
 <span data-ttu-id="93320-120">Tato ukázka je hostována samostatně.</span><span class="sxs-lookup"><span data-stu-id="93320-120">This sample is self-hosted.</span></span> <span data-ttu-id="93320-121">Je k dispozici následující ukázkový výstup ze spuštění vzorku:</span><span class="sxs-lookup"><span data-stu-id="93320-121">The following sample output from running the sample is provided:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="93320-122">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="93320-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="93320-123">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93320-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="93320-124">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93320-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="93320-125">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93320-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="93320-126">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="93320-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="93320-127">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="93320-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="93320-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="93320-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93320-129">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="93320-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
