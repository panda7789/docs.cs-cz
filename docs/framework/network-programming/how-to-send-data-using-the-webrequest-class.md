---
title: 'Postupy: Odeslání dat pomocí třídy WebRequest'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040832"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="a822f-102">Postupy: Odeslání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="a822f-102">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="a822f-103">Následující postup popisuje kroky k odeslání dat na server.</span><span class="sxs-lookup"><span data-stu-id="a822f-103">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="a822f-104">Tento postup se běžně používá k odeslání dat na webovou stránku.</span><span class="sxs-lookup"><span data-stu-id="a822f-104">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="a822f-105">Odeslání dat na hostitelský server</span><span class="sxs-lookup"><span data-stu-id="a822f-105">To send data to a host server</span></span>

1. <span data-ttu-id="a822f-106">Vytvořte instanci voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku, jako je například skript nebo stránka ASP.NET, která přijímá data. <xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="a822f-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="a822f-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a822f-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="a822f-108">.NET Framework poskytuje třídy <xref:System.Net.WebRequest> specifické pro protokol odvozené z tříd a <xref:System.Net.WebResponse> pro identifikátory URI, které začínají na *http:* , *https:* , *FTP:* a *File:* .</span><span class="sxs-lookup"><span data-stu-id="a822f-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="a822f-109">Pokud potřebujete nastavit nebo číst vlastnosti specifické pro protokol, musíte přetypovat <xref:System.Net.WebRequest> objekt nebo <xref:System.Net.WebResponse> na typ objektu specifický pro protokol.</span><span class="sxs-lookup"><span data-stu-id="a822f-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="a822f-110">Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="a822f-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="a822f-111">Nastavte všechny hodnoty vlastností, které v `WebRequest` objektu potřebujete.</span><span class="sxs-lookup"><span data-stu-id="a822f-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="a822f-112">Chcete-li například povolit ověřování, nastavte <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> vlastnost na instanci <xref:System.Net.NetworkCredential> třídy:</span><span class="sxs-lookup"><span data-stu-id="a822f-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="a822f-113">Zadejte metodu protokolu, která umožňuje odesílat data s požadavkem, jako je například metoda HTTP `POST` :</span><span class="sxs-lookup"><span data-stu-id="a822f-113">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="a822f-114"><xref:System.Web.HttpRequest.ContentLength> Nastavte vlastnost na počet bajtů, které jsou součástí vaší žádosti.</span><span class="sxs-lookup"><span data-stu-id="a822f-114">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="a822f-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a822f-115">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="a822f-116"><xref:System.Web.HttpRequest.ContentType> Nastavte vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a822f-116">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="a822f-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a822f-117">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="a822f-118">Získejte datový proud, který uchovává data požadavků, voláním <xref:System.Net.WebRequest.GetRequestStream%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a822f-118">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="a822f-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a822f-119">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="a822f-120">Zápis dat do <xref:System.IO.Stream> objektu vráceného `GetRequestStream` metodou.</span><span class="sxs-lookup"><span data-stu-id="a822f-120">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="a822f-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a822f-121">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="a822f-122">Uzavřete datový proud požadavku voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a822f-122">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a822f-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a822f-123">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="a822f-124">Odešle požadavek na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a822f-124">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a822f-125">Tato metoda vrátí objekt obsahující odpověď serveru.</span><span class="sxs-lookup"><span data-stu-id="a822f-125">This method returns an object containing the server's response.</span></span> <span data-ttu-id="a822f-126">Typ vráceného `WebResponse` objektu je určen schématem identifikátoru URI žádosti.</span><span class="sxs-lookup"><span data-stu-id="a822f-126">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="a822f-127">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a822f-127">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="a822f-128">Můžete získat přístup k vlastnostem `WebResponse` objektu nebo ho přetypovat na instanci specifickou pro protokol pro čtení vlastností specifických pro protokol.</span><span class="sxs-lookup"><span data-stu-id="a822f-128">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="a822f-129">Chcete-li například získat přístup k vlastnostem <xref:System.Net.HttpWebResponse>specifickým pro protokol HTTP, `WebResponse` přetypování <xref:System.Net.HttpWebResponse> objektu na odkaz.</span><span class="sxs-lookup"><span data-stu-id="a822f-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="a822f-130">Následující příklad kódu ukazuje, jak zobrazit vlastnost specifickou <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> pro protokol HTTP odeslanou odpovědí:</span><span class="sxs-lookup"><span data-stu-id="a822f-130">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="a822f-131">Chcete-li získat datový proud obsahující data odpovědí odesílaná serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodu `WebResponse` objektu.</span><span class="sxs-lookup"><span data-stu-id="a822f-131">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="a822f-132">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a822f-132">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="a822f-133">Po načtení dat z objektu Response ho buď zavřete, a to pomocí <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody, nebo zavřete datový proud odpovědi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> s metodou.</span><span class="sxs-lookup"><span data-stu-id="a822f-133">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a822f-134">Pokud nezavřete odpověď nebo datový proud, může aplikace vysílat připojení k serveru a nebude možné zpracovat další požadavky.</span><span class="sxs-lookup"><span data-stu-id="a822f-134">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="a822f-135">Vzhledem k tomu, `Stream.Close` že `Close` metodavolá,kdyžjeodpověďzavřená,nenínutnévolatnaobjektyResponseaStream,ikdyžtaknebudete`WebResponse.Close` mít škodlivou.</span><span class="sxs-lookup"><span data-stu-id="a822f-135">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="a822f-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a822f-136">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="a822f-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="a822f-137">Example</span></span>

<span data-ttu-id="a822f-138">Následující příklad ukazuje, jak odesílat data na webový server a číst data v odpovědi:</span><span class="sxs-lookup"><span data-stu-id="a822f-138">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="a822f-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a822f-139">See also</span></span>

- [<span data-ttu-id="a822f-140">Vytváření internetových požadavků</span><span class="sxs-lookup"><span data-stu-id="a822f-140">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="a822f-141">Použití datových proudů v síti</span><span class="sxs-lookup"><span data-stu-id="a822f-141">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="a822f-142">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="a822f-142">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="a822f-143">Vyžádání dat</span><span class="sxs-lookup"><span data-stu-id="a822f-143">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="a822f-144">Postupy: Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="a822f-144">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
