---
title: 'Postupy: Odesílání dat pomocí třídy WebRequest'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 3878a94debc7066cb8ace3b119d95d3b76d91610
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322872"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Postupy: Odesílání dat pomocí třídy WebRequest
Následující postup popisuje kroky k odesílání dat na server. Tento postup se běžně používá k odesílání dat na webovou stránku. 
  
## <a name="to-send-data-to-a-host-server"></a>K odesílání dat na hostitelský server  
  
1. Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku, jako je skript nebo stránky ASP.NET, která přijímá data. Příklad: 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")  
    ```  
  
    > [!NOTE]
    > Rozhraní .NET Framework poskytuje konkrétní třídy odvozené od <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy pro identifikátory URI, které začínají *http:*, *https:*, *ftp:* , a *souboru:*.
    Pokud je potřeba sada nebo čtení vlastnosti specifické pro protokol, musíte přetypovat vaše <xref:System.Net.WebRequest> nebo <xref:System.Net.WebResponse> objektu na typ object specifický pro protokol. Další informace najdete v tématu [programování připojitelných protokolů](programming-pluggable-protocols.md). 
  
2. Nastavte všechny hodnoty vlastností, které potřebujete ve vaší `WebRequest` objektu. Například chcete-li povolit ověřování, nastavte <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> vlastnost instance <xref:System.Net.NetworkCredential> třídy:
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3. Zadejte metodu protokolu, která povoluje ukládání dat k odeslání požadavku, jako je například HTTP `POST` metody:  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4. Nastavte <xref:System.Web.HttpRequest.ContentLength> na počet bajtů zahrnutí při zpracování požadavku. Příklad: 
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5. Nastavte <xref:System.Web.HttpRequest.ContentType> vlastnost na odpovídající hodnotu. Příklad:
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6. Získání datového proudu, obsahuje data žádosti voláním <xref:System.Net.WebRequest.GetRequestStream%2A> metody. Příklad:
  
    ```csharp  
    Stream dataStream = request.GetRequestStream();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream()  
    ```  
  
7. Zapsat data do <xref:System.IO.Stream> vrácený `GetRequestStream` metody. Příklad:
  
    ```csharp  
    dataStream.Write(byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write(byteArray, 0, byteArray.Length)  
    ```  
  
8. Zavřete datový proud požadavku voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Příklad:
  
    ```csharp  
    dataStream.Close();  
    ```  
  
    ```vb  
    dataStream.Close()  
    ```  
  
9. Odesílání požadavku na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Tato metoda vrátí objekt, který obsahuje odpověď serveru. Vrácený `WebResponse` typ objektu je určeno schéma identifikátoru URI požadavku. Příklad:
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
10. Můžete přistupovat k vlastnosti vaší `WebResponse` objektu nebo přetypování na konkrétní instanci číst vlastnosti specifické pro protokol. 

    Například pro přístup k protokolu HTTP specifické vlastnostem <xref:System.Net.HttpWebResponse>, vícesměrového vysílání vaše `WebResponse` objektu <xref:System.Net.HttpWebResponse> odkaz. Následující příklad kódu ukazuje, jak zobrazit konkrétní HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> vlastnost odeslaných odpovědí:
  
    ```csharp  
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);    
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Chcete-li získat datový proud s daty odpověď odesílanou serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodu vaše `WebResponse` objektu. Příklad:
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
12. Po přečtení dat z objektu odpovědi, buď ji zavřít <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody nebo zavřít pomocí datového proudu odpovědi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metoda. Nezavírejte odpovědi nebo datový proud, může vaše aplikace vyčerpala volné připojení k serveru nebo stát nemůže zpracovat požadavky. Protože `WebResponse.Close` volání metody `Stream.Close` když se toto okno zavře odpověď, není nutné volat `Close` na objekty odpovědi i datový proud, i když to není tak škodlivé. Příklad:
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Příklad  
  
Následující příklad kódu ukazuje, jak odesílat data do webového serveru a tato data číst v odpovědi:  

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a>Viz také:

- [Vytváření internetových žádostí](creating-internet-requests.md)
- [Použití streamů v síti](using-streams-on-the-network.md)
- [Přístup k Internetu prostřednictvím proxy serveru](accessing-the-internet-through-a-proxy.md)
- [Požadavek na data](requesting-data.md)
- [Postupy: Data žádosti pomocí třídy WebRequest](how-to-request-data-using-the-webrequest-class.md)
