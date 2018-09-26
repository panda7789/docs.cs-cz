---
title: 'Postupy: odesílání dat pomocí třídy WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f62775a41f70e4dd96c749acd99bf8b850d96407
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084953"
---
# <a name="how-to-send-data-using-the-webrequest-class"></a>Postupy: odesílání dat pomocí třídy WebRequest
Následující postup popisuje kroky, které používají k odesílání dat na server. Tento postup se běžně používá k odesílání dat na webovou stránku.  
  
### <a name="to-send-data-to-a-host-server"></a>K odesílání dat na hostitelský server  
  
1.  Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A> s identifikátorem URI prostředku, který přijímá data, například, skript nebo stránky ASP.NET.  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  Rozhraní .NET Framework poskytuje třídy pro konkrétní odvozený z **WebRequest** a **WebResponse** pro identifikátory URI, které začínají řetězcem "http:", "protokol https:", "ftp:", a "souboru:". Přístup k prostředkům prostřednictvím jiné protokoly, je nutné implementovat, které jsou odvozeny z třídy pro konkrétní **WebRequest** a **WebResponse**. Další informace najdete v tématu [programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .  
  
2.  Nastavte všechny hodnoty vlastností, které budete potřebovat v **WebRequest**. Například chcete-li povolit ověřování, nastavte **pověření** vlastnost instance <xref:System.Net.NetworkCredential> třídy.  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     Ve většině případů **WebRequest** je dostačující k odesílání dat k řazení samotné. Nicméně, pokud je potřeba nastavit vlastnosti specifické pro protokol, musíte přetypovat **WebRequest** na konkrétní typ. Například pro přístup k protokolu HTTP specifické vlastnostem <xref:System.Net.HttpWebRequest>, vícesměrového vysílání **WebRequest** do **HttpWebRequest** odkaz. Následující příklad kódu ukazuje, jak nastavit konkrétní HTTP <xref:System.Net.HttpWebRequest.UserAgent%2A> vlastnost.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Zadejte metodu protokolu, která povoluje ukládání dat k odeslání požadavku, jako je například HTTP **příspěvek** metody.  
  
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
  
6.  Získání datového proudu, obsahuje data žádosti voláním <xref:System.Net.WebRequest.GetRequestStream%2A> metody.  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  Zapsat data do <xref:System.IO.Stream> objekt vrácený touto metodou.  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  Zavřete datový proud požadavku voláním **Stream.Close** metody.  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. Odesílání požadavku na server voláním <xref:System.Net.WebRequest.GetResponse%2A>. Tato metoda vrátí objekt, který obsahuje odpověď serveru. Vrácený <xref:System.Net.WebResponse> typ objektu je určeno schéma identifikátoru URI požadavku.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Po dokončení <xref:System.Net.WebResponse> objektu, je nutné zavřít voláním <xref:System.Net.WebResponse.Close%2A> metody. Případně, pokud datový proud odpovědí jste získali z objektu odpovědi, můžete zavřít datový proud voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Pokud instalací neukončíte odpovědi nebo datový proud, může vaše aplikace vyčerpala volné připojení k serveru nebo budou moct zpracovávat další požadavky.  
  
10. Můžete přístup k vlastnostem **WebResponse** nebo přetypovat **WebResponse** na konkrétní instanci číst vlastnosti specifické pro protokol. Například pro přístup k protokolu HTTP specifické vlastnostem <xref:System.Net.HttpWebResponse>, vícesměrového vysílání **WebResponse** do **HttpWebResponse** odkaz.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Chcete-li získat datový proud s daty odpověď odesílanou serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A> metodu **WebResponse**.  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. Po načtení dat z odpovědi, musíte buď zavřít pomocí datového proudu odpovědi **Stream.Close** metody nebo Zavřít odpověď pomocí **WebResponse.Close** metody. Není nutné volat **Zavřít** metoda u datového proudu s odpovědí a **WebResponse**, ale to uděláte tak, není škodlivé.  
  
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
 [Vytváření internetových žádostí](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [Použití streamů v síti](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Přístup k internetu přes proxy server](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Žádosti o data](../../../docs/framework/network-programming/requesting-data.md)  
 [Postupy:Vyžádání dat pomocí třídy WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
