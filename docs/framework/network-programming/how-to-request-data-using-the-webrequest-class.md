---
title: 'Postupy: Vyžádání dat pomocí třídy WebRequest'
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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048157"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Postupy: Vyžádání dat pomocí třídy WebRequest

Následující postup popisuje kroky pro vyžádání prostředku, například webové stránky nebo souboru, ze serveru. Prostředek musí být identifikovaný identifikátorem URI.

## <a name="to-request-data-from-a-host-server"></a>Vyžádání dat z hostitelského serveru

1. Vytvořte instanci voláním <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> s identifikátorem URI prostředku. <xref:System.Net.WebRequest> Příklad:

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
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

3. Odešle požadavek na server voláním <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Tato metoda vrátí objekt obsahující odpověď serveru. Typ vráceného <xref:System.Net.WebResponse> objektu je určen schématem identifikátoru URI žádosti. Příklad:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. Můžete získat přístup k vlastnostem `WebResponse` objektu nebo ho přetypovat na instanci specifickou pro protokol pro čtení vlastností specifických pro protokol.

    Chcete-li například získat přístup k vlastnostem <xref:System.Net.HttpWebResponse>specifickým pro protokol HTTP, `WebResponse` přetypování `HttpWebResponse` objektu na odkaz. Následující příklad kódu ukazuje, jak zobrazit vlastnost specifickou <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> pro protokol HTTP odeslanou odpovědí:

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. Chcete-li získat datový proud obsahující data odpovědí odesílaná serverem, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodu. Příklad:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. Po načtení dat z objektu Response ho buď zavřete, a to pomocí <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> metody, nebo zavřete datový proud odpovědi <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> s metodou. Pokud nezavřete objekt Response nebo datový proud, může vaše aplikace vysílat připojení k serveru a nebude možné zpracovat další požadavky. Vzhledem k tomu, `Stream.Close` že `Close` metodavolá,kdyžjeodpověďzavřená,nenínutnévolatnaobjektyResponseaStream,ikdyžtaknebudete`WebResponse.Close` mít škodlivou. Příklad:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak vytvořit požadavek na webový server a jak číst data v odpovědi:

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>Viz také:

- [Vytváření internetových požadavků](creating-internet-requests.md)
- [Použití datových proudů v síti](using-streams-on-the-network.md)
- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
- [Vyžádání dat](requesting-data.md)
- [Postupy: Odeslání dat pomocí třídy WebRequest](how-to-send-data-using-the-webrequest-class.md)
