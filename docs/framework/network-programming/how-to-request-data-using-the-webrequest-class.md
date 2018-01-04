---
title: "Postupy: použití třídy WebRequest Data žádosti"
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
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bd714a9e006f87a817ca931757aaaaed920f50f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-request-data-using-the-webrequest-class"></a><span data-ttu-id="8ddf1-102">Postupy: použití třídy WebRequest Data žádosti</span><span class="sxs-lookup"><span data-stu-id="8ddf1-102">How to: Request Data Using the WebRequest Class</span></span>
<span data-ttu-id="8ddf1-103">Následující postup popisuje kroky, které slouží k vyžádání prostředku ze serveru, například, webovou stránku nebo soubor.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-103">The following procedure describes the steps used to request a resource from a server, for example, a Web page or file.</span></span> <span data-ttu-id="8ddf1-104">Prostředek musí být identifikovaného identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-104">The resource must be identified by a URI.</span></span>  
  
### <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="8ddf1-105">Žádost o data ze serveru hostitele</span><span class="sxs-lookup"><span data-stu-id="8ddf1-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="8ddf1-106">Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A> s identifikátorem URI prostředku.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8ddf1-107">Rozhraní .NET Framework poskytuje specifické třídy odvozené od **WebRequest** a **WebResponse** pro identifikátory URI, který začíná "http:", "https:", "ftp:", a "souboru:".</span><span class="sxs-lookup"><span data-stu-id="8ddf1-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="8ddf1-108">Přístup k prostředkům pomocí jiné protokoly, je nutné implementovat specifické třídy, které jsou odvozeny od **WebRequest** a **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="8ddf1-109">Další informace najdete v tématu [programování modulární protokoly](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span><span class="sxs-lookup"><span data-stu-id="8ddf1-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="8ddf1-110">Nastavit všechny hodnoty vlastností, které potřebujete ve **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="8ddf1-111">Například pokud chcete povolit ověřování, nastavit **pověření** vlastnost, která má instance <xref:System.Net.NetworkCredential> – třída.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="8ddf1-112">Ve většině případů **WebRequest** třída je dostatečná přijímat data.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-112">In most cases, the **WebRequest** class is sufficient to receive data.</span></span> <span data-ttu-id="8ddf1-113">Ale pokud je nutné nastavit vlastnosti specifické pro protokol, musíte vysílat **WebRequest** specifické pro protokol typu.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="8ddf1-114">Například pro přístup k protokolu HTTP specifické vlastnosti <xref:System.Net.HttpWebRequest>, vícesměrového vysílání **WebRequest** k **HttpWebRequest** odkaz.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="8ddf1-115">Následující příklad kódu ukazuje, jak nastavit HTTP specifické <xref:System.Net.HttpWebRequest.UserAgent%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="8ddf1-116">Odeslat požadavek na server, volání <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-116">To send the request to the server, call <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="8ddf1-117">Skutečný typ vrácený **WebResponse** objektu je dáno schéma požadovaný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-117">The actual type of the returned **WebResponse** object is determined by the scheme of the requested URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8ddf1-118">Po dokončení <xref:System.Net.WebResponse> objekt, je třeba nejprve zavřít voláním <xref:System.Net.WebResponse.Close%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-118">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="8ddf1-119">Případně, pokud budete mít, že podmínky datového proudu odpovědi z objektu odpovědi, můžete zavřít datový proud voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-119">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8ddf1-120">Pokud nezavřete odpovědi nebo datový proud, aplikace můžete spustit z připojení k serveru a stát se nepodařilo zpracovat další požadavky.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-120">If you do not close either the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
4.  <span data-ttu-id="8ddf1-121">Můžete přístup k vlastnostem **WebResponse** nebo přetypovat **WebResponse** do instance specifické pro protokol číst vlastnosti specifické pro protokol.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-121">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="8ddf1-122">Například pro přístup k protokolu HTTP specifické vlastnosti <xref:System.Net.HttpWebResponse>, vícesměrového vysílání **WebResponse** k **HttpWebResponse** odkaz.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-122">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to a **HttpWebResponse** reference.</span></span> <span data-ttu-id="8ddf1-123">Následující příklad kódu ukazuje, jak zobrazit informace o stavu odeslané s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-123">The following code example shows how to display the status information sent with a response.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="8ddf1-124">Datový proud obsahující data odpověď odeslaná na server, použijte <xref:System.Net.HttpWebResponse.GetResponseStream%2A> metodu **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-124">To get the stream containing response data sent by the server, use the <xref:System.Net.HttpWebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream ();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="8ddf1-125">Po načtení dat z odpovědi, je nutné buď zavřít pomocí datového proudu odpovědi **Stream.Close** metoda nebo zavřít pomocí odpovědi **WebResponse.Close** metoda.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-125">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="8ddf1-126">Není nutné volat **Zavřít** metodu proudu odpovědi a **WebResponse**, ale to tak není škodlivý.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-126">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span> <span data-ttu-id="8ddf1-127">**WebResponse.Close** volání **Stream.Close** při zavření odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8ddf1-127">**WebResponse.Close** calls **Stream.Close** when closing the response.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="8ddf1-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ddf1-128">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create (  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close ();  
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
  
## <a name="see-also"></a><span data-ttu-id="8ddf1-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ddf1-129">See Also</span></span>  
 [<span data-ttu-id="8ddf1-130">Vytváření internetových žádostí</span><span class="sxs-lookup"><span data-stu-id="8ddf1-130">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="8ddf1-131">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="8ddf1-131">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="8ddf1-132">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="8ddf1-132">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="8ddf1-133">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="8ddf1-133">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="8ddf1-134">Postupy:Odeslání dat pomocí třídy WebRequest</span><span class="sxs-lookup"><span data-stu-id="8ddf1-134">How to: Send Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
