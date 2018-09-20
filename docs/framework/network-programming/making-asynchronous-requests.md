---
title: Vytváření asynchronních žádostí
ms.date: 03/30/2017
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0f5729f0a3d36a631b227c77de51f68b95e8df22
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326605"
---
# <a name="making-asynchronous-requests"></a><span data-ttu-id="bef24-102">Vytváření asynchronních žádostí</span><span class="sxs-lookup"><span data-stu-id="bef24-102">Making Asynchronous Requests</span></span>
<span data-ttu-id="bef24-103"><xref:System.Net> Třídy pomocí rozhraní .NET Framework standardní asynchronní programovací model pro asynchronní přístup k internetovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="bef24-103">The <xref:System.Net> classes use the .NET Framework's standard asynchronous programming model for asynchronous access to Internet resources.</span></span> <span data-ttu-id="bef24-104"><xref:System.Net.WebRequest.BeginGetResponse%2A> a <xref:System.Net.WebRequest.EndGetResponse%2A> metody <xref:System.Net.WebRequest> třídy zahájení a dokončení asynchronní požadavky na internetové prostředky.</span><span class="sxs-lookup"><span data-stu-id="bef24-104">The <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods of the <xref:System.Net.WebRequest> class start and complete asynchronous requests for an Internet resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bef24-105">Použití synchronní volání v asynchronní zpětné volání metod může způsobit snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="bef24-105">Using synchronous calls in asynchronous callback methods can result in severe performance penalties.</span></span> <span data-ttu-id="bef24-106">Internet požadavky provedené přes **WebRequest** a jejích potomků musí používat <xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> číst stream vrácený poskytovatelem <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="bef24-106">Internet requests made with **WebRequest** and its descendants must use <xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> to read the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="bef24-107">Následující ukázkový kód ukazuje, jak použít asynchronní volání s **WebRequest** třídy.</span><span class="sxs-lookup"><span data-stu-id="bef24-107">The following sample code demonstrates how to use asynchronous calls with the **WebRequest** class.</span></span> <span data-ttu-id="bef24-108">Vzorek je konzolový program, který přebírá identifikátor UIR z příkazového řádku, požadavek na prostředek v identifikátoru URI a potom zobrazí data do konzoly přijatá z Internetu.</span><span class="sxs-lookup"><span data-stu-id="bef24-108">The sample is a console program that takes a URI from the command line, requests the resource at the URI, and then prints data to the console as it is received from the Internet.</span></span>  
  
 <span data-ttu-id="bef24-109">Program definuje dvě třídy pro vlastní použití, **RequestState** třídu, která předá data napříč byla zahájena asynchronní volání, a **ClientGetAsync** třídy, která implementuje asynchronního požadavku pro Internetového zdroji.</span><span class="sxs-lookup"><span data-stu-id="bef24-109">The program defines two classes for its own use, the **RequestState** class, which passes data across asynchronous calls, and the **ClientGetAsync** class, which implements the asynchronous request to an Internet resource.</span></span>  
  
 <span data-ttu-id="bef24-110">**RequestState** třídy zachovává stav žádosti napříč volání asynchronní metody, které služby pro tuto žádost.</span><span class="sxs-lookup"><span data-stu-id="bef24-110">The **RequestState** class preserves the state of the request across calls to the asynchronous methods that service the request.</span></span> <span data-ttu-id="bef24-111">Obsahuje **WebRequest** a <xref:System.IO.Stream> instancí, které obsahují aktuální požadavek na prostředek a datový proud vyrovnávací paměti, která obsahuje data aktuálně přijatá z internetového zdroji a jakoodpověď<xref:System.Text.StringBuilder> , který obsahuje úplnou odpověď.</span><span class="sxs-lookup"><span data-stu-id="bef24-111">It contains **WebRequest** and <xref:System.IO.Stream> instances that contain the current request to the resource and the stream received in response, a buffer that contains the data currently received from the Internet resource, and a <xref:System.Text.StringBuilder> that contains the complete response.</span></span> <span data-ttu-id="bef24-112">A **RequestState** je předán jako *stavu* parametr při <xref:System.AsyncCallback> metoda je registrovaný pomocí **WebRequest.BeginGetResponse**.</span><span class="sxs-lookup"><span data-stu-id="bef24-112">A **RequestState** is passed as the *state* parameter when the <xref:System.AsyncCallback> method is registered with **WebRequest.BeginGetResponse**.</span></span>  
  
 <span data-ttu-id="bef24-113">**ClientGetAsync** třída implementuje asynchronního požadavku k internetového zdroji a zapíše výsledný odpovědi do konzoly.</span><span class="sxs-lookup"><span data-stu-id="bef24-113">The **ClientGetAsync** class implements an asynchronous request to an Internet resource and writes the resulting response to the console.</span></span> <span data-ttu-id="bef24-114">Obsahuje metody a vlastnosti, které je popsáno v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="bef24-114">It contains the methods and properties described in the following list.</span></span>  
  
-   <span data-ttu-id="bef24-115">`allDone` Vlastnost obsahuje instanci <xref:System.Threading.ManualResetEvent> třídu, která signalizuje dokončení požadavku.</span><span class="sxs-lookup"><span data-stu-id="bef24-115">The `allDone` property contains an instance of the <xref:System.Threading.ManualResetEvent> class that signals the completion of the request.</span></span>  
  
-   <span data-ttu-id="bef24-116">`Main()` Metoda načte příkazového řádku a zahájí žádost o zadaný internetového zdroji.</span><span class="sxs-lookup"><span data-stu-id="bef24-116">The `Main()` method reads the command line and begins the request for the specified Internet resource.</span></span> <span data-ttu-id="bef24-117">Vytváří **WebRequest** `wreq` a **RequestState** `rs`, volání **BeginGetResponse** začala zpracovat požadavek a poté zavolá `allDone.WaitOne()`metodu tak, že aplikace nebude ukončeno až do dokončení zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="bef24-117">It creates the **WebRequest** `wreq` and the **RequestState** `rs`, calls **BeginGetResponse** to begin processing the request, and then calls the `allDone.WaitOne()`method so that the application will not exit until the callback is complete.</span></span> <span data-ttu-id="bef24-118">Poté, co je pro čtení odpovědi z internetového zdroji `Main()` zapisuje do konzoly a ukončením aplikace.</span><span class="sxs-lookup"><span data-stu-id="bef24-118">After the response is read from the Internet resource, `Main()` writes it to the console and the application ends.</span></span>  
  
-   <span data-ttu-id="bef24-119">`showusage()` Metoda zapíše příklad příkazového řádku v konzole.</span><span class="sxs-lookup"><span data-stu-id="bef24-119">The `showusage()` method writes an example command line on the console.</span></span> <span data-ttu-id="bef24-120">Je volána metodou `Main()` při zadaný žádný identifikátor URI na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="bef24-120">It is called by `Main()` when no URI is provided on the command line.</span></span>  
  
-   <span data-ttu-id="bef24-121">`RespCallBack()` Metoda implementuje metodu asynchronní zpětné volání pro daný požadavek Internet.</span><span class="sxs-lookup"><span data-stu-id="bef24-121">The `RespCallBack()` method implements the asynchronous callback method for the Internet request.</span></span> <span data-ttu-id="bef24-122">Vytváří **WebResponse** instance, který obsahuje odpověď z internetového zdroji získá datového proudu odpovědi a pak spustí asynchronnímu čtení dat z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="bef24-122">It creates the **WebResponse** instance containing the response from the Internet resource, gets the response stream, and then starts reading the data from the stream asynchronously.</span></span>  
  
-   <span data-ttu-id="bef24-123">`ReadCallBack()` Metoda implementuje metodu asynchronní zpětné volání pro čtení datového proudu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="bef24-123">The `ReadCallBack()` method implements the asynchronous callback method for reading the response stream.</span></span> <span data-ttu-id="bef24-124">Přenosy dat přijatých z internetového zdroji do **ResponseData** vlastnost **RequestState** instance a potom spustí jiné asynchronní čtení z datového proudu odpovědi, dokud není žádná další data Vrátí.</span><span class="sxs-lookup"><span data-stu-id="bef24-124">It transfers data received from the Internet resource into the **ResponseData** property of the **RequestState** instance, then starts another asynchronous read of the response stream until no more data is returned.</span></span> <span data-ttu-id="bef24-125">Jakmile všechna data byla načtena, `ReadCallBack()` zavře datový proud odpovědí a volání `allDone.Set()` indikace, že je k dispozici v celé odpovědi **ResponseData**.</span><span class="sxs-lookup"><span data-stu-id="bef24-125">Once all the data has been read, `ReadCallBack()` closes the response stream and calls the `allDone.Set()` method to indicate that the entire response is present in **ResponseData**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bef24-126">Je velmi důležité, že všechny datové proudy sítě zavřená.</span><span class="sxs-lookup"><span data-stu-id="bef24-126">It is critical that all network streams are closed.</span></span> <span data-ttu-id="bef24-127">Pokud jste neukončíte každý datový proud požadavku a odpovědi, vaše aplikace vyčerpala volné připojení k serveru a nebudete moct zpracovávat další požadavky.</span><span class="sxs-lookup"><span data-stu-id="bef24-127">If you do not close each request and response stream, your application will run out of connections to the server and be unable to process additional requests.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bef24-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="bef24-128">See Also</span></span>  
 [<span data-ttu-id="bef24-129">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="bef24-129">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
