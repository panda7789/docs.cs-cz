---
title: 'Postupy: Data žádosti pomocí třídy WebRequest'
ms.date: 03/21/2019
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
ms.openlocfilehash: df61b533801abc4c826d3e711228305c9452498a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819535"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Postupy: Data žádosti pomocí třídy WebRequest
Následující postup popisuje kroky pro žádost o prostředek, například webovou stránku nebo soubor, ze serveru. Prostředek musí být označeny identifikátorem URI.  
  
## <a name="to-request-data-from-a-host-server"></a>Žádost o data z hostitelského serveru  
  
1.  Vytvoření <xref:System.Net.WebRequest> instance voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku. Příklad: 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")  
    ```  
  
    > [!NOTE]
    > Rozhraní .NET Framework poskytuje konkrétní třídy odvozené od <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy pro identifikátory URI, které začínají *http:*, *https:*, *ftp:* , a *souboru:*.
    Pokud je potřeba sada nebo čtení vlastnosti specifické pro protokol, musíte přetypovat vaše <xref:System.Net.WebRequest> nebo <xref:System.Net.WebResponse> objektu na typ object specifický pro protokol. Další informace najdete v tématu [programování připojitelných protokolů](programming-pluggable-protocols.md). 
  
2.  Nastavte všechny hodnoty vlastností, které potřebujete ve vaší `WebRequest` objektu. Například chcete-li povolit ověřování, nastavte <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> vlastnost instance <xref:System.Net.NetworkCredential> třídy:  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  Odesílání požadavku na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Tato metoda vrátí objekt, který obsahuje odpověď serveru. Vrácený <xref:System.Net.WebResponse> typ objektu je určeno schéma identifikátoru URI požadavku. Příklad:
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
4.  Můžete přistupovat k vlastnosti vaší `WebResponse` objektu nebo přetypování na konkrétní instanci číst vlastnosti specifické pro protokol. 

    Například pro přístup k protokolu HTTP specifické vlastnostem <xref:System.Net.HttpWebResponse>, vícesměrového vysílání vaše `WebResponse` objektu `HttpWebResponse` odkaz. Následující příklad kódu ukazuje, jak zobrazit konkrétní HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> vlastnost odeslaných odpovědí:
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  Chcete-li získat datový proud s daty odpověď odesílanou serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody. Příklad:  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  Po přečtení dat z objektu odpovědi, buď ji zavřít <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody nebo zavřít pomocí datového proudu odpovědi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metoda. Nezavírejte objektu odpovědi nebo datový proud, může vaše aplikace vyčerpala volné připojení k serveru nebo stát nemůže zpracovat požadavky. Protože `WebResponse.Close` volání metody `Stream.Close` když se toto okno zavře odpověď, není nutné volat `Close` na objekty odpovědi i datový proud, i když to není tak škodlivé. Příklad:
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Příklad  

Následující příklad kódu ukazuje, jak vytvořit požadavek na webový server a načtěte data v odpovědi:  
  
[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

  
## <a name="see-also"></a>Viz také:
- [Vytváření internetových žádostí](creating-internet-requests.md)
- [Použití streamů v síti](using-streams-on-the-network.md)
- [Přístup k Internetu prostřednictvím proxy serveru](accessing-the-internet-through-a-proxy.md)
- [Požadavek na data](requesting-data.md)
- [Postupy: Odesílání dat pomocí třídy WebRequest](how-to-send-data-using-the-webrequest-class.md)
