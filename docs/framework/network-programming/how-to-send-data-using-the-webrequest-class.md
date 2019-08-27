---
title: 'Postupy: Odeslání dat pomocí třídy WebRequest'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040832"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Postupy: Odeslání dat pomocí třídy WebRequest

Následující postup popisuje kroky k odeslání dat na server. Tento postup se běžně používá k odeslání dat na webovou stránku.

## <a name="to-send-data-to-a-host-server"></a>Odeslání dat na hostitelský server

1. Vytvořte instanci voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku, jako je například skript nebo stránka ASP.NET, která přijímá data. <xref:System.Net.WebRequest> Příklad:

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > .NET Framework poskytuje třídy <xref:System.Net.WebRequest> specifické pro protokol odvozené z tříd a <xref:System.Net.WebResponse> pro identifikátory URI, které začínají na *http:* , *https:* , *FTP:* a *File:* .

    Pokud potřebujete nastavit nebo číst vlastnosti specifické pro protokol, musíte přetypovat <xref:System.Net.WebRequest> objekt nebo <xref:System.Net.WebResponse> na typ objektu specifický pro protokol. Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).

2. Nastavte všechny hodnoty vlastností, které v `WebRequest` objektu potřebujete. Chcete-li například povolit ověřování, nastavte <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> vlastnost na instanci <xref:System.Net.NetworkCredential> třídy:

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. Zadejte metodu protokolu, která umožňuje odesílat data s požadavkem, jako je například metoda HTTP `POST` :

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <xref:System.Web.HttpRequest.ContentLength> Nastavte vlastnost na počet bajtů, které jsou součástí vaší žádosti. Příklad:

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <xref:System.Web.HttpRequest.ContentType> Nastavte vlastnost na odpovídající hodnotu. Příklad:

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. Získejte datový proud, který uchovává data požadavků, voláním <xref:System.Net.WebRequest.GetRequestStream%2A> metody. Příklad:

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. Zápis dat do <xref:System.IO.Stream> objektu vráceného `GetRequestStream` metodou. Příklad:

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. Uzavřete datový proud požadavku voláním <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metody. Příklad:

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. Odešle požadavek na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Tato metoda vrátí objekt obsahující odpověď serveru. Typ vráceného `WebResponse` objektu je určen schématem identifikátoru URI žádosti. Příklad:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. Můžete získat přístup k vlastnostem `WebResponse` objektu nebo ho přetypovat na instanci specifickou pro protokol pro čtení vlastností specifických pro protokol.

    Chcete-li například získat přístup k vlastnostem <xref:System.Net.HttpWebResponse>specifickým pro protokol HTTP, `WebResponse` přetypování <xref:System.Net.HttpWebResponse> objektu na odkaz. Následující příklad kódu ukazuje, jak zobrazit vlastnost specifickou <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> pro protokol HTTP odeslanou odpovědí:

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. Chcete-li získat datový proud obsahující data odpovědí odesílaná serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodu `WebResponse` objektu. Příklad:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. Po načtení dat z objektu Response ho buď zavřete, a to pomocí <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody, nebo zavřete datový proud odpovědi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> s metodou. Pokud nezavřete odpověď nebo datový proud, může aplikace vysílat připojení k serveru a nebude možné zpracovat další požadavky. Vzhledem k tomu, `Stream.Close` že `Close` metodavolá,kdyžjeodpověďzavřená,nenínutnévolatnaobjektyResponseaStream,ikdyžtaknebudete`WebResponse.Close` mít škodlivou. Příklad:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak odesílat data na webový server a číst data v odpovědi:

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a>Viz také:

- [Vytváření internetových požadavků](creating-internet-requests.md)
- [Použití datových proudů v síti](using-streams-on-the-network.md)
- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
- [Vyžádání dat](requesting-data.md)
- [Postupy: Vyžádání dat pomocí třídy WebRequest](how-to-request-data-using-the-webrequest-class.md)
