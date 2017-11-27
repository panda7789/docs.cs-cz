---
title: "Postupy: odesílání dat pomocí třídy WebRequest"
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
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2102fce150f512a49093eb2b214258ac35e276e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-send-data-using-the-webrequest-class"></a><span data-ttu-id="f4274-102">Postupy: odesílání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="f4274-102">How to: Send Data Using the WebRequest Class</span></span>
<span data-ttu-id="f4274-103">Následující postup popisuje kroky, které používají k odesílání dat na server.</span><span class="sxs-lookup"><span data-stu-id="f4274-103">The following procedure describes the steps used to send data to a server.</span></span> <span data-ttu-id="f4274-104">Tento postup se běžně používá k odesílání dat na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="f4274-104">This procedure is commonly used to post data to a Web page.</span></span>  
  
### <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="f4274-105">Odesílání dat na server hostitele</span><span class="sxs-lookup"><span data-stu-id="f4274-105">To send data to a host server</span></span>  
  
1.  <span data-ttu-id="f4274-106">Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A> s identifikátorem URI prostředku, který přijímá data, například, skript nebo stránku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f4274-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource that accepts data, for example, a script or ASP.NET page.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f4274-107">Rozhraní .NET Framework poskytuje specifické třídy odvozené od **WebRequest** a **WebResponse** pro identifikátory URI, který začíná "http:", "https:", "ftp:", a "souboru:".</span><span class="sxs-lookup"><span data-stu-id="f4274-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="f4274-108">Přístup k prostředkům pomocí jiné protokoly, je nutné implementovat specifické třídy, které jsou odvozeny od **WebRequest** a **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="f4274-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="f4274-109">Další informace najdete v tématu [programování modulární protokoly](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span><span class="sxs-lookup"><span data-stu-id="f4274-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="f4274-110">Nastavit všechny hodnoty vlastností, které potřebujete ve **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="f4274-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="f4274-111">Například pokud chcete povolit ověřování, nastavit **pověření** vlastnost, která má instance <xref:System.Net.NetworkCredential> – třída.</span><span class="sxs-lookup"><span data-stu-id="f4274-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="f4274-112">Ve většině případů **WebRequest** k odesílání dat stačí samotná instance.</span><span class="sxs-lookup"><span data-stu-id="f4274-112">In most cases, the **WebRequest** instance itself is sufficient to send data.</span></span> <span data-ttu-id="f4274-113">Ale pokud je nutné nastavit vlastnosti specifické pro protokol, musíte vysílat **WebRequest** specifické pro protokol typu.</span><span class="sxs-lookup"><span data-stu-id="f4274-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="f4274-114">Například pro přístup k protokolu HTTP specifické vlastnosti <xref:System.Net.HttpWebRequest>, vícesměrového vysílání **WebRequest** k **HttpWebRequest** odkaz.</span><span class="sxs-lookup"><span data-stu-id="f4274-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="f4274-115">Následující příklad kódu ukazuje, jak nastavit HTTP specifické <xref:System.Net.HttpWebRequest.UserAgent%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f4274-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="f4274-116">Zadejte metodu protokolu, která umožňuje data k odeslání s žádostí, jako je například HTTP **POST** metoda.</span><span class="sxs-lookup"><span data-stu-id="f4274-116">Specify a protocol method that permits data to be sent with a request, such as the HTTP **POST** method.</span></span>  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  <span data-ttu-id="f4274-117">Nastavte **ContentLength** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f4274-117">Set the **ContentLength** property.</span></span>  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  <span data-ttu-id="f4274-118">Nastavte **ContentType** vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f4274-118">Set the **ContentType** property to an appropriate value.</span></span>  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <span data-ttu-id="f4274-119">Get datového proudu, že data žádosti blokování voláním <xref:System.Net.WebRequest.GetRequestStream%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f4274-119">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span>  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  <span data-ttu-id="f4274-120">Zapsat data do <xref:System.IO.Stream> objekt vrácená touto metodou.</span><span class="sxs-lookup"><span data-stu-id="f4274-120">Write the data to the <xref:System.IO.Stream> object returned by this method.</span></span>  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  <span data-ttu-id="f4274-121">Zavřít datový proud požadavku voláním **Stream.Close** metoda.</span><span class="sxs-lookup"><span data-stu-id="f4274-121">Close the request stream by calling the **Stream.Close** method.</span></span>  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. <span data-ttu-id="f4274-122">Odeslat požadavek na server voláním <xref:System.Net.WebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="f4274-122">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="f4274-123">Tato metoda vrátí objekt, který obsahuje odpověď serveru.</span><span class="sxs-lookup"><span data-stu-id="f4274-123">This method returns an object containing the server's response.</span></span> <span data-ttu-id="f4274-124">Vrácený <xref:System.Net.WebResponse> typ objektu je dáno schéma identifikátoru URI žádosti.</span><span class="sxs-lookup"><span data-stu-id="f4274-124">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f4274-125">Po dokončení <xref:System.Net.WebResponse> objekt, je třeba nejprve zavřít voláním <xref:System.Net.WebResponse.Close%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f4274-125">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="f4274-126">Případně, pokud budete mít, že podmínky datového proudu odpovědi z objektu odpovědi, můžete zavřít datový proud voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="f4274-126">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f4274-127">Pokud nezavřete odpovědi nebo datový proud, aplikace můžete spustit z připojení k serveru a stát se nepodařilo zpracovat další požadavky.</span><span class="sxs-lookup"><span data-stu-id="f4274-127">If you do not close the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
10. <span data-ttu-id="f4274-128">Můžete přístup k vlastnostem **WebResponse** nebo přetypovat **WebResponse** do instance specifické pro protokol číst vlastnosti specifické pro protokol.</span><span class="sxs-lookup"><span data-stu-id="f4274-128">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="f4274-129">Například pro přístup k protokolu HTTP specifické vlastnosti <xref:System.Net.HttpWebResponse>, vícesměrového vysílání **WebResponse** k **HttpWebResponse** odkaz.</span><span class="sxs-lookup"><span data-stu-id="f4274-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to an **HttpWebResponse** reference.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. <span data-ttu-id="f4274-130">Chcete-li získat datový proud obsahující data odpověď odesílanou serverem, volejte <xref:System.Net.WebResponse.GetResponseStream%2A> metodu **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="f4274-130">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. <span data-ttu-id="f4274-131">Po načtení dat z odpovědi, je nutné buď zavřít pomocí datového proudu odpovědi **Stream.Close** metoda nebo zavřít pomocí odpovědi **WebResponse.Close** metoda.</span><span class="sxs-lookup"><span data-stu-id="f4274-131">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="f4274-132">Není nutné volat **Zavřít** metodu proudu odpovědi a **WebResponse**, ale to tak není škodlivý.</span><span class="sxs-lookup"><span data-stu-id="f4274-132">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="f4274-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4274-133">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestPostExample  
    {  
        public static void Main ()  
        {  
            // Create a request using a URL that can receive a post.   
            WebRequest request = WebRequest.Create ("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  
            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes (postData);  
            // Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length;  
            // Get the request stream.  
            Stream dataStream = request.GetRequestStream ();  
            // Write the data to the request stream.  
            dataStream.Write (byteArray, 0, byteArray.Length);  
            // Close the Stream object.  
            dataStream.Close ();  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams.  
            reader.Close ();  
            dataStream.Close ();  
            response.Close ();  
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
    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  
            ' Create a request using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  
            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  
            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  
            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the Stream object.  
            dataStream.Close()  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams.  
            reader.Close()  
            dataStream.Close()  
            response.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4274-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4274-134">See Also</span></span>  
 [<span data-ttu-id="f4274-135">Vytváření žádostí o Internetu</span><span class="sxs-lookup"><span data-stu-id="f4274-135">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="f4274-136">Pomocí datových proudů v síti</span><span class="sxs-lookup"><span data-stu-id="f4274-136">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="f4274-137">Přístup k Internetu prostřednictvím proxy serveru</span><span class="sxs-lookup"><span data-stu-id="f4274-137">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="f4274-138">Požadavek na Data</span><span class="sxs-lookup"><span data-stu-id="f4274-138">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="f4274-139">Postupy: použití třídy WebRequest Data žádosti</span><span class="sxs-lookup"><span data-stu-id="f4274-139">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
