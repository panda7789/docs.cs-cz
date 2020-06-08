---
title: 'Postupy: vyžádání dat pomocí třídy WebRequest'
description: Naučte se, jak vyžádat prostředek, jako je webová stránka nebo soubor, ze serveru pomocí třídy WebRequest v .NET Framework.
ms.date: 03/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
ms.openlocfilehash: 5dcc1a7dad226288e3f74969b86e2dd457c0eed0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502467"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="b7785-103">Postupy: vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="b7785-103">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="b7785-104">Následující postup popisuje kroky pro vyžádání prostředku, například webové stránky nebo souboru, ze serveru.</span><span class="sxs-lookup"><span data-stu-id="b7785-104">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="b7785-105">Prostředek musí být identifikovaný identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="b7785-105">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="b7785-106">Vyžádání dat z hostitelského serveru</span><span class="sxs-lookup"><span data-stu-id="b7785-106">To request data from a host server</span></span>

1. <span data-ttu-id="b7785-107">Vytvořte <xref:System.Net.WebRequest> instanci voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku.</span><span class="sxs-lookup"><span data-stu-id="b7785-107">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="b7785-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b7785-108">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > <span data-ttu-id="b7785-109">.NET Framework poskytuje třídy specifické pro protokol odvozené z <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> tříd a pro identifikátory URI, které začínají na *http:*, *https:*, *FTP:* a *File:*.</span><span class="sxs-lookup"><span data-stu-id="b7785-109">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="b7785-110">Pokud potřebujete nastavit nebo číst vlastnosti specifické pro protokol, musíte přetypovat <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> objekt nebo na typ objektu specifický pro protokol.</span><span class="sxs-lookup"><span data-stu-id="b7785-110">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="b7785-111">Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="b7785-111">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="b7785-112">Nastavte všechny hodnoty vlastností, které v objektu potřebujete `WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="b7785-112">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="b7785-113">Chcete-li například povolit ověřování, nastavte <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> vlastnost na instanci <xref:System.Net.NetworkCredential> třídy:</span><span class="sxs-lookup"><span data-stu-id="b7785-113">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="b7785-114">Odešle požadavek na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b7785-114">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b7785-115">Tato metoda vrátí objekt obsahující odpověď serveru.</span><span class="sxs-lookup"><span data-stu-id="b7785-115">This method returns an object containing the server's response.</span></span> <span data-ttu-id="b7785-116">Typ vráceného <xref:System.Net.WebResponse> objektu je určen schématem identifikátoru URI žádosti.</span><span class="sxs-lookup"><span data-stu-id="b7785-116">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="b7785-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b7785-117">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="b7785-118">Můžete získat přístup k vlastnostem `WebResponse` objektu nebo ho přetypovat na instanci specifickou pro protokol pro čtení vlastností specifických pro protokol.</span><span class="sxs-lookup"><span data-stu-id="b7785-118">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="b7785-119">Chcete-li například získat přístup k vlastnostem specifickým pro protokol HTTP <xref:System.Net.HttpWebResponse> , přetypování `WebResponse` objektu na `HttpWebResponse` odkaz.</span><span class="sxs-lookup"><span data-stu-id="b7785-119">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="b7785-120">Následující příklad kódu ukazuje, jak zobrazit vlastnost specifickou pro protokol HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> odeslanou odpovědí:</span><span class="sxs-lookup"><span data-stu-id="b7785-120">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="b7785-121">Chcete-li získat datový proud obsahující data odpovědí odesílaná serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="b7785-121">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b7785-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b7785-122">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="b7785-123">Po načtení dat z objektu Response ho buď zavřete, a to pomocí <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody, nebo zavřete datový proud odpovědi s <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="b7785-123">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b7785-124">Pokud nezavřete objekt Response nebo datový proud, může vaše aplikace vysílat připojení k serveru a nebude možné zpracovat další požadavky.</span><span class="sxs-lookup"><span data-stu-id="b7785-124">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="b7785-125">Vzhledem k tomu, že `WebResponse.Close` metoda volá `Stream.Close` , když je odpověď zavřená, není nutné volat `Close` na objekty Response a Stream, i když tak nebudete mít škodlivou.</span><span class="sxs-lookup"><span data-stu-id="b7785-125">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="b7785-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b7785-126">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="b7785-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7785-127">Example</span></span>

<span data-ttu-id="b7785-128">Následující příklad kódu ukazuje, jak vytvořit požadavek na webový server a jak číst data v odpovědi:</span><span class="sxs-lookup"><span data-stu-id="b7785-128">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="b7785-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7785-129">See also</span></span>

- [<span data-ttu-id="b7785-130">Vytváření internetových požadavků</span><span class="sxs-lookup"><span data-stu-id="b7785-130">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="b7785-131">Použití datových proudů v síti</span><span class="sxs-lookup"><span data-stu-id="b7785-131">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="b7785-132">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="b7785-132">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="b7785-133">Vyžádání dat</span><span class="sxs-lookup"><span data-stu-id="b7785-133">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="b7785-134">Postupy: odesílání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="b7785-134">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
