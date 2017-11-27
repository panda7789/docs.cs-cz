---
title: "Zpracování chyb"
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: aad78fb509f98a01b5ca072ad476d901fdd1d4d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="handling-errors"></a>Zpracování chyb
<xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy generování výjimek obou systému (například <xref:System.ArgumentException>) a výjimky webových (které jsou <xref:System.Net.WebException> vyvolané <xref:System.Net.WebRequest.GetResponse%2A> – metoda).  
  
 Každý **výjimku WebException** zahrnuje <xref:System.Net.WebException.Status%2A> vlastnost, která obsahuje hodnoty z <xref:System.Net.WebExceptionStatus> výčtu. Můžete zkontrolovat **stav** vlastnost určete chybu, která došlo k chybě a proveďte správné kroky, chcete-li vyřešit chyby.  
  
 Následující tabulka popisuje možné hodnoty **stav** vlastnost.  
  
|Stav|Popis|  
|------------|-----------------|  
|ConnectFailure|Vzdálená služba nemůže být kontaktován na úrovni přenosu.|  
|ConnectionClosed|Připojení bylo předčasně ukončeno.|  
|KeepAliveFailure|Server zavřel připojení pomocí sady udržování záhlaví.|  
|NameResolutionFailure|Název služby nešlo přeložit název hostitele.|  
|Požadavku|Odpověď ze serveru přijata dokončení, ale uvedené chybu na úrovni protokolu.|  
|ReceiveFailure|Dokončení odpověď nebyla přijata ze vzdáleného serveru.|  
|RequestCanceled|Požadavek byl zrušen.|  
|SecureChannelFailure|Došlo k chybě v propojení zabezpečený kanál.|  
|SendFailure|Dokončení požadavku nebylo možné odeslat ke vzdálenému serveru.|  
|ServerProtocolViolation|Odpověď serveru nebyla platná odpověď HTTP.|  
|Úspěch|Byla zjištěna žádná chyba.|  
|Časový limit|Byla přijata žádná odpověď v rámci časového limitu, nastavte pro daný požadavek.|  
|TrustFailure|Nebylo možné ověřit certifikát serveru.|  
|MessageLengthLimitExceeded|Byla přijata zpráva překročení zadané omezení při odesílání požadavku nebo přijímání odpověď ze serveru.|  
|Čekající na vyřízení|Interní Asynchronní požadavek čeká na vyřízení.|  
|PipelineFailure|Tato hodnota podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.|  
|ProxyNameResolutionFailure|Název překladače služby nešlo přeložit název hostitele proxy serveru.|  
|Neznámé chyby|Došlo k výjimce neznámého typu.|  
  
 Když **stav** vlastnost je **WebExceptionStatus.ProtocolError**, **WebResponse** , který obsahuje odpověď ze serveru je k dispozici. Tato odpověď k určení skutečné zdroj Chyba protokolu můžete zkontrolovat.  
  
 Následující příklad ukazuje, jak zachytit **výjimku WebException**.  
  
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
  
 Aplikace, které používají <xref:System.Net.Sockets.Socket> třída throw <xref:System.Net.Sockets.SocketException> když dojde k chybám v systému Windows soketu. <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, A <xref:System.Net.Sockets.UdpClient> třídy jsou postavený na **soketu** třídy a výjimku **SocketExceptions** také.  
  
 Když **SocketException** je vyvolána výjimka, **SocketException** třídy sady <xref:System.Net.Sockets.SocketException.ErrorCode%2A> vlastnost poslední chyba soketu operačního systému, který došlo k chybě. Další informace o chybových kódech soketu najdete v dokumentaci kód chyby rozhraní Winsock 2.0 API na webu MSDN.  
  
## <a name="see-also"></a>Viz také  
 [Základy zpracování výjimek](../../../docs/standard/exceptions/exception-handling-fundamentals.md)  
 [Požadavek na Data](../../../docs/framework/network-programming/requesting-data.md)
