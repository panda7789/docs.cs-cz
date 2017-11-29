---
title: Stream
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8c20f53692bb54b802ce5be555b3832352c09ec0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="stream"></a><span data-ttu-id="9d956-102">Stream</span><span class="sxs-lookup"><span data-stu-id="9d956-102">Stream</span></span>
<span data-ttu-id="9d956-103">Ukázkový datový proud demonstruje použití streamování přenosu režimu komunikace.</span><span class="sxs-lookup"><span data-stu-id="9d956-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="9d956-104">Služba zpřístupňuje několik operací, které odesílat a přijímat datové proudy.</span><span class="sxs-lookup"><span data-stu-id="9d956-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="9d956-105">Tato ukázka se hostuje sama.</span><span class="sxs-lookup"><span data-stu-id="9d956-105">This sample is self-hosted.</span></span> <span data-ttu-id="9d956-106">Klient a služba jsou programy konzoly.</span><span class="sxs-lookup"><span data-stu-id="9d956-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d956-107">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9d956-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="9d956-108">může komunikovat ve dvou režimech přenos – ve vyrovnávací paměti nebo streamování.</span><span class="sxs-lookup"><span data-stu-id="9d956-108"> can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="9d956-109">Ve výchozím režimu přenosu ve vyrovnávací paměti zprávy musí být zcela doručována předtím, než příjemce může číst.</span><span class="sxs-lookup"><span data-stu-id="9d956-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="9d956-110">V režimu datového přenosu můžete začít příjemce zprávu zpracovat, než je zcela doručit.</span><span class="sxs-lookup"><span data-stu-id="9d956-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="9d956-111">Streamování režimu je užitečné, když informace, které se předá je náročná a může být zpracována sériově.</span><span class="sxs-lookup"><span data-stu-id="9d956-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="9d956-112">Streamování režimu je také užitečné, pokud zpráva je moc velká, aby se zcela do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d956-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="9d956-113">Streaming kontraktů a kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="9d956-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="9d956-114">Streamování je něco zvážit při návrhu kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="9d956-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="9d956-115">Pokud operace obdrží nebo vrátí velké objemy dat, měli byste zvážit, tato data, aby se zabránilo využití velkého množství paměti z důvodu ukládání do vyrovnávací paměti zpráv vstupních nebo výstupních datových proudů.</span><span class="sxs-lookup"><span data-stu-id="9d956-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="9d956-116">K datům datového proudu, parametr, který obsahuje, že data musí být parametr pouze ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="9d956-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="9d956-117">Například pokud je vstupní zpráva má Streamovat, operaci musí mít přesně jeden vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="9d956-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="9d956-118">Podobně pokud zpráva výstup je odesílání, operaci musí mít právě jednu výstupní parametr nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9d956-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="9d956-119">V případě, parametr nebo return hodnotě typ musí být buď `Stream`, `Message`, nebo `IXmlSerializable`.</span><span class="sxs-lookup"><span data-stu-id="9d956-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="9d956-120">Zde je použit v této ukázce streamování kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="9d956-120">The following is the service contract used in this streaming sample.</span></span>  
  
```  
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
  
 <span data-ttu-id="9d956-121">`GetStream` Operace přijímá některé vstupní data jako řetězec, který je uloží do vyrovnávací paměti a vrátí `Stream`, který je prostřednictvím datového proudu.</span><span class="sxs-lookup"><span data-stu-id="9d956-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="9d956-122">Naopak `UploadStream` přebírá `Stream` (streamování) a vrátí `bool` (uložená do vyrovnávací paměti).</span><span class="sxs-lookup"><span data-stu-id="9d956-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="9d956-123">`EchoStream`provede a vrátí `Stream` je příkladem operace, jejichž vstup a výstup zprávy jsou obě streamování.</span><span class="sxs-lookup"><span data-stu-id="9d956-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="9d956-124">Nakonec `GetReversedStream` přebere žádné vstupy a vrátí `Stream` (streamování).</span><span class="sxs-lookup"><span data-stu-id="9d956-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="9d956-125">Povolení přenášené datovými proudy přenosů</span><span class="sxs-lookup"><span data-stu-id="9d956-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="9d956-126">Definování kontraktů operaci výše popsané poskytuje streamování na úrovni modelu programování.</span><span class="sxs-lookup"><span data-stu-id="9d956-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="9d956-127">Pokud zastavíte existuje, přenos stále ukládá do vyrovnávací paměti obsahu celé zprávy.</span><span class="sxs-lookup"><span data-stu-id="9d956-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="9d956-128">Pokud chcete povolit přenos streamování, vyberte režim přenosu u prvku vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="9d956-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="9d956-129">Obsahuje prvku vazby `TransferMode` vlastnost, která může být nastaven na `Buffered`, `Streamed`, `StreamedRequest`, nebo `StreamedResponse`.</span><span class="sxs-lookup"><span data-stu-id="9d956-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="9d956-130">Nastavení režimu přenosu `Streamed` umožňuje streamování komunikace v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="9d956-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="9d956-131">Nastavení režimu přenosu `StreamedRequest` nebo `StreamedResponse` umožňuje streamování komunikaci v požadavek nebo odpověď, a to v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9d956-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="9d956-132">`basicHttpBinding` Zpřístupní `TransferMode` vlastnost vazby stejně `NetTcpBinding` a `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="9d956-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="9d956-133">Pro ostatní přenosy musíte vytvořit vlastní vazby nastavit režim přenosu.</span><span class="sxs-lookup"><span data-stu-id="9d956-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="9d956-134">Následující kód konfigurace z ukázky ukazuje nastavení `TransferMode` vlastnost streamování na `basicHttpBinding` a vlastní vazby HTTP:</span><span class="sxs-lookup"><span data-stu-id="9d956-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
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
  
 <span data-ttu-id="9d956-135">Kromě nastavení `transferMode` k `Streamed`, předchozí sady konfigurace kódu `maxReceivedMessageSize` na 64 MB.</span><span class="sxs-lookup"><span data-stu-id="9d956-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="9d956-136">Jako mechanismus obrany `maxReceivedMessageSize` přijímat zakončení na maximální povolenou velikost zprávy v místech.</span><span class="sxs-lookup"><span data-stu-id="9d956-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="9d956-137">Výchozí hodnota `maxReceivedMessageSize` je 64 KB, který je obvykle příliš nízká pro streamování scénáře.</span><span class="sxs-lookup"><span data-stu-id="9d956-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="9d956-138">Zpracování dat, jako je streamování</span><span class="sxs-lookup"><span data-stu-id="9d956-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="9d956-139">Operace `GetStream`, `UploadStream` a `EchoStream` všechny řešení odesílání dat přímo ze souboru nebo ukládání dat přijatých přímo do souboru.</span><span class="sxs-lookup"><span data-stu-id="9d956-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="9d956-140">Ale v některých případech je potřeba odesílat nebo přijímat velké objemy dat a provedení některých zpracování na bloky dat, jako je právě odesílané nebo přijímané.</span><span class="sxs-lookup"><span data-stu-id="9d956-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="9d956-141">Jeden způsob, jak vyřešit takových scénářů je napsat vlastní datový proud (třídy odvozené z <xref:System.IO.Stream>), zpracovává data, jako je číst nebo zapisovat.</span><span class="sxs-lookup"><span data-stu-id="9d956-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="9d956-142">`GetReversedStream` Operace a `ReverseStream` třídy jsou příklady.</span><span class="sxs-lookup"><span data-stu-id="9d956-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="9d956-143">`GetReversedStream`vytvoří a vrátí novou instanci třídy `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="9d956-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="9d956-144">Vlastní zpracování se stane, protože systém přečte z tohoto `ReverseStream` objektu.</span><span class="sxs-lookup"><span data-stu-id="9d956-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="9d956-145">`ReverseStream.Read` Implementace čte blok bajtů z podkladový soubor, obrátí je a pak vrátí odstínech bajtů.</span><span class="sxs-lookup"><span data-stu-id="9d956-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="9d956-146">Toto není reverse celý soubor obsahu; současně se obrátí jeden blok bajtů.</span><span class="sxs-lookup"><span data-stu-id="9d956-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="9d956-147">Jedná se o příklad zobrazit, jak můžete provádět zpracování datového proudu, jak se obsah číst nebo zapisovat z a do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="9d956-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="9d956-148">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="9d956-148">Running the Sample</span></span>  
 <span data-ttu-id="9d956-149">Ke spuštění ukázky, nejprve vytvořte službu a klienta podle následujících pokynů na konci tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9d956-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="9d956-150">Spusťte službu a klienta ve dvou různých konzoly windows.</span><span class="sxs-lookup"><span data-stu-id="9d956-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="9d956-151">Když se klient spustí, se zobrazí výzvu k stiskněte klávesu ENTER, pokud služba je připravena.</span><span class="sxs-lookup"><span data-stu-id="9d956-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="9d956-152">Klient pak zavolá metodu `GetStream()`, `UploadStream()` a `GetReversedStream()` nejprve přes protokol HTTP a pak přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="9d956-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="9d956-153">Tady je příklad výstup ze služby následuje příklad výstupu z klienta:</span><span class="sxs-lookup"><span data-stu-id="9d956-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="9d956-154">Výstup služby:</span><span class="sxs-lookup"><span data-stu-id="9d956-154">Service Output:</span></span>  
  
```  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="9d956-155">Výstup klienta:</span><span class="sxs-lookup"><span data-stu-id="9d956-155">Client Output:</span></span>  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9d956-156">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="9d956-156">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9d956-157">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9d956-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9d956-158">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9d956-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9d956-159">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9d956-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d956-160">Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="9d956-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9d956-161">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="9d956-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9d956-162">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9d956-162">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9d956-163">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9d956-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9d956-164">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9d956-164">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a><span data-ttu-id="9d956-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d956-165">See Also</span></span>
