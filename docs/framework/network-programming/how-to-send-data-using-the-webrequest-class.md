---
title: "Postupy: odesílání dat pomocí třídy WebRequest"
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
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2102fce150f512a49093eb2b214258ac35e276e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-send-data-using-the-webrequest-class"></a>Postupy: odesílání dat pomocí třídy WebRequest
Následující postup popisuje kroky, které používají k odesílání dat na server. Tento postup se běžně používá k odesílání dat na webové stránce.  
  
### <a name="to-send-data-to-a-host-server"></a>Odesílání dat na server hostitele  
  
1.  Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A> s identifikátorem URI prostředku, který přijímá data, například, skript nebo stránku ASP.NET.  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  Rozhraní .NET Framework poskytuje specifické třídy odvozené od **WebRequest** a **WebResponse** pro identifikátory URI, který začíná "http:", "https:", "ftp:", a "souboru:". Přístup k prostředkům pomocí jiné protokoly, je nutné implementovat specifické třídy, které jsou odvozeny od **WebRequest** a **WebResponse**. Další informace najdete v tématu [programování modulární protokoly](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .  
  
2.  Nastavit všechny hodnoty vlastností, které potřebujete ve **WebRequest**. Například pokud chcete povolit ověřování, nastavit **pověření** vlastnost, která má instance <xref:System.Net.NetworkCredential> – třída.  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     Ve většině případů **WebRequest** k odesílání dat stačí samotná instance. Ale pokud je nutné nastavit vlastnosti specifické pro protokol, musíte vysílat **WebRequest** specifické pro protokol typu. Například pro přístup k protokolu HTTP specifické vlastnosti <xref:System.Net.HttpWebRequest>, vícesměrového vysílání **WebRequest** k **HttpWebRequest** odkaz. Následující příklad kódu ukazuje, jak nastavit HTTP specifické <xref:System.Net.HttpWebRequest.UserAgent%2A> vlastnost.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Zadejte metodu protokolu, která umožňuje data k odeslání s žádostí, jako je například HTTP **POST** metoda.  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  Nastavte **ContentLength** vlastnost.  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  Nastavte **ContentType** vlastnost na odpovídající hodnotu.  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  Get datového proudu, že data žádosti blokování voláním <xref:System.Net.WebRequest.GetRequestStream%2A> metoda.  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  Zapsat data do <xref:System.IO.Stream> objekt vrácená touto metodou.  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  Zavřít datový proud požadavku voláním **Stream.Close** metoda.  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. Odeslat požadavek na server voláním <xref:System.Net.WebRequest.GetResponse%2A>. Tato metoda vrátí objekt, který obsahuje odpověď serveru. Vrácený <xref:System.Net.WebResponse> typ objektu je dáno schéma identifikátoru URI žádosti.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Po dokončení <xref:System.Net.WebResponse> objekt, je třeba nejprve zavřít voláním <xref:System.Net.WebResponse.Close%2A> metoda. Případně, pokud budete mít, že podmínky datového proudu odpovědi z objektu odpovědi, můžete zavřít datový proud voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metoda. Pokud nezavřete odpovědi nebo datový proud, aplikace můžete spustit z připojení k serveru a stát se nepodařilo zpracovat další požadavky.  
  
10. Můžete přístup k vlastnostem **WebResponse** nebo přetypovat **WebResponse** do instance specifické pro protokol číst vlastnosti specifické pro protokol. Například pro přístup k protokolu HTTP specifické vlastnosti <xref:System.Net.HttpWebResponse>, vícesměrového vysílání **WebResponse** k **HttpWebResponse** odkaz.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Chcete-li získat datový proud obsahující data odpověď odesílanou serverem, volejte <xref:System.Net.WebResponse.GetResponseStream%2A> metodu **WebResponse**.  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. Po načtení dat z odpovědi, je nutné buď zavřít pomocí datového proudu odpovědi **Stream.Close** metoda nebo zavřít pomocí odpovědi **WebResponse.Close** metoda. Není nutné volat **Zavřít** metodu proudu odpovědi a **WebResponse**, ale to tak není škodlivý.  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Příklad  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestPostExample  
    {  
        public static void Main ()  
        {  
            // Create a request using a URL that can receive a post.   
            WebRequest request = WebRequest.Create ("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  
            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes (postData);  
            // Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length;  
            // Get the request stream.  
            Stream dataStream = request.GetRequestStream ();  
            // Write the data to the request stream.  
            dataStream.Write (byteArray, 0, byteArray.Length);  
            // Close the Stream object.  
            dataStream.Close ();  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams.  
            reader.Close ();  
            dataStream.Close ();  
            response.Close ();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  
Namespace Examples.System.Net  
    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  
            ' Create a request using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  
            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  
            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  
            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the Stream object.  
            dataStream.Close()  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams.  
            reader.Close()  
            dataStream.Close()  
            response.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření žádostí o Internetu](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [Pomocí datových proudů v síti](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Přístup k Internetu prostřednictvím proxy serveru](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Požadavek na Data](../../../docs/framework/network-programming/requesting-data.md)  
 [Postupy: použití třídy WebRequest Data žádosti](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
