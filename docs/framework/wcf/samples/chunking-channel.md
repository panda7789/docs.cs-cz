---
title: "Kanál s dělením dat do bloků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2fe0ad62a55c6536b0054aa23ac556b896b02be4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="chunking-channel"></a><span data-ttu-id="d1253-102">Kanál s dělením dat do bloků</span><span class="sxs-lookup"><span data-stu-id="d1253-102">Chunking Channel</span></span>
<span data-ttu-id="d1253-103">Při odesílání velkých zpráv pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], je často žádoucí omezit množství paměti k přechodnému ukládání těchto zpráv.</span><span class="sxs-lookup"><span data-stu-id="d1253-103">When sending large messages using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="d1253-104">Jedním z možných řešení je k vysílání datového proudu tělo zprávy (za předpokladu, že hromadné dat je v textu).</span><span class="sxs-lookup"><span data-stu-id="d1253-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="d1253-105">Ale vyžadují některé protokoly ukládání do vyrovnávací paměti celé zprávy.</span><span class="sxs-lookup"><span data-stu-id="d1253-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="d1253-106">Spolehlivé zasílání zpráv a zabezpečení jsou dva příklady takových.</span><span class="sxs-lookup"><span data-stu-id="d1253-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="d1253-107">Další možnou příčinou je zdola nahoru velké zprávy do menších zpráv názvem bloky dat, najednou odeslat jeden blok tyto bloků a rekonstruovat velké zprávy na straně příjmu.</span><span class="sxs-lookup"><span data-stu-id="d1253-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="d1253-108">Vlastní aplikace udělat toto rozdělování a zrušte rozdělování nebo použít vlastní kanál to udělat.</span><span class="sxs-lookup"><span data-stu-id="d1253-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="d1253-109">Bloku dat kanál příklad ukazuje, jak vlastního protokolu nebo vrstveného kanál slouží k rozdělování a zrušte rozdělování libovolně velké zpráv.</span><span class="sxs-lookup"><span data-stu-id="d1253-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>  
  
 <span data-ttu-id="d1253-110">Rozdělování by měl vždycky být použity pouze po celé zprávy před jejich odesláním byla vytvořená.</span><span class="sxs-lookup"><span data-stu-id="d1253-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="d1253-111">Bloku dat kanál, který by měl vrstvený vždy pod zabezpečený kanál a spolehlivé relace kanál.</span><span class="sxs-lookup"><span data-stu-id="d1253-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1253-112">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d1253-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1253-113">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="d1253-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d1253-114">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d1253-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d1253-115">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d1253-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d1253-116">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d1253-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="d1253-117">Rozdělování kanál předpoklady a omezení</span><span class="sxs-lookup"><span data-stu-id="d1253-117">Chunking Channel Assumptions and Limitations</span></span>  
  
### <a name="message-structure"></a><span data-ttu-id="d1253-118">Struktura zprávy</span><span class="sxs-lookup"><span data-stu-id="d1253-118">Message Structure</span></span>  
 <span data-ttu-id="d1253-119">Bloku dat kanál předpokládá následující strukturu zpráva pro zpráv, které mají být blokové:</span><span class="sxs-lookup"><span data-stu-id="d1253-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>  
  
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
  
 <span data-ttu-id="d1253-120">Při použití ServiceModel, kontrakt operace, které mají 1 vstupní parametr v souladu se tento tvar zprávy pro jejich vstupní zprávu.</span><span class="sxs-lookup"><span data-stu-id="d1253-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="d1253-121">Podobně kontrakt operace, které mají 1 výstupní parametr, nebo může vracet hodnotu v souladu se tento tvar zprávy pro jejich výstup zprávu.</span><span class="sxs-lookup"><span data-stu-id="d1253-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="d1253-122">Následují příklady těchto operací:</span><span class="sxs-lookup"><span data-stu-id="d1253-122">The following are examples of such operations:</span></span>  
  
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
  
### <a name="sessions"></a><span data-ttu-id="d1253-123">Relace</span><span class="sxs-lookup"><span data-stu-id="d1253-123">Sessions</span></span>  
 <span data-ttu-id="d1253-124">Kanál bloku dat vyžaduje zpráv, které mají být doručeny právě jednou, v doručení zprávy (bloky).</span><span class="sxs-lookup"><span data-stu-id="d1253-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="d1253-125">To znamená, že základní zásobník kanál musí být relacemi.</span><span class="sxs-lookup"><span data-stu-id="d1253-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="d1253-126">Relace se dá zajistit přenos (například přenos TCP) nebo protokol relacemi kanál (například ReliableSession kanál).</span><span class="sxs-lookup"><span data-stu-id="d1253-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>  
  
### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="d1253-127">Asynchronní odesílání a přijímání</span><span class="sxs-lookup"><span data-stu-id="d1253-127">Asynchronous Send and Receive</span></span>  
 <span data-ttu-id="d1253-128">Asynchronní odesílání a příjmu metody nejsou implementované v této verzi bloku dat ukázkový kanál.</span><span class="sxs-lookup"><span data-stu-id="d1253-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>  
  
## <a name="chunking-protocol"></a><span data-ttu-id="d1253-129">Bloku dat protokolu</span><span class="sxs-lookup"><span data-stu-id="d1253-129">Chunking Protocol</span></span>  
 <span data-ttu-id="d1253-130">Bloku dat kanál definuje protokol, který označuje začátek a konec řadu bloky dat, a také pořadové číslo od každého bloku.</span><span class="sxs-lookup"><span data-stu-id="d1253-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="d1253-131">Následující tři příklad zprávy ukazují spuštění a bloku a end zprávy s komentáři, které popisují každou klíčové aspekty.</span><span class="sxs-lookup"><span data-stu-id="d1253-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>  
  
### <a name="start-message"></a><span data-ttu-id="d1253-132">Spusťte zprávu</span><span class="sxs-lookup"><span data-stu-id="d1253-132">Start Message</span></span>  
  
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
  
### <a name="chunk-message"></a><span data-ttu-id="d1253-133">Bloku zpráv</span><span class="sxs-lookup"><span data-stu-id="d1253-133">Chunk Message</span></span>  
  
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
  
### <a name="end-message"></a><span data-ttu-id="d1253-134">Zpráva konce</span><span class="sxs-lookup"><span data-stu-id="d1253-134">End Message</span></span>  
  
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
  
## <a name="chunking-channel-architecture"></a><span data-ttu-id="d1253-135">Architektura bloku dat kanál</span><span class="sxs-lookup"><span data-stu-id="d1253-135">Chunking Channel Architecture</span></span>  
 <span data-ttu-id="d1253-136">Kanál bloku dat je `IDuplexSessionChannel` , na vysoké úrovni, odpovídá architektuře typické kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="d1253-137">Je `ChunkingBindingElement` , můžete vytvořit `ChunkingChannelFactory` a `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="d1253-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="d1253-138">`ChunkingChannelFactory` Vytváří instance `ChunkingChannel` když jej požaduje.</span><span class="sxs-lookup"><span data-stu-id="d1253-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="d1253-139">`ChunkingChannelListener` Vytváří instance `ChunkingChannel` datum přijetí nového vnitřní kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="d1253-140">`ChunkingChannel` Samotné zodpovídá za odesílání a přijímání zpráv.</span><span class="sxs-lookup"><span data-stu-id="d1253-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>  
  
 <span data-ttu-id="d1253-141">Na další úrovni dolů `ChunkingChannel` spoléhá na několik součástí k provádění bloku dat protokolu.</span><span class="sxs-lookup"><span data-stu-id="d1253-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="d1253-142">Na straně odesílání kanál používá vlastní `XmlDictionaryWriter` názvem `ChunkingWriter` , nebude skutečná rozdělování.</span><span class="sxs-lookup"><span data-stu-id="d1253-142">On the send side, the channel uses a custom `XmlDictionaryWriter` called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="d1253-143">`ChunkingWriter`používá vnitřní kanál přímo k odesílání bloků.</span><span class="sxs-lookup"><span data-stu-id="d1253-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="d1253-144">Použití vlastní `XmlDictionaryWriter` umožňuje nám poslat bloky dat jako rozsáhlý soubor na původní zprávu o probíhá zápis.</span><span class="sxs-lookup"><span data-stu-id="d1253-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="d1253-145">To znamená, že jsme neukládaného ve vyrovnávací paměti celý původní zprávy.</span><span class="sxs-lookup"><span data-stu-id="d1253-145">This means we do not buffer the entire original message.</span></span>  
  
 <span data-ttu-id="d1253-146">![Rozdělování kanál](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")</span><span class="sxs-lookup"><span data-stu-id="d1253-146">![Chunking Channel](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")</span></span>  
  
 <span data-ttu-id="d1253-147">Na straně příjmu `ChunkingChannel` vrátí zprávy z tohoto vnitřní kanálu a předá je na vlastní `XmlDictionaryReader` názvem `ChunkingReader`, který reconstitutes na původní zprávu z příchozí datové dávky.</span><span class="sxs-lookup"><span data-stu-id="d1253-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom `XmlDictionaryReader` called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="d1253-148">`ChunkingChannel`To zahrnuje `ChunkingReader` ve vlastní `Message` implementace volá `ChunkingMessage` a vrátí tuto zprávu do vrstvy výše.</span><span class="sxs-lookup"><span data-stu-id="d1253-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="d1253-149">Tato kombinace `ChunkingReader` a `ChunkingMessage` umožňuje zrušte bloku dat původní text zprávy, jako je číst vrstvu nad místo nutnosti ukládat do vyrovnávací paměti celý původní text zprávy.</span><span class="sxs-lookup"><span data-stu-id="d1253-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="d1253-150">`ChunkingReader`má fronty, kde ukládány příchozí bloky až do maximální konfigurovat počet bloků dat z vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d1253-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="d1253-151">Když je dosaženo této maximální limit, čtečka čeká zpráv, které mají být nečekaně z fronty vrstvou výše (to znamená, načtením právě z původní text zprávy) nebo dokud nebude přijímat maximální je dosaženo časového limitu.</span><span class="sxs-lookup"><span data-stu-id="d1253-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>  
  
 <span data-ttu-id="d1253-152">![Rozdělování kanál](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")</span><span class="sxs-lookup"><span data-stu-id="d1253-152">![Chunking Channel](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")</span></span>  
  
## <a name="chunking-programming-model"></a><span data-ttu-id="d1253-153">Rozdělování modelu programování</span><span class="sxs-lookup"><span data-stu-id="d1253-153">Chunking Programming Model</span></span>  
 <span data-ttu-id="d1253-154">Vývojáři služeb můžete zadat zprávy, které mají být blokové použitím `ChunkingBehavior` atribut operace v rámci smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d1253-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="d1253-155">Atribut zpřístupní `AppliesTo` vlastnost, která umožňuje vývojáři k určení, zda rozdělování platí pro zprávu vstupní, výstupní zprávu nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="d1253-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="d1253-156">Následující příklad ukazuje použití `ChunkingBehavior` atribut:</span><span class="sxs-lookup"><span data-stu-id="d1253-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>  
  
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
  
 <span data-ttu-id="d1253-157">Z tohoto modelu programování `ChunkingBindingElement` sestaví seznam akce identifikátory URI, který identifikovat zpráv, které mají být blokové.</span><span class="sxs-lookup"><span data-stu-id="d1253-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="d1253-158">Akce každé odchozí zprávy se porovná s tohoto seznamu k určení, pokud zpráva by měla být blokové nebo odeslat přímo.</span><span class="sxs-lookup"><span data-stu-id="d1253-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>  
  
## <a name="implementing-the-send-operation"></a><span data-ttu-id="d1253-159">Implementace operaci odeslání</span><span class="sxs-lookup"><span data-stu-id="d1253-159">Implementing the Send Operation</span></span>  
 <span data-ttu-id="d1253-160">Na vysoké úrovni, po operaci odeslání nejprve ověří, zda odchozí zprávy musí být blokové a pokud ne, odešle zprávu přímo pomocí vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>  
  
 <span data-ttu-id="d1253-161">Pokud zpráva musí blokové, odeslání vytvoří novou `ChunkingWriter` a volání `WriteBodyContents` na odchozí zprávy předání to `ChunkingWriter`.</span><span class="sxs-lookup"><span data-stu-id="d1253-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="d1253-162">`ChunkingWriter` Nemá rozdělování zprávy (včetně kopírování původní záhlaví zprávy na zprávu počáteční blok) a odešle bloky dat pomocí vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>  
  
 <span data-ttu-id="d1253-163">Několik podrobnosti vhodné poznamenat:</span><span class="sxs-lookup"><span data-stu-id="d1253-163">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="d1253-164">Odeslat první volání `ThrowIfDisposedOrNotOpened` zajistit `CommunicationState` je otevřen.</span><span class="sxs-lookup"><span data-stu-id="d1253-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>  
  
-   <span data-ttu-id="d1253-165">Odesílání se synchronizují, aby pouze jeden zpráva byla odeslána současně pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="d1253-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="d1253-166">Je `ManualResetEvent` s názvem `sendingDone` , se resetuje při odesílání bloku zprávy.</span><span class="sxs-lookup"><span data-stu-id="d1253-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="d1253-167">Jakmile je koncový blok zpráva odeslána, tato událost je nastavena.</span><span class="sxs-lookup"><span data-stu-id="d1253-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="d1253-168">Metoda odesílání čeká na tuto událost, chcete-li nastavit před pokusem o odeslání odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="d1253-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>  
  
-   <span data-ttu-id="d1253-169">Odeslat zámky `CommunicationObject.ThisLock` aby synchronizovat změny stavu při odesílání.</span><span class="sxs-lookup"><span data-stu-id="d1253-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="d1253-170">Najdete v článku <xref:System.ServiceModel.Channels.CommunicationObject> dokumentace pro další informace o <xref:System.ServiceModel.Channels.CommunicationObject> stavy a stav počítače.</span><span class="sxs-lookup"><span data-stu-id="d1253-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>  
  
-   <span data-ttu-id="d1253-171">Časový limit předaný odesílání slouží jako časový limit pro operaci celý odeslání, který zahrnuje všechny bloky dat odesílání.</span><span class="sxs-lookup"><span data-stu-id="d1253-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>  
  
-   <span data-ttu-id="d1253-172">Vlastní `XmlDictionaryWriter` návrhu jste vybrali, aby se zabránilo ukládání do vyrovnávací paměti celý původní text zprávy.</span><span class="sxs-lookup"><span data-stu-id="d1253-172">The custom `XmlDictionaryWriter` design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="d1253-173">Pokud nám chcete-li získat `XmlDictionaryReader` na text pomocí `message.GetReaderAtBodyContents` celého obsahu by do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d1253-173">If we were to get an `XmlDictionaryReader` on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="d1253-174">Místo toho máme vlastní `XmlDictionaryWriter` předá do `message.WriteBodyContents`.</span><span class="sxs-lookup"><span data-stu-id="d1253-174">Instead, we have a custom `XmlDictionaryWriter` that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="d1253-175">Jako zprávu pomocí volání WriteBase64 zapisovače zapisovač bloky dat do zpráv zabalí a odešle je vnitřní kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="d1253-176">Bloky WriteBase64 dlouho, dokud se neodešle u bloku.</span><span class="sxs-lookup"><span data-stu-id="d1253-176">WriteBase64 blocks until the chunk is sent.</span></span>  
  
## <a name="implementing-the-receive-operation"></a><span data-ttu-id="d1253-177">Implementace přijímat operace</span><span class="sxs-lookup"><span data-stu-id="d1253-177">Implementing the Receive Operation</span></span>  
 <span data-ttu-id="d1253-178">Na vysoké úrovni, operace příjmu nejprve zkontroluje, že příchozí zpráva není `null` a že je jeho akce `ChunkingAction`.</span><span class="sxs-lookup"><span data-stu-id="d1253-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="d1253-179">Pokud obě kritéria nesplňuje, bude vráceno beze změny z Receive.</span><span class="sxs-lookup"><span data-stu-id="d1253-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="d1253-180">Jinak, vytvoří novou Receive `ChunkingReader` a novou `ChunkingMessage` zabalené kolem něj (voláním `GetNewChunkingMessage`).</span><span class="sxs-lookup"><span data-stu-id="d1253-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="d1253-181">Před vrácením že noví `ChunkingMessage`, Receive používá podproces fondu podprocesů provést `ReceiveChunkLoop`, který volá `innerChannel.Receive` v smyčku a rukou vypnout bloky dat pro `ChunkingReader` dokud doručení zprávy koncového bloku nebo je dosaženo časového limitu příjmu.</span><span class="sxs-lookup"><span data-stu-id="d1253-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>  
  
 <span data-ttu-id="d1253-182">Několik podrobnosti vhodné poznamenat:</span><span class="sxs-lookup"><span data-stu-id="d1253-182">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="d1253-183">Jako odesílání, příjem první volání `ThrowIfDisposedOrNotOepned` zajistit `CommunicationState` je otevřen.</span><span class="sxs-lookup"><span data-stu-id="d1253-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>  
  
-   <span data-ttu-id="d1253-184">Zobrazí se synchronizují taky, že pouze jednu zprávu lze přijímat současně z relace.</span><span class="sxs-lookup"><span data-stu-id="d1253-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="d1253-185">To je obzvláště důležité, protože po přijetí zprávy počáteční blok je všechny následné přijaté zprávy se měl bloků dat v rámci tohoto nového pořadí bloku dokud neobdrží zprávu koncového bloku.</span><span class="sxs-lookup"><span data-stu-id="d1253-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="d1253-186">Přijímat zprávy z tohoto kanálu vnitřní nemůže vyžádat, dokud všechny bloky dat, které patří do zprávy aktuálně probíhá zrušte blokové jsou přijaty.</span><span class="sxs-lookup"><span data-stu-id="d1253-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="d1253-187">K tomu, přijímat používá `ManualResetEvent` s názvem `currentMessageCompleted`, který je nastaven při zprávu bloku end přijme a resetovat při přijetí nové zprávy počáteční blok.</span><span class="sxs-lookup"><span data-stu-id="d1253-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>  
  
-   <span data-ttu-id="d1253-188">Na rozdíl od odeslání Receive nezabrání přechodů mezi stavy synchronizované při přijetí.</span><span class="sxs-lookup"><span data-stu-id="d1253-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="d1253-189">Například Zavřít lze volat při přijetí a čeká, až do dokončení čekající receive původní zprávy nebo zadaný časový limit.</span><span class="sxs-lookup"><span data-stu-id="d1253-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>  
  
-   <span data-ttu-id="d1253-190">Časový limit předaný příjmu se používá jako časového limitu pro celý zobrazí operaci, která zahrnuje všechny bloky dat přijetí.</span><span class="sxs-lookup"><span data-stu-id="d1253-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>  
  
-   <span data-ttu-id="d1253-191">Pokud vrstva, která načítá zprávy spotřebovává tělo zprávy s rychlostí nižší než počet příchozích zpráv bloku, `ChunkingReader` uloží tyto příchozí bloky až do limitu určeného `ChunkingBindingElement.MaxBufferedChunks`.</span><span class="sxs-lookup"><span data-stu-id="d1253-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="d1253-192">Po dosažení tohoto limitu jsou žádné další bloky vyžádány z nižší vrstvy, dokud se využívá ve vyrovnávací paměti datových dávek nebo je dosaženo časového limitu příjmu.</span><span class="sxs-lookup"><span data-stu-id="d1253-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>  
  
## <a name="communicationobject-overrides"></a><span data-ttu-id="d1253-193">Přepsání objektu CommunicationObject</span><span class="sxs-lookup"><span data-stu-id="d1253-193">CommunicationObject Overrides</span></span>  
  
### <a name="onopen"></a><span data-ttu-id="d1253-194">Při otevření</span><span class="sxs-lookup"><span data-stu-id="d1253-194">OnOpen</span></span>  
 <span data-ttu-id="d1253-195">`OnOpen`volání `innerChannel.Open` otevřít vnitřní kanál.</span><span class="sxs-lookup"><span data-stu-id="d1253-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>  
  
### <a name="onclose"></a><span data-ttu-id="d1253-196">Při zavření</span><span class="sxs-lookup"><span data-stu-id="d1253-196">OnClose</span></span>  
 <span data-ttu-id="d1253-197">`OnClose`nejprve nastaví `stopReceive` k `true` signál na čekající `ReceiveChunkLoop` zastavit.</span><span class="sxs-lookup"><span data-stu-id="d1253-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="d1253-198">Potom čeká `receiveStopped``ManualResetEvent`, který je nastaven při `ReceiveChunkLoop` zastaví.</span><span class="sxs-lookup"><span data-stu-id="d1253-198">It then waits for the `receiveStopped``ManualResetEvent`, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="d1253-199">Za předpokladu, že `ReceiveChunkLoop` zastaví v rámci zadaného časového limitu, `OnClose` volání `innerChannel.Close` s zbývající časový limit.</span><span class="sxs-lookup"><span data-stu-id="d1253-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>  
  
### <a name="onabort"></a><span data-ttu-id="d1253-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="d1253-200">OnAbort</span></span>  
 <span data-ttu-id="d1253-201">`OnAbort`volání `innerChannel.Abort` k přerušení vnitřní kanál.</span><span class="sxs-lookup"><span data-stu-id="d1253-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="d1253-202">Pokud dojde čekající `ReceiveChunkLoop` získá výjimku z na čekající `innerChannel.Receive` volání.</span><span class="sxs-lookup"><span data-stu-id="d1253-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>  
  
### <a name="onfaulted"></a><span data-ttu-id="d1253-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="d1253-203">OnFaulted</span></span>  
 <span data-ttu-id="d1253-204">`ChunkingChannel` Nevyžaduje speciální chování, pokud je kanál s chybou, tak `OnFaulted` není přepsána.</span><span class="sxs-lookup"><span data-stu-id="d1253-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>  
  
## <a name="implementing-channel-factory"></a><span data-ttu-id="d1253-205">Implementace kanálu</span><span class="sxs-lookup"><span data-stu-id="d1253-205">Implementing Channel Factory</span></span>  
 <span data-ttu-id="d1253-206">`ChunkingChannelFactory` Zodpovídá za vytvoření instancí `ChunkingDuplexSessionChannel` a pro kaskádové přechodů mezi stavy pro vnitřní kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>  
  
 <span data-ttu-id="d1253-207">`OnCreateChannel`vnitřní kanálu používá k vytvoření `IDuplexSessionChannel` vnitřní kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="d1253-208">Ta poté vytvoří nový `ChunkingDuplexSessionChannel` předání tohoto vnitřní kanálu spolu s seznam zpráv akce, které mají být blokové a maximální počet bloků dat do vyrovnávací paměti při příjmu.</span><span class="sxs-lookup"><span data-stu-id="d1253-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="d1253-209">Seznam zpráv akce, které mají být blokové a maximální počet bloků dat do vyrovnávací paměti jsou dva parametry předaný `ChunkingChannelFactory` v jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d1253-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="d1253-210">V části na `ChunkingBindingElement` popisuje, kde se tyto hodnoty pocházejí z.</span><span class="sxs-lookup"><span data-stu-id="d1253-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>  
  
 <span data-ttu-id="d1253-211">`OnOpen`, `OnClose`, `OnAbort` a jejich ekvivalenty u asynchronního volání metody odpovídající přechod stavu na vnitřní kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>  
  
## <a name="implementing-channel-listener"></a><span data-ttu-id="d1253-212">Implementace naslouchací proces kanálu</span><span class="sxs-lookup"><span data-stu-id="d1253-212">Implementing Channel Listener</span></span>  
 <span data-ttu-id="d1253-213">`ChunkingChannelListener` Představuje obálku kolem naslouchací proces vnitřní kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="d1253-214">Jeho hlavní funkce, kromě delegáta volání této naslouchací proces vnitřní kanálu je zabalit nové `ChunkingDuplexSessionChannels` kolem kanály přijímán z naslouchací proces vnitřní kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="d1253-215">To se provádí v `OnAcceptChannel` a `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="d1253-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="d1253-216">Nově vytvořený `ChunkingDuplexSessionChannel` je předána vnitřní kanálu spolu s ostatní parametry popsaných výše.</span><span class="sxs-lookup"><span data-stu-id="d1253-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>  
  
## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="d1253-217">Implementaci prvku vazby a vazby</span><span class="sxs-lookup"><span data-stu-id="d1253-217">Implementing Binding Element and Binding</span></span>  
 <span data-ttu-id="d1253-218">`ChunkingBindingElement`zodpovídá za vytvoření `ChunkingChannelFactory` a `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="d1253-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="d1253-219">`ChunkingBindingElement` Kontroluje, zda T v `CanBuildChannelFactory` \<T > a `CanBuildChannelListener` \<T > je typu `IDuplexSessionChannel` (pouze kanál nepodporuje bloku dat kanál) a další prvky vazby vazba podporují tuto Typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>  
  
 <span data-ttu-id="d1253-220">`BuildChannelFactory`\<T > nejdřív zkontroluje, zda požadovaný kanál typu se dají vytvářet a pak získá seznam zpráv akce, které mají být blokové.</span><span class="sxs-lookup"><span data-stu-id="d1253-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="d1253-221">Další informace najdete v následující části.</span><span class="sxs-lookup"><span data-stu-id="d1253-221">For more information, see the following section.</span></span> <span data-ttu-id="d1253-222">Ta poté vytvoří nový `ChunkingChannelFactory` předání vnitřní kanálu (vrácený z `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), seznam zpráv akce a maximální počet bloků dat do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d1253-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="d1253-223">Maximální počet bloků pochází z vlastnost s názvem `MaxBufferedChunks` vystavené `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="d1253-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>  
  
 <span data-ttu-id="d1253-224">`BuildChannelListener<T>`má podobné implementace pro vytvoření `ChunkingChannelListener` a předání naslouchací proces vnitřní kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1253-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>  
  
 <span data-ttu-id="d1253-225">Je třeba vazbu zahrnuté v této ukázce s názvem `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="d1253-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="d1253-226">Tato vazba se skládá ze dvou prvků vazby: `TcpTransportBindingElement` a `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="d1253-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="d1253-227">Kromě vystavení `MaxBufferedChunks` vlastnost vazby také nastaví některá `TcpTransportBindingElement` vlastnosti, jako `MaxReceivedMessageSize` (ji nastaví na `ChunkingUtils.ChunkSize` + 100 KB bajtů pro hlavičky).</span><span class="sxs-lookup"><span data-stu-id="d1253-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>  
  
 <span data-ttu-id="d1253-228">`TcpChunkingBinding`také implementuje `IBindingRuntimePreferences` a vrací hodnotu true z `ReceiveSynchronously` metoda, která určuje, že jsou implementované synchronní volání Receive.</span><span class="sxs-lookup"><span data-stu-id="d1253-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>  
  
### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="d1253-229">Určení, které zpráv do bloku</span><span class="sxs-lookup"><span data-stu-id="d1253-229">Determining Which Messages To Chunk</span></span>  
 <span data-ttu-id="d1253-230">Bloku dat kanál chunks pouze zprávy, které jsou identifikovány prostřednictvím `ChunkingBehavior` atribut.</span><span class="sxs-lookup"><span data-stu-id="d1253-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="d1253-231">`ChunkingBehavior` Třída implementuje `IOperationBehavior` a je implementováno modulem volání `AddBindingParameter` metoda.</span><span class="sxs-lookup"><span data-stu-id="d1253-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="d1253-232">Tato metoda `ChunkingBehavior` ověří hodnotu jeho `AppliesTo` vlastnost (`InMessage`, `OutMessage` nebo obojí) k určení zprávy, které by měl být blokové.</span><span class="sxs-lookup"><span data-stu-id="d1253-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="d1253-233">Potom získá akce jednotlivé zprávy (z kolekce zprávy na `OperationDescription`) a přidá do kolekce řetězec obsažené v instanci `ChunkingBindingParameter`.</span><span class="sxs-lookup"><span data-stu-id="d1253-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="d1253-234">Potom přidá to `ChunkingBindingParameter` zadanému `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="d1253-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>  
  
 <span data-ttu-id="d1253-235">To `BindingParameterCollection` je předán uvnitř `BindingContext` na každý element vazby vazba, pokud daný element vazby sestavení kanálu nebo naslouchací proces kanálu nástroje.</span><span class="sxs-lookup"><span data-stu-id="d1253-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="d1253-236">`ChunkingBindingElement`Na implementaci `BuildChannelFactory<T>` a `BuildChannelListener<T>` to pro vyžádání obsahu `ChunkingBindingParameter` mimo `BindingContext’`s `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="d1253-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="d1253-237">Kolekci akcí, které jsou obsažené v `ChunkingBindingParameter` se pak předá do `ChunkingChannelFactory` nebo `ChunkingChannelListener`, který naopak předává jej do `ChunkingDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="d1253-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="d1253-238">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d1253-238">Running the Sample</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d1253-239">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="d1253-239">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d1253-240">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="d1253-240">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="d1253-241">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1253-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="d1253-242">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1253-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="d1253-243">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d1253-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="d1253-244">Nejprve spustit Service.exe, spusťte Client.exe a podívejte se na obě okna konzoly pro výstup.</span><span class="sxs-lookup"><span data-stu-id="d1253-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>  
  
 <span data-ttu-id="d1253-245">Při spuštění ukázky, očekává se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="d1253-245">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="d1253-246">Klient:</span><span class="sxs-lookup"><span data-stu-id="d1253-246">Client:</span></span>  
  
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
  
 <span data-ttu-id="d1253-247">Server:</span><span class="sxs-lookup"><span data-stu-id="d1253-247">Server:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1253-248">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1253-248">See Also</span></span>
