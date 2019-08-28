---
title: Stream
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: 3f52ba01dfd3290e4b0f728e5832a11f2f9c3eeb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045471"
---
# <a name="stream"></a><span data-ttu-id="2efe9-102">Stream</span><span class="sxs-lookup"><span data-stu-id="2efe9-102">Stream</span></span>
<span data-ttu-id="2efe9-103">Ukázka streamu demonstruje použití komunikace režimu přenosu datového proudu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="2efe9-104">Služba zveřejňuje několik operací, které odesílají a přijímají streamy.</span><span class="sxs-lookup"><span data-stu-id="2efe9-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="2efe9-105">Tato ukázka je v místním prostředí hostovaná.</span><span class="sxs-lookup"><span data-stu-id="2efe9-105">This sample is self-hosted.</span></span> <span data-ttu-id="2efe9-106">Klient i služba jsou konzolové programy.</span><span class="sxs-lookup"><span data-stu-id="2efe9-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2efe9-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2efe9-108">Windows Communication Foundation (WCF) může komunikovat ve dvou režimech přenosu – ve vyrovnávací paměti nebo streamování.</span><span class="sxs-lookup"><span data-stu-id="2efe9-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="2efe9-109">Ve výchozím režimu přenosu do vyrovnávací paměti musí být zpráva zcela doručena předtím, než ji příjemce může přečíst.</span><span class="sxs-lookup"><span data-stu-id="2efe9-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="2efe9-110">V režimu přenosu datových proudů může příjemce zahájit zpracování zprávy před úplným doručením.</span><span class="sxs-lookup"><span data-stu-id="2efe9-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="2efe9-111">Režim streamování je užitečný v případě, že předávané informace jsou zdlouhavé a dají se zpracovat sériově.</span><span class="sxs-lookup"><span data-stu-id="2efe9-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="2efe9-112">Režim streamování je vhodný také v případě, že je zpráva příliš velká a nemůže být zcela ukládána do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2efe9-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="2efe9-113">Streamování a kontrakty služeb</span><span class="sxs-lookup"><span data-stu-id="2efe9-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="2efe9-114">Streamování je něco, co je potřeba vzít v úvahu při návrhu kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="2efe9-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="2efe9-115">Pokud operace přijme nebo vrátí velké objemy dat, měli byste zvážit streamování těchto dat, aby se zabránilo vysokému využití paměti kvůli ukládání vstupních nebo výstupních zpráv do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2efe9-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="2efe9-116">Pro streamování dat musí být parametr, který obsahuje tato data, jediným parametrem ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="2efe9-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="2efe9-117">Pokud je vstupní zpráva například ta, která se má streamovat, musí mít operace přesně jeden vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="2efe9-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="2efe9-118">Podobně platí, že pokud má být výstupní zpráva streamovaná, operace musí mít buď přesně jeden výstupní parametr, nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="2efe9-119">V obou případech musí být parametr nebo návratový typ hodnoty buď `Stream`, `Message`nebo `IXmlSerializable`.</span><span class="sxs-lookup"><span data-stu-id="2efe9-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="2efe9-120">Níže je uvedené kontrakt služby použitý v této ukázce streamování.</span><span class="sxs-lookup"><span data-stu-id="2efe9-120">The following is the service contract used in this streaming sample.</span></span>  
  
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
  
 <span data-ttu-id="2efe9-121">Operace přijme některá vstupní data jako řetězec, který je uložen do vyrovnávací paměti, a `Stream`vrátí, který je datovým proudem. `GetStream`</span><span class="sxs-lookup"><span data-stu-id="2efe9-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="2efe9-122">Naopak `UploadStream` přebírá `Stream` v (streamované) a vrací `bool` (ve vyrovnávací paměti).</span><span class="sxs-lookup"><span data-stu-id="2efe9-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="2efe9-123">`EchoStream`přijímá a vrací `Stream` a je příkladem operace, jejíž vstupní a výstupní zprávy jsou přenášeny datovým proudem.</span><span class="sxs-lookup"><span data-stu-id="2efe9-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="2efe9-124">Nakonec neprovede žádné vstupy a `Stream` vrátí (streamované). `GetReversedStream`</span><span class="sxs-lookup"><span data-stu-id="2efe9-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="2efe9-125">Povolení přenosů odeslaných datovým proudem</span><span class="sxs-lookup"><span data-stu-id="2efe9-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="2efe9-126">Definování kontraktů operací, jak je popsáno výše, poskytuje streamování na úrovni programovacího modelu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="2efe9-127">Pokud tam zastavíte, přenos bude ukládat celý obsah zprávy do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2efe9-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="2efe9-128">Chcete-li povolit streamování přenosu, vyberte režim přenosu na elementu vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="2efe9-129">Element `TransferMode` Binding má vlastnost, která může být nastavena na `Streamed` `Buffered`,, `StreamedRequest`nebo `StreamedResponse`.</span><span class="sxs-lookup"><span data-stu-id="2efe9-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="2efe9-130">Nastavení režimu přenosu pro `Streamed` povolení komunikace streamování v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="2efe9-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="2efe9-131">Nastavení režimu `StreamedRequest` přenosu nebo `StreamedResponse` povolení komunikace streamování pouze v žádosti nebo odpovědi v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="2efe9-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="2efe9-132">Vlastnost zpřístupňuje vlastnost vazby jako `NetTcpBinding` a `NetNamedPipeBinding`. `basicHttpBinding` `TransferMode`</span><span class="sxs-lookup"><span data-stu-id="2efe9-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="2efe9-133">Pro jiné přenosy je nutné vytvořit vlastní vazbu pro nastavení režimu přenosu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="2efe9-134">Následující konfigurační kód z ukázky ukazuje nastavení `TransferMode` vlastnosti pro streamování `basicHttpBinding` na a vlastní vazby http:</span><span class="sxs-lookup"><span data-stu-id="2efe9-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
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
  
 <span data-ttu-id="2efe9-135">Kromě nastavení `transferMode` na `Streamed`, `maxReceivedMessageSize` předchozí konfigurační kód nastaví na 64 MB.</span><span class="sxs-lookup"><span data-stu-id="2efe9-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="2efe9-136">V rámci mechanismu ochrany je `maxReceivedMessageSize` limit maximální povolené velikosti zpráv na příjmu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="2efe9-137">Výchozí hodnota `maxReceivedMessageSize` je 64 KB, což je obvykle příliš nízké pro scénáře streamování.</span><span class="sxs-lookup"><span data-stu-id="2efe9-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="2efe9-138">Zpracování dat při streamování</span><span class="sxs-lookup"><span data-stu-id="2efe9-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="2efe9-139">Operace `GetStream` `UploadStream` a všechnysetýkajíposílánídatpřímozesouboruneboukládánípřijatýchdatpřímodosouboru.`EchoStream`</span><span class="sxs-lookup"><span data-stu-id="2efe9-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="2efe9-140">V některých případech však existuje požadavek na odeslání nebo přijetí velkých objemů dat a provádění určitého zpracování datových bloků dat při jejich posílání nebo přijímání.</span><span class="sxs-lookup"><span data-stu-id="2efe9-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="2efe9-141">Jedním ze způsobů, jak tyto scénáře vyřešit, je napsat vlastní datový proud (třídu, která je <xref:System.IO.Stream>odvozena z), která zpracovává data při čtení nebo zápisu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="2efe9-142">Tato operace je `ReverseStream` příkladem této operace a třídy. `GetReversedStream`</span><span class="sxs-lookup"><span data-stu-id="2efe9-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="2efe9-143">`GetReversedStream`Vytvoří a vrátí novou instanci `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="2efe9-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="2efe9-144">Ke skutečnému zpracování dochází jako systém čte z tohoto `ReverseStream` objektu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="2efe9-145">`ReverseStream.Read` Implementace načte blok bajtů z podkladového souboru, obrátí je a potom vrátí obrácené bajty.</span><span class="sxs-lookup"><span data-stu-id="2efe9-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="2efe9-146">Tím se nevrátí celý obsah souboru. v jednom okamžiku vrátí jeden blok bajtů.</span><span class="sxs-lookup"><span data-stu-id="2efe9-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="2efe9-147">Toto je příklad, který ukazuje, jak lze provádět zpracování datového proudu při čtení nebo zápisu obsahu z a do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="2efe9-148">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2efe9-148">Running the Sample</span></span>  
 <span data-ttu-id="2efe9-149">Chcete-li spustit ukázku, nejprve Sestavte službu i klienta podle pokynů na konci tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2efe9-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="2efe9-150">Pak spusťte službu a klienta ve dvou různých oknech konzoly.</span><span class="sxs-lookup"><span data-stu-id="2efe9-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="2efe9-151">Po spuštění klienta počká, až bude služba připravena, po stisknutí klávesy ENTER.</span><span class="sxs-lookup"><span data-stu-id="2efe9-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="2efe9-152">Klient pak zavolá metody `GetStream()` `UploadStream()` a `GetReversedStream()` nejprve zavolá protokol HTTP a potom přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="2efe9-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="2efe9-153">Tady je příklad výstupu služby následovaný ukázkovým výstupem z klienta:</span><span class="sxs-lookup"><span data-stu-id="2efe9-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="2efe9-154">Výstup služby:</span><span class="sxs-lookup"><span data-stu-id="2efe9-154">Service Output:</span></span>  
  
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
  
 <span data-ttu-id="2efe9-155">Výstup klienta:</span><span class="sxs-lookup"><span data-stu-id="2efe9-155">Client Output:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2efe9-156">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2efe9-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2efe9-157">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2efe9-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2efe9-158">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2efe9-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2efe9-159">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2efe9-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2efe9-160">Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="2efe9-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2efe9-161">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="2efe9-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2efe9-162">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2efe9-162">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2efe9-163">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="2efe9-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2efe9-164">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2efe9-164">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
