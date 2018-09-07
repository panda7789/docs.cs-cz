---
title: Kanál s dělením dat do bloků
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 9572ad6f88786af34252cea1f3c62d5067257b8b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087906"
---
# <a name="chunking-channel"></a><span data-ttu-id="1f2ae-102">Kanál s dělením dat do bloků</span><span class="sxs-lookup"><span data-stu-id="1f2ae-102">Chunking Channel</span></span>
<span data-ttu-id="1f2ae-103">Při odesílání velkých zpráv pomocí služby Windows Communication Foundation (WCF), je často žádoucí omezit množství paměti pro zprávy ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="1f2ae-104">Jedním z možných řešení je do datového proudu zprávy (za předpokladu, že hromadných dat je v textu).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="1f2ae-105">Ale některé protokoly vyžadují celé zprávy do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="1f2ae-106">Spolehlivé zasílání zpráv a zabezpečení jsou tyto dva příklady.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="1f2ae-107">Další možnou příčinou je zdola nahoru objemné zprávy do menších zprávy označované jako bloky dat, odesílání jednoho bloku tyto bloky dat najednou a znovuvytvoření velkých zpráv na straně příjmu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="1f2ae-108">Zrušení bloků nebo ho může používat vlastní kanál k tomu a samotná aplikace udělat tento bloků.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="1f2ae-109">Vytváření bloků kanál příklad ukazuje, jak vlastní protokol nebo vrstvami kanálu lze provést bloků a zrušení bloků libovolně velkých zpráv.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>  
  
 <span data-ttu-id="1f2ae-110">Dělením dat do bloků by měl vždy být použity až poté, co byl vytvořen celé zprávy k odeslání.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="1f2ae-111">Vytváření bloků kanálu by měl vždy vrstvy pod zabezpečení kanálu a jeho kanál stabilní relace.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f2ae-112">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1f2ae-113">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1f2ae-114">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1f2ae-115">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1f2ae-116">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="1f2ae-117">Vytváření bloků kanál předpoklady a omezení</span><span class="sxs-lookup"><span data-stu-id="1f2ae-117">Chunking Channel Assumptions and Limitations</span></span>  
  
### <a name="message-structure"></a><span data-ttu-id="1f2ae-118">Struktura zprávy</span><span class="sxs-lookup"><span data-stu-id="1f2ae-118">Message Structure</span></span>  
 <span data-ttu-id="1f2ae-119">Vytváření bloků kanálu se předpokládá následující strukturu zprávu pro zprávy být rozdělený do bloků dat:</span><span class="sxs-lookup"><span data-stu-id="1f2ae-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>  
  
```xml  
<soap:Envelope ...>  
  <!-- headers -->  
  <soap:Body>  
    <operationElement>  
      <paramElement>data to be chunked</paramElement>  
    </operationElement>  
  </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="1f2ae-120">Při použití modelu, kontrakt operace, které mají 1 vstupní parametr v souladu s tohoto obrazce zprávy pro jejich vstupní zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="1f2ae-121">Podobně kontrakt operace, které mají 1 výstupní parametr nebo návratovou hodnotu v souladu s tohoto obrazce zprávy pro jejich výstupní zprávu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="1f2ae-122">Následují příklady takových operací:</span><span class="sxs-lookup"><span data-stu-id="1f2ae-122">The following are examples of such operations:</span></span>  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay = true)]  
    void UploadStream(Stream stream);  
}  
```  
  
### <a name="sessions"></a><span data-ttu-id="1f2ae-123">Relace</span><span class="sxs-lookup"><span data-stu-id="1f2ae-123">Sessions</span></span>  
 <span data-ttu-id="1f2ae-124">Vytváření bloků kanálu vyžaduje zprávy v pořadí doručení zpráv (bloky) doručit přesně jednou.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="1f2ae-125">To znamená, že musí být základní zásobník kanál s relacemi.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="1f2ae-126">Relace je možné poskytnou přenosu (například přenosu protokolu TCP) nebo kanál s relacemi protokolu (například ReliableSession kanál).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>  
  
### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="1f2ae-127">Asynchronní odesílání a přijímání</span><span class="sxs-lookup"><span data-stu-id="1f2ae-127">Asynchronous Send and Receive</span></span>  
 <span data-ttu-id="1f2ae-128">Asynchronní odesílání a příjem metody nejsou v této verzi bloků ukázkový kanál implementovány.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>  
  
## <a name="chunking-protocol"></a><span data-ttu-id="1f2ae-129">Vytváření bloků protokolu</span><span class="sxs-lookup"><span data-stu-id="1f2ae-129">Chunking Protocol</span></span>  
 <span data-ttu-id="1f2ae-130">Vytváření bloků kanál definuje protokol, který označuje začátek a konec řadu bloky dat, a také pořadové číslo od každého bloku.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="1f2ae-131">Následující tři příklad zprávy ukazují spuštění, bloků dat a end zprávy s komentáři, které popisují klíčové aspekty každého.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>  
  
### <a name="start-message"></a><span data-ttu-id="1f2ae-132">Zpráva spuštění</span><span class="sxs-lookup"><span data-stu-id="1f2ae-132">Start Message</span></span>  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
<!—Original message action is replaced with a chunking-specific action. -->  
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>  
<!--  
Original message is assigned a unique id that is transmitted   
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.  
-->  
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">  
53f183ee-04aa-44a0-b8d3-e45224563109  
</MessageId>  
<!--  
ChunkingStart header signals the start of a chunked message.  
-->  
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />  
<!--  
Original message action is transmitted in OriginalAction.  
This is required to re-create the original message on the other side.  
-->  
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">  
http://tempuri.org/ITestService/EchoStream  
    </OriginalAction>  
   <!--  
    All original message headers are included here.  
   -->  
  </s:Header>  
  <s:Body>  
<!--  
Chunking assumes this structure of Body content:  
<element>  
  <childelement>large data to be chunked<childelement>  
</element>  
The start message contains just <element> and <childelement> without  
the data to be chunked.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="chunk-message"></a><span data-ttu-id="1f2ae-133">Blok zpráv</span><span class="sxs-lookup"><span data-stu-id="1f2ae-133">Chunk Message</span></span>  
  
```xml  
<s:Envelope   
  xmlns:a="http://www.w3.org/2005/08/addressing"   
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
   <!--  
    All chunking protocol messages have this action.  
   -->  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
The sequence number of the chunk.  
This number restarts at 1 with each new sequence of chunks.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      1096  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The chunked data is wrapped in a chunk element.  
The encoding of this data (and the entire message)   
depends on the encoder used. The chunking channel does not mandate an encoding.  
-->  
    <chunk xmlns="http://samples.microsoft.com/chunking">  
kfSr2QcBlkHTvQ==  
    </chunk>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="end-message"></a><span data-ttu-id="1f2ae-134">Zpráva ukončení</span><span class="sxs-lookup"><span data-stu-id="1f2ae-134">End Message</span></span>  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
ChunkingEnd header signals the end of a chunk sequence.  
-->  
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"   
                 xmlns="http://samples.microsoft.com/chunking" />  
<!--  
ChunkingEnd messages have a sequence number.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      79  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The ChunkingEnd message has the same <element><childelement> structure  
as the ChunkingStart message.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="chunking-channel-architecture"></a><span data-ttu-id="1f2ae-135">Vytváření bloků architektura kanálů</span><span class="sxs-lookup"><span data-stu-id="1f2ae-135">Chunking Channel Architecture</span></span>  
 <span data-ttu-id="1f2ae-136">Vytváření bloků kanál `IDuplexSessionChannel` , na vysoké úrovni, následuje architektura typické kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="1f2ae-137">Je `ChunkingBindingElement` , které můžete vytvářet `ChunkingChannelFactory` a `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="1f2ae-138">`ChunkingChannelFactory` Vytváří instance `ChunkingChannel` když je vyzván k.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="1f2ae-139">`ChunkingChannelListener` Vytváří instance `ChunkingChannel` při přijetí nového vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="1f2ae-140">`ChunkingChannel` Samotného je zodpovědná za odesílání a příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>  
  
 <span data-ttu-id="1f2ae-141">Na další úrovni, `ChunkingChannel` spoléhá na několik komponent k implementaci bloků protokolu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="1f2ae-142">Na straně odesílání kanál používá vlastní `XmlDictionaryWriter` volá `ChunkingWriter` , který neodpovídá skutečné bloků.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-142">On the send side, the channel uses a custom `XmlDictionaryWriter` called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="1f2ae-143">`ChunkingWriter` používá vnitřního kanálu přímo k odesílání bloků.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="1f2ae-144">Použití vlastní `XmlDictionaryWriter` , umožníte nám odeslat bloky dat jako rozsáhlý na původní zprávu o průběhu zapisování.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="1f2ae-145">To znamená, že jsme neukládaného ve vyrovnávací paměti celý původní zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-145">This means we do not buffer the entire original message.</span></span>  
  
 <span data-ttu-id="1f2ae-146">![Dělením dat do bloků kanál](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")</span><span class="sxs-lookup"><span data-stu-id="1f2ae-146">![Chunking Channel](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")</span></span>  
  
 <span data-ttu-id="1f2ae-147">Na straně příjmu `ChunkingChannel` přetáhne zprávy z vnitřního kanálu a předá je do vlastní `XmlDictionaryReader` volá `ChunkingReader`, který reconstitutes původní zprávu z příchozí datové dávky.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom `XmlDictionaryReader` called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="1f2ae-148">`ChunkingChannel` zabalí to `ChunkingReader` ve vlastním `Message` volaná implementaci `ChunkingMessage` a vrátí tuto zprávu vrstvě nad ní.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="1f2ae-149">Tato kombinace `ChunkingReader` a `ChunkingMessage` umožňuje zrušení bloku dat původní text zprávy, jako je čten stranou vrstvu nad namísto toho, aby do vyrovnávací paměti celý původní text zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="1f2ae-150">`ChunkingReader` má fronty, kde vyrovnávacích pamětí příchozí bloky dat až po maximální Konfigurovatelný počet bloků dat ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="1f2ae-151">Po dosažení maximální limit čtečky čeká na zprávy z fronty vybíjet ve vrstvě nad ní (to znamená podle jen pro čtení z původní text zprávy) nebo dokud se zobrazí maximální počet je dosaženo časového limitu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>  
  
 <span data-ttu-id="1f2ae-152">![Dělením dat do bloků kanál](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")</span><span class="sxs-lookup"><span data-stu-id="1f2ae-152">![Chunking Channel](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")</span></span>  
  
## <a name="chunking-programming-model"></a><span data-ttu-id="1f2ae-153">Dělením dat do bloků programovací Model</span><span class="sxs-lookup"><span data-stu-id="1f2ae-153">Chunking Programming Model</span></span>  
 <span data-ttu-id="1f2ae-154">Vývojáři služeb můžete zadat zprávy, které mají být blokové použitím `ChunkingBehavior` atribut do operací v rámci smlouvy.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="1f2ae-155">Poskytuje atribut `AppliesTo` vlastnost, která umožňuje vývojářům k určení, jestli dat platí pro vstupní zprávy, výstupní zpráva nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="1f2ae-156">Následující příklad ukazuje použití `ChunkingBehavior` atribut:</span><span class="sxs-lookup"><span data-stu-id="1f2ae-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.Both)]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay=true)]  
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]  
    void UploadStream(Stream stream);  
  
}  
```  
  
 <span data-ttu-id="1f2ae-157">V tomto programovacím modelu `ChunkingBindingElement` sestaví seznam identifikátorů URI, který identifikuje tak ty být rozdělený do bloků dat akce.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="1f2ae-158">Akce každé odchozí zprávy se porovná tento seznam a určují, jestli zprávy by měl být rozdělený do bloků dat nebo odesílají přímo.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>  
  
## <a name="implementing-the-send-operation"></a><span data-ttu-id="1f2ae-159">Implementace operace odeslání</span><span class="sxs-lookup"><span data-stu-id="1f2ae-159">Implementing the Send Operation</span></span>  
 <span data-ttu-id="1f2ae-160">Na vysoké úrovni operace odeslání nejprve zkontroluje, zda odchozí zprávy musí být rozdělený do bloků dat a pokud ne, odešle zprávu přímo pomocí vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>  
  
 <span data-ttu-id="1f2ae-161">Pokud zpráva musí být rozdělený do bloků dat, vytvoří novou odeslat `ChunkingWriter` a volání `WriteBodyContents` v odchozí zprávě předají se jí to `ChunkingWriter`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="1f2ae-162">`ChunkingWriter` Neodpovídá zprávu dělením dat do bloků (včetně kopírování původní záhlaví zpráv do bloku zpráva spuštění) a odešle bloky dat pomocí vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>  
  
 <span data-ttu-id="1f2ae-163">Za zmínku několik podrobností:</span><span class="sxs-lookup"><span data-stu-id="1f2ae-163">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="1f2ae-164">Poslat prvním volání `ThrowIfDisposedOrNotOpened` zajistit, `CommunicationState` je otevřen.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>  
  
-   <span data-ttu-id="1f2ae-165">Odesílání se synchronizuje, aby tento pouze jedna zpráva byla odeslána současně pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="1f2ae-166">Je `ManualResetEvent` s názvem `sendingDone` , která se resetuje při odesílání bloku zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="1f2ae-167">Jakmile je odeslána zpráva koncovým bloků dat, je tato událost nastavit.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="1f2ae-168">Tato událost nastavit před pokusem o odeslání odchozí zprávy čeká metody Send.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>  
  
-   <span data-ttu-id="1f2ae-169">Odeslat zámky `CommunicationObject.ThisLock` zabránit nesynchronizuje, změny stavu při odesílání.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="1f2ae-170">Najdete v článku <xref:System.ServiceModel.Channels.CommunicationObject> dokumentaci pro další informace o <xref:System.ServiceModel.Channels.CommunicationObject> stavy a stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>  
  
-   <span data-ttu-id="1f2ae-171">Časový limit předaný k odeslání se používá jako časový limit operace celý odeslání, který obsahuje všechny bloky dat odesílání.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>  
  
-   <span data-ttu-id="1f2ae-172">Vlastní `XmlDictionaryWriter` návrh byl zvolen ke Vyhněte se ukládání do vyrovnávací paměti celý původní text zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-172">The custom `XmlDictionaryWriter` design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="1f2ae-173">Pokud se nám získat `XmlDictionaryReader` na text pomocí `message.GetReaderAtBodyContents` celého obsahu by být ukládány do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-173">If we were to get an `XmlDictionaryReader` on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="1f2ae-174">Místo toho budeme mít vlastní `XmlDictionaryWriter` , který je předán `message.WriteBodyContents`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-174">Instead, we have a custom `XmlDictionaryWriter` that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="1f2ae-175">Jako zprávu, která volá WriteBase64 zapisovače zapisovač zabalí bloků dat do zpráv a odešle je pomocí vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="1f2ae-176">WriteBase64 blokuje, dokud se nepošle bloků.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-176">WriteBase64 blocks until the chunk is sent.</span></span>  
  
## <a name="implementing-the-receive-operation"></a><span data-ttu-id="1f2ae-177">Implementace operace přijetí</span><span class="sxs-lookup"><span data-stu-id="1f2ae-177">Implementing the Receive Operation</span></span>  
 <span data-ttu-id="1f2ae-178">Na vysoké úrovni operace obdržení nejprve zkontroluje, že příchozí zpráva není `null` a, který je akcí `ChunkingAction`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="1f2ae-179">Pokud obě kritéria nesplňuje, je vrácená zpráva beze změny z parametru Receive.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="1f2ae-180">Jinak, vytvoří novou Receive `ChunkingReader` a nový `ChunkingMessage` zabalené kolem něj (pomocí volání `GetNewChunkingMessage`).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="1f2ae-181">Teprve potom se informuje, že noví `ChunkingMessage`, příjmu používá ke spouštění vláken fondu vláken `ReceiveChunkLoop`, který volá `innerChannel.Receive` ve smyčce a praktické vypnout bloků dat na `ChunkingReader` dokud přijatá zpráva ukončení bloku nebo dosažení časový limit přijetí.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>  
  
 <span data-ttu-id="1f2ae-182">Za zmínku několik podrobností:</span><span class="sxs-lookup"><span data-stu-id="1f2ae-182">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="1f2ae-183">Jako je odesílání, příjem první volání `ThrowIfDisposedOrNotOepned` zajistit, `CommunicationState` je otevřen.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>  
  
-   <span data-ttu-id="1f2ae-184">Zobrazí se synchronizují také tak, že pouze jeden zpráva může dostat současně z relace.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="1f2ae-185">To je obzvláště důležité, protože po doručení zprávy do začátku bloku dat, všechny následné přijaté zprávy jsou očekávány bloků dat v rámci tohoto nového pořadí bloků dokud přijal zprávu ukončení bloku.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="1f2ae-186">Přijímat nelze vytahují zprávy z vnitřního kanálu, dokud se všechny bloky dat, které patří k aktuálně Probíhá zrušení rozdělený do bloků dat zprávy jsou přijímány.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="1f2ae-187">Chcete-li to provést, obdržet používá `ManualResetEvent` s názvem `currentMessageCompleted`, který je nastaven při zpráva ukončení bloku dat je přijetí a resetovat při doručení zprávy do nového bloku start.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>  
  
-   <span data-ttu-id="1f2ae-188">Na rozdíl od odeslání přijetí nezabraňuje synchronizované přechodů mezi stavy při příjmu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="1f2ae-189">Například Zavřít lze volat při přijímání a čeká, až do dokončení čeká na příjem původní zpráva nebo zadaný časový limit.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>  
  
-   <span data-ttu-id="1f2ae-190">Časový limit předaný k příjmu se používá jako vypršení časového limitu pro celý přijímat operace, která zahrnuje příjem všechny bloky dat.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>  
  
-   <span data-ttu-id="1f2ae-191">Pokud vrstva, která zpracovává zprávy spotřebovává text zprávy s rychlostí nižší než počet příchozích zpráv bloků dat `ChunkingReader` ukládá do vyrovnávací paměti tyto příchozí bloky až do limitu určeném `ChunkingBindingElement.MaxBufferedChunks`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="1f2ae-192">Po dosažení tohoto limitu, nemá nečistoty, se berou z nižší vrstvě, dokud nebude využívat ve vyrovnávací paměti datových dávek nebo je dosaženo časového limitu příjmu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>  
  
## <a name="communicationobject-overrides"></a><span data-ttu-id="1f2ae-193">V objektu CommunicationObject přepsání</span><span class="sxs-lookup"><span data-stu-id="1f2ae-193">CommunicationObject Overrides</span></span>  
  
### <a name="onopen"></a><span data-ttu-id="1f2ae-194">Při otevření</span><span class="sxs-lookup"><span data-stu-id="1f2ae-194">OnOpen</span></span>  
 <span data-ttu-id="1f2ae-195">`OnOpen` volání `innerChannel.Open` vnitřního kanálu otevřít.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>  
  
### <a name="onclose"></a><span data-ttu-id="1f2ae-196">Při zavření</span><span class="sxs-lookup"><span data-stu-id="1f2ae-196">OnClose</span></span>  
 <span data-ttu-id="1f2ae-197">`OnClose` nejprve nastaví `stopReceive` k `true` který signalizuje, že čeká na `ReceiveChunkLoop` zastavit.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="1f2ae-198">Pak čeká `receiveStopped``ManualResetEvent`, která je nastavena, když `ReceiveChunkLoop` zastaví.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-198">It then waits for the `receiveStopped``ManualResetEvent`, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="1f2ae-199">Za předpokladu, že `ReceiveChunkLoop` zastaví v rámci zadaného časového limitu, `OnClose` volání `innerChannel.Close` s zbývající časový limit.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>  
  
### <a name="onabort"></a><span data-ttu-id="1f2ae-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="1f2ae-200">OnAbort</span></span>  
 <span data-ttu-id="1f2ae-201">`OnAbort` volání `innerChannel.Abort` přerušit vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="1f2ae-202">Pokud je na čekající `ReceiveChunkLoop` získá výjimku z na čekající `innerChannel.Receive` volání.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>  
  
### <a name="onfaulted"></a><span data-ttu-id="1f2ae-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="1f2ae-203">OnFaulted</span></span>  
 <span data-ttu-id="1f2ae-204">`ChunkingChannel` Nevyžaduje zvláštní chování, pokud je v kanálu došlo k chybě tak `OnFaulted` nepřepíše.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>  
  
## <a name="implementing-channel-factory"></a><span data-ttu-id="1f2ae-205">Implementace objektu pro vytváření kanálů</span><span class="sxs-lookup"><span data-stu-id="1f2ae-205">Implementing Channel Factory</span></span>  
 <span data-ttu-id="1f2ae-206">`ChunkingChannelFactory` Je zodpovědný za vytváření instancí `ChunkingDuplexSessionChannel` a pro kaskádové přechodů mezi stavy k výroba vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>  
  
 <span data-ttu-id="1f2ae-207">`OnCreateChannel` Výroba vnitřního kanálu použije k vytvoření `IDuplexSessionChannel` vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="1f2ae-208">Potom vytvoří nový `ChunkingDuplexSessionChannel` předáním tohoto vnitřního kanálu společně se seznamem zpráva akce, které mají být rozdělený do bloků dat a maximální počet bloků dat do vyrovnávací paměti při příjmu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="1f2ae-209">Seznam zpráv akce, které mají být rozdělený do bloků dat a maximální počet bloků dat do vyrovnávací paměti jsou dva parametry předány `ChunkingChannelFactory` 've svém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="1f2ae-210">V sekci `ChunkingBindingElement` popisuje, odkud pocházejí tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>  
  
 <span data-ttu-id="1f2ae-211">`OnOpen`, `OnClose`, `OnAbort` a ekvivalenty asynchronní volání odpovídající metody přechod stavu na výroba vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>  
  
## <a name="implementing-channel-listener"></a><span data-ttu-id="1f2ae-212">Prováděcí modul pro naslouchání kanálu</span><span class="sxs-lookup"><span data-stu-id="1f2ae-212">Implementing Channel Listener</span></span>  
 <span data-ttu-id="1f2ae-213">`ChunkingChannelListener` Představuje obálku kolem naslouchací proces vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="1f2ae-214">Jeho hlavním smyslem, kromě volání delegáta pro tuto naslouchací proces vnitřního kanálu je zabalit nové `ChunkingDuplexSessionChannels` kolem kanály přijímán z vnitřního kanálu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="1f2ae-215">To se provádí v `OnAcceptChannel` a `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="1f2ae-216">Nově vytvořený `ChunkingDuplexSessionChannel` je předán vnitřního kanálu společně s další parametry popsaných výše.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>  
  
## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="1f2ae-217">Implementující Element vazby a vazby</span><span class="sxs-lookup"><span data-stu-id="1f2ae-217">Implementing Binding Element and Binding</span></span>  
 <span data-ttu-id="1f2ae-218">`ChunkingBindingElement` zodpovídá za vytvoření `ChunkingChannelFactory` a `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="1f2ae-219">`ChunkingBindingElement` Kontroluje, zda T v `CanBuildChannelFactory` \<T > a `CanBuildChannelListener` \<T > je typu `IDuplexSessionChannel` (pouze kanál nepodporuje vytváření bloků kanálu) a další prvky vazby ve vazbě podporu tohoto Typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>  
  
 <span data-ttu-id="1f2ae-220">`BuildChannelFactory`\<T > nejprve zkontroluje, že typ požadované kanálu může být sestaven a potom získá seznam zpráv akce, které mají být rozdělený do bloků dat.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="1f2ae-221">Další informace najdete v následující části.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-221">For more information, see the following section.</span></span> <span data-ttu-id="1f2ae-222">Potom vytvoří nový `ChunkingChannelFactory` předáním výroba vnitřního kanálu (vrácená `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), seznam zpráv akce a maximální počet bloků dat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="1f2ae-223">Maximální počet bloků, které pocházejí z vlastnost s názvem `MaxBufferedChunks` vystavené `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>  
  
 <span data-ttu-id="1f2ae-224">`BuildChannelListener<T>` má podobné implementace pro vytvoření `ChunkingChannelListener` a předají se jí vnitřního kanálu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>  
  
 <span data-ttu-id="1f2ae-225">Je vazbu příklad zahrnuté v této ukázce s názvem `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="1f2ae-226">Tato vazba se skládá ze dvou elementů vazby: `TcpTransportBindingElement` a `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="1f2ae-227">Kromě vystavení `MaxBufferedChunks` vlastnost vazby také nastaví některá `TcpTransportBindingElement` vlastnosti, jako `MaxReceivedMessageSize` (nastaví na `ChunkingUtils.ChunkSize` + 100 KB bajtů pro záhlaví).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>  
  
 <span data-ttu-id="1f2ae-228">`TcpChunkingBinding` také implementuje `IBindingRuntimePreferences` a vrátí hodnotu true z `ReceiveSynchronously` metoda označující, že jsou implementovány pouze synchronní volání Receive.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>  
  
### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="1f2ae-229">Určení, které zprávy do bloků dat</span><span class="sxs-lookup"><span data-stu-id="1f2ae-229">Determining Which Messages To Chunk</span></span>  
 <span data-ttu-id="1f2ae-230">Vytváření bloků kanál chunks pouze zprávy identifikován `ChunkingBehavior` atribut.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="1f2ae-231">`ChunkingBehavior` Implementuje třída `IOperationBehavior` a je implementována pomocí volání `AddBindingParameter` metody.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="1f2ae-232">V této metodě `ChunkingBehavior` ověří hodnotu jeho `AppliesTo` vlastnosti (`InMessage`, `OutMessage` nebo obojí) k určení, které zprávy by měl být rozdělený do bloků dat.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="1f2ae-233">Potom získá akce pro každou z těchto zpráv z (z kolekce zpráv na `OperationDescription`) a přidá jej do kolekce řetězců obsažených v rámci instance `ChunkingBindingParameter`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="1f2ae-234">To potom přidá `ChunkingBindingParameter` zadanému `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>  
  
 <span data-ttu-id="1f2ae-235">To `BindingParameterCollection` je předáno uvnitř `BindingContext` na každý prvek vazby ve vazbě při tento element vazby sestavení výrobu kanálu nebo modul pro naslouchání kanálu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="1f2ae-236">`ChunkingBindingElement`Vaší implementace `BuildChannelFactory<T>` a `BuildChannelListener<T>` toto vyžádat `ChunkingBindingParameter` z celkového počtu `BindingContext’`s `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="1f2ae-237">Kolekci akcí, které jsou obsažené `ChunkingBindingParameter` je pak předán `ChunkingChannelFactory` nebo `ChunkingChannelListener`, který pak předává jej do `ChunkingDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="1f2ae-238">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="1f2ae-238">Running the Sample</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1f2ae-239">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="1f2ae-239">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1f2ae-240">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-240">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="1f2ae-241">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="1f2ae-242">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="1f2ae-243">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1f2ae-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="1f2ae-244">Nejprve spustit Service.exe, spusťte Client.exe a podívejte se na obě okna konzoly pro výstup.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>  
  
 <span data-ttu-id="1f2ae-245">Při spuštění ukázky, očekává se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="1f2ae-245">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="1f2ae-246">Klient:</span><span class="sxs-lookup"><span data-stu-id="1f2ae-246">Client:</span></span>  
  
```  
Press enter when service is available  
  
 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
 <span data-ttu-id="1f2ae-247">Server:</span><span class="sxs-lookup"><span data-stu-id="1f2ae-247">Server:</span></span>  
  
```  
Service started, press enter to exit  
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f2ae-248">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f2ae-248">See Also</span></span>
