---
title: 'Postupy: použití třídy WebRequest Data žádosti'
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
manager: markl
ms.openlocfilehash: e02ad4772d3ba84a2735a2e146a9979862d75989
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397712"
---
# <a name="how-to-request-data-using-the-webrequest-class"></a>Postupy: použití třídy WebRequest Data žádosti
Následující postup popisuje kroky, které slouží k vyžádání prostředku ze serveru, například, webovou stránku nebo soubor. Prostředek musí být identifikovaného identifikátorem URI.  
  
### <a name="to-request-data-from-a-host-server"></a>Žádost o data ze serveru hostitele  
  
1.  Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A> s identifikátorem URI prostředku.  
  
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
  
     Ve většině případů **WebRequest** třída je dostatečná přijímat data. Ale pokud je nutné nastavit vlastnosti specifické pro protokol, musíte vysílat **WebRequest** specifické pro protokol typu. Například pro přístup k protokolu HTTP specifické vlastnosti <xref:System.Net.HttpWebRequest>, vícesměrového vysílání **WebRequest** k **HttpWebRequest** odkaz. Následující příklad kódu ukazuje, jak nastavit HTTP specifické <xref:System.Net.HttpWebRequest.UserAgent%2A> vlastnost.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Odeslat požadavek na server, volání <xref:System.Net.HttpWebRequest.GetResponse%2A>. Skutečný typ vrácený **WebResponse** objektu je dáno schéma požadovaný identifikátor URI.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Po dokončení <xref:System.Net.WebResponse> objekt, je třeba nejprve zavřít voláním <xref:System.Net.WebResponse.Close%2A> metoda. Případně, pokud budete mít, že podmínky datového proudu odpovědi z objektu odpovědi, můžete zavřít datový proud voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metoda. Pokud nezavřete odpovědi nebo datový proud, aplikace můžete spustit z připojení k serveru a stát se nepodařilo zpracovat další požadavky.  
  
4.  Můžete přístup k vlastnostem **WebResponse** nebo přetypovat **WebResponse** do instance specifické pro protokol číst vlastnosti specifické pro protokol. Například pro přístup k protokolu HTTP specifické vlastnosti <xref:System.Net.HttpWebResponse>, vícesměrového vysílání **WebResponse** k **HttpWebResponse** odkaz. Následující příklad kódu ukazuje, jak zobrazit informace o stavu odeslané s odpovědí.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  Datový proud obsahující data odpověď odeslaná na server, použijte <xref:System.Net.HttpWebResponse.GetResponseStream%2A> metodu **WebResponse**.  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  Po načtení dat z odpovědi, je nutné buď zavřít pomocí datového proudu odpovědi **Stream.Close** metoda nebo zavřít pomocí odpovědi **WebResponse.Close** metoda. Není nutné volat **Zavřít** metodu proudu odpovědi a **WebResponse**, ale to tak není škodlivý. **WebResponse.Close** volání **Stream.Close** při zavření odpovědi.  
  
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
