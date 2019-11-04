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
ms.openlocfilehash: 7084c4579dd5fca0075c7516754195f7cea9e27c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458049"
---
# <a name="handling-errors"></a>Zpracování chyb

Třídy <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> vyvolají výjimky systému (například <xref:System.ArgumentException>) a výjimky specifické pro web (které jsou <xref:System.Net.WebException> vyvolány metodou <xref:System.Net.WebRequest.GetResponse%2A>).  
  
Každý **WebException** obsahuje vlastnost <xref:System.Net.WebException.Status%2A>, která obsahuje hodnotu ze výčtu <xref:System.Net.WebExceptionStatus>. Můžete prostudovat vlastnost **stav** a zjistit tak chybu, ke které došlo, a provést správné kroky k vyřešení chyby.  
  
Následující tabulka popisuje možné hodnoty vlastnosti **status** .  
  
|Stav|Popis|  
|------------|-----------------|  
|ConnectFailure|Vzdálenou službu nelze kontaktovat na úrovni přenosu.|  
|ConnectionClosed|Připojení bylo předčasně ukončeno.|  
|KeepAliveFailure|Server uzavřel připojení vytvořené pomocí sady hlaviček Keep-Alive.|  
|NameResolutionFailure|Názvová služba nemohla přeložit název hostitele.|  
|ProtocolError|Odpověď přijatá ze serveru byla dokončena, ale na úrovni protokolu byla označena chyba.|  
|ReceiveFailure|Ze vzdáleného serveru nebyla přijata úplná odpověď.|  
|RequestCanceled|Žádost se zrušila.|  
|SecureChannelFailure|V odkazu na zabezpečený kanál došlo k chybě.|  
|SendFailure|Do vzdáleného serveru nelze odeslat úplnou žádost.|  
|ServerProtocolViolation|Odpověď serveru nebyla platnou odpovědí HTTP.|  
|Nástup|Nedošlo k žádné chybě.|  
|prodlev|V rámci nastaveného časového limitu pro požadavek nebyla přijata žádná odpověď.|  
|TrustFailure|Certifikát serveru nelze ověřit.|  
|MessageLengthLimitExceeded|Byla přijata zpráva, která překročila zadaný limit při odesílání žádosti nebo přijetí odpovědi ze serveru.|  
|Uložené|Interní asynchronní požadavek čeká na vyřízení.|  
|PipelineFailure|Tato hodnota podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.|  
|ProxyNameResolutionFailure|Služba překladač názvů nemohla přeložit název hostitele proxy.|  
|UnknownError|Došlo k výjimce neznámého typu.|  
  
Je- li vlastnost status **WebExceptionStatus rovným. ProtocolError**, je k dispozici odpověď na **WebResponse** obsahující odpověď ze serveru. Tuto odpověď můžete prostudovat a určit skutečný zdroj chyby protokolu.  
  
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
  
Aplikace, které používají <xref:System.Net.Sockets.Socket> třídy, vyvolávají <xref:System.Net.Sockets.SocketException> při výskytu chyb na soketu Windows. Třídy <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>a <xref:System.Net.Sockets.UdpClient> jsou postaveny na třídě **soketu** a také vyvolávají **SocketExceptions** .  
  
Když je vyvolána výjimka **SocketException** , třída **SocketException** nastaví vlastnost <xref:System.Net.Sockets.SocketException.ErrorCode%2A> na poslední chybu soketu operačního systému, ke které došlo. Další informace o kódech chyb soketu najdete v dokumentaci k kódu chyby rozhraní API Winsock 2,0 na webu MSDN.  
  
## <a name="see-also"></a>Viz také:

- [Zpracování a vyvolávání výjimek v rozhraní .NET](../../standard/exceptions/index.md)
- [Žádosti o data](requesting-data.md)
