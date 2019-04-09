---
title: 'Postupy: Data žádosti pomocí třídy WebRequest'
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
ms.openlocfilehash: 0a2d60a31b1875d948e07615e1613e2b163c15b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171051"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="6774a-102">Postupy: Data žádosti pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="6774a-102">How to: Request data by using the WebRequest class</span></span>
<span data-ttu-id="6774a-103">Následující postup popisuje kroky pro žádost o prostředek, například webovou stránku nebo soubor, ze serveru.</span><span class="sxs-lookup"><span data-stu-id="6774a-103">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="6774a-104">Prostředek musí být označeny identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="6774a-104">The resource must be identified by a URI.</span></span>  
  
## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="6774a-105">Žádost o data z hostitelského serveru</span><span class="sxs-lookup"><span data-stu-id="6774a-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="6774a-106">Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku.</span><span class="sxs-lookup"><span data-stu-id="6774a-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="6774a-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6774a-107">For example:</span></span> 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="6774a-108">Rozhraní .NET Framework poskytuje konkrétní třídy odvozené od <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy pro identifikátory URI, které začínají *http:*, *https:*, *ftp:* , a *souboru:*.</span><span class="sxs-lookup"><span data-stu-id="6774a-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>
    <span data-ttu-id="6774a-109">Pokud je potřeba sada nebo čtení vlastnosti specifické pro protokol, musíte přetypovat vaše <xref:System.Net.WebRequest> nebo <xref:System.Net.WebResponse> objektu na typ object specifický pro protokol.</span><span class="sxs-lookup"><span data-stu-id="6774a-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="6774a-110">Další informace najdete v tématu [programování připojitelných protokolů](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="6774a-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span> 
  
2.  <span data-ttu-id="6774a-111">Nastavte všechny hodnoty vlastností, které potřebujete ve vaší `WebRequest` objektu.</span><span class="sxs-lookup"><span data-stu-id="6774a-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="6774a-112">Například chcete-li povolit ověřování, nastavte <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> vlastnost instance <xref:System.Net.NetworkCredential> třídy:</span><span class="sxs-lookup"><span data-stu-id="6774a-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  <span data-ttu-id="6774a-113">Odesílání požadavku na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6774a-113">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6774a-114">Tato metoda vrátí objekt, který obsahuje odpověď serveru.</span><span class="sxs-lookup"><span data-stu-id="6774a-114">This method returns an object containing the server's response.</span></span> <span data-ttu-id="6774a-115">Vrácený <xref:System.Net.WebResponse> typ objektu je určeno schéma identifikátoru URI požadavku.</span><span class="sxs-lookup"><span data-stu-id="6774a-115">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="6774a-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6774a-116">For example:</span></span>
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
4.  <span data-ttu-id="6774a-117">Můžete přistupovat k vlastnosti vaší `WebResponse` objektu nebo přetypování na konkrétní instanci číst vlastnosti specifické pro protokol.</span><span class="sxs-lookup"><span data-stu-id="6774a-117">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span> 

    <span data-ttu-id="6774a-118">Například pro přístup k protokolu HTTP specifické vlastnostem <xref:System.Net.HttpWebResponse>, vícesměrového vysílání vaše `WebResponse` objektu `HttpWebResponse` odkaz.</span><span class="sxs-lookup"><span data-stu-id="6774a-118">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="6774a-119">Následující příklad kódu ukazuje, jak zobrazit konkrétní HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> vlastnost odeslaných odpovědí:</span><span class="sxs-lookup"><span data-stu-id="6774a-119">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="6774a-120">Chcete-li získat datový proud s daty odpověď odesílanou serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6774a-120">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6774a-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6774a-121">For example:</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="6774a-122">Po přečtení dat z objektu odpovědi, buď ji zavřít <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody nebo zavřít pomocí datového proudu odpovědi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="6774a-122">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6774a-123">Nezavírejte objektu odpovědi nebo datový proud, může vaše aplikace vyčerpala volné připojení k serveru nebo stát nemůže zpracovat požadavky.</span><span class="sxs-lookup"><span data-stu-id="6774a-123">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="6774a-124">Protože `WebResponse.Close` volání metody `Stream.Close` když se toto okno zavře odpověď, není nutné volat `Close` na objekty odpovědi i datový proud, i když to není tak škodlivé.</span><span class="sxs-lookup"><span data-stu-id="6774a-124">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="6774a-125">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6774a-125">For example:</span></span>
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="6774a-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="6774a-126">Example</span></span>  

<span data-ttu-id="6774a-127">Následující příklad kódu ukazuje, jak vytvořit požadavek na webový server a načtěte data v odpovědi:</span><span class="sxs-lookup"><span data-stu-id="6774a-127">The following code example shows how to create a request to a web server and read the data in its response:</span></span>  
  
[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="6774a-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6774a-128">See also</span></span>

- [<span data-ttu-id="6774a-129">Vytváření internetových žádostí</span><span class="sxs-lookup"><span data-stu-id="6774a-129">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="6774a-130">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="6774a-130">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="6774a-131">Přístup k Internetu prostřednictvím proxy serveru</span><span class="sxs-lookup"><span data-stu-id="6774a-131">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="6774a-132">Požadavek na data</span><span class="sxs-lookup"><span data-stu-id="6774a-132">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="6774a-133">Postupy: Odesílání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="6774a-133">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
