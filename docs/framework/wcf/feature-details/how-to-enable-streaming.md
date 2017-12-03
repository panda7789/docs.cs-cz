---
title: "Postupy: Povolení streamování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea506499cf6678beb51195654739f2537b98a188
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-streaming"></a><span data-ttu-id="cc0ca-102">Postupy: Povolení streamování</span><span class="sxs-lookup"><span data-stu-id="cc0ca-102">How to: Enable Streaming</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="cc0ca-103">můžete odesílat zprávy pomocí ve vyrovnávací paměti nebo přenášené datovými proudy přenosů.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-103"> can send messages using either buffered or streamed transfers.</span></span> <span data-ttu-id="cc0ca-104">Ve výchozím režimu přenosu do vyrovnávací paměti zprávy musí být zcela doručována předtím, než příjemce může číst.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-104">In the default buffered-transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="cc0ca-105">Při streamování režim přenosu, můžete začít příjemce zprávu zpracovat, než je zcela doručit.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-105">In streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="cc0ca-106">Streamování režimu je užitečné, když informace, které se předá je náročná a může být zpracována sériově.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-106">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="cc0ca-107">Streamování režimu je také užitečné, pokud zpráva je moc velká, aby se zcela do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-107">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
 <span data-ttu-id="cc0ca-108">Chcete-li povolit, streamování, definovat `OperationContract` správně a umožňoval vysílání datového proudu na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-108">To enable streaming, define the `OperationContract` appropriately and enable streaming at the transport level.</span></span>  
  
### <a name="to-stream-data"></a><span data-ttu-id="cc0ca-109">K datům datového proudu</span><span class="sxs-lookup"><span data-stu-id="cc0ca-109">To stream data</span></span>  
  
1.  <span data-ttu-id="cc0ca-110">K datům datového proudu `OperationContract` pro službu musí být splněny dva požadavky:</span><span class="sxs-lookup"><span data-stu-id="cc0ca-110">To stream data, the `OperationContract` for the service must satisfy two requirements:</span></span>  
  
    1.  <span data-ttu-id="cc0ca-111">Parametr, který obsahuje data, která mají být prostřednictvím datového proudu musí být parametr pouze v metodě.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-111">The parameter that holds the data to be streamed must be the only parameter in the method.</span></span> <span data-ttu-id="cc0ca-112">Například pokud je vstupní zpráva má Streamovat, operaci musí mít přesně jeden vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-112">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="cc0ca-113">Podobně pokud zpráva výstup je odesílání, operaci musí mít právě jednu výstupní parametr nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-113">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span>  
  
    2.  <span data-ttu-id="cc0ca-114">Alespoň jeden z typů parametr a návratové hodnoty musí být buď <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, nebo <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-114">At least one of the types of the parameter and return value must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, or <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
     <span data-ttu-id="cc0ca-115">Následuje příklad kontraktu pro datové proudy.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-115">The following is an example of a contract for streamed data.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     <span data-ttu-id="cc0ca-116">`GetStream` Operace přijímá některé z vyrovnávací paměti vstupní data jako `string`, která je uložená do vyrovnávací paměti a vrátí `Stream`, který datového proudu.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-116">The `GetStream` operation receives some buffered input data as a `string`, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="cc0ca-117">Na druhé straně `UploadStream` přebírá `Stream` (streamování) a vrátí `bool` (uložená do vyrovnávací paměti).</span><span class="sxs-lookup"><span data-stu-id="cc0ca-117">Conversely `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="cc0ca-118">`EchoStream`provede a vrátí `Stream` je příkladem operace, jejichž vstup a výstup zprávy jsou obě streamování.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-118">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="cc0ca-119">Nakonec `GetReversedStream` přebere žádné vstupy a vrátí `Stream` (streamování).</span><span class="sxs-lookup"><span data-stu-id="cc0ca-119">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
2.  <span data-ttu-id="cc0ca-120">Streamování musí být povolené na vazby.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-120">Streaming must be enabled on the binding.</span></span> <span data-ttu-id="cc0ca-121">Můžete nastavit `TransferMode` vlastnosti, které můžete provést jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="cc0ca-121">You set a `TransferMode` property, which can take one of the following values:</span></span>  
  
    1.  <span data-ttu-id="cc0ca-122">`Buffered`,</span><span class="sxs-lookup"><span data-stu-id="cc0ca-122">`Buffered`,</span></span>  
  
    2.  <span data-ttu-id="cc0ca-123">`Streamed`, která umožňuje streamování komunikace v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-123">`Streamed`, which enables streaming communication in both directions.</span></span>  
  
    3.  <span data-ttu-id="cc0ca-124">`StreamedRequest`, která umožňuje streamování jenom žádosti.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-124">`StreamedRequest`, which enables streaming the request only.</span></span>  
  
    4.  <span data-ttu-id="cc0ca-125">`StreamedResponse`, která umožňuje streamování pouze odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-125">`StreamedResponse`, which enables streaming the response only.</span></span>  
  
     <span data-ttu-id="cc0ca-126">`BasicHttpBinding` Zpřístupní `TransferMode` vlastnost vazby, jak to dělá `NetTcpBinding` a `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-126">The `BasicHttpBinding` exposes the `TransferMode` property on the binding, as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="cc0ca-127">`TransferMode` Vlastnosti také můžete nastavit v prvku vazby přenosu a použít v vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-127">The `TransferMode` property can also be set on the transport binding element and used in a custom binding.</span></span>  
  
     <span data-ttu-id="cc0ca-128">Následující ukázky ukazují, jak nastavit `TransferMode` kódem a změnou konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-128">The following samples show how to set `TransferMode` by code and by changing the configuration file.</span></span> <span data-ttu-id="cc0ca-129">Ukázky také obě nastaveny `maxReceivedMessageSize` vlastnost 64 MB, který nahradí zakončení na maximální povolenou velikost zprávy na přijímat.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-129">The samples also both set the `maxReceivedMessageSize` property to 64 MB, which places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="cc0ca-130">Výchozí hodnota `maxReceivedMessageSize` je 64 KB, který je obvykle příliš nízká pro streamování scénáře.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-130">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span> <span data-ttu-id="cc0ca-131">Tato kvóta nastavení podle potřeby v závislosti na maximální velikost zprávy, které vaše aplikace očekává.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-131">Set this quota setting as appropriate depending on the maximum size of messages your application expects to receive.</span></span> <span data-ttu-id="cc0ca-132">Všimněte si také, že `maxBufferSize` určuje maximální velikost, která je uložená do vyrovnávací paměti a nastavte ji odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-132">Also note that `maxBufferSize` controls the maximum size that is buffered, and set it appropriately.</span></span>  
  
    1.  <span data-ttu-id="cc0ca-133">Následující fragment konfigurace z ukázky ukazuje nastavení `TransferMode` vlastnost streamování na `basicHttpBinding` a vlastní vazby HTTP.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-133">The following configuration snippet from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  <span data-ttu-id="cc0ca-134">Následující fragment kódu ukazuje nastavení `TransferMode` vlastnost streamování na `basicHttpBinding` a vlastní vazby HTTP.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-134">The following code snippet shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  <span data-ttu-id="cc0ca-135">Následující fragment kódu ukazuje nastavení `TransferMode` vlastnost streamování na vlastní vazby protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-135">The following code snippet shows setting the `TransferMode` property to streaming on a custom TCP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3.  <span data-ttu-id="cc0ca-136">Operace `GetStream`, `UploadStream`, a `EchoStream` všechny řešení odesílání dat přímo ze souboru nebo ukládání dat přijatých přímo do souboru.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-136">The operations `GetStream`, `UploadStream`, and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="cc0ca-137">Následující kód je pro `GetStream`.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-137">The following code is for `GetStream`.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a><span data-ttu-id="cc0ca-138">Psaní vlastních datového proudu</span><span class="sxs-lookup"><span data-stu-id="cc0ca-138">Writing a custom stream</span></span>  
  
1.  <span data-ttu-id="cc0ca-139">Pro zvláštní zpracování na každého bloku datový proud jako odesílání nemusí být přijata, odvození třídy vlastního datového proudu z <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-139">To do special processing on each chunk of a data stream as it is being sent or received, derive a custom stream class from <xref:System.IO.Stream>.</span></span> <span data-ttu-id="cc0ca-140">Jako příklad vlastního datového proudu, obsahuje následující kód `GetReversedStream` metoda a `ReverseStream` třída-.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-140">As an example of a custom stream, the following code contains a `GetReversedStream` method and a `ReverseStream` class-.</span></span>  
  
     <span data-ttu-id="cc0ca-141">`GetReversedStream`vytvoří a vrátí novou instanci třídy `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-141">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="cc0ca-142">Vlastní zpracování se stane, protože systém přečte z `ReverseStream` objektu.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-142">The actual processing happens as the system reads from the `ReverseStream` object.</span></span> <span data-ttu-id="cc0ca-143">`ReverseStream.Read` Metoda čte blok bajtů z podkladový soubor, obrátí je a pak vrátí odstínech bajtů.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-143">The `ReverseStream.Read` method reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="cc0ca-144">Tato metoda reverse není celý soubor obsahu; současně se obrátí jeden blok bajtů.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-144">This method does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="cc0ca-145">Tento příklad ukazuje, jak můžete provádět zpracování datového proudu, jak se obsah pro čtení nebo zapsat z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="cc0ca-145">This example shows how you can perform stream processing as the content is being read to or written from the stream.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cc0ca-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc0ca-146">See Also</span></span>  
 [<span data-ttu-id="cc0ca-147">Velkého množství dat a vysílání datového proudu</span><span class="sxs-lookup"><span data-stu-id="cc0ca-147">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 [<span data-ttu-id="cc0ca-148">Datový proud</span><span class="sxs-lookup"><span data-stu-id="cc0ca-148">Stream</span></span>](../../../../docs/framework/wcf/samples/stream.md)
