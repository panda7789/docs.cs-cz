---
title: "Vytváření asynchronních požadavků"
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
- Internet, asynchronous access
- Networking
- asynchronous requests, Internet resources
- Network Resources
- WebRequest class, asynchronous access
ms.assetid: 735d3fce-f80c-437f-b02c-5c47f5739674
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3bd739a4d8fd5995855b51902a9f101546745dd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="making-asynchronous-requests"></a>Vytváření asynchronních požadavků
<xref:System.Net> Třídy používat rozhraní .NET Framework standardní asynchronní programovací model pro asynchronní přístup k internetovým prostředkům. <xref:System.Net.WebRequest.BeginGetResponse%2A> a <xref:System.Net.WebRequest.EndGetResponse%2A> metody <xref:System.Net.WebRequest> třídy zahájení a dokončení asynchronní požadavky na internetové prostředky.  
  
> [!NOTE]
>  Použití synchronní volání v asynchronní zpětné volání, které metody může mít za následek postihy ovlivňuje výkon. Internet žádosti provedené **WebRequest** a musí používat jeho následníky <xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> číst datový proud vrácený <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metoda.  
  
 Následující vzorový kód ukazuje, jak použít asynchronní volání s **WebRequest** třídy. Ukázka je program konzoly, která přebírá URI z příkazového řádku, požadavek na prostředek pro identifikátor URI a potom zobrazí data do konzoly nástroje, jako je přijaté z Internetu.  
  
 Program definuje dvě třídy pro vlastní použití **RequestState** třídy, která předá dat napříč asynchronní volání, a **ClientGetAsync** třídy, která implementuje asynchronní požadavek na Internetového zdroji.  
  
 **RequestState** třída zachovává stav žádosti napříč volání asynchronních metod, které obsloužit požadavek. Obsahuje **WebRequest** a <xref:System.IO.Stream> instancí, které obsahují aktuální požadavek na prostředek a datový proud obdrželi v odpovědi, vyrovnávací paměť, která obsahuje aktuálně získaná z internetových prostředků a data<xref:System.Text.StringBuilder> obsahující kompletní odpovědi. A **RequestState**se předá jako *stavu* parametr při <xref:System.AsyncCallback> metoda není zaregistrována **WebRequest.BeginGetResponse**.  
  
 **ClientGetAsync** třída implementuje asynchronní požadavek na internetových prostředků a zapíše výsledný odpověď do konzoly. Obsahuje metody a vlastnosti, které jsou popsané v následujícím seznamu.  
  
-   `allDone` Vlastnost obsahuje instanci <xref:System.Threading.ManualResetEvent> třídu, která signalizuje dokončení požadavku.  
  
-   `Main()` Metoda čte příkazového řádku a zahájí požadavek zadaný prostředek Internetu. Vytvoří **WebRequest** `wreq` a **RequestState** `rs`, volání **BeginGetResponse** k zahájení zpracování požadavků a pak volání `allDone.WaitOne()`metoda tak, aby aplikace nebude ukončena až do dokončení zpětného volání. Po odpovědi je pro čtení z Internetu, `Main()` zapíše ho do konzole a ukončení aplikace.  
  
-   `showusage()` Metoda zapíše příkazového řádku s příklad v konzole. Je volána metodou `Main()` při žádné URI zadání na příkazovém řádku.  
  
-   `RespCallBack()` Metoda implementuje metodu asynchronní zpětné volání pro daný požadavek Internetu. Vytvoří **WebResponse** instance obsahujícího odpověď z internetového zdroji, získá datového proudu odpovědi a pak spustí asynchronně čtení dat z datového proudu.  
  
-   `ReadCallBack()` Metoda implementuje metodu asynchronní zpětné volání pro čtení datového proudu odpovědi. Přenáší data přijatá z Internetu prostředku do **ResponseData** vlastnost **RequestState** instance a potom spustí jiné asynchronní čtení datového proudu odpovědi, dokud nebude žádná další data Vrátí. Jakmile byl načten všechna data, `ReadCallBack()` zavře datového proudu odpovědi a volání `allDone.Set()` metoda indikující, zda je v celé odpovědi **ResponseData**.  
  
    > [!NOTE]
    >  Je důležité, aby byly zavřeny všechny datové proudy sítě. Pokud nezavřete každý datový proud požadavku a odpovědi, bude vaše aplikace dostatek připojení k serveru a nemůže zpracovávat další požadavky.  
  
```csharp  
using System;  
using System.Net;  
using System.Threading;  
using System.Text;  
using System.IO;  
  
// The RequestState class passes data across async calls.  
public class RequestState  
{  
   const int BufferSize = 1024;  
   public StringBuilder RequestData;  
   public byte[] BufferRead;  
   public WebRequest Request;  
   public Stream ResponseStream;  
   // Create Decoder for appropriate enconding type.  
   public Decoder StreamDecode = Encoding.UTF8.GetDecoder();  
  
   public RequestState()  
   {  
      BufferRead = new byte[BufferSize];  
      RequestData = new StringBuilder(String.Empty);  
      Request = null;  
      ResponseStream = null;  
   }       
}  
  
// ClientGetAsync issues the async request.  
class ClientGetAsync   
{  
   public static ManualResetEvent allDone = new ManualResetEvent(false);  
   const int BUFFER_SIZE = 1024;  
  
   public static void Main(string[] args)   
   {  
      if (args.Length < 1)   
      {  
         showusage();  
         return;  
      }  
  
      // Get the URI from the command line.  
      Uri httpSite = new Uri(args[0]);  
  
      // Create the request object.  
      WebRequest wreq = WebRequest.Create(httpSite);  
  
      // Create the state object.  
      RequestState rs = new RequestState();  
  
      // Put the request into the state object so it can be passed around.  
      rs.Request = wreq;  
  
      // Issue the async request.  
      IAsyncResult r = (IAsyncResult) wreq.BeginGetResponse(  
         new AsyncCallback(RespCallback), rs);  
  
      // Wait until the ManualResetEvent is set so that the application   
      // does not exit until after the callback is called.  
      allDone.WaitOne();  
  
      Console.WriteLine(rs.RequestData.ToString());  
   }  
  
   public static void showusage() {  
      Console.WriteLine("Attempts to GET a URL");  
      Console.WriteLine("\r\nUsage:");  
      Console.WriteLine("   ClientGetAsync URL");  
      Console.WriteLine("   Example:");  
      Console.WriteLine("      ClientGetAsync http://www.contoso.com/");  
   }  
  
   private static void RespCallback(IAsyncResult ar)  
   {  
      // Get the RequestState object from the async result.  
      RequestState rs = (RequestState) ar.AsyncState;  
  
      // Get the WebRequest from RequestState.  
      WebRequest req = rs.Request;  
  
      // Call EndGetResponse, which produces the WebResponse object  
      //  that came from the request issued above.  
      WebResponse resp = req.EndGetResponse(ar);           
  
      //  Start reading data from the response stream.  
      Stream ResponseStream = resp.GetResponseStream();  
  
      // Store the response stream in RequestState to read   
      // the stream asynchronously.  
      rs.ResponseStream = ResponseStream;  
  
      //  Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead  
      IAsyncResult iarRead = ResponseStream.BeginRead(rs.BufferRead, 0,   
         BUFFER_SIZE, new AsyncCallback(ReadCallBack), rs);   
   }  
  
   private static void ReadCallBack(IAsyncResult asyncResult)  
   {  
      // Get the RequestState object from AsyncResult.  
      RequestState rs = (RequestState)asyncResult.AsyncState;  
  
      // Retrieve the ResponseStream that was set in RespCallback.   
      Stream responseStream = rs.ResponseStream;  
  
      // Read rs.BufferRead to verify that it contains data.   
      int read = responseStream.EndRead( asyncResult );  
      if (read > 0)  
      {  
         // Prepare a Char array buffer for converting to Unicode.  
         Char[] charBuffer = new Char[BUFFER_SIZE];  
  
         // Convert byte stream to Char array and then to String.  
         // len contains the number of characters converted to Unicode.  
      int len =   
         rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0);  
  
         String str = new String(charBuffer, 0, len);  
  
         // Append the recently read data to the RequestData stringbuilder  
         // object contained in RequestState.  
         rs.RequestData.Append(  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read));           
  
         // Continue reading data until   
         // responseStream.EndRead returns –1.  
         IAsyncResult ar = responseStream.BeginRead(   
            rs.BufferRead, 0, BUFFER_SIZE,   
            new AsyncCallback(ReadCallBack), rs);  
      }  
      else  
      {  
         if(rs.RequestData.Length>0)  
         {  
            //  Display data to the console.  
            string strContent;                    
            strContent = rs.RequestData.ToString();  
         }  
         // Close down the response stream.  
         responseStream.Close();           
         // Set the ManualResetEvent so the main thread can exit.  
         allDone.Set();                             
      }  
      return;  
   }      
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Threading  
Imports System.Text  
Imports System.IO  
  
' The RequestState class passes data across async calls.  
Public Class RequestState  
  
      Public RequestData As New StringBuilder("")  
      Public BufferRead(1024) As Byte  
      Public Request As HttpWebRequest  
      Public ResponseStream As Stream  
      ' Create Decoder for appropriate encoding type.  
      Public StreamDecode As Decoder = Encoding.UTF8.GetDecoder()  
  
      Public Sub New  
         Request = Nothing  
         ResponseStream = Nothing  
      End Sub  
End Class  
  
' ClientGetAsync issues the async request.  
Class ClientGetAsync  
   Shared allDone As New ManualResetEvent(False)  
      Const BUFFER_SIZE As Integer = 1024  
  
    Shared Sub Main()  
        Dim Args As String() = Environment.GetCommandLineArgs()  
  
        If Args.Length < 2 Then  
            ShowUsage()  
            Return  
        End If  
  
      ' Get the URI from the command line.  
        Dim HttpSite As Uri = New Uri(Args(1))  
  
      ' Create the request object.  
        Dim wreq As HttpWebRequest = _  
           CType(WebRequest.Create(HttpSite), HttpWebRequest)  
  
      ' Create the state object.  
      Dim rs As RequestState = New RequestState()  
  
      ' Put the request into the state so it can be passed around.  
      rs.Request = wreq  
  
      ' Issue the async request.  
        Dim r As IAsyncResult = _  
           CType(wreq.BeginGetResponse( _  
           New AsyncCallback(AddressOf RespCallback), rs), IAsyncResult)  
  
      ' Wait until the ManualResetEvent is set so that the application  
      ' does not exit until after the callback is called.  
        allDone.WaitOne()  
    End Sub  
  
    Shared Sub ShowUsage()  
        Console.WriteLine("Attempts to GET a URI")  
        Console.WriteLine()  
        Console.WriteLine("Usage:")  
        Console.WriteLine("ClientGetAsync URI")  
        Console.WriteLine("Examples:")  
        Console.WriteLine("ClientGetAsync http://www.contoso.com/")  
    End Sub  
  
    Shared Sub RespCallback(ar As IAsyncResult)  
       ' Get the RequestState object from the async result.  
       Dim rs As RequestState = CType(ar.AsyncState, RequestState)  
  
       ' Get the HttpWebRequest from RequestState.  
       Dim req As HttpWebRequest= rs.Request  
  
       ' Call EndGetResponse, which returns the HttpWebResponse object  
       ' that came from the request issued above.  
       Dim resp As HttpWebResponse = _  
           CType(req.EndGetResponse(ar), HttpWebResponse)  
  
       ' Start reading data from the respons stream.  
       Dim ResponseStream As Stream = resp.GetResponseStream()  
  
       ' Store the reponse stream in RequestState to read  
       ' the stream asynchronously.  
       rs.ResponseStream = ResponseStream  
  
       ' Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead.  
       Dim iarRead As IAsyncResult = _  
          ResponseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
          New AsyncCallback(AddressOf ReadCallBack), rs)  
    End Sub  
  
   Shared Sub ReadCallBack(asyncResult As IAsyncResult)  
      ' Get the RequestState object from the AsyncResult.  
      Dim rs As RequestState = CType(asyncResult.AsyncState, RequestState)  
  
      ' Retrieve the ResponseStream that was set in RespCallback.  
      Dim responseStream As Stream = rs.ResponseStream  
  
      ' Read rs.BufferRead to verify that it contains data.  
      Dim read As Integer = responseStream.EndRead( asyncResult )  
      If read > 0 Then  
         ' Prepare a Char array buffer for converting to Unicode.  
         Dim charBuffer(1024) As Char  
  
         ' Convert byte stream to Char array and then String.  
         ' len contains the number of characters converted to Unicode.  
         Dim len As Integer = _  
           rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0)  
         Dim str As String = new String(charBuffer, 0, len)      
  
         ' Append the recently read data to the RequestData stringbuilder   
         ' object contained in RequestState.  
         rs.RequestData.Append( _  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read))  
  
         ' Continue reading data until responseStream.EndRead  
         ' returns –1.  
         Dim ar As IAsyncResult = _  
            responseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
            New AsyncCallback(AddressOf ReadCallBack), rs)  
      Else  
          If rs.RequestData.Length > 1 Then  
            ' Display data to the console.  
            Dim strContent As String  
            strContent = rs.RequestData.ToString()  
            Console.WriteLine(strContent)  
         End If  
  
         ' Close down the response stream.  
         responseStream.Close()  
  
         ' Set the ManualResetEvent so the main thread can exit.  
         allDone.Set()  
      End If  
  
      Return  
   End Sub  
End Class  
```  
  
## <a name="see-also"></a>Viz také  
 [Žádosti o data](../../../docs/framework/network-programming/requesting-data.md)
