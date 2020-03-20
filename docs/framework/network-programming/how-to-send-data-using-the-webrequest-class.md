---
title: 'Postup: Odeslání dat pomocí třídy WebRequest'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70040832"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="e2d91-102">Postup: Odeslání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="e2d91-102">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="e2d91-103">Následující postup popisuje postup odesílání dat na server.</span><span class="sxs-lookup"><span data-stu-id="e2d91-103">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="e2d91-104">Tento postup se běžně používá k zaúčtování dat na webovou stránku.</span><span class="sxs-lookup"><span data-stu-id="e2d91-104">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="e2d91-105">Odeslání dat na hostitelský server</span><span class="sxs-lookup"><span data-stu-id="e2d91-105">To send data to a host server</span></span>

1. <span data-ttu-id="e2d91-106">Vytvořte <xref:System.Net.WebRequest> instanci voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> pomocí identifikátoru URI prostředku, například skriptu nebo stránky ASP.NET, která přijímá data.</span><span class="sxs-lookup"><span data-stu-id="e2d91-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="e2d91-107">Například:</span><span class="sxs-lookup"><span data-stu-id="e2d91-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="e2d91-108">Rozhraní .NET Framework poskytuje třídy specifické <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> pro protokol odvozené z tříd a pro identifikátory URI začínající *protokolem http:*, *https:* *, ftp:* a *soubor:*.</span><span class="sxs-lookup"><span data-stu-id="e2d91-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="e2d91-109">Pokud potřebujete nastavit nebo číst vlastnosti specifické pro <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> protokol, musíte přetypovat typ objektu specifického pro protokol.</span><span class="sxs-lookup"><span data-stu-id="e2d91-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="e2d91-110">Další informace naleznete [v tématu Programování připojitelných protokolů](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="e2d91-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="e2d91-111">Nastavte všechny hodnoty vlastností, `WebRequest` které potřebujete v objektu.</span><span class="sxs-lookup"><span data-stu-id="e2d91-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="e2d91-112">Chcete-li například povolit <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> ověřování, nastavte <xref:System.Net.NetworkCredential> vlastnost na instanci třídy:</span><span class="sxs-lookup"><span data-stu-id="e2d91-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="e2d91-113">Zadejte metodu protokolu, která umožňuje odesílat data `POST` s požadavkem, například metodou HTTP:</span><span class="sxs-lookup"><span data-stu-id="e2d91-113">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="e2d91-114">Nastavte <xref:System.Web.HttpRequest.ContentLength> vlastnost na počet bajtů, které do aplikace aplikace aplikace zahrnuli.</span><span class="sxs-lookup"><span data-stu-id="e2d91-114">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="e2d91-115">Například:</span><span class="sxs-lookup"><span data-stu-id="e2d91-115">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="e2d91-116">Nastavte <xref:System.Web.HttpRequest.ContentType> vlastnost na příslušnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e2d91-116">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="e2d91-117">Například:</span><span class="sxs-lookup"><span data-stu-id="e2d91-117">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="e2d91-118">Získejte datový proud, který <xref:System.Net.WebRequest.GetRequestStream%2A> obsahuje data požadavku voláním metody.</span><span class="sxs-lookup"><span data-stu-id="e2d91-118">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="e2d91-119">Například:</span><span class="sxs-lookup"><span data-stu-id="e2d91-119">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="e2d91-120">Zapište data <xref:System.IO.Stream> do objektu `GetRequestStream` vrácené metodou.</span><span class="sxs-lookup"><span data-stu-id="e2d91-120">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="e2d91-121">Například:</span><span class="sxs-lookup"><span data-stu-id="e2d91-121">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="e2d91-122">Zavřete datový proud <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> požadavku voláním metody.</span><span class="sxs-lookup"><span data-stu-id="e2d91-122">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e2d91-123">Například:</span><span class="sxs-lookup"><span data-stu-id="e2d91-123">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="e2d91-124">Odešlete požadavek na <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>server voláním .</span><span class="sxs-lookup"><span data-stu-id="e2d91-124">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e2d91-125">Tato metoda vrátí objekt obsahující odpověď serveru.</span><span class="sxs-lookup"><span data-stu-id="e2d91-125">This method returns an object containing the server's response.</span></span> <span data-ttu-id="e2d91-126">Typ `WebResponse` vráceného objektu je určen schématem identifikátoru URI požadavku požadavku.</span><span class="sxs-lookup"><span data-stu-id="e2d91-126">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="e2d91-127">Například:</span><span class="sxs-lookup"><span data-stu-id="e2d91-127">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="e2d91-128">Můžete přistupovat k `WebResponse` vlastnostem objektu nebo ho přetypovat do instance specifické pro protokol ke čtení vlastností specifických pro protokol.</span><span class="sxs-lookup"><span data-stu-id="e2d91-128">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="e2d91-129">Chcete-li například získat přístup <xref:System.Net.HttpWebResponse>k vlastnostem specifické pro protokol HTTP , přetypujte `WebResponse` objekt na odkaz. <xref:System.Net.HttpWebResponse></span><span class="sxs-lookup"><span data-stu-id="e2d91-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="e2d91-130">Následující příklad kódu ukazuje, jak zobrazit <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> vlastnost specifickou pro protokol HTTP odeslanou s odpovědí:</span><span class="sxs-lookup"><span data-stu-id="e2d91-130">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="e2d91-131">Chcete-li získat datový proud obsahující data odpovědí <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> odeslaná `WebResponse` serverem, zavolejte metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="e2d91-131">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="e2d91-132">Například:</span><span class="sxs-lookup"><span data-stu-id="e2d91-132">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="e2d91-133">Po přečtení dat z objektu odpovědi zavřete <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> je metodou nebo zavřete <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> datový proud odpovědí metodou.</span><span class="sxs-lookup"><span data-stu-id="e2d91-133">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e2d91-134">Pokud nezavřete odpověď ani datový proud, může aplikace spustit mimo připojení serveru a nebude možné zpracovat další požadavky.</span><span class="sxs-lookup"><span data-stu-id="e2d91-134">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="e2d91-135">Vzhledem `WebResponse.Close` k `Stream.Close` tomu, že metoda volá, když zavře `Close` odpověď, není nutné volat na odpovědi a datového proudu objekty, i když přitom není škodlivé.</span><span class="sxs-lookup"><span data-stu-id="e2d91-135">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="e2d91-136">Například:</span><span class="sxs-lookup"><span data-stu-id="e2d91-136">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="e2d91-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2d91-137">Example</span></span>

<span data-ttu-id="e2d91-138">Následující příklad ukazuje, jak odeslat data na webový server a číst data v jeho odpovědi:</span><span class="sxs-lookup"><span data-stu-id="e2d91-138">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="e2d91-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2d91-139">See also</span></span>

- [<span data-ttu-id="e2d91-140">Vytváření internetových požadavků</span><span class="sxs-lookup"><span data-stu-id="e2d91-140">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="e2d91-141">Používání datových proudů v síti</span><span class="sxs-lookup"><span data-stu-id="e2d91-141">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="e2d91-142">Přístup k internetu prostřednictvím proxy</span><span class="sxs-lookup"><span data-stu-id="e2d91-142">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="e2d91-143">Vyžádání údajů</span><span class="sxs-lookup"><span data-stu-id="e2d91-143">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="e2d91-144">Postup: Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="e2d91-144">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
