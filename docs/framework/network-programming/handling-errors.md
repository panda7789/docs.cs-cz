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
ms.openlocfilehash: f5be5d8e14d7aa2d98009fc10c9cce314e745ed1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180872"
---
# <a name="handling-errors"></a><span data-ttu-id="e1ffd-102">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="e1ffd-102">Handling Errors</span></span>

<span data-ttu-id="e1ffd-103">A <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> třídy vyvolat obě systémové <xref:System.ArgumentException>výjimky (například) a <xref:System.Net.WebException> výjimky specifické <xref:System.Net.WebRequest.GetResponse%2A> pro web (které jsou vyvolány metodou).</span><span class="sxs-lookup"><span data-stu-id="e1ffd-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
<span data-ttu-id="e1ffd-104">Každý **WebException** <xref:System.Net.WebException.Status%2A> obsahuje vlastnost, která <xref:System.Net.WebExceptionStatus> obsahuje hodnotu z výčtu.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="e1ffd-105">Můžete zkontrolovat **Stav** vlastnost určit chybu, ke které došlo a provést příslušné kroky k vyřešení chyby.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
<span data-ttu-id="e1ffd-106">Následující tabulka popisuje možné hodnoty vlastnosti **Stav.**</span><span class="sxs-lookup"><span data-stu-id="e1ffd-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="e1ffd-107">Status</span><span class="sxs-lookup"><span data-stu-id="e1ffd-107">Status</span></span>|<span data-ttu-id="e1ffd-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e1ffd-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e1ffd-109">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="e1ffd-109">ConnectFailure</span></span>|<span data-ttu-id="e1ffd-110">Vzdálenou službu nelze kontaktovat na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="e1ffd-111">Připojení uzavřeno</span><span class="sxs-lookup"><span data-stu-id="e1ffd-111">ConnectionClosed</span></span>|<span data-ttu-id="e1ffd-112">Připojení bylo předčasně ukončeno.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="e1ffd-113">KeepAliveSelhání</span><span class="sxs-lookup"><span data-stu-id="e1ffd-113">KeepAliveFailure</span></span>|<span data-ttu-id="e1ffd-114">Server uzavřel připojení nastojen se sadou hlaviček Keep-alive.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="e1ffd-115">NázevResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="e1ffd-115">NameResolutionFailure</span></span>|<span data-ttu-id="e1ffd-116">Název služby nelze přeložit název hostitele.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="e1ffd-117">Chyba protokolu</span><span class="sxs-lookup"><span data-stu-id="e1ffd-117">ProtocolError</span></span>|<span data-ttu-id="e1ffd-118">Odpověď přijatá ze serveru byla dokončena, ale na úrovni protokolu byla uvedena chyba.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="e1ffd-119">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="e1ffd-119">ReceiveFailure</span></span>|<span data-ttu-id="e1ffd-120">Ze vzdáleného serveru nebyla přijata úplná odpověď.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="e1ffd-121">Požadavek byl zrušen.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-121">RequestCanceled</span></span>|<span data-ttu-id="e1ffd-122">Požadavek byl zrušen.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-122">The request was canceled.</span></span>|  
|<span data-ttu-id="e1ffd-123">SecureChannelSelhání</span><span class="sxs-lookup"><span data-stu-id="e1ffd-123">SecureChannelFailure</span></span>|<span data-ttu-id="e1ffd-124">V zabezpečeném propojení kanálu došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="e1ffd-125">SendFailure</span><span class="sxs-lookup"><span data-stu-id="e1ffd-125">SendFailure</span></span>|<span data-ttu-id="e1ffd-126">Úplný požadavek nelze odeslat na vzdálený server.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="e1ffd-127">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="e1ffd-127">ServerProtocolViolation</span></span>|<span data-ttu-id="e1ffd-128">Odpověď serveru nebyla platnou odpovědí HTTP.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="e1ffd-129">Úspěch</span><span class="sxs-lookup"><span data-stu-id="e1ffd-129">Success</span></span>|<span data-ttu-id="e1ffd-130">Nebyla zjištěna žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-130">No error was encountered.</span></span>|  
|<span data-ttu-id="e1ffd-131">Časový limit</span><span class="sxs-lookup"><span data-stu-id="e1ffd-131">Timeout</span></span>|<span data-ttu-id="e1ffd-132">V době stanovené pro požadavek nebyla přijata žádná odpověď.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="e1ffd-133">Selhání důvěryhodnosti</span><span class="sxs-lookup"><span data-stu-id="e1ffd-133">TrustFailure</span></span>|<span data-ttu-id="e1ffd-134">Certifikát serveru nelze ověřit.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="e1ffd-135">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="e1ffd-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="e1ffd-136">Byla přijata zpráva, která překročila zadaný limit při odesílání požadavku nebo přijímání odpovědi ze serveru.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="e1ffd-137">Čekající na vyřízení</span><span class="sxs-lookup"><span data-stu-id="e1ffd-137">Pending</span></span>|<span data-ttu-id="e1ffd-138">Interní asynchronní požadavek čeká na vyřízení.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="e1ffd-139">Selhání kanálu</span><span class="sxs-lookup"><span data-stu-id="e1ffd-139">PipelineFailure</span></span>|<span data-ttu-id="e1ffd-140">Tato hodnota podporuje infrastrukturu rozhraní .NET Framework a není určena k použití přímo ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="e1ffd-141">Selhání rezoluce__sychu</span><span class="sxs-lookup"><span data-stu-id="e1ffd-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="e1ffd-142">Služba překladače názvů nemohla přeložit název hostitele proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="e1ffd-143">Neznámýchyba</span><span class="sxs-lookup"><span data-stu-id="e1ffd-143">UnknownError</span></span>|<span data-ttu-id="e1ffd-144">Došlo k výjimce neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-144">An exception of unknown type has occurred.</span></span>|  
  
<span data-ttu-id="e1ffd-145">Pokud je vlastnost **Stav** **WebExceptionStatus.ProtocolError**, je k dispozici **webová odpověď** obsahující odpověď ze serveru.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="e1ffd-146">Tuto odpověď můžete zkontrolovat a určit skutečný zdroj chyby protokolu.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
<span data-ttu-id="e1ffd-147">Následující příklad ukazuje, jak zachytit **WebException**.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-147">The following example shows how to catch a **WebException**.</span></span>  
  
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
  
<span data-ttu-id="e1ffd-148">Aplikace, které <xref:System.Net.Sockets.Socket> používají <xref:System.Net.Sockets.SocketException> class throw při výskytu chyb v soketu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="e1ffd-149">, <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>a <xref:System.Net.Sockets.UdpClient> třídy jsou postaveny na vrcholu **Socket** třídy a vyvolat **SocketExceptions** také.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
<span data-ttu-id="e1ffd-150">Při vyvolání **SocketException,** **SocketException** třída <xref:System.Net.Sockets.SocketException.ErrorCode%2A> nastaví vlastnost na poslední chybu soketu operačního systému, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="e1ffd-151">Další informace o kódech chyb soketu naleznete v dokumentaci k kódu chybrozhraní WINSOCK 2.0 API v msdn.</span><span class="sxs-lookup"><span data-stu-id="e1ffd-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ffd-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1ffd-152">See also</span></span>

- [<span data-ttu-id="e1ffd-153">Zpracování a vyvolání výjimek v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="e1ffd-153">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="e1ffd-154">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="e1ffd-154">Requesting Data</span></span>](requesting-data.md)
