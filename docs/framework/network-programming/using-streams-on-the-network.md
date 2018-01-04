---
title: "Pomocí datových proudů v síti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9f6cf68115f69e7238d2bec226258ab06c417d7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="06faf-102">Pomocí datových proudů v síti</span><span class="sxs-lookup"><span data-stu-id="06faf-102">Using Streams on the Network</span></span>
<span data-ttu-id="06faf-103">Síťové prostředky jsou v rozhraní .NET Framework vyjádřené datových proudů.</span><span class="sxs-lookup"><span data-stu-id="06faf-103">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="06faf-104">Rozhraní .NET Framework tak, že obecně považuje datové proudy, nabízí následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="06faf-104">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
-   <span data-ttu-id="06faf-105">Běžný způsob, jak odesílat a přijímat Web data.</span><span class="sxs-lookup"><span data-stu-id="06faf-105">A common way to send and receive Web data.</span></span> <span data-ttu-id="06faf-106">Ať skutečný obsah souboru – HTML, XML nebo cokoliv jiného – vaše aplikace bude používat <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> a <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> odesílat a přijímat data.</span><span class="sxs-lookup"><span data-stu-id="06faf-106">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
-   <span data-ttu-id="06faf-107">Kompatibilita s datovými proudy v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06faf-107">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="06faf-108">Datové proudy se používají v rozhraní .NET Framework, který má bohaté infrastrukturu pro jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="06faf-108">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="06faf-109">Například můžete upravit aplikaci, která čte data XML z <xref:System.IO.FileStream> čtení dat z <xref:System.Net.Sockets.NetworkStream> místo změnou pouze několik řádky kódu, které inicializace datového proudu.</span><span class="sxs-lookup"><span data-stu-id="06faf-109">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="06faf-110">Hlavní rozdíly mezi **NetworkStream** třídy a jiné datové proudy jsou **NetworkStream** není prohledávat, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> vlastnost vždy vrátí hodnotu **false**a <xref:System.Net.Sockets.NetworkStream.Seek%2A> a <xref:System.Net.Sockets.NetworkStream.Position%2A> metody throw <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="06faf-110">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
-   <span data-ttu-id="06faf-111">Zpracování dat jako jeho přijetí.</span><span class="sxs-lookup"><span data-stu-id="06faf-111">Processing of data as it arrives.</span></span> <span data-ttu-id="06faf-112">Datové proudy poskytnout přístup k datům za ze sítě, nikoli vynucení aplikace čekat celá sada dat ke stažení.</span><span class="sxs-lookup"><span data-stu-id="06faf-112">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="06faf-113"><xref:System.Net.Sockets> Obor názvů obsahuje **NetworkStream** třídu, která implementuje <xref:System.IO.Stream> třída speciálně pro použití s síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="06faf-113">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="06faf-114">Třídy v <xref:System.Net.Sockets> oboru názvů používají **NetworkStream** třída představující datových proudů.</span><span class="sxs-lookup"><span data-stu-id="06faf-114">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="06faf-115">Chcete-li odesílat data k síti pomocí vráceném datovém proudu, volejte <xref:System.Net.WebRequest.GetRequestStream%2A> na vaše <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="06faf-115">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="06faf-116">**WebRequest** odešle hlaviček požadavků na server; potom může odesílat data k síťovému prostředku pomocí volání <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, nebo <xref:System.IO.Stream.Write%2A> metodu na vrácených datového proudu.</span><span class="sxs-lookup"><span data-stu-id="06faf-116">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="06faf-117">Může vyžadovat některé protokoly, jako je například HTTP, můžete nastavit vlastnosti specifické pro protokol před odesláním údajů.</span><span class="sxs-lookup"><span data-stu-id="06faf-117">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="06faf-118">Následující příklad kódu ukazuje, jak nastavit vlastnosti specifické pro odesílání dat.</span><span class="sxs-lookup"><span data-stu-id="06faf-118">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="06faf-119">Předpokládá, že proměnná `sendData` obsahuje data k odeslání a že proměnnou `sendLength` je počet bajtů dat k odeslání.</span><span class="sxs-lookup"><span data-stu-id="06faf-119">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
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
  
 <span data-ttu-id="06faf-120">Chcete-li přijímat data ze sítě, volejte <xref:System.Net.WebResponse.GetResponseStream%2A> na vaše <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="06faf-120">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="06faf-121">Pak můžete číst data z síťovému prostředku pomocí volání <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, nebo <xref:System.IO.Stream.Read%2A> metodu na vrácených datového proudu.</span><span class="sxs-lookup"><span data-stu-id="06faf-121">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="06faf-122">Při použití datové proudy z síťovým prostředkům, mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="06faf-122">When using streams from network resources, keep in mind the following points:</span></span>  
  
-   <span data-ttu-id="06faf-123">**CanSeek** vlastnost vždy vrátí hodnotu **false** vzhledem k tomu **NetworkStream** třída nelze změnit pozici v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="06faf-123">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="06faf-124">**Seek** a **pozice** metody throw **NotSupportedException**.</span><span class="sxs-lookup"><span data-stu-id="06faf-124">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
-   <span data-ttu-id="06faf-125">Při použití **WebRequest** a **WebResponse**, stream instance vytvořená voláním **GetResponseStream** jsou jen pro čtení a stream instance vytvořená voláním  **GetRequestStream** jsou jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="06faf-125">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
-   <span data-ttu-id="06faf-126">Použití <xref:System.IO.StreamReader> třída aby kódování snazší.</span><span class="sxs-lookup"><span data-stu-id="06faf-126">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="06faf-127">Následující příklad kódu používá **StreamReader** číst stream kódováním ASCII z **WebResponse** (v příkladu nezobrazuje vytváření požadavek).</span><span class="sxs-lookup"><span data-stu-id="06faf-127">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
-   <span data-ttu-id="06faf-128">Volání **GetResponse** můžete blokovat, pokud nejsou k dispozici síťové prostředky.</span><span class="sxs-lookup"><span data-stu-id="06faf-128">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="06faf-129">Měli byste zvážit použití asynchronní požadavek s <xref:System.Net.WebRequest.BeginGetResponse%2A> a <xref:System.Net.WebRequest.EndGetResponse%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06faf-129">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
-   <span data-ttu-id="06faf-130">Volání **GetRequestStream** můžete blokovat, když se vytvoří připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="06faf-130">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="06faf-131">Měli byste zvážit použití asynchronní požadavek pro datový proud s <xref:System.Net.WebRequest.BeginGetRequestStream%2A> a <xref:System.Net.WebRequest.EndGetRequestStream%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06faf-131">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06faf-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="06faf-132">See Also</span></span>  
 [<span data-ttu-id="06faf-133">Postupy:Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="06faf-133">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [<span data-ttu-id="06faf-134">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="06faf-134">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
