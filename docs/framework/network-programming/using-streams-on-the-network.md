---
title: Použití streamů v síti
description: .NET Framework představuje síťové prostředky jako proudy. Třída NetworkStream implementuje třídu Stream pro použití se síťovými prostředky.
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
ms.openlocfilehash: f8d35b43c9b46a77bfd0c78f7d0118093b6fe824
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501973"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="517a2-104">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="517a2-104">Using Streams on the Network</span></span>
<span data-ttu-id="517a2-105">Síťové prostředky jsou reprezentovány v .NET Framework jako datové proudy.</span><span class="sxs-lookup"><span data-stu-id="517a2-105">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="517a2-106">Při obecném zpracování datových proudů nabízí .NET Framework následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="517a2-106">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="517a2-107">Běžný způsob, jak odesílat a přijímat webová data.</span><span class="sxs-lookup"><span data-stu-id="517a2-107">A common way to send and receive Web data.</span></span> <span data-ttu-id="517a2-108">Bez ohledu na skutečný obsah souboru – HTML, XML nebo cokoli jiného – vaše aplikace bude používat <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> a <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> k posílání a přijímání dat.</span><span class="sxs-lookup"><span data-stu-id="517a2-108">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="517a2-109">Kompatibilita s datovými proudy napříč .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="517a2-109">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="517a2-110">Datové proudy se používají v rámci .NET Framework, které mají bohatou infrastrukturu pro jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="517a2-110">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="517a2-111">Například můžete upravit aplikaci, která čte data jazyka XML z a, a to tak, že <xref:System.IO.FileStream> <xref:System.Net.Sockets.NetworkStream> změníte pouze pár řádků kódu, které inicializují datový proud.</span><span class="sxs-lookup"><span data-stu-id="517a2-111">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="517a2-112">Hlavní rozdíly mezi třídou **NetworkStream** a jinými datovými proudy je, že **NetworkStream** nelze vyhledat, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> vlastnost vždy vrátí **hodnotu false**a <xref:System.Net.Sockets.NetworkStream.Seek%2A> metody a <xref:System.Net.Sockets.NetworkStream.Position%2A> vyvolávají výjimku <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="517a2-112">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="517a2-113">Zpracování dat při jejich doručení.</span><span class="sxs-lookup"><span data-stu-id="517a2-113">Processing of data as it arrives.</span></span> <span data-ttu-id="517a2-114">Datové proudy poskytují přístup k datům, když se dorazí ze sítě, a nenutí, aby aplikace čekala na stažení celé datové sady.</span><span class="sxs-lookup"><span data-stu-id="517a2-114">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="517a2-115"><xref:System.Net.Sockets>Obor názvů obsahuje třídu **NetworkStream** , která implementuje <xref:System.IO.Stream> specifickou třídu pro použití se síťovými prostředky.</span><span class="sxs-lookup"><span data-stu-id="517a2-115">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="517a2-116">Třídy v <xref:System.Net.Sockets> oboru názvů používají třídu **NetworkStream** k reprezentování datových proudů.</span><span class="sxs-lookup"><span data-stu-id="517a2-116">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="517a2-117">Pokud chcete odesílat data do sítě pomocí vráceného datového proudu, zavolejte <xref:System.Net.WebRequest.GetRequestStream%2A> na <xref:System.Net.WebRequest> .</span><span class="sxs-lookup"><span data-stu-id="517a2-117">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="517a2-118">**WebRequest** pošle hlavičky žádosti na server. pak můžete odeslat data do síťového prostředku voláním <xref:System.IO.Stream.BeginWrite%2A> <xref:System.IO.Stream.EndWrite%2A> metody, nebo <xref:System.IO.Stream.Write%2A> na vráceném datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="517a2-118">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="517a2-119">Některé protokoly, například HTTP, můžou před odesláním dat vyžadovat, abyste nastavili vlastnosti specifické pro protokol.</span><span class="sxs-lookup"><span data-stu-id="517a2-119">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="517a2-120">Následující příklad kódu ukazuje, jak nastavit vlastnosti specifické pro protokol HTTP pro odesílání dat.</span><span class="sxs-lookup"><span data-stu-id="517a2-120">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="517a2-121">Předpokládá, že proměnná `sendData` obsahuje data k odeslání a že proměnná `sendLength` je počet bajtů dat k odeslání.</span><span class="sxs-lookup"><span data-stu-id="517a2-121">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
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
  
 <span data-ttu-id="517a2-122">Pokud chcete přijímat data ze sítě, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A> na <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="517a2-122">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="517a2-123">Pak můžete číst data ze síťového prostředku voláním <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> metody, nebo <xref:System.IO.Stream.Read%2A> ve vráceném datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="517a2-123">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="517a2-124">Při použití datových proudů ze síťových prostředků mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="517a2-124">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="517a2-125">Vlastnost **CanSeek** vždy vrací **hodnotu false** , protože třída **NetworkStream** nemůže měnit pozici v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="517a2-125">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="517a2-126">Metody **hledání** a **umístění** vyvolávají výjimku **NotSupportedException**.</span><span class="sxs-lookup"><span data-stu-id="517a2-126">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="517a2-127">Když použijete **WebRequest** a **WebResponse**, instance streamu vytvořené voláním **GetResponseStream** jsou jen pro čtení a instance streamu vytvořené voláním **GetRequestStream** jsou jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="517a2-127">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="517a2-128">Použijte <xref:System.IO.StreamReader> třídu, aby bylo kódování snazší.</span><span class="sxs-lookup"><span data-stu-id="517a2-128">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="517a2-129">Následující příklad kódu používá **StreamReader** ke čtení datového proudu kódovaného ASCII z **WebResponse** (příklad neukazuje vytvoření žádosti).</span><span class="sxs-lookup"><span data-stu-id="517a2-129">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="517a2-130">Volání **GetResponse** může blokovat, pokud nejsou k dispozici síťové prostředky.</span><span class="sxs-lookup"><span data-stu-id="517a2-130">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="517a2-131">Měli byste zvážit použití asynchronního požadavku s <xref:System.Net.WebRequest.BeginGetResponse%2A> <xref:System.Net.WebRequest.EndGetResponse%2A> metodami a.</span><span class="sxs-lookup"><span data-stu-id="517a2-131">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="517a2-132">Volání **GetRequestStream** může blokovat při vytvoření připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="517a2-132">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="517a2-133">Měli byste zvážit použití asynchronního požadavku pro datový proud s <xref:System.Net.WebRequest.BeginGetRequestStream%2A> <xref:System.Net.WebRequest.EndGetRequestStream%2A> metodami a.</span><span class="sxs-lookup"><span data-stu-id="517a2-133">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="517a2-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="517a2-134">See also</span></span>

- [<span data-ttu-id="517a2-135">Postupy:Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="517a2-135">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="517a2-136">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="517a2-136">Requesting Data</span></span>](requesting-data.md)
