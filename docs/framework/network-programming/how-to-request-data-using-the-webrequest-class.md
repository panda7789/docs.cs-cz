---
title: 'Postupy: Vyžádání dat pomocí třídy WebRequest'
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
ms.openlocfilehash: e670a2a503ce704eff847e9e0b3ee340ab52fe62
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048157"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="d1a4d-102">Postupy: Vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="d1a4d-102">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="d1a4d-103">Následující postup popisuje kroky pro vyžádání prostředku, například webové stránky nebo souboru, ze serveru.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-103">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="d1a4d-104">Prostředek musí být identifikovaný identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-104">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="d1a4d-105">Vyžádání dat z hostitelského serveru</span><span class="sxs-lookup"><span data-stu-id="d1a4d-105">To request data from a host server</span></span>

1. <span data-ttu-id="d1a4d-106">Vytvořte instanci voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku. <xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="d1a4d-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="d1a4d-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d1a4d-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > <span data-ttu-id="d1a4d-108">.NET Framework poskytuje třídy <xref:System.Net.WebRequest> specifické pro protokol odvozené z tříd a <xref:System.Net.WebResponse> pro identifikátory URI, které začínají na *http:* , *https:* , *FTP:* a *File:* .</span><span class="sxs-lookup"><span data-stu-id="d1a4d-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="d1a4d-109">Pokud potřebujete nastavit nebo číst vlastnosti specifické pro protokol, musíte přetypovat <xref:System.Net.WebRequest> objekt nebo <xref:System.Net.WebResponse> na typ objektu specifický pro protokol.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="d1a4d-110">Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="d1a4d-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="d1a4d-111">Nastavte všechny hodnoty vlastností, které v `WebRequest` objektu potřebujete.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="d1a4d-112">Chcete-li například povolit ověřování, nastavte <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> vlastnost na instanci <xref:System.Net.NetworkCredential> třídy:</span><span class="sxs-lookup"><span data-stu-id="d1a4d-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="d1a4d-113">Odešle požadavek na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-113">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d1a4d-114">Tato metoda vrátí objekt obsahující odpověď serveru.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-114">This method returns an object containing the server's response.</span></span> <span data-ttu-id="d1a4d-115">Typ vráceného <xref:System.Net.WebResponse> objektu je určen schématem identifikátoru URI žádosti.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-115">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="d1a4d-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d1a4d-116">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="d1a4d-117">Můžete získat přístup k vlastnostem `WebResponse` objektu nebo ho přetypovat na instanci specifickou pro protokol pro čtení vlastností specifických pro protokol.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-117">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="d1a4d-118">Chcete-li například získat přístup k vlastnostem <xref:System.Net.HttpWebResponse>specifickým pro protokol HTTP, `WebResponse` přetypování `HttpWebResponse` objektu na odkaz.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-118">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="d1a4d-119">Následující příklad kódu ukazuje, jak zobrazit vlastnost specifickou <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> pro protokol HTTP odeslanou odpovědí:</span><span class="sxs-lookup"><span data-stu-id="d1a4d-119">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="d1a4d-120">Chcete-li získat datový proud obsahující data odpovědí odesílaná serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-120">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d1a4d-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d1a4d-121">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="d1a4d-122">Po načtení dat z objektu Response ho buď zavřete, a to pomocí <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody, nebo zavřete datový proud odpovědi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> s metodou.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-122">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d1a4d-123">Pokud nezavřete objekt Response nebo datový proud, může vaše aplikace vysílat připojení k serveru a nebude možné zpracovat další požadavky.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-123">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="d1a4d-124">Vzhledem k tomu, `Stream.Close` že `Close` metodavolá,kdyžjeodpověďzavřená,nenínutnévolatnaobjektyResponseaStream,ikdyžtaknebudete`WebResponse.Close` mít škodlivou.</span><span class="sxs-lookup"><span data-stu-id="d1a4d-124">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="d1a4d-125">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d1a4d-125">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="d1a4d-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1a4d-126">Example</span></span>

<span data-ttu-id="d1a4d-127">Následující příklad kódu ukazuje, jak vytvořit požadavek na webový server a jak číst data v odpovědi:</span><span class="sxs-lookup"><span data-stu-id="d1a4d-127">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="d1a4d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1a4d-128">See also</span></span>

- [<span data-ttu-id="d1a4d-129">Vytváření internetových požadavků</span><span class="sxs-lookup"><span data-stu-id="d1a4d-129">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="d1a4d-130">Použití datových proudů v síti</span><span class="sxs-lookup"><span data-stu-id="d1a4d-130">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="d1a4d-131">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="d1a4d-131">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="d1a4d-132">Vyžádání dat</span><span class="sxs-lookup"><span data-stu-id="d1a4d-132">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="d1a4d-133">Postupy: Odeslání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="d1a4d-133">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
