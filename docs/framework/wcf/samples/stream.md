---
title: Datový proud
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: f22339ca298f053fa636cc37281276051c70f6d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183319"
---
# <a name="stream"></a><span data-ttu-id="002e1-102">Datový proud</span><span class="sxs-lookup"><span data-stu-id="002e1-102">Stream</span></span>
<span data-ttu-id="002e1-103">Stream ukázka ukazuje použití přenosu datového proudu režimu komunikace.</span><span class="sxs-lookup"><span data-stu-id="002e1-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="002e1-104">Služba zveřejňuje několik operací, které odesílají a přijímají datové proudy.</span><span class="sxs-lookup"><span data-stu-id="002e1-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="002e1-105">Tato ukázka je hostována samostatně.</span><span class="sxs-lookup"><span data-stu-id="002e1-105">This sample is self-hosted.</span></span> <span data-ttu-id="002e1-106">Klient i služba jsou konzolové programy.</span><span class="sxs-lookup"><span data-stu-id="002e1-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="002e1-107">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="002e1-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="002e1-108">Windows Communication Foundation (WCF) může komunikovat ve dvou režimech přenosu – ve vyrovnávací paměti nebo streamování.</span><span class="sxs-lookup"><span data-stu-id="002e1-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="002e1-109">Ve výchozím režimu přenosu ve vyrovnávací paměti musí být zpráva zcela doručena, aby ji příjemce mohl přečíst.</span><span class="sxs-lookup"><span data-stu-id="002e1-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="002e1-110">V režimu přenosu datových proudů může příjemce začít zpracovávat zprávu před úplným doručením.</span><span class="sxs-lookup"><span data-stu-id="002e1-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="002e1-111">Režim streamování je užitečný, pokud jsou informace, které jsou předány, zdlouhavé a mohou být zpracovány sériově.</span><span class="sxs-lookup"><span data-stu-id="002e1-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="002e1-112">Režim streamování je také užitečné, když je zpráva příliš velká, aby byla zcela uložena do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="002e1-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="002e1-113">Smlouvy o streamování a poskytování služeb</span><span class="sxs-lookup"><span data-stu-id="002e1-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="002e1-114">Streamování je něco, co je třeba vzít v úvahu při navrhování smlouvy o poskytování služeb.</span><span class="sxs-lookup"><span data-stu-id="002e1-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="002e1-115">Pokud operace přijímá nebo vrací velké množství dat, měli byste zvážit streamování těchto dat, abyste se vyhnuli vysokému využití paměti z důvodu ukládání vstupních nebo výstupních zpráv do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="002e1-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="002e1-116">Chcete-li streamovat data, musí být parametr, který tato data obsahuje, jediným parametrem ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="002e1-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="002e1-117">Například pokud vstupní zpráva je ten, který má být datový proud, operace musí mít přesně jeden vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="002e1-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="002e1-118">Podobně pokud výstupní zpráva má být datový proud, operace musí mít přesně jeden výstupní parametr nebo vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="002e1-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="002e1-119">V obou případech musí být parametr nebo `Stream` `Message`typ `IXmlSerializable`vrácené hodnoty buď , nebo .</span><span class="sxs-lookup"><span data-stu-id="002e1-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="002e1-120">Následuje smlouva o poskytování služeb použitá v této ukázce streamování.</span><span class="sxs-lookup"><span data-stu-id="002e1-120">The following is the service contract used in this streaming sample.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 <span data-ttu-id="002e1-121">Operace `GetStream` obdrží některá vstupní data jako řetězec, který je `Stream`do vyrovnávací paměti a vrátí , který je přenášen datovým proudem.</span><span class="sxs-lookup"><span data-stu-id="002e1-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="002e1-122">Naopak `UploadStream` bere v `Stream` (streamed) a `bool` vrátí (ve vyrovnávací paměti).</span><span class="sxs-lookup"><span data-stu-id="002e1-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="002e1-123">`EchoStream`bere a `Stream` vrací a je příkladem operace, jejíž vstupní a výstupní zprávy jsou oba datového proudu.</span><span class="sxs-lookup"><span data-stu-id="002e1-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="002e1-124">Nakonec `GetReversedStream` trvá žádné vstupy `Stream` a vrátí (streamed).</span><span class="sxs-lookup"><span data-stu-id="002e1-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="002e1-125">Povolení datových proudů přenosů</span><span class="sxs-lookup"><span data-stu-id="002e1-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="002e1-126">Definování smluv operace, jak bylo popsáno výše, poskytuje streamování na úrovni programovacího modelu.</span><span class="sxs-lookup"><span data-stu-id="002e1-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="002e1-127">Pokud zastavíte tam, přenos stále vyrovnávací paměti celý obsah zprávy.</span><span class="sxs-lookup"><span data-stu-id="002e1-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="002e1-128">Chcete-li povolit přenos datových proudů, vyberte režim přenosu na prvek vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="002e1-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="002e1-129">Element vazby `TransferMode` má vlastnost, kterou `Buffered` `Streamed`lze `StreamedRequest`nastavit `StreamedResponse`na , , nebo .</span><span class="sxs-lookup"><span data-stu-id="002e1-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="002e1-130">Nastavení režimu `Streamed` přenosu na umožňuje streamování komunikace v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="002e1-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="002e1-131">Nastavení režimu `StreamedRequest` přenosu `StreamedResponse` na nebo umožňuje streamování komunikace pouze v požadavku nebo odpovědi, resp.</span><span class="sxs-lookup"><span data-stu-id="002e1-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="002e1-132">Zpřístupňuje `basicHttpBinding` `TransferMode` vlastnost na vazbu `NetTcpBinding` `NetNamedPipeBinding`jako a .</span><span class="sxs-lookup"><span data-stu-id="002e1-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="002e1-133">Pro ostatní přenosy je nutné vytvořit vlastní vazbu pro nastavení režimu přenosu.</span><span class="sxs-lookup"><span data-stu-id="002e1-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="002e1-134">Následující konfigurační kód z `TransferMode` ukázky ukazuje `basicHttpBinding` nastavení vlastnosti na streamování na a vlastní vazbě HTTP:</span><span class="sxs-lookup"><span data-stu-id="002e1-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="002e1-135">Kromě nastavení `transferMode` na `Streamed`, předchozí konfigurační kód nastaví `maxReceivedMessageSize` 64 MB.</span><span class="sxs-lookup"><span data-stu-id="002e1-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="002e1-136">Jako obranný mechanismus umístí `maxReceivedMessageSize` omezení na maximální přípustnou velikost zpráv při příjmu.</span><span class="sxs-lookup"><span data-stu-id="002e1-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="002e1-137">Výchozí `maxReceivedMessageSize` hodnota je 64 kB, což je obvykle příliš nízká pro scénáře streamování.</span><span class="sxs-lookup"><span data-stu-id="002e1-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="002e1-138">Zpracování dat tak, jak jsou streamována</span><span class="sxs-lookup"><span data-stu-id="002e1-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="002e1-139">Operace `GetStream` `UploadStream` a `EchoStream` všechny se zabývají odesíláním dat přímo ze souboru nebo ukládáním přijatých dat přímo do souboru.</span><span class="sxs-lookup"><span data-stu-id="002e1-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="002e1-140">V některých případech však existuje požadavek na odesílání nebo přijímání velkého množství dat a provádění některých zpracování na blocích dat při odesílání nebo přijímání.</span><span class="sxs-lookup"><span data-stu-id="002e1-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="002e1-141">Jedním ze způsobů, jak řešit tyto scénáře je napsat <xref:System.IO.Stream>vlastní datový proud (třída, která je odvozena z ) , který zpracovává data, jak je čtení nebo zápis.</span><span class="sxs-lookup"><span data-stu-id="002e1-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="002e1-142">Operace `GetReversedStream` a `ReverseStream` třída jsou příkladem tohoto.</span><span class="sxs-lookup"><span data-stu-id="002e1-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="002e1-143">`GetReversedStream`vytvoří a vrátí novou `ReverseStream`instanci .</span><span class="sxs-lookup"><span data-stu-id="002e1-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="002e1-144">Skutečné zpracování se stane při `ReverseStream` čtení systému z tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="002e1-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="002e1-145">Implementace `ReverseStream.Read` přečte část bajtů z podkladového souboru, obrátí je a vrátí stornované bajty.</span><span class="sxs-lookup"><span data-stu-id="002e1-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="002e1-146">Tím se neobrátí celý obsah souboru; obrátí jeden kus bajtů najednou.</span><span class="sxs-lookup"><span data-stu-id="002e1-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="002e1-147">Toto je příklad, který ukazuje, jak můžete provádět zpracování datového proudu při čtení nebo zápisu obsahu z datového proudu a do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="002e1-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="002e1-148">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="002e1-148">Running the Sample</span></span>  
 <span data-ttu-id="002e1-149">Chcete-li spustit ukázku, nejprve sestavte službu i klienta podle pokynů na konci tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="002e1-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="002e1-150">Potom spusťte službu a klienta ve dvou různých oknech konzoly.</span><span class="sxs-lookup"><span data-stu-id="002e1-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="002e1-151">Když se klient spustí, čeká, až stisknete klávesu ENTER, jakmile bude služba připravena.</span><span class="sxs-lookup"><span data-stu-id="002e1-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="002e1-152">Klient pak volá `GetStream()`metody `UploadStream()` `GetReversedStream()` a nejprve přes HTTP a potom přes TCP.</span><span class="sxs-lookup"><span data-stu-id="002e1-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="002e1-153">Zde je příklad výstupu ze služby následovaný ukázkovým výstupem z klienta:</span><span class="sxs-lookup"><span data-stu-id="002e1-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="002e1-154">Výstup služby:</span><span class="sxs-lookup"><span data-stu-id="002e1-154">Service Output:</span></span>  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="002e1-155">Výstup klienta:</span><span class="sxs-lookup"><span data-stu-id="002e1-155">Client Output:</span></span>  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="002e1-156">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="002e1-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="002e1-157">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="002e1-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="002e1-158">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="002e1-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="002e1-159">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="002e1-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="002e1-160">Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit název koncového bodu v konfiguraci klienta tak, aby odpovídalkódu klienta.</span><span class="sxs-lookup"><span data-stu-id="002e1-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="002e1-161">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="002e1-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="002e1-162">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="002e1-162">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="002e1-163">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="002e1-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="002e1-164">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="002e1-164">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
