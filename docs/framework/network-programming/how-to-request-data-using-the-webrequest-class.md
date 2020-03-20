---
title: 'Postup: Vyžádání dat pomocí třídy WebRequest'
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
ms.openlocfilehash: e670a2a503ce704eff847e9e0b3ee340ab52fe62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048157"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Postup: Vyžádání dat pomocí třídy WebRequest

Následující postup popisuje kroky k vyžádání prostředku, například webové stránky nebo souboru, ze serveru. Prostředek musí být identifikován identifikátorem URI.

## <a name="to-request-data-from-a-host-server"></a>Vyžádání dat z hostitelského serveru

1. Vytvořte <xref:System.Net.WebRequest> instanci voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> pomocí identifikátoru URI prostředku. Například:

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
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

3. Odešlete požadavek na <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>server voláním . Tato metoda vrátí objekt obsahující odpověď serveru. Typ <xref:System.Net.WebResponse> vráceného objektu je určen schématem identifikátoru URI požadavku požadavku. Například:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. Můžete přistupovat k `WebResponse` vlastnostem objektu nebo ho přetypovat do instance specifické pro protokol ke čtení vlastností specifických pro protokol.

    Chcete-li například získat přístup <xref:System.Net.HttpWebResponse>k vlastnostem specifické pro protokol HTTP , přetypujte `WebResponse` objekt na odkaz. `HttpWebResponse` Následující příklad kódu ukazuje, jak zobrazit <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> vlastnost specifickou pro protokol HTTP odeslanou s odpovědí:

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. Chcete-li získat datový proud obsahující data odpovědí <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> odeslaná serverem, zavolejte metodu. Například:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. Po přečtení dat z objektu odpovědi zavřete <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> je metodou nebo zavřete <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> datový proud odpovědí metodou. Pokud nezavřete objekt odpovědi nebo datový proud, aplikace může spustit mimo připojení serveru a nebude možné zpracovat další požadavky. Vzhledem `WebResponse.Close` k `Stream.Close` tomu, že metoda volá, když zavře `Close` odpověď, není nutné volat na odpovědi a datového proudu objekty, i když přitom není škodlivé. Například:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak vytvořit požadavek na webový server a číst data v jeho odpovědi:

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>Viz také

- [Vytváření internetových požadavků](creating-internet-requests.md)
- [Používání datových proudů v síti](using-streams-on-the-network.md)
- [Přístup k internetu prostřednictvím proxy](accessing-the-internet-through-a-proxy.md)
- [Vyžádání údajů](requesting-data.md)
- [Postup: Odeslání dat pomocí třídy WebRequest](how-to-send-data-using-the-webrequest-class.md)
