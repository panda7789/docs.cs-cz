---
title: 'Postupy: odesílání dat pomocí třídy WebRequest'
description: Naučte se, jak odesílat data na server pomocí třídy WebRequest v .NET Framework. Tento postup se běžně používá k odesílání dat na webovou stránku.
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 4b353250fec778ee8b352f13de6d7faaf15c13ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502441"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="547c6-104">Postupy: odesílání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="547c6-104">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="547c6-105">Následující postup popisuje kroky k odeslání dat na server.</span><span class="sxs-lookup"><span data-stu-id="547c6-105">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="547c6-106">Tento postup se běžně používá k odeslání dat na webovou stránku.</span><span class="sxs-lookup"><span data-stu-id="547c6-106">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="547c6-107">Odeslání dat na hostitelský server</span><span class="sxs-lookup"><span data-stu-id="547c6-107">To send data to a host server</span></span>

1. <span data-ttu-id="547c6-108">Vytvořte <xref:System.Net.WebRequest> instanci voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku, jako je například skript nebo stránka ASP.NET, která přijímá data.</span><span class="sxs-lookup"><span data-stu-id="547c6-108">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="547c6-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="547c6-109">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="547c6-110">.NET Framework poskytuje třídy specifické pro protokol odvozené z <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> tříd a pro identifikátory URI, které začínají na *http:*, *https:*, *FTP:* a *File:*.</span><span class="sxs-lookup"><span data-stu-id="547c6-110">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="547c6-111">Pokud potřebujete nastavit nebo číst vlastnosti specifické pro protokol, musíte přetypovat <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> objekt nebo na typ objektu specifický pro protokol.</span><span class="sxs-lookup"><span data-stu-id="547c6-111">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="547c6-112">Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="547c6-112">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="547c6-113">Nastavte všechny hodnoty vlastností, které v objektu potřebujete `WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="547c6-113">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="547c6-114">Chcete-li například povolit ověřování, nastavte <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> vlastnost na instanci <xref:System.Net.NetworkCredential> třídy:</span><span class="sxs-lookup"><span data-stu-id="547c6-114">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="547c6-115">Zadejte metodu protokolu, která umožňuje odesílat data s požadavkem, jako je například `POST` Metoda http:</span><span class="sxs-lookup"><span data-stu-id="547c6-115">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="547c6-116">Nastavte <xref:System.Web.HttpRequest.ContentLength> vlastnost na počet bajtů, které jsou součástí vaší žádosti.</span><span class="sxs-lookup"><span data-stu-id="547c6-116">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="547c6-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="547c6-117">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="547c6-118">Nastavte <xref:System.Web.HttpRequest.ContentType> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="547c6-118">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="547c6-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="547c6-119">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="547c6-120">Získejte datový proud, který uchovává data požadavků, voláním <xref:System.Net.WebRequest.GetRequestStream%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="547c6-120">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="547c6-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="547c6-121">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="547c6-122">Zápis dat do <xref:System.IO.Stream> objektu vráceného `GetRequestStream` metodou.</span><span class="sxs-lookup"><span data-stu-id="547c6-122">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="547c6-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="547c6-123">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="547c6-124">Uzavřete datový proud požadavku voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="547c6-124">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="547c6-125">Příklad:</span><span class="sxs-lookup"><span data-stu-id="547c6-125">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="547c6-126">Odešle požadavek na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="547c6-126">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="547c6-127">Tato metoda vrátí objekt obsahující odpověď serveru.</span><span class="sxs-lookup"><span data-stu-id="547c6-127">This method returns an object containing the server's response.</span></span> <span data-ttu-id="547c6-128">Typ vráceného `WebResponse` objektu je určen schématem identifikátoru URI žádosti.</span><span class="sxs-lookup"><span data-stu-id="547c6-128">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="547c6-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="547c6-129">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="547c6-130">Můžete získat přístup k vlastnostem `WebResponse` objektu nebo ho přetypovat na instanci specifickou pro protokol pro čtení vlastností specifických pro protokol.</span><span class="sxs-lookup"><span data-stu-id="547c6-130">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="547c6-131">Chcete-li například získat přístup k vlastnostem specifickým pro protokol HTTP <xref:System.Net.HttpWebResponse> , přetypování `WebResponse` objektu na <xref:System.Net.HttpWebResponse> odkaz.</span><span class="sxs-lookup"><span data-stu-id="547c6-131">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="547c6-132">Následující příklad kódu ukazuje, jak zobrazit vlastnost specifickou pro protokol HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> odeslanou odpovědí:</span><span class="sxs-lookup"><span data-stu-id="547c6-132">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="547c6-133">Chcete-li získat datový proud obsahující data odpovědí odesílaná serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodu `WebResponse` objektu.</span><span class="sxs-lookup"><span data-stu-id="547c6-133">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="547c6-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="547c6-134">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="547c6-135">Po načtení dat z objektu Response ho buď zavřete, a to pomocí <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody, nebo zavřete datový proud odpovědi s <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="547c6-135">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="547c6-136">Pokud nezavřete odpověď nebo datový proud, může aplikace vysílat připojení k serveru a nebude možné zpracovat další požadavky.</span><span class="sxs-lookup"><span data-stu-id="547c6-136">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="547c6-137">Vzhledem k tomu, že `WebResponse.Close` metoda volá `Stream.Close` , když je odpověď zavřená, není nutné volat `Close` na objekty Response a Stream, i když tak nebudete mít škodlivou.</span><span class="sxs-lookup"><span data-stu-id="547c6-137">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="547c6-138">Příklad:</span><span class="sxs-lookup"><span data-stu-id="547c6-138">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="547c6-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="547c6-139">Example</span></span>

<span data-ttu-id="547c6-140">Následující příklad ukazuje, jak odesílat data na webový server a číst data v odpovědi:</span><span class="sxs-lookup"><span data-stu-id="547c6-140">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="547c6-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="547c6-141">See also</span></span>

- [<span data-ttu-id="547c6-142">Vytváření internetových požadavků</span><span class="sxs-lookup"><span data-stu-id="547c6-142">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="547c6-143">Použití datových proudů v síti</span><span class="sxs-lookup"><span data-stu-id="547c6-143">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="547c6-144">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="547c6-144">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="547c6-145">Vyžádání dat</span><span class="sxs-lookup"><span data-stu-id="547c6-145">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="547c6-146">Postupy: vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="547c6-146">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
