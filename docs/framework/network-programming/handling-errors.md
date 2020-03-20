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
# <a name="handling-errors"></a>Zpracování chyb

A <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> třídy vyvolat obě systémové <xref:System.ArgumentException>výjimky (například) a <xref:System.Net.WebException> výjimky specifické <xref:System.Net.WebRequest.GetResponse%2A> pro web (které jsou vyvolány metodou).  
  
Každý **WebException** <xref:System.Net.WebException.Status%2A> obsahuje vlastnost, která <xref:System.Net.WebExceptionStatus> obsahuje hodnotu z výčtu. Můžete zkontrolovat **Stav** vlastnost určit chybu, ke které došlo a provést příslušné kroky k vyřešení chyby.  
  
Následující tabulka popisuje možné hodnoty vlastnosti **Stav.**  
  
|Status|Popis|  
|------------|-----------------|  
|ConnectFailure|Vzdálenou službu nelze kontaktovat na úrovni přenosu.|  
|Připojení uzavřeno|Připojení bylo předčasně ukončeno.|  
|KeepAliveSelhání|Server uzavřel připojení nastojen se sadou hlaviček Keep-alive.|  
|NázevResolutionFailure|Název služby nelze přeložit název hostitele.|  
|Chyba protokolu|Odpověď přijatá ze serveru byla dokončena, ale na úrovni protokolu byla uvedena chyba.|  
|ReceiveFailure|Ze vzdáleného serveru nebyla přijata úplná odpověď.|  
|Požadavek byl zrušen.|Požadavek byl zrušen.|  
|SecureChannelSelhání|V zabezpečeném propojení kanálu došlo k chybě.|  
|SendFailure|Úplný požadavek nelze odeslat na vzdálený server.|  
|ServerProtocolViolation|Odpověď serveru nebyla platnou odpovědí HTTP.|  
|Úspěch|Nebyla zjištěna žádná chyba.|  
|Časový limit|V době stanovené pro požadavek nebyla přijata žádná odpověď.|  
|Selhání důvěryhodnosti|Certifikát serveru nelze ověřit.|  
|MessageLengthLimitExceeded|Byla přijata zpráva, která překročila zadaný limit při odesílání požadavku nebo přijímání odpovědi ze serveru.|  
|Čekající na vyřízení|Interní asynchronní požadavek čeká na vyřízení.|  
|Selhání kanálu|Tato hodnota podporuje infrastrukturu rozhraní .NET Framework a není určena k použití přímo ve vašem kódu.|  
|Selhání rezoluce__sychu|Služba překladače názvů nemohla přeložit název hostitele proxy serveru.|  
|Neznámýchyba|Došlo k výjimce neznámého typu.|  
  
Pokud je vlastnost **Stav** **WebExceptionStatus.ProtocolError**, je k dispozici **webová odpověď** obsahující odpověď ze serveru. Tuto odpověď můžete zkontrolovat a určit skutečný zdroj chyby protokolu.  
  
Následující příklad ukazuje, jak zachytit **WebException**.  
  
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
  
Aplikace, které <xref:System.Net.Sockets.Socket> používají <xref:System.Net.Sockets.SocketException> class throw při výskytu chyb v soketu systému Windows. , <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>a <xref:System.Net.Sockets.UdpClient> třídy jsou postaveny na vrcholu **Socket** třídy a vyvolat **SocketExceptions** také.  
  
Při vyvolání **SocketException,** **SocketException** třída <xref:System.Net.Sockets.SocketException.ErrorCode%2A> nastaví vlastnost na poslední chybu soketu operačního systému, ke které došlo. Další informace o kódech chyb soketu naleznete v dokumentaci k kódu chybrozhraní WINSOCK 2.0 API v msdn.  
  
## <a name="see-also"></a>Viz také

- [Zpracování a vyvolání výjimek v rozhraní .NET](../../standard/exceptions/index.md)
- [Žádosti o data](requesting-data.md)
