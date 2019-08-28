---
title: Kanál s dělením dat do bloků
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: b59f5c42f5a0f81f666bc5d22924f14c678a60e1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045702"
---
# <a name="chunking-channel"></a><span data-ttu-id="4b3e2-102">Kanál s dělením dat do bloků</span><span class="sxs-lookup"><span data-stu-id="4b3e2-102">Chunking Channel</span></span>

<span data-ttu-id="4b3e2-103">Při posílání velkých zpráv pomocí Windows Communication Foundation (WCF) je často žádoucí omezit množství paměti využité k ukládání těchto zpráv do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="4b3e2-104">Jedním z možných řešení je vysílat datový proud zprávy (za předpokladu, že část dat je v těle).</span><span class="sxs-lookup"><span data-stu-id="4b3e2-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="4b3e2-105">Některé protokoly ale vyžadují ukládání celé zprávy do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="4b3e2-106">Spolehlivé zasílání zpráv a zabezpečení jsou dva příklady.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="4b3e2-107">Dalším možným řešením je rozdělit velkou zprávu na menší zprávy s názvem bloky dat, odeslat tyto bloky v jednom okamžiku a znovu vytvořit velkou zprávu na straně příjmu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="4b3e2-108">Samotná aplikace by mohla provádět tyto bloky dat a neblokování nebo by k tomu mohla použít vlastní kanál.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="4b3e2-109">Ukázka kanálu pro dělení na bloky dat ukazuje, jak lze použít vlastní protokol nebo vrstvený kanál k provádění bloků dat a rozblokování libovolně velkých zpráv.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="4b3e2-110">Blokování by mělo být vždy použito až po sestavení celé zprávy, která má být odeslána.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="4b3e2-111">Kanál bloků dat by měl být vždy vrstven pod kanálem zabezpečení a spolehlivým kanálem relace.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="4b3e2-112">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b3e2-113">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4b3e2-114">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="4b3e2-115">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4b3e2-116">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="4b3e2-117">Předpoklady a omezení kanálu pro vytváření bloků dat</span><span class="sxs-lookup"><span data-stu-id="4b3e2-117">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="4b3e2-118">Struktura zprávy</span><span class="sxs-lookup"><span data-stu-id="4b3e2-118">Message Structure</span></span>

<span data-ttu-id="4b3e2-119">Kanál pro zpracování zpráv předpokládá, že pro zprávy, které mají být v bloku dat, má následující strukturu zpráv:</span><span class="sxs-lookup"><span data-stu-id="4b3e2-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

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

<span data-ttu-id="4b3e2-120">Při použití třídy ServiceModel musí operace kontraktu s 1 vstupním parametrem odpovídat tomuto obrazci zprávy pro svou vstupní zprávu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="4b3e2-121">Podobně operace kontraktu, které mají 1 výstupní parametr nebo návratovou hodnotu, jsou v rozporu s tímto tvarem zprávy pro výstupní zprávu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="4b3e2-122">Následují příklady takových operací:</span><span class="sxs-lookup"><span data-stu-id="4b3e2-122">The following are examples of such operations:</span></span>

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

### <a name="sessions"></a><span data-ttu-id="4b3e2-123">Relace</span><span class="sxs-lookup"><span data-stu-id="4b3e2-123">Sessions</span></span>

<span data-ttu-id="4b3e2-124">Kanál pro dělení na bloky dat vyžaduje, aby se zprávy přesně předávaly v seřazeném doručování zpráv (bloků dat).</span><span class="sxs-lookup"><span data-stu-id="4b3e2-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="4b3e2-125">To znamená, že musí být příslušný zásobník kanálů relace.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="4b3e2-126">Relace můžou být poskytovány přenosem (například přenos TCP) nebo kanálem protokolu relace (například ReliableSession Channel).</span><span class="sxs-lookup"><span data-stu-id="4b3e2-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="4b3e2-127">Asynchronní odesílání a příjem</span><span class="sxs-lookup"><span data-stu-id="4b3e2-127">Asynchronous Send and Receive</span></span>

<span data-ttu-id="4b3e2-128">Asynchronní metody Send a Receive nejsou v této verzi ukázky kanálu bloků dat implementovány.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="4b3e2-129">Protokol bloků dat</span><span class="sxs-lookup"><span data-stu-id="4b3e2-129">Chunking Protocol</span></span>

<span data-ttu-id="4b3e2-130">Kanál pro dělení na bloky dat definuje protokol, který indikuje začátek a konec série bloků dat a také pořadové číslo každého bloku.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="4b3e2-131">V následujících třech příkladech se zprávy ukazují na úvodní, blokové a koncové zprávy s komentáři, které popisují klíčové aspekty každého z nich.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="4b3e2-132">Spustit zprávu</span><span class="sxs-lookup"><span data-stu-id="4b3e2-132">Start Message</span></span>

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

### <a name="chunk-message"></a><span data-ttu-id="4b3e2-133">Zpráva bloku</span><span class="sxs-lookup"><span data-stu-id="4b3e2-133">Chunk Message</span></span>

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

### <a name="end-message"></a><span data-ttu-id="4b3e2-134">Koncová zpráva</span><span class="sxs-lookup"><span data-stu-id="4b3e2-134">End Message</span></span>

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

## <a name="chunking-channel-architecture"></a><span data-ttu-id="4b3e2-135">Architektura kanálu bloků dat</span><span class="sxs-lookup"><span data-stu-id="4b3e2-135">Chunking Channel Architecture</span></span>

<span data-ttu-id="4b3e2-136">Kanál pro dělení na bloky dat `IDuplexSessionChannel` je na nejvyšší úrovni, který následuje za typickou architekturou kanálů.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="4b3e2-137">Existuje, který může `ChunkingChannelFactory` vytvořit a `ChunkingChannelListener`. `ChunkingBindingElement`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="4b3e2-138">`ChunkingChannelFactory` Vytvoří instance,když`ChunkingChannel` se na ni žádá.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="4b3e2-139">`ChunkingChannelListener` Vytvoří`ChunkingChannel` instance při přijetí nového vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="4b3e2-140">K posílání a přijímání zpráv zodpovídá sámsebe.`ChunkingChannel`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="4b3e2-141">Na další úrovni `ChunkingChannel` spoléhá na několik komponent k implementaci protokolu bloků dat.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="4b3e2-142">Na straně odeslání kanál používá vlastní <xref:System.Xml.XmlDictionaryWriter> volanou `ChunkingWriter` zprávu, která provádí skutečné zpracování dat.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="4b3e2-143">`ChunkingWriter`používá vnitřní kanál přímo k odesílání bloků dat.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="4b3e2-144">Pomocí vlastního `XmlDictionaryWriter` obsahu můžeme poslat bloky dat, když se zapisuje velký text původní zprávy.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="4b3e2-145">To znamená, že neuložíme do vyrovnávací paměti celou původní zprávu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-145">This means we do not buffer the entire original message.</span></span>

![Diagram znázorňující architekturu odesílání kanálu bloků dat.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="4b3e2-147">Na straně příjmu se `ChunkingChannel` stáhnou zprávy z vnitřního kanálu a zadají se do vlastního <xref:System.Xml.XmlDictionaryReader> volaného `ChunkingReader`, který znovu vytvoří původní zprávu z příchozích bloků dat.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="4b3e2-148">`ChunkingChannel`zabalí `Message`dovlastní implementace s názvem `ChunkingMessage` a vrátí tuto zprávu do vrstvy výše. `ChunkingReader`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="4b3e2-149">Tato kombinace `ChunkingReader` a `ChunkingMessage` umožňuje nám deserializovat původní text zprávy, který je čten vrstvou výše, místo abyste museli ukládat celý původní text zprávy do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="4b3e2-150">`ChunkingReader`má frontu, ve které vyrovnávací paměti ukládají příchozí bloky až do maximálního konfigurovatelného počtu bloků v bufferu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="4b3e2-151">Když je dosaženo tohoto maximálního limitu, čtečka čeká na vyřazení zpráv z fronty výše uvedenou vrstvou (to znamená pouhým čtením z původního těla zprávy) nebo až do dosažení maximálního časového limitu příjmu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Diagram znázorňující architekturu příjmu kanálu bloků dat.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="4b3e2-153">Model programování bloků dat</span><span class="sxs-lookup"><span data-stu-id="4b3e2-153">Chunking Programming Model</span></span>

<span data-ttu-id="4b3e2-154">Vývojáři služeb mohou určit, které zprávy mají být v bloku, použitím `ChunkingBehavior` atributu na operace v rámci kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="4b3e2-155">Atribut zpřístupňuje `AppliesTo` vlastnost, která vývojářům umožňuje určit, zda se má použít pro vstupní zprávu, výstupní zprávu nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="4b3e2-156">Následující příklad ukazuje použití `ChunkingBehavior` atributu:</span><span class="sxs-lookup"><span data-stu-id="4b3e2-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

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

<span data-ttu-id="4b3e2-157">Z tohoto programovacího modelu `ChunkingBindingElement` zkompiluje seznam identifikátorů URI akcí, které identifikují zprávy, které mají být zablokované.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="4b3e2-158">Akce každé odchozí zprávy je porovnána s tímto seznamem, aby bylo možné určit, zda má být zpráva v bloku nebo odeslána přímo.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="4b3e2-159">Implementace operace Send</span><span class="sxs-lookup"><span data-stu-id="4b3e2-159">Implementing the Send Operation</span></span>

<span data-ttu-id="4b3e2-160">Na vysoké úrovni operace odeslání nejprve zkontroluje, zda musí být odchozí zpráva v bloku, a pokud ne, odesílá zprávu přímo pomocí vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="4b3e2-161">Pokud je zpráva musí obsahovat bloky dat, odešle se nové `ChunkingWriter` a zavolá se na `ChunkingWriter`odchozí zprávu, která to přesměruje `WriteBodyContents` .</span><span class="sxs-lookup"><span data-stu-id="4b3e2-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="4b3e2-162">V `ChunkingWriter` takovém případě nakopíruje do bloku zprávy (včetně kopírování původních hlaviček zpráv do zprávy spustit blok) a odešle bloky dat pomocí vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="4b3e2-163">Je potřeba poznamenat si několik podrobností:</span><span class="sxs-lookup"><span data-stu-id="4b3e2-163">A few details worth noting:</span></span>

- <span data-ttu-id="4b3e2-164">Odešlete první `ThrowIfDisposedOrNotOpened` volání, aby `CommunicationState` se zajistilo, že se otevře.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="4b3e2-165">Odesílání je synchronizováno, aby bylo možné každou relaci odeslat současně pouze jednu zprávu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="4b3e2-166">Při posílání `ManualResetEvent` zprávy `sendingDone` se systémem se zobrazí název, který se resetuje.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="4b3e2-167">Po odeslání zprávy koncového bloku se tato událost nastaví.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="4b3e2-168">Metoda send počká na nastavení této události, než se pokusí odeslat odchozí zprávu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="4b3e2-169">Odeslat zamkne, `CommunicationObject.ThisLock` aby se zabránilo synchronizovaným změnám stavu při odesílání.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="4b3e2-170">Další informace o <xref:System.ServiceModel.Channels.CommunicationObject> stavech a stavu počítače najdete v dokumentaci.<xref:System.ServiceModel.Channels.CommunicationObject></span><span class="sxs-lookup"><span data-stu-id="4b3e2-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="4b3e2-171">Časový limit odeslaný do odeslání se používá jako časový limit pro celou operaci odeslání, která zahrnuje odesílání všech bloků dat.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="4b3e2-172">Vlastní <xref:System.Xml.XmlDictionaryWriter> návrh byl vybrán, aby nedošlo k ukládání do vyrovnávací paměti pro celý původní text zprávy.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="4b3e2-173"><xref:System.Xml.XmlDictionaryReader> V případě, že jsme se dostali na tělo s `message.GetReaderAtBodyContents` použitím celého těla, bude uloženo do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="4b3e2-174">Místo toho máme vlastní <xref:System.Xml.XmlDictionaryWriter> předaný do. `message.WriteBodyContents`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="4b3e2-175">Když zpráva volá WriteBase64, zapisovač zabalí do zpráv bloky a pošle je pomocí vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="4b3e2-176">WriteBase64 bloky až do odeslání bloku dat.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-176">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="4b3e2-177">Implementace operace Receive</span><span class="sxs-lookup"><span data-stu-id="4b3e2-177">Implementing the Receive Operation</span></span>

<span data-ttu-id="4b3e2-178">V případě vysoké úrovně operace Receive nejprve zkontroluje, že příchozí zpráva `null` není a že se jedná o `ChunkingAction`akci.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="4b3e2-179">Pokud nesplňuje obě kritéria, zpráva se z příjmu vrátí beze změny.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="4b3e2-180">V opačném případě příjem vytvoří `ChunkingReader` nový a `ChunkingMessage` kolem něj obtékající (voláním `GetNewChunkingMessage`).</span><span class="sxs-lookup"><span data-stu-id="4b3e2-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="4b3e2-181">Před vrácením tohoto `ChunkingMessage`nového příkazu obdrží použití vlákna podprocesu `ReceiveChunkLoop`ke spuštění, `innerChannel.Receive` které volá `ChunkingReader` smyčku a předá bloky dat do doby, než je obdržena zpráva koncového bloku nebo dojde k vypršení časového limitu příjmu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="4b3e2-182">Je potřeba poznamenat si několik podrobností:</span><span class="sxs-lookup"><span data-stu-id="4b3e2-182">A few details worth noting:</span></span>

- <span data-ttu-id="4b3e2-183">Podobně jako u Send přijímají `ThrowIfDisposedOrNotOepned` první volání, `CommunicationState` aby se zajistilo, že se otevře.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="4b3e2-184">Příjem je také synchronizovaný, aby bylo možné současně přijmout jenom jednu zprávu z relace.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="4b3e2-185">To je obzvláště důležité, protože po přijetí zprávy počátečního bloku se očekává, že všechny následné přijaté zprávy budou obsahovat bloky dat v této nové sekvenci bloků dat, dokud se nepřijme zpráva koncového bloku dat.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="4b3e2-186">Příjem nemůže přijímat zprávy z vnitřního kanálu, dokud nebudou přijaty všechny bloky, které patří do zprávy, která je v současné době deblokovaná.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="4b3e2-187">K tomu je potřeba přijmout pomocí `ManualResetEvent` pojmenovaného `currentMessageCompleted`, který se nastaví, když se přijme zpráva o ukončení bloku dat a resetování, když se přijme nová zpráva o počátečním bloku.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="4b3e2-188">Na rozdíl od odeslání nebrání přijímání synchronizovaného stavu při příjmu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="4b3e2-189">Například možnost Zavřít může být volána při přijímání a čeká na dokončení probíhajícího příjmu původní zprávy nebo dosažení zadané hodnoty časového limitu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="4b3e2-190">Časový limit předaný do přijetí se používá jako časový limit pro celou operaci přijetí, která zahrnuje příjem všech bloků dat.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="4b3e2-191">Pokud vrstva, která využívá zprávu, spotřebovává tělo zprávy o sazbě nižší, než je počet příchozích zpráv bloku dat, `ChunkingReader` vyrovnávací paměti těchto vstupních bloků až do limitu určeného parametrem. `ChunkingBindingElement.MaxBufferedChunks`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="4b3e2-192">Po dosažení tohoto limitu nebudou z nižší vrstvy načítány žádné další bloky, dokud se nespotřebovává blok dat ve vyrovnávací paměti nebo dokud nedosáhnete časového limitu příjmu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="4b3e2-193">CommunicationObject přepsání</span><span class="sxs-lookup"><span data-stu-id="4b3e2-193">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="4b3e2-194">Otevřít</span><span class="sxs-lookup"><span data-stu-id="4b3e2-194">OnOpen</span></span>

<span data-ttu-id="4b3e2-195">`OnOpen`volání `innerChannel.Open` pro otevření vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="4b3e2-196">OnClose –</span><span class="sxs-lookup"><span data-stu-id="4b3e2-196">OnClose</span></span>

<span data-ttu-id="4b3e2-197">`OnClose`nejprve nastaví `stopReceive` , `true` aby bylo signalizaci `ReceiveChunkLoop` čekání na zastavení.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="4b3e2-198">Potom počká `receiveStopped` <xref:System.Threading.ManualResetEvent>na, který je nastaven při `ReceiveChunkLoop` zastavení.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="4b3e2-199">Za předpokladu, že se `ReceiveChunkLoop` zastaví v rámci zadaného časového limitu, `OnClose` volání `innerChannel.Close` se zbývajícím časovým limitem</span><span class="sxs-lookup"><span data-stu-id="4b3e2-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="4b3e2-200">Přerušení</span><span class="sxs-lookup"><span data-stu-id="4b3e2-200">OnAbort</span></span>

<span data-ttu-id="4b3e2-201">`OnAbort`volání `innerChannel.Abort` přeruší vnitřní kanál.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="4b3e2-202">V případě, že se `ReceiveChunkLoop` čeká na vyřízení, získá výjimku `innerChannel.Receive` z nedokončeného volání.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="4b3e2-203">Došlo k chybě</span><span class="sxs-lookup"><span data-stu-id="4b3e2-203">OnFaulted</span></span>

<span data-ttu-id="4b3e2-204">Při chybě kanálu není nutné speciální chování, takže `OnFaulted` není přepsán. `ChunkingChannel`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="4b3e2-205">Implementace objektu pro vytváření kanálů</span><span class="sxs-lookup"><span data-stu-id="4b3e2-205">Implementing Channel Factory</span></span>

<span data-ttu-id="4b3e2-206">Je zodpovědný za vytváření instancí a pro `ChunkingDuplexSessionChannel` přechody mezi stavy do továrny vnitřního kanálu. `ChunkingChannelFactory`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="4b3e2-207">`OnCreateChannel`vytvoří `IDuplexSessionChannel` vnitřní kanál pomocí továrny vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="4b3e2-208">Pak vytvoří nové `ChunkingDuplexSessionChannel` předání tohoto vnitřního kanálu společně se seznamem akcí zpráv, které mají být v bloku, a maximální počet bloků dat, které se po přijetí ukládají do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="4b3e2-209">Seznam akcí zprávy, které mají být `ChunkingChannelFactory` v bloku, a maximální počet bloků na vyrovnávací paměť jsou dva parametry předané do svého konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="4b3e2-210">Část `ChunkingBindingElement` popisující, kde tyto hodnoty pocházejí.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="4b3e2-211">Rozhraní `OnOpen` ,`OnClose`a jejich asynchronní ekvivalenty volají odpovídající metodu přechodu stavu na objektu pro vytváření vnitřních kanálů. `OnAbort`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="4b3e2-212">Implementace naslouchacího procesu kanálu</span><span class="sxs-lookup"><span data-stu-id="4b3e2-212">Implementing Channel Listener</span></span>

<span data-ttu-id="4b3e2-213">`ChunkingChannelListener` Je Obálka kolem naslouchacího procesu vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="4b3e2-214">Jeho hlavní funkce, kromě volání delegátů do tohoto naslouchacího procesu interního kanálu, je `ChunkingDuplexSessionChannels` zabalit nové kolem kanálů přijatých od naslouchacího procesu vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="4b3e2-215">To se provádí v `OnAcceptChannel` a `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="4b3e2-216">Nově vytvořená `ChunkingDuplexSessionChannel` se předává vnitřní kanál spolu s dalšími parametry uvedenými výše.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="4b3e2-217">Implementace elementu vazby a vazby</span><span class="sxs-lookup"><span data-stu-id="4b3e2-217">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="4b3e2-218">`ChunkingBindingElement`zodpovídá za vytváření `ChunkingChannelFactory` a `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="4b3e2-219">\< `CanBuildChannelListener` `IDuplexSessionChannel` Kontroluje, zda t in `CanBuildChannelFactory`t > a \<t > je typu (jediný kanál podporovaný kanálem bloků dat) a že ostatní prvky vazby ve vazbě tuto možnost podporují. `ChunkingBindingElement` typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="4b3e2-220">`BuildChannelFactory`\<T > nejdřív zkontroluje, jestli jde sestavit požadovaný typ kanálu, a pak získá seznam akcí zprávy, které se mají zablokovat.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="4b3e2-221">Další informace najdete v následující části.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-221">For more information, see the following section.</span></span> <span data-ttu-id="4b3e2-222">Potom vytvoří nový `ChunkingChannelFactory` průchod objektem pro vytváření vnitřního kanálu (vráceným ze `context.BuildInnerChannelFactory<IDuplexSessionChannel>`seznamu), seznamem akcí zpráv a maximálním počtem bloků, které mají být uloženy do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="4b3e2-223">Maximální počet bloků dat pochází z vlastnosti s názvem `MaxBufferedChunks` vystaveno. `ChunkingBindingElement`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="4b3e2-224">`BuildChannelListener<T>`má podobnou implementaci pro vytvoření `ChunkingChannelListener` a předání naslouchací proces vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="4b3e2-225">V této ukázce je obsažena příklad vazby s názvem `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="4b3e2-226">Tato vazba se skládá ze dvou prvků vazby `TcpTransportBindingElement` : `ChunkingBindingElement`a.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="4b3e2-227">Kromě `MaxBufferedChunks` vystavení vlastnosti vazba také nastaví některé `TcpTransportBindingElement` vlastnosti, například `MaxReceivedMessageSize` (nastaví ji na `ChunkingUtils.ChunkSize` + 100 KB bajty pro záhlaví).</span><span class="sxs-lookup"><span data-stu-id="4b3e2-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="4b3e2-228">`TcpChunkingBinding`také implementuje `IBindingRuntimePreferences` a vrátí hodnotu true `ReceiveSynchronously` z metody, což znamená, že jsou implementována pouze synchronní volání Receive.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="4b3e2-229">Určení zpráv pro blok dat</span><span class="sxs-lookup"><span data-stu-id="4b3e2-229">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="4b3e2-230">Kanál bloků dat zablokuje pouze zprávy identifikované pomocí `ChunkingBehavior` atributu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="4b3e2-231">Třída implementuje `IOperationBehavior` a`AddBindingParameter` je implementována voláním metody. `ChunkingBehavior`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="4b3e2-232">V této metodě `ChunkingBehavior` ověřuje hodnota své `AppliesTo` vlastnosti (`InMessage` `OutMessage` nebo obou) k určení, které zprávy mají být v bloku.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="4b3e2-233">Pak získá akci každé z těchto zpráv (z kolekce messages on `OperationDescription`) a přidá je do kolekce řetězců obsažené v `ChunkingBindingParameter`instanci.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="4b3e2-234">Pak to `ChunkingBindingParameter` přidá k poskytnutému `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="4b3e2-235">Tato `BindingParameterCollection` třída je předána `BindingContext` do každého prvku vazby ve vazbě, pokud prvek vazby vytvoří objekt pro vytváření kanálu nebo naslouchací proces kanálu.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="4b3e2-236">`ChunkingBindingElement` Implementacea`BuildChannelListener<T>`vyžádá si tento `ChunkingBindingParameter` výstup z`BindingContext’`s `BindingParameterCollection`. `BuildChannelFactory<T>`</span><span class="sxs-lookup"><span data-stu-id="4b3e2-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="4b3e2-237">Kolekce `ChunkingBindingParameter` akcí obsažených v rámci je pak předána `ChunkingChannelFactory` do nebo `ChunkingChannelListener` `ChunkingDuplexSessionChannel`, která je následně předává do.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="4b3e2-238">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4b3e2-238">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4b3e2-239">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4b3e2-239">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4b3e2-240">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-240">Install ASP.NET 4.0 using the following command.</span></span>

    ```
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="4b3e2-241">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b3e2-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="4b3e2-242">Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b3e2-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="4b3e2-243">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b3e2-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

5. <span data-ttu-id="4b3e2-244">Nejprve spusťte Service. exe a potom spusťte soubor Client. exe a Sledujte výstup oken konzoly.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="4b3e2-245">Při spuštění ukázky se očekává následující výstup.</span><span class="sxs-lookup"><span data-stu-id="4b3e2-245">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="4b3e2-246">Klient:</span><span class="sxs-lookup"><span data-stu-id="4b3e2-246">Client:</span></span>

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

<span data-ttu-id="4b3e2-247">WebServer</span><span class="sxs-lookup"><span data-stu-id="4b3e2-247">Server:</span></span>

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
