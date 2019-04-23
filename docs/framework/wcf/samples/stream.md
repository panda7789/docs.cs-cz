---
title: Stream
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: f6ca887240ec4f6a304f0d5972790837c0121721
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330217"
---
# <a name="stream"></a><span data-ttu-id="2e625-102">Stream</span><span class="sxs-lookup"><span data-stu-id="2e625-102">Stream</span></span>
<span data-ttu-id="2e625-103">Stream ukázce použití streamování komunikace režim přenosu.</span><span class="sxs-lookup"><span data-stu-id="2e625-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="2e625-104">Služba zpřístupňuje několik operací, které odesílání a příjem streamů.</span><span class="sxs-lookup"><span data-stu-id="2e625-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="2e625-105">Tato ukázka je v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="2e625-105">This sample is self-hosted.</span></span> <span data-ttu-id="2e625-106">Klient a služba se o programy konzoly.</span><span class="sxs-lookup"><span data-stu-id="2e625-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e625-107">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2e625-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2e625-108">Windows Communication Foundation (WCF) můžou komunikovat ve dvou režimech přenos – ve vyrovnávací paměti nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="2e625-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="2e625-109">Ve výchozím režimu přenosu ve vyrovnávací paměti zprávy musí být zcela doručována předtím, než příjemce může číst.</span><span class="sxs-lookup"><span data-stu-id="2e625-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="2e625-110">V režim tvorby datového proudu přenosu můžete začít příjemce zprávu zpracovat, než úplně doručení.</span><span class="sxs-lookup"><span data-stu-id="2e625-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="2e625-111">Režim tvorby datového proudu je užitečné, když informace, které je předáno příliš dlouhý a může být zpracována sériově.</span><span class="sxs-lookup"><span data-stu-id="2e625-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="2e625-112">Režim tvorby datového proudu je také užitečné, pokud zpráva je příliš velký, aby se zcela ukládány do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2e625-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="2e625-113">Streamování a kontrakty služeb</span><span class="sxs-lookup"><span data-stu-id="2e625-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="2e625-114">Streamování je něco, co vzít v úvahu při navrhování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="2e625-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="2e625-115">Pokud operace přijímá nebo vrací velké množství dat, měli byste zvážit, tato data, aby se zabránilo vysoké využití paměti z důvodu ukládání do vyrovnávací paměti zpráv vstupních nebo výstupních datových proudů.</span><span class="sxs-lookup"><span data-stu-id="2e625-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="2e625-116">Pro streamování dat, parametr, který obsahuje, data musí být jediným parametrem ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="2e625-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="2e625-117">Například pokud vstupní zprávy je ten, který má být datovým proudem, operace musí mít přesně jeden vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="2e625-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="2e625-118">Podobně při odesílání zprávy výstup operace musí mít právě jeden výstupní parametr nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2e625-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="2e625-119">V případě, parametr nebo návratovou hodnotu typu musí být buď `Stream`, `Message`, nebo `IXmlSerializable`.</span><span class="sxs-lookup"><span data-stu-id="2e625-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="2e625-120">Tady je kontrakt služby používané v tomto příkladu datových proudů.</span><span class="sxs-lookup"><span data-stu-id="2e625-120">The following is the service contract used in this streaming sample.</span></span>  
  
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
  
 <span data-ttu-id="2e625-121">`GetStream` Operace přijímá vstupní data jako řetězec, který je uložená do vyrovnávací paměti a vrátí `Stream`, které streamuje.</span><span class="sxs-lookup"><span data-stu-id="2e625-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="2e625-122">Naopak `UploadStream` přijímá `Stream` (streamování) a vrátí `bool` (ukládány do vyrovnávací paměti).</span><span class="sxs-lookup"><span data-stu-id="2e625-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="2e625-123">`EchoStream` přijímá a vrací `Stream` je příkladem operace, vstupní a výstupní zprávy jsou obě streamování.</span><span class="sxs-lookup"><span data-stu-id="2e625-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="2e625-124">Nakonec `GetReversedStream` žádné vstupy přijímá a vrací `Stream` (streamování).</span><span class="sxs-lookup"><span data-stu-id="2e625-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="2e625-125">Povolení streamovaná přenosy</span><span class="sxs-lookup"><span data-stu-id="2e625-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="2e625-126">Definování kontraktů operace, jak je uvedeno výše poskytuje datové proudy na úrovni modelu programování.</span><span class="sxs-lookup"><span data-stu-id="2e625-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="2e625-127">Chcete-li zrušit existuje přenos stále ukládá do vyrovnávací paměti obsah celé zprávy.</span><span class="sxs-lookup"><span data-stu-id="2e625-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="2e625-128">Pokud chcete povolit přenos streamování, vyberte režim přenosu na element vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="2e625-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="2e625-129">Má element vazby `TransferMode` vlastnost, která může být nastaven na `Buffered`, `Streamed`, `StreamedRequest`, nebo `StreamedResponse`.</span><span class="sxs-lookup"><span data-stu-id="2e625-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="2e625-130">Nastavení režimu převodu na `Streamed` umožňuje streamování komunikace v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="2e625-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="2e625-131">Nastavení režimu převodu na `StreamedRequest` nebo `StreamedResponse` umožňuje streamování komunikace v požadavku nebo odpovědi, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="2e625-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="2e625-132">`basicHttpBinding` Zpřístupňuje `TransferMode` vlastnost pro vazbu, stejně jako `NetTcpBinding` a `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="2e625-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="2e625-133">Pro další přenosy musíte vytvořit vlastní vazby pro nastavení režimu převodu.</span><span class="sxs-lookup"><span data-stu-id="2e625-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="2e625-134">Následující kód z ukázkového konfigurace zobrazuje nastavení `TransferMode` vlastnost streamování na `basicHttpBinding` a vlastních vazeb protokolu HTTP:</span><span class="sxs-lookup"><span data-stu-id="2e625-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
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
  
 <span data-ttu-id="2e625-135">Kromě nastavení `transferMode` k `Streamed`, předchozí konfiguračních sad kód `maxReceivedMessageSize` 64 MB.</span><span class="sxs-lookup"><span data-stu-id="2e625-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="2e625-136">Jako mechanismus ochrany před mobilními `maxReceivedMessageSize` zobrazit zakončení na maximální povolenou velikost zprávy v místech.</span><span class="sxs-lookup"><span data-stu-id="2e625-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="2e625-137">Výchozí hodnota `maxReceivedMessageSize` je 64 KB, což je obvykle příliš nízká pro streamování scénáře.</span><span class="sxs-lookup"><span data-stu-id="2e625-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="2e625-138">Zpracování dat, jako je streamování</span><span class="sxs-lookup"><span data-stu-id="2e625-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="2e625-139">Operace `GetStream`, `UploadStream` a `EchoStream` všechna řešení odesílat data přímo ze souboru nebo uložení přijatá data přímo do souboru.</span><span class="sxs-lookup"><span data-stu-id="2e625-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="2e625-140">Ale v některých případech je požadavek na odeslání nebo příjem velkých objemů dat a provádět některé zpracování na bloky dat se ještě odeslány nebo přijaty.</span><span class="sxs-lookup"><span data-stu-id="2e625-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="2e625-141">Jedním ze způsobů takových situacích je napsat vlastní datový proud (třída, která je odvozena z <xref:System.IO.Stream>), který zpracovává data, jako je číst nebo zapisovat.</span><span class="sxs-lookup"><span data-stu-id="2e625-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="2e625-142">`GetReversedStream` Operace a `ReverseStream` třídy jsou příkladem.</span><span class="sxs-lookup"><span data-stu-id="2e625-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="2e625-143">`GetReversedStream` vytvoří a vrátí novou instanci třídy `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="2e625-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="2e625-144">Vlastní zpracování se stane, jak systém přečte od `ReverseStream` objektu.</span><span class="sxs-lookup"><span data-stu-id="2e625-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="2e625-145">`ReverseStream.Read` Implementace čte blok bajtů ze základního souboru, obrátí je a potom vrátí obrácený bajtů.</span><span class="sxs-lookup"><span data-stu-id="2e625-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="2e625-146">Toto zpětné celý soubor obsahu; jeden blok bajtů se obrátí najednou.</span><span class="sxs-lookup"><span data-stu-id="2e625-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="2e625-147">Toto je příklad, chcete-li zobrazit, jak můžete provádět zpracování datového proudu jako obsah se číst nebo zapisovat z a do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="2e625-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="2e625-148">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2e625-148">Running the Sample</span></span>  
 <span data-ttu-id="2e625-149">Ke spuštění ukázky, nejdřív sestavte službu a klienta podle pokynů na konci tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2e625-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="2e625-150">Potom spusťte službu a klienta ve dvou různých konzoly windows.</span><span class="sxs-lookup"><span data-stu-id="2e625-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="2e625-151">Když se klient spustí, čeká až stisknete ENTER, když se tato služba je připravena.</span><span class="sxs-lookup"><span data-stu-id="2e625-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="2e625-152">Klient pak zavolá metodu `GetStream()`, `UploadStream()` a `GetReversedStream()` nejprve přes protokol HTTP a pak přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="2e625-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="2e625-153">Tady je příklad výstupu ze služby, za nímž následuje příklad výstupu z klienta:</span><span class="sxs-lookup"><span data-stu-id="2e625-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="2e625-154">Výstup služby:</span><span class="sxs-lookup"><span data-stu-id="2e625-154">Service Output:</span></span>  
  
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
  
 <span data-ttu-id="2e625-155">Výstup klienta:</span><span class="sxs-lookup"><span data-stu-id="2e625-155">Client Output:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2e625-156">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="2e625-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2e625-157">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e625-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2e625-158">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e625-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2e625-159">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e625-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e625-160">Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.</span><span class="sxs-lookup"><span data-stu-id="2e625-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e625-161">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="2e625-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e625-162">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="2e625-162">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2e625-163">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2e625-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e625-164">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2e625-164">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
