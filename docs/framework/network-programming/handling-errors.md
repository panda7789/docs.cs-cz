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
ms.openlocfilehash: d199219b36e2cc06314b38303fb2296f9f3794ea
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50045284"
---
# <a name="handling-errors"></a>Zpracování chyb
<xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy vyvolávat výjimky i systému (například <xref:System.ArgumentException>) a výjimky pro konkrétní Web (které jsou <xref:System.Net.WebException> vyvolané <xref:System.Net.WebRequest.GetResponse%2A> – metoda).  
  
 Každý **o výjimku WebException** zahrnuje <xref:System.Net.WebException.Status%2A> vlastnost, která obsahuje hodnoty z <xref:System.Net.WebExceptionStatus> výčtu. Můžete zkontrolovat **stav** vlastnost zjistit chyby, ke které došlo k chybě a správné kroky k vyřešení chyby.  
  
 Následující tabulka popisuje možné hodnoty pro **stav** vlastnost.  
  
|Stav|Popis|  
|------------|-----------------|  
|ConnectFailure|Vzdálenou službu nešlo kontaktovat na úrovni přenosu.|  
|ConnectionClosed|Připojení bylo předčasně ukončeno.|  
|KeepAliveFailure|Server uzavřel připojení vytvořené pomocí sady hlavičky Keep-alive.|  
|NameResolutionFailure|Název služby nešlo přeložit název hostitele.|  
|Požadavku|Odpověď přijatou ze serveru byl dokončen, ale uvedené chybě na úrovni protokolu.|  
|ReceiveFailure|Úplnou odpověď nebyla přijata ze vzdáleného serveru.|  
|RequestCanceled|Požadavek byl zrušen.|  
|SecureChannelFailure|Kanál zabezpečeného odkazu došlo k chybě.|  
|SendFailure|Ke vzdálenému serveru nelze odeslat žádost o dokončení.|  
|ServerProtocolViolation|Odpověď serveru nebyla platná odpověď HTTP.|  
|Úspěch|Byla zjištěna žádná chyba.|  
|časový limit|V rámci časového limitu pro žádost nebyla přijata žádná odpověď.|  
|TrustFailure|Nebylo možné ověřit certifikát serveru.|  
|MessageLengthLimitExceeded|Byla přijata zpráva, která překročila limit zadaný při odesílání požadavku nebo příjmu odpovědi ze serveru.|  
|Čekající na vyřízení|Interní Asynchronní požadavek čeká na vyřízení.|  
|PipelineFailure|Tato hodnota podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.|  
|ProxyNameResolutionFailure|Službě překládání názvu nešlo přeložit název hostitele proxy serveru.|  
|Neznámé chyby|Došlo k výjimce neznámého typu.|  
  
 Když **stav** vlastnost **WebExceptionStatus.ProtocolError**, **WebResponse** , který obsahuje odpověď ze serveru je k dispozici. Můžete zkontrolovat tuto odpověď určit skutečný zdroj chyby protokolu.  
  
 Následující příklad ukazuje, jak zachytit **o výjimku WebException**.  
  
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
  
 Aplikace, které používají <xref:System.Net.Sockets.Socket> třídy throw <xref:System.Net.Sockets.SocketException> když dojde k chybám na soketu Windows. <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, A <xref:System.Net.Sockets.UdpClient> třídy jsou zabudovány nad **soketu** třídy a vyvolat **SocketExceptions** také.  
  
 Když **socketexception –** je vyvolána výjimka, **socketexception –** třídy sady <xref:System.Net.Sockets.SocketException.ErrorCode%2A> vlastnost poslední chyba soketu operačního systému, ke které došlo. Další informace o chybových kódech soketu najdete v dokumentaci kód chyby rozhraní Winsock 2.0 API na webu MSDN.  
  
## <a name="see-also"></a>Viz také  
 [Základy zpracování výjimek](../../../docs/standard/exceptions/exception-handling-fundamentals.md)  
 [Žádosti o data](../../../docs/framework/network-programming/requesting-data.md)
