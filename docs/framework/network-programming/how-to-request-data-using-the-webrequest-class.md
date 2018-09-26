---
title: 'Postupy: vyžádání dat pomocí třídy WebRequest'
ms.date: 03/30/2017
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8928ce8790f58b6920c16cbfd9fc8d9aa6644a44
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075408"
---
# <a name="how-to-request-data-using-the-webrequest-class"></a><span data-ttu-id="091d7-102">Postupy: vyžádání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="091d7-102">How to: Request Data Using the WebRequest Class</span></span>
<span data-ttu-id="091d7-103">Následující postup popisuje kroky používaná pro požádání o prostředku ze serveru, například webovou stránku nebo soubor.</span><span class="sxs-lookup"><span data-stu-id="091d7-103">The following procedure describes the steps used to request a resource from a server, for example, a Web page or file.</span></span> <span data-ttu-id="091d7-104">Prostředek musí být označeny identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="091d7-104">The resource must be identified by a URI.</span></span>  
  
### <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="091d7-105">Žádost o data z hostitelského serveru</span><span class="sxs-lookup"><span data-stu-id="091d7-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="091d7-106">Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A> s identifikátorem URI prostředku.</span><span class="sxs-lookup"><span data-stu-id="091d7-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="091d7-107">Rozhraní .NET Framework poskytuje třídy pro konkrétní odvozený z **WebRequest** a **WebResponse** pro identifikátory URI, které začínají řetězcem "http:", "protokol https:", "ftp:", a "souboru:".</span><span class="sxs-lookup"><span data-stu-id="091d7-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="091d7-108">Přístup k prostředkům prostřednictvím jiné protokoly, je nutné implementovat, které jsou odvozeny z třídy pro konkrétní **WebRequest** a **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="091d7-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="091d7-109">Další informace najdete v tématu [programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span><span class="sxs-lookup"><span data-stu-id="091d7-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="091d7-110">Nastavte všechny hodnoty vlastností, které budete potřebovat v **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="091d7-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="091d7-111">Například chcete-li povolit ověřování, nastavte **pověření** vlastnost instance <xref:System.Net.NetworkCredential> třídy.</span><span class="sxs-lookup"><span data-stu-id="091d7-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="091d7-112">Ve většině případů **WebRequest** třídy je dostačující přijímat data.</span><span class="sxs-lookup"><span data-stu-id="091d7-112">In most cases, the **WebRequest** class is sufficient to receive data.</span></span> <span data-ttu-id="091d7-113">Nicméně, pokud je potřeba nastavit vlastnosti specifické pro protokol, musíte přetypovat **WebRequest** na konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="091d7-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="091d7-114">Například pro přístup k protokolu HTTP specifické vlastnostem <xref:System.Net.HttpWebRequest>, vícesměrového vysílání **WebRequest** do **HttpWebRequest** odkaz.</span><span class="sxs-lookup"><span data-stu-id="091d7-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="091d7-115">Následující příklad kódu ukazuje, jak nastavit konkrétní HTTP <xref:System.Net.HttpWebRequest.UserAgent%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="091d7-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="091d7-116">Chcete-li odeslat požadavek na server, zavolejte <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="091d7-116">To send the request to the server, call <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="091d7-117">Skutečný typ vrácený **WebResponse** objektu se určuje podle schématu požadovaný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="091d7-117">The actual type of the returned **WebResponse** object is determined by the scheme of the requested URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="091d7-118">Po dokončení <xref:System.Net.WebResponse> objektu, je nutné zavřít voláním <xref:System.Net.WebResponse.Close%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="091d7-118">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="091d7-119">Případně, pokud datový proud odpovědí jste získali z objektu odpovědi, můžete zavřít datový proud voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="091d7-119">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="091d7-120">Pokud instalací neukončíte odpovědi nebo datový proud, může vaše aplikace vyčerpala volné připojení k serveru nebo budou moct zpracovávat další požadavky.</span><span class="sxs-lookup"><span data-stu-id="091d7-120">If you do not close either the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
4.  <span data-ttu-id="091d7-121">Můžete přístup k vlastnostem **WebResponse** nebo přetypovat **WebResponse** na konkrétní instanci číst vlastnosti specifické pro protokol.</span><span class="sxs-lookup"><span data-stu-id="091d7-121">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="091d7-122">Například pro přístup k protokolu HTTP specifické vlastnostem <xref:System.Net.HttpWebResponse>, vícesměrového vysílání **WebResponse** k **HttpWebResponse** odkaz.</span><span class="sxs-lookup"><span data-stu-id="091d7-122">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to a **HttpWebResponse** reference.</span></span> <span data-ttu-id="091d7-123">Následující příklad kódu ukazuje, jak zobrazit informace o stavu odeslaných odpovědí.</span><span class="sxs-lookup"><span data-stu-id="091d7-123">The following code example shows how to display the status information sent with a response.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="091d7-124">Chcete-li získat datový proud s daty odpověď odesílanou serverem, použijte <xref:System.Net.HttpWebResponse.GetResponseStream%2A> metodu **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="091d7-124">To get the stream containing response data sent by the server, use the <xref:System.Net.HttpWebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="091d7-125">Po načtení dat z odpovědi, musíte buď zavřít pomocí datového proudu odpovědi **Stream.Close** metody nebo Zavřít odpověď pomocí **WebResponse.Close** metody.</span><span class="sxs-lookup"><span data-stu-id="091d7-125">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="091d7-126">Není nutné volat **Zavřít** metoda u datového proudu s odpovědí a **WebResponse**, ale to uděláte tak, není škodlivé.</span><span class="sxs-lookup"><span data-stu-id="091d7-126">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span> <span data-ttu-id="091d7-127">**WebResponse.Close** volání **Stream.Close** při zavření odpovědi.</span><span class="sxs-lookup"><span data-stu-id="091d7-127">**WebResponse.Close** calls **Stream.Close** when closing the response.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="091d7-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="091d7-128">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create(  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close();  
            response.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  
Namespace Examples.System.Net  
    Public Class WebRequestGetExample  
  
        Public Shared Sub Main()  
            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams and the response.  
            reader.Close()  
            response.Close()  
        End Sub   
    End Class   
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="091d7-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="091d7-129">See Also</span></span>  
 [<span data-ttu-id="091d7-130">Vytváření internetových žádostí</span><span class="sxs-lookup"><span data-stu-id="091d7-130">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="091d7-131">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="091d7-131">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="091d7-132">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="091d7-132">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="091d7-133">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="091d7-133">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="091d7-134">Postupy:Odeslání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="091d7-134">How to: Send Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
