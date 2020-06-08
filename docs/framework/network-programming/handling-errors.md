---
title: Zpracování chyb
description: Seznamte se se systémovými a webovými výjimkami, které vyvolají WebRequest a WebResponse. K pochopení a vyřešení problému použijte vlastnost status.
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
ms.openlocfilehash: 786b2bd8bc4d1b394bcfe920053b2f4f55d1cdea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502571"
---
# <a name="handling-errors"></a><span data-ttu-id="6e7de-104">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="6e7de-104">Handling Errors</span></span>

<span data-ttu-id="6e7de-105"><xref:System.Net.WebRequest>Třídy a <xref:System.Net.WebResponse> vyvolají výjimky systému (například <xref:System.ArgumentException> ) a výjimky specifické pro web (které jsou <xref:System.Net.WebException> vyvolány <xref:System.Net.WebRequest.GetResponse%2A> metodou).</span><span class="sxs-lookup"><span data-stu-id="6e7de-105">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
<span data-ttu-id="6e7de-106">Každý **WebException** obsahuje <xref:System.Net.WebException.Status%2A> vlastnost, která obsahuje hodnotu z <xref:System.Net.WebExceptionStatus> výčtu.</span><span class="sxs-lookup"><span data-stu-id="6e7de-106">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="6e7de-107">Můžete prostudovat vlastnost **stav** a zjistit tak chybu, ke které došlo, a provést správné kroky k vyřešení chyby.</span><span class="sxs-lookup"><span data-stu-id="6e7de-107">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
<span data-ttu-id="6e7de-108">Následující tabulka popisuje možné hodnoty vlastnosti **status** .</span><span class="sxs-lookup"><span data-stu-id="6e7de-108">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="6e7de-109">Status</span><span class="sxs-lookup"><span data-stu-id="6e7de-109">Status</span></span>|<span data-ttu-id="6e7de-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6e7de-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6e7de-111">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="6e7de-111">ConnectFailure</span></span>|<span data-ttu-id="6e7de-112">Vzdálenou službu nelze kontaktovat na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="6e7de-112">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="6e7de-113">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="6e7de-113">ConnectionClosed</span></span>|<span data-ttu-id="6e7de-114">Připojení bylo předčasně ukončeno.</span><span class="sxs-lookup"><span data-stu-id="6e7de-114">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="6e7de-115">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="6e7de-115">KeepAliveFailure</span></span>|<span data-ttu-id="6e7de-116">Server uzavřel připojení vytvořené pomocí sady hlaviček Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="6e7de-116">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="6e7de-117">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="6e7de-117">NameResolutionFailure</span></span>|<span data-ttu-id="6e7de-118">Názvová služba nemohla přeložit název hostitele.</span><span class="sxs-lookup"><span data-stu-id="6e7de-118">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="6e7de-119">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="6e7de-119">ProtocolError</span></span>|<span data-ttu-id="6e7de-120">Odpověď přijatá ze serveru byla dokončena, ale na úrovni protokolu byla označena chyba.</span><span class="sxs-lookup"><span data-stu-id="6e7de-120">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="6e7de-121">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="6e7de-121">ReceiveFailure</span></span>|<span data-ttu-id="6e7de-122">Ze vzdáleného serveru nebyla přijata úplná odpověď.</span><span class="sxs-lookup"><span data-stu-id="6e7de-122">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="6e7de-123">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="6e7de-123">RequestCanceled</span></span>|<span data-ttu-id="6e7de-124">Žádost se zrušila.</span><span class="sxs-lookup"><span data-stu-id="6e7de-124">The request was canceled.</span></span>|  
|<span data-ttu-id="6e7de-125">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="6e7de-125">SecureChannelFailure</span></span>|<span data-ttu-id="6e7de-126">V odkazu na zabezpečený kanál došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="6e7de-126">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="6e7de-127">SendFailure</span><span class="sxs-lookup"><span data-stu-id="6e7de-127">SendFailure</span></span>|<span data-ttu-id="6e7de-128">Do vzdáleného serveru nelze odeslat úplnou žádost.</span><span class="sxs-lookup"><span data-stu-id="6e7de-128">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="6e7de-129">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="6e7de-129">ServerProtocolViolation</span></span>|<span data-ttu-id="6e7de-130">Odpověď serveru nebyla platnou odpovědí HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e7de-130">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="6e7de-131">Úspěch</span><span class="sxs-lookup"><span data-stu-id="6e7de-131">Success</span></span>|<span data-ttu-id="6e7de-132">Nedošlo k žádné chybě.</span><span class="sxs-lookup"><span data-stu-id="6e7de-132">No error was encountered.</span></span>|  
|<span data-ttu-id="6e7de-133">Časový limit</span><span class="sxs-lookup"><span data-stu-id="6e7de-133">Timeout</span></span>|<span data-ttu-id="6e7de-134">V rámci nastaveného časového limitu pro požadavek nebyla přijata žádná odpověď.</span><span class="sxs-lookup"><span data-stu-id="6e7de-134">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="6e7de-135">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="6e7de-135">TrustFailure</span></span>|<span data-ttu-id="6e7de-136">Certifikát serveru nelze ověřit.</span><span class="sxs-lookup"><span data-stu-id="6e7de-136">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="6e7de-137">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="6e7de-137">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="6e7de-138">Byla přijata zpráva, která překročila zadaný limit při odesílání žádosti nebo přijetí odpovědi ze serveru.</span><span class="sxs-lookup"><span data-stu-id="6e7de-138">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="6e7de-139">Čekající na vyřízení</span><span class="sxs-lookup"><span data-stu-id="6e7de-139">Pending</span></span>|<span data-ttu-id="6e7de-140">Interní asynchronní požadavek čeká na vyřízení.</span><span class="sxs-lookup"><span data-stu-id="6e7de-140">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="6e7de-141">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="6e7de-141">PipelineFailure</span></span>|<span data-ttu-id="6e7de-142">Tato hodnota podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="6e7de-142">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="6e7de-143">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="6e7de-143">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="6e7de-144">Služba překladač názvů nemohla přeložit název hostitele proxy.</span><span class="sxs-lookup"><span data-stu-id="6e7de-144">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="6e7de-145">UnknownError</span><span class="sxs-lookup"><span data-stu-id="6e7de-145">UnknownError</span></span>|<span data-ttu-id="6e7de-146">Došlo k výjimce neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="6e7de-146">An exception of unknown type has occurred.</span></span>|  
  
<span data-ttu-id="6e7de-147">Je- **Status** li vlastnost status **WebExceptionStatus rovným. ProtocolError**, je k dispozici odpověď na **WebResponse** obsahující odpověď ze serveru.</span><span class="sxs-lookup"><span data-stu-id="6e7de-147">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="6e7de-148">Tuto odpověď můžete prostudovat a určit skutečný zdroj chyby protokolu.</span><span class="sxs-lookup"><span data-stu-id="6e7de-148">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
<span data-ttu-id="6e7de-149">Následující příklad ukazuje, jak zachytit **WebException**.</span><span class="sxs-lookup"><span data-stu-id="6e7de-149">The following example shows how to catch a **WebException**.</span></span>  
  
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
  
<span data-ttu-id="6e7de-150">Aplikace, které používají <xref:System.Net.Sockets.Socket> třídu, jsou vyhozeny, <xref:System.Net.Sockets.SocketException> Pokud dojde k chybám na soketu Windows.</span><span class="sxs-lookup"><span data-stu-id="6e7de-150">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="6e7de-151"><xref:System.Net.Sockets.TcpClient>Třídy, <xref:System.Net.Sockets.TcpListener> a <xref:System.Net.Sockets.UdpClient> jsou postaveny na vrcholu třídy **soketu** a také vyvolávají výjimku **SocketExceptions** .</span><span class="sxs-lookup"><span data-stu-id="6e7de-151">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
<span data-ttu-id="6e7de-152">Když je vyvolána výjimka **SocketException** , třída **SocketException** nastaví <xref:System.Net.Sockets.SocketException.ErrorCode%2A> vlastnost na poslední chybu soketu operačního systému, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="6e7de-152">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="6e7de-153">Další informace o kódech chyb soketu najdete v dokumentaci k kódu chyby rozhraní API Winsock 2,0 na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="6e7de-153">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7de-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e7de-154">See also</span></span>

- [<span data-ttu-id="6e7de-155">Zpracování a vyvolávání výjimek v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="6e7de-155">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="6e7de-156">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="6e7de-156">Requesting Data</span></span>](requesting-data.md)
