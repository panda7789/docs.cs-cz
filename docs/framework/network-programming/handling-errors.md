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
ms.openlocfilehash: 255a4ab3d6d6e3fc133e809ce360b25d6f82c8d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940071"
---
# <a name="handling-errors"></a><span data-ttu-id="d2f0b-102">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="d2f0b-102">Handling Errors</span></span>
<span data-ttu-id="d2f0b-103"><xref:System.Net.WebRequest.GetResponse%2A> <xref:System.Net.WebException> <xref:System.ArgumentException>Třídy a <xref:System.Net.WebResponse>vyvolají výjimky systému (například) a výjimky specifické pro web (které jsou vyvolány <xref:System.Net.WebRequest> metodou).</span><span class="sxs-lookup"><span data-stu-id="d2f0b-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
 <span data-ttu-id="d2f0b-104">Každý **WebException** obsahuje <xref:System.Net.WebException.Status%2A> vlastnost, která obsahuje hodnotu z <xref:System.Net.WebExceptionStatus> výčtu.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="d2f0b-105">Můžete prostudovat vlastnost **stav** a zjistit tak chybu, ke které došlo, a provést správné kroky k vyřešení chyby.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
 <span data-ttu-id="d2f0b-106">Následující tabulka popisuje možné hodnoty vlastnosti **status** .</span><span class="sxs-lookup"><span data-stu-id="d2f0b-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="d2f0b-107">Stav</span><span class="sxs-lookup"><span data-stu-id="d2f0b-107">Status</span></span>|<span data-ttu-id="d2f0b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d2f0b-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d2f0b-109">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="d2f0b-109">ConnectFailure</span></span>|<span data-ttu-id="d2f0b-110">Vzdálenou službu nelze kontaktovat na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="d2f0b-111">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="d2f0b-111">ConnectionClosed</span></span>|<span data-ttu-id="d2f0b-112">Připojení bylo předčasně ukončeno.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="d2f0b-113">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="d2f0b-113">KeepAliveFailure</span></span>|<span data-ttu-id="d2f0b-114">Server uzavřel připojení vytvořené pomocí sady hlaviček Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="d2f0b-115">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="d2f0b-115">NameResolutionFailure</span></span>|<span data-ttu-id="d2f0b-116">Názvová služba nemohla přeložit název hostitele.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="d2f0b-117">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="d2f0b-117">ProtocolError</span></span>|<span data-ttu-id="d2f0b-118">Odpověď přijatá ze serveru byla dokončena, ale na úrovni protokolu byla označena chyba.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="d2f0b-119">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="d2f0b-119">ReceiveFailure</span></span>|<span data-ttu-id="d2f0b-120">Ze vzdáleného serveru nebyla přijata úplná odpověď.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="d2f0b-121">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="d2f0b-121">RequestCanceled</span></span>|<span data-ttu-id="d2f0b-122">Žádost se zrušila.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-122">The request was canceled.</span></span>|  
|<span data-ttu-id="d2f0b-123">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="d2f0b-123">SecureChannelFailure</span></span>|<span data-ttu-id="d2f0b-124">V odkazu na zabezpečený kanál došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="d2f0b-125">SendFailure</span><span class="sxs-lookup"><span data-stu-id="d2f0b-125">SendFailure</span></span>|<span data-ttu-id="d2f0b-126">Do vzdáleného serveru nelze odeslat úplnou žádost.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="d2f0b-127">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="d2f0b-127">ServerProtocolViolation</span></span>|<span data-ttu-id="d2f0b-128">Odpověď serveru nebyla platnou odpovědí HTTP.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="d2f0b-129">Úspěch</span><span class="sxs-lookup"><span data-stu-id="d2f0b-129">Success</span></span>|<span data-ttu-id="d2f0b-130">Nedošlo k žádné chybě.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-130">No error was encountered.</span></span>|  
|<span data-ttu-id="d2f0b-131">časový limit</span><span class="sxs-lookup"><span data-stu-id="d2f0b-131">Timeout</span></span>|<span data-ttu-id="d2f0b-132">V rámci nastaveného časového limitu pro požadavek nebyla přijata žádná odpověď.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="d2f0b-133">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="d2f0b-133">TrustFailure</span></span>|<span data-ttu-id="d2f0b-134">Certifikát serveru nelze ověřit.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="d2f0b-135">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="d2f0b-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="d2f0b-136">Byla přijata zpráva, která překročila zadaný limit při odesílání žádosti nebo přijetí odpovědi ze serveru.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="d2f0b-137">Čekající na vyřízení</span><span class="sxs-lookup"><span data-stu-id="d2f0b-137">Pending</span></span>|<span data-ttu-id="d2f0b-138">Interní asynchronní požadavek čeká na vyřízení.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="d2f0b-139">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="d2f0b-139">PipelineFailure</span></span>|<span data-ttu-id="d2f0b-140">Tato hodnota podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="d2f0b-141">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="d2f0b-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="d2f0b-142">Služba překladač názvů nemohla přeložit název hostitele proxy.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="d2f0b-143">Neznámé chyby</span><span class="sxs-lookup"><span data-stu-id="d2f0b-143">UnknownError</span></span>|<span data-ttu-id="d2f0b-144">Došlo k výjimce neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-144">An exception of unknown type has occurred.</span></span>|  
  
 <span data-ttu-id="d2f0b-145">Je- li vlastnost status **WebExceptionStatus rovným. ProtocolError**, je k dispozici odpověď na WebResponse obsahující odpověď ze serveru.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="d2f0b-146">Tuto odpověď můžete prostudovat a určit skutečný zdroj chyby protokolu.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
 <span data-ttu-id="d2f0b-147">Následující příklad ukazuje, jak zachytit **WebException**.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-147">The following example shows how to catch a **WebException**.</span></span>  
  
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
  
 <span data-ttu-id="d2f0b-148">Aplikace, které používají <xref:System.Net.Sockets.Socket> třídu, <xref:System.Net.Sockets.SocketException> jsou vyhozeny, pokud dojde k chybám na soketu Windows.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="d2f0b-149"><xref:System.Net.Sockets.TcpClient>Třídy, <xref:System.Net.Sockets.TcpListener> a jsou<xref:System.Net.Sockets.UdpClient> postaveny na vrcholu třídy soketu a také vyvolávají výjimku **SocketExceptions** .</span><span class="sxs-lookup"><span data-stu-id="d2f0b-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
 <span data-ttu-id="d2f0b-150">Když je vyvolána výjimka **SocketException** , <xref:System.Net.Sockets.SocketException.ErrorCode%2A> třída **SocketException** nastaví vlastnost na poslední chybu soketu operačního systému, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="d2f0b-151">Další informace o kódech chyb soketu najdete v dokumentaci k kódu chyby rozhraní API Winsock 2,0 na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f0b-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2f0b-152">See also</span></span>

- [<span data-ttu-id="d2f0b-153">Základy zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="d2f0b-153">Exception Handling Fundamentals</span></span>](../../standard/exceptions/exception-handling-fundamentals.md)
- [<span data-ttu-id="d2f0b-154">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="d2f0b-154">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
