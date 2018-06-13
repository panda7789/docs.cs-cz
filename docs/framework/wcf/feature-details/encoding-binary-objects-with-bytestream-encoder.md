---
title: Kódování binárních objektů pomocí kodéru ByteStream
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 9619fdf6979833c30159e1ea02b3f8d6b98a6629
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489479"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="c1b67-102">Kódování binárních objektů pomocí kodéru ByteStream</span><span class="sxs-lookup"><span data-stu-id="c1b67-102">Encoding Binary Objects with ByteStream Encoder</span></span>
<span data-ttu-id="c1b67-103">Odesílání a příjmu Nezpracovaná binární data s Windows Communication Foundation (WCF) je konfigurován pomocí <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="c1b67-103">Sending and receiving raw binary data with Windows Communication Foundation (WCF) is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="c1b67-104">Architektura kodér zpráv datového proudu bajtů</span><span class="sxs-lookup"><span data-stu-id="c1b67-104">Byte Stream Message Encoder Architecture</span></span>  
 <span data-ttu-id="c1b67-105">Kodér zprávy v binární používá technologie WCF nemá žádné zařízení pro zpracování, ověřování nebo identifikace základní binární data ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="c1b67-105">The binary message encoder used by WCF has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="c1b67-106">Datový balíček je kódovaný do souboru XML, odeslané, obdržel a dekódovat.</span><span class="sxs-lookup"><span data-stu-id="c1b67-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="c1b67-107">Kodér zpracovává data po předávány k přenosu a předtím, než odešle zprávu do fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="c1b67-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="c1b67-108">Funkčně, binární kodér zabalí zprávu data v `<binary>` prvky pro odesílání a odebere elementy po doručení zprávy.</span><span class="sxs-lookup"><span data-stu-id="c1b67-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="c1b67-109">Pomocí kodéru zpráv datového proudu bajtů</span><span class="sxs-lookup"><span data-stu-id="c1b67-109">Using the Byte Stream Message Encoder</span></span>  
 <span data-ttu-id="c1b67-110">Následující příklad ukazuje kontraktu služby, který implementuje kodér bajtů datového proudu zpráv.</span><span class="sxs-lookup"><span data-stu-id="c1b67-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="c1b67-111">Následující příklad ukazuje službu volaná.</span><span class="sxs-lookup"><span data-stu-id="c1b67-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="c1b67-112">V případě používání služby, který implementuje zpráva infrastruktury (třeba směrovač), je zpráva zpracována bez kontroly, ověřování nebo jinak interakci se zprávou, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c1b67-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="c1b67-113">Scénáře</span><span class="sxs-lookup"><span data-stu-id="c1b67-113">Scenarios</span></span>  
 <span data-ttu-id="c1b67-114">Kodér datového proudu bajtů je užitečné v následujících scénářích.</span><span class="sxs-lookup"><span data-stu-id="c1b67-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
-   <span data-ttu-id="c1b67-115">Ve formátu JPEG přenosu mezi počítači pomocí WCF.</span><span class="sxs-lookup"><span data-stu-id="c1b67-115">Transferring a JPEG image between computers using WCF.</span></span> <span data-ttu-id="c1b67-116">V tomto scénáři image budou doručeny prostřednictvím přenosu z vnějšího zdroje a data odeslána bude nezpracovaná bajtů, které tvoří bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="c1b67-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="c1b67-117">Služba bude přijímat binární data a umožňuje zobrazit obrázek.</span><span class="sxs-lookup"><span data-stu-id="c1b67-117">A service will receive the binary data and display the image.</span></span>  
  
-   <span data-ttu-id="c1b67-118">Čtení informací z fronty zpráv a její zpracování.</span><span class="sxs-lookup"><span data-stu-id="c1b67-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="c1b67-119">Zpráva bude číst ze Správce fronty zpráv a předána do kanálu zprávu fronty ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="c1b67-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="c1b67-120">Kanál zprávy fronty bude fungovat jako správce front v zásobníku kanálu WCF.</span><span class="sxs-lookup"><span data-stu-id="c1b67-120">The message queue channel will act as a queue manager in the WCF channel stack.</span></span>  
  
 <span data-ttu-id="c1b67-121">V případě odesílání zprávy přes kanál fronty zpráv, odesílatel nemá žádnou kontrolu nad bajtů přijatých ze správce front.</span><span class="sxs-lookup"><span data-stu-id="c1b67-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="c1b67-122">Pokud proces přijímající bez možnosti čtení nezpracované bajtů, bude přijímat zprávy, jako chybně formátována a nebude zpracován; předpokládá se, že proces přijímající budou mít funkce překladu přijatých bajtů zpět do použitelného formátu.</span><span class="sxs-lookup"><span data-stu-id="c1b67-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
