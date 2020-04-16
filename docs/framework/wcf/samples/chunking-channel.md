---
title: Kanál s dělením dat do bloků
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 7b436e2ce708a122a7eae3b07ad01515fb2dce96
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463969"
---
# <a name="chunking-channel"></a><span data-ttu-id="4d9fa-102">Kanál s dělením dat do bloků</span><span class="sxs-lookup"><span data-stu-id="4d9fa-102">Chunking Channel</span></span>

<span data-ttu-id="4d9fa-103">Při odesílání velkých zpráv pomocí Windows Communication Foundation (WCF), je často žádoucí omezit množství paměti používané k ukládání těchto zpráv do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="4d9fa-104">Jedním z možných řešení je streamovat text zprávy (za předpokladu, že většina dat je v těle).</span><span class="sxs-lookup"><span data-stu-id="4d9fa-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="4d9fa-105">Některé protokoly však vyžadují ukládání do vyrovnávací paměti celé zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="4d9fa-106">Spolehlivé zasílání zpráv a zabezpečení jsou dva takové příklady.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="4d9fa-107">Dalším možným řešením je rozdělit velké zprávy do menších zpráv s názvem bloky, odeslat tyto bloky jeden blok najednou a rekonstruovat velké zprávy na straně příjmu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="4d9fa-108">Samotná aplikace může provést tento bloků a de-chunking nebo může použít vlastní kanál k tomu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="4d9fa-109">Ukázka kanálu bloků ukazuje, jak vlastní protokol nebo vrstvený kanál lze použít k provádění bloků a odstranění bloků libovolně velkých zpráv.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="4d9fa-110">Bloků by měla být vždy použita pouze po vytvoření celé zprávy, která má být odeslána.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="4d9fa-111">Kanál bloků by měl být vždy vrstvený pod kanálem zabezpečení a spolehlivým kanálem relace.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="4d9fa-112">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d9fa-113">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d9fa-114">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="4d9fa-115">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d9fa-116">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="4d9fa-117">Předpoklady a omezení bloků kanálu</span><span class="sxs-lookup"><span data-stu-id="4d9fa-117">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="4d9fa-118">Struktura zpráv</span><span class="sxs-lookup"><span data-stu-id="4d9fa-118">Message Structure</span></span>

<span data-ttu-id="4d9fa-119">Kanál bloků předpokládá následující strukturu zpráv pro zprávy, které mají být bloků dat:</span><span class="sxs-lookup"><span data-stu-id="4d9fa-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

```xml
<soap:Envelope>
  <!-- headers -->
  <soap:Body>
    <operationElement>
      <paramElement>data to be chunked</paramElement>
    </operationElement>
  </soap:Body>
</soap:Envelope>
```

<span data-ttu-id="4d9fa-120">Při použití ServiceModel, operace smlouvy, které mají 1 vstupní parametr v souladu s tímto obrazcem zprávy pro jejich vstupní zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="4d9fa-121">Podobně smlouvy operace, které mají 1 výstupní parametr nebo vrácená hodnota v souladu s tímto obrazcem zprávy pro jejich výstupní zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="4d9fa-122">Následují příklady těchto operací:</span><span class="sxs-lookup"><span data-stu-id="4d9fa-122">The following are examples of such operations:</span></span>

```csharp
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

### <a name="sessions"></a><span data-ttu-id="4d9fa-123">Relace</span><span class="sxs-lookup"><span data-stu-id="4d9fa-123">Sessions</span></span>

<span data-ttu-id="4d9fa-124">Kanál bloků vyžaduje, aby zprávy byly doručeny přesně jednou, v objednaném doručování zpráv (bloků).</span><span class="sxs-lookup"><span data-stu-id="4d9fa-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="4d9fa-125">To znamená, že základní zásobník kanálu musí být relace.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="4d9fa-126">Relace mohou být poskytovány přenosem (například přenost CP) nebo kanálem protokolu relace (například kanál ReliableSession).</span><span class="sxs-lookup"><span data-stu-id="4d9fa-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="4d9fa-127">Asynchronní odesílání a přijímání</span><span class="sxs-lookup"><span data-stu-id="4d9fa-127">Asynchronous Send and Receive</span></span>

<span data-ttu-id="4d9fa-128">Asynchronní metody odesílání a přijímání nejsou implementovány v této verzi ukázky kanálu bloků.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="4d9fa-129">Protokol bloků</span><span class="sxs-lookup"><span data-stu-id="4d9fa-129">Chunking Protocol</span></span>

<span data-ttu-id="4d9fa-130">Kanál bloků definuje protokol, který označuje začátek a konec řady bloků dat a pořadové číslo každého bloku.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="4d9fa-131">Následující tři ukázkové zprávy ukazují počáteční, blok a konec zprávy s komentáři, které popisují klíčové aspekty každého.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="4d9fa-132">Spustit zprávu</span><span class="sxs-lookup"><span data-stu-id="4d9fa-132">Start Message</span></span>

```xml
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
<!--Original message action is replaced with a chunking-specific action. -->
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

### <a name="chunk-message"></a><span data-ttu-id="4d9fa-133">Zpráva bloku</span><span class="sxs-lookup"><span data-stu-id="4d9fa-133">Chunk Message</span></span>

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

### <a name="end-message"></a><span data-ttu-id="4d9fa-134">Ukončit zprávu</span><span class="sxs-lookup"><span data-stu-id="4d9fa-134">End Message</span></span>

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

## <a name="chunking-channel-architecture"></a><span data-ttu-id="4d9fa-135">Architektura kanálu bloků</span><span class="sxs-lookup"><span data-stu-id="4d9fa-135">Chunking Channel Architecture</span></span>

<span data-ttu-id="4d9fa-136">Kanál bloků je, `IDuplexSessionChannel` že na vysoké úrovni následuje typickou architekturu kanálu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="4d9fa-137">Tam `ChunkingBindingElement` je, že `ChunkingChannelFactory` může `ChunkingChannelListener`stavět a .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="4d9fa-138">Vytvoří `ChunkingChannelFactory` instance, `ChunkingChannel` kdy je požádán.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="4d9fa-139">Vytvoří `ChunkingChannelListener` instance, `ChunkingChannel` kdy je přijat nový vnitřní kanál.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="4d9fa-140">Sám `ChunkingChannel` je zodpovědný za odesílání a přijímání zpráv.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="4d9fa-141">Na další úroveň `ChunkingChannel` dolů, spoléhá na několik součástí k implementaci bloku protokolu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="4d9fa-142">Na straně odeslání kanál používá <xref:System.Xml.XmlDictionaryWriter> vlastní `ChunkingWriter` volané, který provádí skutečné bloků.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="4d9fa-143">`ChunkingWriter`používá vnitřní kanál přímo k odesílání bloků dat.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="4d9fa-144">Použití vlastní `XmlDictionaryWriter` nám umožňuje vyslat bloky jako velké tělo původní zprávy je psáno.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="4d9fa-145">To znamená, že nebudeme do vyrovnávací paměti celou původní zprávu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-145">This means we do not buffer the entire original message.</span></span>

![Diagram, který ukazuje architekturu odesílání kanálu bloků.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="4d9fa-147">Na straně příjmu `ChunkingChannel` vytáhne zprávy z vnitřního kanálu <xref:System.Xml.XmlDictionaryReader> a `ChunkingReader`předá je vlastní volal , který rekonstituuje původní zprávy z příchozí bloky.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="4d9fa-148">`ChunkingChannel`zabalí `ChunkingReader` to ve `Message` vlastní `ChunkingMessage` implementaci s názvem a vrátí tuto zprávu do výše uvedené vrstvy.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="4d9fa-149">Tato kombinace `ChunkingReader` `ChunkingMessage` a umožňuje nám de-chunk původní text zprávy, jak je čteno vrstvou výše namísto nutnosti vyrovnávací paměti celé původní text zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="4d9fa-150">`ChunkingReader`má frontu, kde vyrovnávací paměti příchozí bloky až do maximálního konfigurovatelného počtu bloků vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="4d9fa-151">Po dosažení tohoto maximálního limitu čtenář čeká na zprávy, které mají být vyprázdněny z fronty vrstvou výše (to znamená, že pouze čtení z původního textu zprávy) nebo dokud není dosaženo maximálního časového limitu příjmu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Diagram, který ukazuje blokovací kanál přijímat architekturu.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="4d9fa-153">Blokovací programovací model</span><span class="sxs-lookup"><span data-stu-id="4d9fa-153">Chunking Programming Model</span></span>

<span data-ttu-id="4d9fa-154">Vývojáři služeb můžete určit, které zprávy `ChunkingBehavior` mají být bloků dat pomocí atributu operace v rámci smlouvy.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="4d9fa-155">Atribut zpřístupňuje `AppliesTo` vlastnost, která umožňuje vývojáři určit, zda bloing platí pro vstupní zprávu, výstupní zprávu nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="4d9fa-156">Následující příklad ukazuje použití `ChunkingBehavior` atributu:</span><span class="sxs-lookup"><span data-stu-id="4d9fa-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

```csharp
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

<span data-ttu-id="4d9fa-157">Z tohoto programovacího `ChunkingBindingElement` modelu zkompiluje seznam identifikátorů URI akce, které identifikují zprávy, které mají být odebrány.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="4d9fa-158">Akce každé odchozí zprávy je porovnán s tímto seznamem k určení, zda má být zpráva na bloky dat nebo odeslané přímo.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="4d9fa-159">Implementace operace odeslání</span><span class="sxs-lookup"><span data-stu-id="4d9fa-159">Implementing the Send Operation</span></span>

<span data-ttu-id="4d9fa-160">Na vysoké úrovni Send operace nejprve zkontroluje, zda odchozí zpráva musí být na bloky dat a pokud ne, odešle zprávu přímo pomocí vnitřníkanál.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="4d9fa-161">Pokud zpráva musí být bloků, Send `ChunkingWriter` vytvoří `WriteBodyContents` nový a volá na `ChunkingWriter`odchozí zprávy předání tohoto .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="4d9fa-162">Potom `ChunkingWriter` se zpráva bloků (včetně kopírování záhlaví původní zprávy na počáteční zprávu bloku) a odešle bloky pomocí vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="4d9fa-163">Několik detailů stojí za zmínku:</span><span class="sxs-lookup"><span data-stu-id="4d9fa-163">A few details worth noting:</span></span>

- <span data-ttu-id="4d9fa-164">Odešlete `ThrowIfDisposedOrNotOpened` první `CommunicationState` volání, abyste se ujistili, že je otevřen.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="4d9fa-165">Odesílání je synchronizováno tak, aby bylo možné odeslat pouze jednu zprávu pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="4d9fa-166">Je `ManualResetEvent` název, `sendingDone` který je resetován při odeslání zprávy bloku.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="4d9fa-167">Po odeslání zprávy koncového bloku je tato událost nastavena.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="4d9fa-168">Send Metoda čeká na tuto událost, která má být nastavena před pokusem o odeslání odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="4d9fa-169">Odeslat `CommunicationObject.ThisLock` zámky zabránit synchronizované změny stavu při odesílání.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="4d9fa-170">Další <xref:System.ServiceModel.Channels.CommunicationObject> informace o <xref:System.ServiceModel.Channels.CommunicationObject> stavech a stavovém počítači naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="4d9fa-171">Časový čas předaný odeslat se používá jako časový časový výtok pro celou operaci odeslání, která zahrnuje odeslání všech bloků.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="4d9fa-172">Vlastní <xref:System.Xml.XmlDictionaryWriter> návrh byl vybrán, aby se zabránilo ukládání do vyrovnávací paměti celé původní tělo zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="4d9fa-173">Pokud bychom měli <xref:System.Xml.XmlDictionaryReader> dostat na `message.GetReaderAtBodyContents` tělo pomocí celého těla by se pufrované.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="4d9fa-174">Místo toho máme <xref:System.Xml.XmlDictionaryWriter> vlastní, který `message.WriteBodyContents`je předán .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="4d9fa-175">Jako zpráva volá WriteBase64 na zapisovače, zapisovač balíčky do bloků do zpráv a odešle je pomocí vnitřníkanál.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="4d9fa-176">WriteBase64 bloky, dokud je odeslán blok.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-176">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="4d9fa-177">Implementace operace příjmu</span><span class="sxs-lookup"><span data-stu-id="4d9fa-177">Implementing the Receive Operation</span></span>

<span data-ttu-id="4d9fa-178">Na vysoké úrovni receive operace nejprve zkontroluje, `null` zda příchozí zpráva `ChunkingAction`není a že její akce je .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="4d9fa-179">Pokud nesplňuje obě kritéria, zpráva je vrácena beze změny z Receive.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="4d9fa-180">V opačném případě `ChunkingReader` Receive vytvoří `ChunkingMessage` nové a nové `GetNewChunkingMessage`zabalené kolem něj (voláním ).</span><span class="sxs-lookup"><span data-stu-id="4d9fa-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="4d9fa-181">Před vrácením, `ChunkingMessage`že nové receive používá `ReceiveChunkLoop`vlákno threadpool ke spuštění , který `innerChannel.Receive` `ChunkingReader` volá ve smyčce a ruce pryč bloky až do konce bloku zprávy je přijata nebo příjem časový režim je přístupná.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="4d9fa-182">Několik detailů stojí za zmínku:</span><span class="sxs-lookup"><span data-stu-id="4d9fa-182">A few details worth noting:</span></span>

- <span data-ttu-id="4d9fa-183">Stejně jako Odeslat, Přijímat první hovory, `ThrowIfDisposedOrNotOepned` abyste se ujistili, že `CommunicationState` je otevřeno.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="4d9fa-184">Příjem je také synchronizován tak, aby z relace mohla být přijata pouze jedna zpráva.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="4d9fa-185">To je obzvláště důležité, protože po přijetí zprávy počáteční houska, všechny následné přijaté zprávy se očekává, že bloky v rámci této nové sekvence bloku dat, dokud je přijata zpráva konce bloku.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="4d9fa-186">Přijímat nelze vyžádat zprávy z vnitřního kanálu, dokud nejsou přijaty všechny bloky, které patří do zprávy aktuálně de-chunked.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="4d9fa-187">Chcete-li to provést, Receive používá `ManualResetEvent` pojmenovaný `currentMessageCompleted`, který je nastaven při přijetí zprávy bloku ukončení a obnovit při přijetí nové zprávy počáteční blok.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="4d9fa-188">Na rozdíl od odeslat, Příjem nezabrání synchronizované přechody stavu při příjmu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="4d9fa-189">Například Close lze volat při příjmu a čeká na dokončení čekající příjem původní zprávy nebo zadaný časový rozsah je dosaženo.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="4d9fa-190">Časový čas předaný Receive se používá jako časový časový rozsah pro celou operaci příjmu, která zahrnuje příjem všech bloků.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="4d9fa-191">Pokud vrstva, která spotřebovává zprávu spotřebovává text zprávy rychlostí nižší než rychlost příchozích `ChunkingReader` zpráv bloku, vyrovnávací paměti těchto příchozích bloků dat až do limitu určeného . `ChunkingBindingElement.MaxBufferedChunks`</span><span class="sxs-lookup"><span data-stu-id="4d9fa-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="4d9fa-192">Jakmile je dosaženo tohoto limitu, žádné další bloky jsou vytaženy z nižší vrstvy, dokud je spotřebována do vyrovnávací paměti bloku nebo je dosaženo časového limitu příjmu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="4d9fa-193">Přepsání objektu CommunicationObject</span><span class="sxs-lookup"><span data-stu-id="4d9fa-193">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="4d9fa-194">OnOpen</span><span class="sxs-lookup"><span data-stu-id="4d9fa-194">OnOpen</span></span>

<span data-ttu-id="4d9fa-195">`OnOpen`volání `innerChannel.Open` pro otevření vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="4d9fa-196">Při uzavření</span><span class="sxs-lookup"><span data-stu-id="4d9fa-196">OnClose</span></span>

<span data-ttu-id="4d9fa-197">`OnClose`první `stopReceive` nastaví na `true` `ReceiveChunkLoop` signál čekající zastavit.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="4d9fa-198">Potom čeká na `receiveStopped` <xref:System.Threading.ManualResetEvent>, který je `ReceiveChunkLoop` nastaven při zastavení.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="4d9fa-199">Za `ReceiveChunkLoop` předpokladu, že zastaví `OnClose` `innerChannel.Close` v rámci zadaného časového času, volání se zbývajícím časovým časem.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="4d9fa-200">Onabort</span><span class="sxs-lookup"><span data-stu-id="4d9fa-200">OnAbort</span></span>

<span data-ttu-id="4d9fa-201">`OnAbort`volání `innerChannel.Abort` přerušit vnitřní kanál.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="4d9fa-202">Pokud je čekající `ReceiveChunkLoop` získá výjimku z `innerChannel.Receive` čekající volání.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="4d9fa-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="4d9fa-203">OnFaulted</span></span>

<span data-ttu-id="4d9fa-204">Nevyžaduje `ChunkingChannel` zvláštní chování při chybě kanálu, `OnFaulted` takže není přepsán.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="4d9fa-205">Implementace továrny kanálů</span><span class="sxs-lookup"><span data-stu-id="4d9fa-205">Implementing Channel Factory</span></span>

<span data-ttu-id="4d9fa-206">Je `ChunkingChannelFactory` zodpovědný za vytváření `ChunkingDuplexSessionChannel` instancí a pro kaskádové přechody stavu do vnitřní hotova kanálu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="4d9fa-207">`OnCreateChannel`používá vnitřní kanál factory `IDuplexSessionChannel` k vytvoření vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="4d9fa-208">Potom vytvoří nový `ChunkingDuplexSessionChannel` předávání tento vnitřní kanál spolu se seznamem akcí zprávy, které mají být bloků a maximální počet bloků do vyrovnávací paměti při příjmu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="4d9fa-209">Seznam akcí zprávy, které mají být bloků dat a maximální počet bloků `ChunkingChannelFactory` do vyrovnávací paměti jsou dva parametry předané v jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="4d9fa-210">Část popisuje, `ChunkingBindingElement` odkud tyto hodnoty pocházejí.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="4d9fa-211">`OnOpen`, `OnClose`a `OnAbort` jejich asynchronní ekvivalenty volání odpovídající metody přechodu stavu na vnitřní kanálu factory.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="4d9fa-212">Implementace naslouchací proces kanálu</span><span class="sxs-lookup"><span data-stu-id="4d9fa-212">Implementing Channel Listener</span></span>

<span data-ttu-id="4d9fa-213">Je `ChunkingChannelListener` obálka kolem naslouchací proces vnitřní kanál.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="4d9fa-214">Jeho hlavní funkcí, kromě delegáta volání, že `ChunkingDuplexSessionChannels` vnitřní kanál posluchače, je zabalit nové kolem kanály přijaté z vnitřního kanálu posluchače.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="4d9fa-215">To se `OnAcceptChannel` provádí `OnEndAcceptChannel`v a .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="4d9fa-216">Nově vytvořené `ChunkingDuplexSessionChannel` je předán vnitřní kanál spolu s dalšími parametry dříve popsanými.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="4d9fa-217">Implementace prvku vazby a vazby</span><span class="sxs-lookup"><span data-stu-id="4d9fa-217">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="4d9fa-218">`ChunkingBindingElement`je zodpovědný za `ChunkingChannelFactory` `ChunkingChannelListener`vytvoření a .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="4d9fa-219">Zkontroluje, `ChunkingBindingElement` zda `CanBuildChannelFactory` \<T `CanBuildChannelListener` \<v T> `IDuplexSessionChannel` a T> je typu (jediný kanál podporovaný kanálu bloků) a že ostatní elementy vazby podporují tento typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="4d9fa-220">`BuildChannelFactory`\<T> nejprve zkontroluje, zda lze sestavit požadovaný typ kanálu, a poté získá seznam akcí zpráv, které mají být na bloky dat.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="4d9fa-221">Další informace naleznete v následující části.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-221">For more information, see the following section.</span></span> <span data-ttu-id="4d9fa-222">Potom vytvoří nový `ChunkingChannelFactory` předávání vnitřní kanálu factory (jak se vrátil z `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), seznam akcí zprávy a maximální počet bloků do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="4d9fa-223">Maximální počet bloků dat pochází z `MaxBufferedChunks` vlastnosti, která je vystavena `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="4d9fa-224">`BuildChannelListener<T>`má podobnou implementaci `ChunkingChannelListener` pro vytvoření a předání naslouchací proces vnitřní kanál.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="4d9fa-225">V této ukázce je `TcpChunkingBinding`zahrnuta příklad vazby s názvem .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="4d9fa-226">Tato vazba se skládá `TcpTransportBindingElement` ze `ChunkingBindingElement`dvou prvků vazby: a .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="4d9fa-227">`MaxBufferedChunks` Kromě vystavení vlastnosti, vazba také nastaví `TcpTransportBindingElement` některé `MaxReceivedMessageSize` vlastnosti, `ChunkingUtils.ChunkSize` jako je například (nastaví ji na + 100 kB bajtů pro záhlaví).</span><span class="sxs-lookup"><span data-stu-id="4d9fa-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="4d9fa-228">`TcpChunkingBinding`také implementuje `IBindingRuntimePreferences` a `ReceiveSynchronously` vrátí true z metody označující, že jsou implementovány pouze synchronní Receive volání.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="4d9fa-229">Určení, které zprávy na blok</span><span class="sxs-lookup"><span data-stu-id="4d9fa-229">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="4d9fa-230">Blokovací kanál bloky pouze zprávy identifikované prostřednictvím atributu. `ChunkingBehavior`</span><span class="sxs-lookup"><span data-stu-id="4d9fa-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="4d9fa-231">Třída `ChunkingBehavior` implementuje `IOperationBehavior` a je `AddBindingParameter` implementována voláním metody.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="4d9fa-232">V `ChunkingBehavior` této metodě zkoumá hodnotu `AppliesTo` jeho`InMessage` `OutMessage` vlastnost ( , nebo obojí) k určení, které zprávy by měly být bloků dat.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="4d9fa-233">Potom získá akci každé z těchto zpráv (z `OperationDescription`kolekce Messages na ) a přidá ji `ChunkingBindingParameter`do kolekce řetězců obsažené v instanci .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="4d9fa-234">Poté to `ChunkingBindingParameter` toto přidá `BindingParameterCollection`k poskytnutému .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="4d9fa-235">To `BindingParameterCollection` je předán `BindingContext` uvnitř do každý element vazby ve vazbě při tento element vazby vytvoří factory kanálu nebo naslouchací proces kanálu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="4d9fa-236">'s `ChunkingBindingElement`provádění `BuildChannelFactory<T>` a `BuildChannelListener<T>` vytáhnout `ChunkingBindingParameter` to `BindingContext’`z `BindingParameterCollection`s .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="4d9fa-237">Kolekce akcí obsažených v `ChunkingBindingParameter` je pak `ChunkingChannelFactory` předána nebo `ChunkingChannelListener`, která `ChunkingDuplexSessionChannel`zase předá do .</span><span class="sxs-lookup"><span data-stu-id="4d9fa-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="4d9fa-238">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4d9fa-238">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d9fa-239">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4d9fa-239">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4d9fa-240">Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-240">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="4d9fa-241">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d9fa-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="4d9fa-242">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d9fa-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="4d9fa-243">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d9fa-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

5. <span data-ttu-id="4d9fa-244">Nejprve spusťte soubor Service.exe, potom spusťte soubor Client.exe a sledujte výstup obou oken konzoly.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="4d9fa-245">Při spuštění ukázky se očekává následující výstup.</span><span class="sxs-lookup"><span data-stu-id="4d9fa-245">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="4d9fa-246">Klient:</span><span class="sxs-lookup"><span data-stu-id="4d9fa-246">Client:</span></span>

```console
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

<span data-ttu-id="4d9fa-247">Server:</span><span class="sxs-lookup"><span data-stu-id="4d9fa-247">Server:</span></span>

```console
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
