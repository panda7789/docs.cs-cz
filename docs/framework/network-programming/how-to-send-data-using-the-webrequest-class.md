---
title: 'Postupy: odesílání dat pomocí třídy WebRequest'
description: Naučte se, jak odesílat data na server pomocí třídy WebRequest v .NET Framework. Tento postup se běžně používá k odesílání dat na webovou stránku.
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 4b353250fec778ee8b352f13de6d7faaf15c13ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502441"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Postupy: odesílání dat pomocí třídy WebRequest

Následující postup popisuje kroky k odeslání dat na server. Tento postup se běžně používá k odeslání dat na webovou stránku.

## <a name="to-send-data-to-a-host-server"></a>Odeslání dat na hostitelský server

1. Vytvořte <xref:System.Net.WebRequest> instanci voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku, jako je například skript nebo stránka ASP.NET, která přijímá data. Příklad:

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > .NET Framework poskytuje třídy specifické pro protokol odvozené z <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> tříd a pro identifikátory URI, které začínají na *http:*, *https:*, *FTP:* a *File:*.

    Pokud potřebujete nastavit nebo číst vlastnosti specifické pro protokol, musíte přetypovat <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> objekt nebo na typ objektu specifický pro protokol. Další informace najdete v tématu [programování protokolů pro připojení](programming-pluggable-protocols.md).

2. Nastavte všechny hodnoty vlastností, které v objektu potřebujete `WebRequest` . Chcete-li například povolit ověřování, nastavte <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> vlastnost na instanci <xref:System.Net.NetworkCredential> třídy:

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. Zadejte metodu protokolu, která umožňuje odesílat data s požadavkem, jako je například `POST` Metoda http:

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. Nastavte <xref:System.Web.HttpRequest.ContentLength> vlastnost na počet bajtů, které jsou součástí vaší žádosti. Příklad:

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

9. Odešle požadavek na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> . Tato metoda vrátí objekt obsahující odpověď serveru. Typ vráceného `WebResponse` objektu je určen schématem identifikátoru URI žádosti. Příklad:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. Můžete získat přístup k vlastnostem `WebResponse` objektu nebo ho přetypovat na instanci specifickou pro protokol pro čtení vlastností specifických pro protokol.

    Chcete-li například získat přístup k vlastnostem specifickým pro protokol HTTP <xref:System.Net.HttpWebResponse> , přetypování `WebResponse` objektu na <xref:System.Net.HttpWebResponse> odkaz. Následující příklad kódu ukazuje, jak zobrazit vlastnost specifickou pro protokol HTTP <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> odeslanou odpovědí:

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

12. Po načtení dat z objektu Response ho buď zavřete, a to pomocí <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody, nebo zavřete datový proud odpovědi s <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> metodou. Pokud nezavřete odpověď nebo datový proud, může aplikace vysílat připojení k serveru a nebude možné zpracovat další požadavky. Vzhledem k tomu, že `WebResponse.Close` metoda volá `Stream.Close` , když je odpověď zavřená, není nutné volat `Close` na objekty Response a Stream, i když tak nebudete mít škodlivou. Příklad:

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
- [Postupy: vyžádání dat pomocí třídy WebRequest](how-to-request-data-using-the-webrequest-class.md)
