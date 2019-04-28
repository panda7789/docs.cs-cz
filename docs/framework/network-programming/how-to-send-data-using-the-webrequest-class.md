---
title: 'Postupy: Odesílání dat pomocí třídy WebRequest'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 3878a94debc7066cb8ace3b119d95d3b76d91610
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642500"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="abb4b-102">Postupy: Odesílání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="abb4b-102">How to: Send data by using the WebRequest class</span></span>
<span data-ttu-id="abb4b-103">Následující postup popisuje kroky k odesílání dat na server.</span><span class="sxs-lookup"><span data-stu-id="abb4b-103">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="abb4b-104">Tento postup se běžně používá k odesílání dat na webovou stránku.</span><span class="sxs-lookup"><span data-stu-id="abb4b-104">This procedure is commonly used to post data to a Web page.</span></span> 
  
## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="abb4b-105">K odesílání dat na hostitelský server</span><span class="sxs-lookup"><span data-stu-id="abb4b-105">To send data to a host server</span></span>  
  
1. <span data-ttu-id="abb4b-106">Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku, jako je skript nebo stránky ASP.NET, která přijímá data.</span><span class="sxs-lookup"><span data-stu-id="abb4b-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="abb4b-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="abb4b-107">For example:</span></span> 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="abb4b-108">Rozhraní .NET Framework poskytuje konkrétní třídy odvozené od <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy pro identifikátory URI, které začínají *http:*, *https:*, *ftp:* , a *souboru:*.</span><span class="sxs-lookup"><span data-stu-id="abb4b-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>
    <span data-ttu-id="abb4b-109">Pokud je potřeba sada nebo čtení vlastnosti specifické pro protokol, musíte přetypovat vaše <xref:System.Net.WebRequest> nebo <xref:System.Net.WebResponse> objektu na typ object specifický pro protokol.</span><span class="sxs-lookup"><span data-stu-id="abb4b-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="abb4b-110">Další informace najdete v tématu [programování připojitelných protokolů](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="abb4b-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span> 
  
2. <span data-ttu-id="abb4b-111">Nastavte všechny hodnoty vlastností, které potřebujete ve vaší `WebRequest` objektu.</span><span class="sxs-lookup"><span data-stu-id="abb4b-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="abb4b-112">Například chcete-li povolit ověřování, nastavte <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> vlastnost instance <xref:System.Net.NetworkCredential> třídy:</span><span class="sxs-lookup"><span data-stu-id="abb4b-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3. <span data-ttu-id="abb4b-113">Zadejte metodu protokolu, která povoluje ukládání dat k odeslání požadavku, jako je například HTTP `POST` metody:</span><span class="sxs-lookup"><span data-stu-id="abb4b-113">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4. <span data-ttu-id="abb4b-114">Nastavte <xref:System.Web.HttpRequest.ContentLength> na počet bajtů zahrnutí při zpracování požadavku.</span><span class="sxs-lookup"><span data-stu-id="abb4b-114">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="abb4b-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="abb4b-115">For example:</span></span> 
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5. <span data-ttu-id="abb4b-116">Nastavte <xref:System.Web.HttpRequest.ContentType> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="abb4b-116">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="abb4b-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="abb4b-117">For example:</span></span>
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6. <span data-ttu-id="abb4b-118">Získání datového proudu, obsahuje data žádosti voláním <xref:System.Net.WebRequest.GetRequestStream%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="abb4b-118">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="abb4b-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="abb4b-119">For example:</span></span>
  
    ```csharp  
    Stream dataStream = request.GetRequestStream();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream()  
    ```  
  
7. <span data-ttu-id="abb4b-120">Zapsat data do <xref:System.IO.Stream> vrácený `GetRequestStream` metody.</span><span class="sxs-lookup"><span data-stu-id="abb4b-120">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="abb4b-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="abb4b-121">For example:</span></span>
  
    ```csharp  
    dataStream.Write(byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write(byteArray, 0, byteArray.Length)  
    ```  
  
8. <span data-ttu-id="abb4b-122">Zavřete datový proud požadavku voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="abb4b-122">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="abb4b-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="abb4b-123">For example:</span></span>
  
    ```csharp  
    dataStream.Close();  
    ```  
  
    ```vb  
    dataStream.Close()  
    ```  
  
9. <span data-ttu-id="abb4b-124">Odesílání požadavku na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="abb4b-124">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="abb4b-125">Tato metoda vrátí objekt, který obsahuje odpověď serveru.</span><span class="sxs-lookup"><span data-stu-id="abb4b-125">This method returns an object containing the server's response.</span></span> <span data-ttu-id="abb4b-126">Vrácený `WebResponse` typ objektu je určeno schéma identifikátoru URI požadavku.</span><span class="sxs-lookup"><span data-stu-id="abb4b-126">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="abb4b-127">Příklad:</span><span class="sxs-lookup"><span data-stu-id="abb4b-127">For example:</span></span>
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
10. <span data-ttu-id="abb4b-128">Můžete přistupovat k vlastnosti vaší `WebResponse` objektu nebo přetypování na konkrétní instanci číst vlastnosti specifické pro protokol.</span><span class="sxs-lookup"><span data-stu-id="abb4b-128">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span> 

    <span data-ttu-id="abb4b-129">Například pro přístup k protokolu HTTP specifické vlastnostem <xref:System.Net.HttpWebResponse>, vícesměrového vysílání vaše `WebResponse` objektu <xref:System.Net.HttpWebResponse> odkaz.</span><span class="sxs-lookup"><span data-stu-id="abb4b-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="abb4b-130">Následující příklad kódu ukazuje, jak zobrazit konkrétní HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> vlastnost odeslaných odpovědí:</span><span class="sxs-lookup"><span data-stu-id="abb4b-130">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>
  
    ```csharp  
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);    
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. <span data-ttu-id="abb4b-131">Chcete-li získat datový proud s daty odpověď odesílanou serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodu vaše `WebResponse` objektu.</span><span class="sxs-lookup"><span data-stu-id="abb4b-131">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="abb4b-132">Příklad:</span><span class="sxs-lookup"><span data-stu-id="abb4b-132">For example:</span></span>
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
12. <span data-ttu-id="abb4b-133">Po přečtení dat z objektu odpovědi, buď ji zavřít <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody nebo zavřít pomocí datového proudu odpovědi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="abb4b-133">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="abb4b-134">Nezavírejte odpovědi nebo datový proud, může vaše aplikace vyčerpala volné připojení k serveru nebo stát nemůže zpracovat požadavky.</span><span class="sxs-lookup"><span data-stu-id="abb4b-134">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="abb4b-135">Protože `WebResponse.Close` volání metody `Stream.Close` když se toto okno zavře odpověď, není nutné volat `Close` na objekty odpovědi i datový proud, i když to není tak škodlivé.</span><span class="sxs-lookup"><span data-stu-id="abb4b-135">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="abb4b-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="abb4b-136">For example:</span></span>
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="abb4b-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="abb4b-137">Example</span></span>  
  
<span data-ttu-id="abb4b-138">Následující příklad kódu ukazuje, jak odesílat data do webového serveru a tato data číst v odpovědi:</span><span class="sxs-lookup"><span data-stu-id="abb4b-138">The following code example shows how to send data to a web server and read the data in its response:</span></span>  

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="abb4b-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abb4b-139">See also</span></span>

- [<span data-ttu-id="abb4b-140">Vytváření internetových žádostí</span><span class="sxs-lookup"><span data-stu-id="abb4b-140">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="abb4b-141">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="abb4b-141">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="abb4b-142">Přístup k Internetu prostřednictvím proxy serveru</span><span class="sxs-lookup"><span data-stu-id="abb4b-142">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="abb4b-143">Požadavek na data</span><span class="sxs-lookup"><span data-stu-id="abb4b-143">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="abb4b-144">Postupy: Data žádosti pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="abb4b-144">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
