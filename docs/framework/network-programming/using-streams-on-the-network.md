---
title: Použití streamů v síti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
ms.openlocfilehash: 7d5a2e3eec9b49731a09f6eb41a8d8500a59b45c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180626"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="8df3d-102">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="8df3d-102">Using Streams on the Network</span></span>
<span data-ttu-id="8df3d-103">Síťové prostředky jsou reprezentovány v rozhraní .NET Framework jako datové proudy.</span><span class="sxs-lookup"><span data-stu-id="8df3d-103">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="8df3d-104">Při obecném zacházení s datovými proudy nabízí rozhraní .NET Framework následující funkce:</span><span class="sxs-lookup"><span data-stu-id="8df3d-104">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="8df3d-105">Běžný způsob odesílání a přijímání webových dat.</span><span class="sxs-lookup"><span data-stu-id="8df3d-105">A common way to send and receive Web data.</span></span> <span data-ttu-id="8df3d-106">Bez ohledu na skutečný obsah souboru – HTML, XML <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> nebo <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> cokoli jiného – aplikace bude používat a odesílat a přijímat data.</span><span class="sxs-lookup"><span data-stu-id="8df3d-106">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="8df3d-107">Kompatibilita s datovými proudy v rámci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8df3d-107">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="8df3d-108">Datové proudy se používají v rámci rozhraní .NET Framework, který má bohatou infrastrukturu pro jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="8df3d-108">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="8df3d-109">Můžete například upravit aplikaci, která čte <xref:System.IO.FileStream> data XML <xref:System.Net.Sockets.NetworkStream> z a číst data z místo toho změnou pouze několik řádků kódu, které inicializují datový proud.</span><span class="sxs-lookup"><span data-stu-id="8df3d-109">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="8df3d-110">Hlavní rozdíly mezi **NetworkStream** třídy a jiné datové proudy jsou, že **NetworkStream** není <xref:System.Net.Sockets.NetworkStream.Seek%2A> <xref:System.Net.Sockets.NetworkStream.Position%2A> vyhledatelný, <xref:System.NotSupportedException> <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> vlastnost vždy vrátí **false**a a metody a vyvolat .</span><span class="sxs-lookup"><span data-stu-id="8df3d-110">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="8df3d-111">Zpracování dat při jejich příchodu.</span><span class="sxs-lookup"><span data-stu-id="8df3d-111">Processing of data as it arrives.</span></span> <span data-ttu-id="8df3d-112">Datové proudy poskytují přístup k datům při jejich příchodu ze sítě, místo aby nutily vaši aplikaci čekat na stažení celé sady dat.</span><span class="sxs-lookup"><span data-stu-id="8df3d-112">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="8df3d-113">Obor <xref:System.Net.Sockets> názvů obsahuje třídu **NetworkStream,** která implementuje třídu <xref:System.IO.Stream> speciálně pro použití se síťovými prostředky.</span><span class="sxs-lookup"><span data-stu-id="8df3d-113">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="8df3d-114">Třídy <xref:System.Net.Sockets> v oboru názvů používají třídu **NetworkStream** k reprezentaci datových proudů.</span><span class="sxs-lookup"><span data-stu-id="8df3d-114">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="8df3d-115">Chcete-li odesílat data do sítě <xref:System.Net.WebRequest.GetRequestStream%2A> pomocí <xref:System.Net.WebRequest>vráceného datového proudu, zavolejte na svůj .</span><span class="sxs-lookup"><span data-stu-id="8df3d-115">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="8df3d-116">**WebRequest** odešle hlavičky požadavku na server. potom můžete odesílat data do síťového <xref:System.IO.Stream.EndWrite%2A>prostředku <xref:System.IO.Stream.Write%2A> voláním <xref:System.IO.Stream.BeginWrite%2A>, nebo metody na vrácený datový proud.</span><span class="sxs-lookup"><span data-stu-id="8df3d-116">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="8df3d-117">Některé protokoly, například HTTP, mohou vyžadovat nastavení vlastností specifických pro protokol před odesláním dat.</span><span class="sxs-lookup"><span data-stu-id="8df3d-117">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="8df3d-118">Následující příklad kódu ukazuje, jak nastavit vlastnosti specifické pro protokol HTTP pro odesílání dat.</span><span class="sxs-lookup"><span data-stu-id="8df3d-118">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="8df3d-119">Předpokládá, že proměnná `sendData` obsahuje data k odeslání `sendLength` a že proměnná je počet bajtů dat k odeslání.</span><span class="sxs-lookup"><span data-stu-id="8df3d-119">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
```csharp  
HttpWebRequest request =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 <span data-ttu-id="8df3d-120">Chcete-li přijímat data <xref:System.Net.WebResponse.GetResponseStream%2A> ze <xref:System.Net.WebResponse>sítě, obraťte se na aplikaci .</span><span class="sxs-lookup"><span data-stu-id="8df3d-120">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="8df3d-121">Potom můžete číst data ze síťového <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A>prostředku <xref:System.IO.Stream.Read%2A> voláním , nebo metoda na vrácený datový proud.</span><span class="sxs-lookup"><span data-stu-id="8df3d-121">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="8df3d-122">Při použití datových proudů ze síťových prostředků mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="8df3d-122">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="8df3d-123">**Vlastnost CanSeek** vždy vrátí **false,** protože **NetworkStream** třídy nelze změnit pozici v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="8df3d-123">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="8df3d-124">**Seek** a **Position** metody vyvolat **NotSupportedException**.</span><span class="sxs-lookup"><span data-stu-id="8df3d-124">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="8df3d-125">Při použití **WebRequest** a **WebResponse**, stream instance vytvořené voláním **GetResponseStream** jsou jen pro čtení a stream instance vytvořené voláním **GetRequestStream** jsou jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="8df3d-125">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="8df3d-126">Použijte <xref:System.IO.StreamReader> třídu, abyste usnadnili kódování.</span><span class="sxs-lookup"><span data-stu-id="8df3d-126">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="8df3d-127">Následující příklad kódu používá **StreamReader** ke čtení ascii kódovaný datový proud z **WebResponse** (příklad nezobrazuje vytváření požadavku).</span><span class="sxs-lookup"><span data-stu-id="8df3d-127">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="8df3d-128">Volání **GetResponse** můžete blokovat, pokud síťové prostředky nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8df3d-128">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="8df3d-129">Měli byste zvážit použití asynchronní <xref:System.Net.WebRequest.BeginGetResponse%2A> ho <xref:System.Net.WebRequest.EndGetResponse%2A> požadavku s metodami a.</span><span class="sxs-lookup"><span data-stu-id="8df3d-129">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="8df3d-130">Volání **GetRequestStream** můžete blokovat při vytvoření připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="8df3d-130">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="8df3d-131">Měli byste zvážit použití asynchronní požadavek <xref:System.Net.WebRequest.BeginGetRequestStream%2A> pro <xref:System.Net.WebRequest.EndGetRequestStream%2A> datový proud s a metody.</span><span class="sxs-lookup"><span data-stu-id="8df3d-131">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="8df3d-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="8df3d-132">See also</span></span>

- [<span data-ttu-id="8df3d-133">Postupy:Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="8df3d-133">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="8df3d-134">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="8df3d-134">Requesting Data</span></span>](requesting-data.md)
