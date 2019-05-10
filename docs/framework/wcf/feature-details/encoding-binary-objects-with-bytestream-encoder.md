---
title: Kódování binárních objektů pomocí kodéru ByteStream
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 09a919e11971f81bc76dca0e45a7eb0e70ef749e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626929"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="74739-102">Kódování binárních objektů pomocí kodéru ByteStream</span><span class="sxs-lookup"><span data-stu-id="74739-102">Encoding Binary Objects with ByteStream Encoder</span></span>
<span data-ttu-id="74739-103">Odesílání a příjem Nezpracovaná binární data Windows Communication Foundation (WCF) je nakonfigurovaný nástrojem <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="74739-103">Sending and receiving raw binary data with Windows Communication Foundation (WCF) is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="74739-104">Architektura kodér zprávy Stream bajtů</span><span class="sxs-lookup"><span data-stu-id="74739-104">Byte Stream Message Encoder Architecture</span></span>  
 <span data-ttu-id="74739-105">Kodér binárních zpráv používá WCF nemá žádné zařízení pro zpracování, ověřování nebo identifikace základní binární data ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="74739-105">The binary message encoder used by WCF has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="74739-106">Balíček dat překóduje se na XML, odeslání, přijetí a dekódovat.</span><span class="sxs-lookup"><span data-stu-id="74739-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="74739-107">Kodér zpracuje data po předávaný přenosu a před odesláním zprávy do fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="74739-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="74739-108">Funkčně binárního kodéru zabalí data zprávy v `<binary>` prvky pro odesílání a odebere prvky po doručení zprávy.</span><span class="sxs-lookup"><span data-stu-id="74739-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="74739-109">Pomocí kodéru zpráv Stream bajtů</span><span class="sxs-lookup"><span data-stu-id="74739-109">Using the Byte Stream Message Encoder</span></span>  
 <span data-ttu-id="74739-110">Následující příklad ukazuje kontraktu služby, který implementuje kodéru zpráv datového proudu bajtů.</span><span class="sxs-lookup"><span data-stu-id="74739-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="74739-111">Následující příklad ukazuje vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="74739-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="74739-112">V případě použití služby, který implementuje infrastrukturu zprávy (jako jsou směrovače), je zpracovat zprávu bez kontroly, ověřování nebo jinak interakci s touto zprávou, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="74739-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="74739-113">Scénáře</span><span class="sxs-lookup"><span data-stu-id="74739-113">Scenarios</span></span>  
 <span data-ttu-id="74739-114">Kodér Stream bajt je užitečná v následujících scénářích.</span><span class="sxs-lookup"><span data-stu-id="74739-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
- <span data-ttu-id="74739-115">Obrázek JPEG přenosu mezi počítače pomocí technologie WCF.</span><span class="sxs-lookup"><span data-stu-id="74739-115">Transferring a JPEG image between computers using WCF.</span></span> <span data-ttu-id="74739-116">V tomto scénáři image dorazí prostřednictvím přenos z externího zdroje a data odesílají bude nezpracovaná bajtů, které tvoří bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="74739-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="74739-117">Služba bude přijímat binární data a zobrazit obrázek.</span><span class="sxs-lookup"><span data-stu-id="74739-117">A service will receive the binary data and display the image.</span></span>  
  
- <span data-ttu-id="74739-118">Čtení informací z fronty zpráv a její zpracování.</span><span class="sxs-lookup"><span data-stu-id="74739-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="74739-119">Zpráva bude číst z správce fronty zpráv a předané do kanálu zpráv fronty ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="74739-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="74739-120">Kanál zpráva fronty bude fungovat jako správce fronty v zásobníku kanál WCF.</span><span class="sxs-lookup"><span data-stu-id="74739-120">The message queue channel will act as a queue manager in the WCF channel stack.</span></span>  
  
 <span data-ttu-id="74739-121">V případě odesílání zprávy přes kanál fronty zpráv, odesílatel nemá žádnou kontrolu nad bajtů přijatých ze Správce fronty.</span><span class="sxs-lookup"><span data-stu-id="74739-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="74739-122">Pokud přijímající procesu nemá žádné funkce pro čtení nezpracovaných bajtů, zprávy budou přijata chybně formátovány a nebudou zpracovány; předpokládá se, že přijímající proces bude mít funkce z překladu přijatých bajtů zpět do použitelného formátu.</span><span class="sxs-lookup"><span data-stu-id="74739-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
