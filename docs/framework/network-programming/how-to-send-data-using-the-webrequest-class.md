---
title: 'Postup: Odeslání dat pomocí třídy WebRequest'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70040832"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Postup: Odeslání dat pomocí třídy WebRequest

Následující postup popisuje postup odesílání dat na server. Tento postup se běžně používá k zaúčtování dat na webovou stránku.

## <a name="to-send-data-to-a-host-server"></a>Odeslání dat na hostitelský server

1. Vytvořte <xref:System.Net.WebRequest> instanci voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> pomocí identifikátoru URI prostředku, například skriptu nebo stránky ASP.NET, která přijímá data. Například:

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > Rozhraní .NET Framework poskytuje třídy specifické <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> pro protokol odvozené z tříd a pro identifikátory URI začínající *protokolem http:*, *https:* *, ftp:* a *soubor:*.

    Pokud potřebujete nastavit nebo číst vlastnosti specifické pro <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> protokol, musíte přetypovat typ objektu specifického pro protokol. Další informace naleznete [v tématu Programování připojitelných protokolů](programming-pluggable-protocols.md).

2. Nastavte všechny hodnoty vlastností, `WebRequest` které potřebujete v objektu. Chcete-li například povolit <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> ověřování, nastavte <xref:System.Net.NetworkCredential> vlastnost na instanci třídy:

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. Zadejte metodu protokolu, která umožňuje odesílat data `POST` s požadavkem, například metodou HTTP:

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. Nastavte <xref:System.Web.HttpRequest.ContentLength> vlastnost na počet bajtů, které do aplikace aplikace aplikace zahrnuli. Například:

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. Nastavte <xref:System.Web.HttpRequest.ContentType> vlastnost na příslušnou hodnotu. Například:

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. Získejte datový proud, který <xref:System.Net.WebRequest.GetRequestStream%2A> obsahuje data požadavku voláním metody. Například:

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. Zapište data <xref:System.IO.Stream> do objektu `GetRequestStream` vrácené metodou. Například:

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. Zavřete datový proud <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> požadavku voláním metody. Například:

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. Odešlete požadavek na <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>server voláním . Tato metoda vrátí objekt obsahující odpověď serveru. Typ `WebResponse` vráceného objektu je určen schématem identifikátoru URI požadavku požadavku. Například:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. Můžete přistupovat k `WebResponse` vlastnostem objektu nebo ho přetypovat do instance specifické pro protokol ke čtení vlastností specifických pro protokol.

    Chcete-li například získat přístup <xref:System.Net.HttpWebResponse>k vlastnostem specifické pro protokol HTTP , přetypujte `WebResponse` objekt na odkaz. <xref:System.Net.HttpWebResponse> Následující příklad kódu ukazuje, jak zobrazit <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> vlastnost specifickou pro protokol HTTP odeslanou s odpovědí:

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. Chcete-li získat datový proud obsahující data odpovědí <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> odeslaná `WebResponse` serverem, zavolejte metodu objektu. Například:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. Po přečtení dat z objektu odpovědi zavřete <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> je metodou nebo zavřete <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> datový proud odpovědí metodou. Pokud nezavřete odpověď ani datový proud, může aplikace spustit mimo připojení serveru a nebude možné zpracovat další požadavky. Vzhledem `WebResponse.Close` k `Stream.Close` tomu, že metoda volá, když zavře `Close` odpověď, není nutné volat na odpovědi a datového proudu objekty, i když přitom není škodlivé. Například:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak odeslat data na webový server a číst data v jeho odpovědi:

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a>Viz také

- [Vytváření internetových požadavků](creating-internet-requests.md)
- [Používání datových proudů v síti](using-streams-on-the-network.md)
- [Přístup k internetu prostřednictvím proxy](accessing-the-internet-through-a-proxy.md)
- [Vyžádání údajů](requesting-data.md)
- [Postup: Vyžádání dat pomocí třídy WebRequest](how-to-request-data-using-the-webrequest-class.md)
