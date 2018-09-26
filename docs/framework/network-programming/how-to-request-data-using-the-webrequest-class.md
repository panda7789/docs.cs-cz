---
title: 'Postupy: vyžádání dat pomocí třídy WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8928ce8790f58b6920c16cbfd9fc8d9aa6644a44
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47197822"
---
# <a name="how-to-request-data-using-the-webrequest-class"></a>Postupy: vyžádání dat pomocí třídy WebRequest
Následující postup popisuje kroky používaná pro požádání o prostředku ze serveru, například webovou stránku nebo soubor. Prostředek musí být označeny identifikátorem URI.  
  
### <a name="to-request-data-from-a-host-server"></a>Žádost o data z hostitelského serveru  
  
1.  Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A> s identifikátorem URI prostředku.  
  
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
  
     Ve většině případů **WebRequest** třídy je dostačující přijímat data. Nicméně, pokud je potřeba nastavit vlastnosti specifické pro protokol, musíte přetypovat **WebRequest** na konkrétní typ. Například pro přístup k protokolu HTTP specifické vlastnostem <xref:System.Net.HttpWebRequest>, vícesměrového vysílání **WebRequest** do **HttpWebRequest** odkaz. Následující příklad kódu ukazuje, jak nastavit konkrétní HTTP <xref:System.Net.HttpWebRequest.UserAgent%2A> vlastnost.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Chcete-li odeslat požadavek na server, zavolejte <xref:System.Net.HttpWebRequest.GetResponse%2A>. Skutečný typ vrácený **WebResponse** objektu se určuje podle schématu požadovaný identifikátor URI.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Po dokončení <xref:System.Net.WebResponse> objektu, je nutné zavřít voláním <xref:System.Net.WebResponse.Close%2A> metody. Případně, pokud datový proud odpovědí jste získali z objektu odpovědi, můžete zavřít datový proud voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Pokud instalací neukončíte odpovědi nebo datový proud, může vaše aplikace vyčerpala volné připojení k serveru nebo budou moct zpracovávat další požadavky.  
  
4.  Můžete přístup k vlastnostem **WebResponse** nebo přetypovat **WebResponse** na konkrétní instanci číst vlastnosti specifické pro protokol. Například pro přístup k protokolu HTTP specifické vlastnostem <xref:System.Net.HttpWebResponse>, vícesměrového vysílání **WebResponse** k **HttpWebResponse** odkaz. Následující příklad kódu ukazuje, jak zobrazit informace o stavu odeslaných odpovědí.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  Chcete-li získat datový proud s daty odpověď odesílanou serverem, použijte <xref:System.Net.HttpWebResponse.GetResponseStream%2A> metodu **WebResponse**.  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  Po načtení dat z odpovědi, musíte buď zavřít pomocí datového proudu odpovědi **Stream.Close** metody nebo Zavřít odpověď pomocí **WebResponse.Close** metody. Není nutné volat **Zavřít** metoda u datového proudu s odpovědí a **WebResponse**, ale to uděláte tak, není škodlivé. **WebResponse.Close** volání **Stream.Close** při zavření odpovědi.  
  
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
    public class WebRequestGetExample  
    {  
        public static void Main()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create(  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close();  
            response.Close();  
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
    Public Class WebRequestGetExample  
  
        Public Shared Sub Main()  
            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams and the response.  
            reader.Close()  
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
 [Postupy:Odeslání dat pomocí třídy WebRequest](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
