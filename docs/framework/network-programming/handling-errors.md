---
title: Zpracování chyb
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, WebRequest and WebResponse classes exceptions
- Status property
- WebExceptions class, about WebExceptions class
- Timeout enumeration member
- ConnectFailure enumeration member
- TrustFailure enumeration member
- WebRequest class, exceptions
- requesting data from Internet, error handling
- Success enumeration member
- receiving data, errors
- ProtocolError enumeration member
- downloading Internet resources, error handling
- WebResponse class, exceptions
- SendFailure enumeration member
- errors [.NET Framework], WebRequest and WebResponse classes exceptions
- sending data, errors
- response to Internet request, error handling
- NameResolutionFailure enumeration member
- KeepAliveFailure enumeration member
- network resources, WebRequest and WebResponse classes exceptions
- RequestCanceled enumeration member
- ReceiveFailure enumeration member
- ServerProtocolViolation enumeration member
- ConnectionClosed enumeration member
- SecureChannelFailure enumeration member
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
ms.openlocfilehash: 26e2a25855485bdd19d30e8497d0f75b7d4432e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642721"
---
# <a name="handling-errors"></a><span data-ttu-id="e4d38-102">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="e4d38-102">Handling Errors</span></span>
<span data-ttu-id="e4d38-103"><xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy vyvolávat výjimky i systému (například <xref:System.ArgumentException>) a výjimky pro konkrétní Web (které jsou <xref:System.Net.WebException> vyvolané <xref:System.Net.WebRequest.GetResponse%2A> – metoda).</span><span class="sxs-lookup"><span data-stu-id="e4d38-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
 <span data-ttu-id="e4d38-104">Každý **o výjimku WebException** zahrnuje <xref:System.Net.WebException.Status%2A> vlastnost, která obsahuje hodnoty z <xref:System.Net.WebExceptionStatus> výčtu.</span><span class="sxs-lookup"><span data-stu-id="e4d38-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="e4d38-105">Můžete zkontrolovat **stav** vlastnost zjistit chyby, ke které došlo k chybě a správné kroky k vyřešení chyby.</span><span class="sxs-lookup"><span data-stu-id="e4d38-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
 <span data-ttu-id="e4d38-106">Následující tabulka popisuje možné hodnoty pro **stav** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e4d38-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="e4d38-107">Stav</span><span class="sxs-lookup"><span data-stu-id="e4d38-107">Status</span></span>|<span data-ttu-id="e4d38-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e4d38-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e4d38-109">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="e4d38-109">ConnectFailure</span></span>|<span data-ttu-id="e4d38-110">Vzdálenou službu nešlo kontaktovat na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="e4d38-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="e4d38-111">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="e4d38-111">ConnectionClosed</span></span>|<span data-ttu-id="e4d38-112">Připojení bylo předčasně ukončeno.</span><span class="sxs-lookup"><span data-stu-id="e4d38-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="e4d38-113">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="e4d38-113">KeepAliveFailure</span></span>|<span data-ttu-id="e4d38-114">Server uzavřel připojení vytvořené pomocí sady hlavičky Keep-alive.</span><span class="sxs-lookup"><span data-stu-id="e4d38-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="e4d38-115">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="e4d38-115">NameResolutionFailure</span></span>|<span data-ttu-id="e4d38-116">Název služby nešlo přeložit název hostitele.</span><span class="sxs-lookup"><span data-stu-id="e4d38-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="e4d38-117">Požadavku</span><span class="sxs-lookup"><span data-stu-id="e4d38-117">ProtocolError</span></span>|<span data-ttu-id="e4d38-118">Odpověď přijatou ze serveru byl dokončen, ale uvedené chybě na úrovni protokolu.</span><span class="sxs-lookup"><span data-stu-id="e4d38-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="e4d38-119">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="e4d38-119">ReceiveFailure</span></span>|<span data-ttu-id="e4d38-120">Úplnou odpověď nebyla přijata ze vzdáleného serveru.</span><span class="sxs-lookup"><span data-stu-id="e4d38-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="e4d38-121">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="e4d38-121">RequestCanceled</span></span>|<span data-ttu-id="e4d38-122">Požadavek byl zrušen.</span><span class="sxs-lookup"><span data-stu-id="e4d38-122">The request was canceled.</span></span>|  
|<span data-ttu-id="e4d38-123">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="e4d38-123">SecureChannelFailure</span></span>|<span data-ttu-id="e4d38-124">Kanál zabezpečeného odkazu došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="e4d38-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="e4d38-125">SendFailure</span><span class="sxs-lookup"><span data-stu-id="e4d38-125">SendFailure</span></span>|<span data-ttu-id="e4d38-126">Ke vzdálenému serveru nelze odeslat žádost o dokončení.</span><span class="sxs-lookup"><span data-stu-id="e4d38-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="e4d38-127">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="e4d38-127">ServerProtocolViolation</span></span>|<span data-ttu-id="e4d38-128">Odpověď serveru nebyla platná odpověď HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4d38-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="e4d38-129">Úspěch</span><span class="sxs-lookup"><span data-stu-id="e4d38-129">Success</span></span>|<span data-ttu-id="e4d38-130">Byla zjištěna žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="e4d38-130">No error was encountered.</span></span>|  
|<span data-ttu-id="e4d38-131">časový limit</span><span class="sxs-lookup"><span data-stu-id="e4d38-131">Timeout</span></span>|<span data-ttu-id="e4d38-132">V rámci časového limitu pro žádost nebyla přijata žádná odpověď.</span><span class="sxs-lookup"><span data-stu-id="e4d38-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="e4d38-133">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="e4d38-133">TrustFailure</span></span>|<span data-ttu-id="e4d38-134">Nebylo možné ověřit certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="e4d38-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="e4d38-135">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="e4d38-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="e4d38-136">Byla přijata zpráva, která překročila limit zadaný při odesílání požadavku nebo příjmu odpovědi ze serveru.</span><span class="sxs-lookup"><span data-stu-id="e4d38-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="e4d38-137">Čekající na vyřízení</span><span class="sxs-lookup"><span data-stu-id="e4d38-137">Pending</span></span>|<span data-ttu-id="e4d38-138">Interní Asynchronní požadavek čeká na vyřízení.</span><span class="sxs-lookup"><span data-stu-id="e4d38-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="e4d38-139">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="e4d38-139">PipelineFailure</span></span>|<span data-ttu-id="e4d38-140">Tato hodnota podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e4d38-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="e4d38-141">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="e4d38-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="e4d38-142">Službě překládání názvu nešlo přeložit název hostitele proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="e4d38-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="e4d38-143">Neznámé chyby</span><span class="sxs-lookup"><span data-stu-id="e4d38-143">UnknownError</span></span>|<span data-ttu-id="e4d38-144">Došlo k výjimce neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="e4d38-144">An exception of unknown type has occurred.</span></span>|  
  
 <span data-ttu-id="e4d38-145">Když **stav** vlastnost **WebExceptionStatus.ProtocolError**, **WebResponse** , který obsahuje odpověď ze serveru je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e4d38-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="e4d38-146">Můžete zkontrolovat tuto odpověď určit skutečný zdroj chyby protokolu.</span><span class="sxs-lookup"><span data-stu-id="e4d38-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
 <span data-ttu-id="e4d38-147">Následující příklad ukazuje, jak zachytit **o výjimku WebException**.</span><span class="sxs-lookup"><span data-stu-id="e4d38-147">The following example shows how to catch a **WebException**.</span></span>  
  
```csharp  
try   
{  
    // Create a request instance.  
    WebRequest myRequest =   
    WebRequest.Create("http://www.contoso.com");  
    // Get the response.  
    WebResponse myResponse = myRequest.GetResponse();  
    //Get a readable stream from the server.   
    Stream sr = myResponse.GetResponseStream();  
  
    //Read from the stream and write any data to the console.  
    bytesread = sr.Read( myBuffer, 0, length);  
    while( bytesread > 0 )   
    {  
        for (int i=0; i<bytesread; i++) {  
            Console.Write( "{0}", myBuffer[i]);  
        }  
        Console.WriteLine();  
        bytesread = sr.Read( myBuffer, 0, length);  
    }  
    sr.Close();  
    myResponse.Close();  
}  
catch (WebException webExcp)   
{  
    // If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.");  
    // Write out the WebException message.  
    Console.WriteLine(webExcp.ToString());  
    // Get the WebException status code.  
    WebExceptionStatus status =  webExcp.Status;  
    // If status is WebExceptionStatus.ProtocolError,   
    //   there has been a protocol error and a WebResponse   
    //   should exist. Display the protocol error.  
    if (status == WebExceptionStatus.ProtocolError) {  
        Console.Write("The server returned protocol error ");  
        // Get HttpWebResponse so that you can check the HTTP status code.  
        HttpWebResponse httpResponse = (HttpWebResponse)webExcp.Response;  
        Console.WriteLine((int)httpResponse.StatusCode + " - "  
           + httpResponse.StatusCode);  
    }  
}  
catch (Exception e)   
{  
    // Code to catch other exceptions goes here.  
}  
```  
  
```vb  
Try  
    ' Create a request instance.  
    Dim myRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ' Get the response.  
    Dim myResponse As WebResponse = myRequest.GetResponse()  
    'Get a readable stream from the server.   
    Dim sr As Stream = myResponse.GetResponseStream()  
  
    Dim i As Integer      
    'Read from the stream and write any data to the console.  
    bytesread = sr.Read(myBuffer, 0, length)  
    While bytesread > 0  
        For i = 0 To bytesread - 1  
            Console.Write("{0}", myBuffer(i))  
        Next i  
        Console.WriteLine()  
        bytesread = sr.Read(myBuffer, 0, length)  
    End While  
    sr.Close()  
    myResponse.Close()  
Catch webExcp As WebException  
    ' If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.")  
    ' Write out the WebException message.  
    Console.WriteLine(webExcp.ToString())  
    ' Get the WebException status code.  
    Dim status As WebExceptionStatus = webExcp.Status  
    ' If status is WebExceptionStatus.ProtocolError,   
    '   there has been a protocol error and a WebResponse   
    '   should exist. Display the protocol error.  
    If status = WebExceptionStatus.ProtocolError Then  
        Console.Write("The server returned protocol error ")  
        ' Get HttpWebResponse so that you can check the HTTP status code.  
        Dim httpResponse As HttpWebResponse = _  
           CType(webExcp.Response, HttpWebResponse)  
        Console.WriteLine(CInt(httpResponse.StatusCode).ToString() & _  
           " - " & httpResponse.StatusCode.ToString())  
    End If  
Catch e As Exception  
    ' Code to catch other exceptions goes here.  
End Try  
```  
  
 <span data-ttu-id="e4d38-148">Aplikace, které používají <xref:System.Net.Sockets.Socket> třídy throw <xref:System.Net.Sockets.SocketException> když dojde k chybám na soketu Windows.</span><span class="sxs-lookup"><span data-stu-id="e4d38-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="e4d38-149"><xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, A <xref:System.Net.Sockets.UdpClient> třídy jsou zabudovány nad **soketu** třídy a vyvolat **SocketExceptions** také.</span><span class="sxs-lookup"><span data-stu-id="e4d38-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
 <span data-ttu-id="e4d38-150">Když **socketexception –** je vyvolána výjimka, **socketexception –** třídy sady <xref:System.Net.Sockets.SocketException.ErrorCode%2A> vlastnost poslední chyba soketu operačního systému, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="e4d38-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="e4d38-151">Další informace o chybových kódech soketu najdete v dokumentaci kód chyby rozhraní Winsock 2.0 API na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="e4d38-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d38-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4d38-152">See also</span></span>

- [<span data-ttu-id="e4d38-153">Základy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="e4d38-153">Exception Handling Fundamentals</span></span>](../../../docs/standard/exceptions/exception-handling-fundamentals.md)
- [<span data-ttu-id="e4d38-154">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="e4d38-154">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
