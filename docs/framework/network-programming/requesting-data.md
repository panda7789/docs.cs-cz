---
title: Žádosti o data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
ms.openlocfilehash: 1f367caf7656a83597b6262a5746686df15d33b4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047317"
---
# <a name="requesting-data"></a>Žádosti o data
Vývoj aplikací, které běží v distribuovaném operačním prostředí dnešního Internetu, vyžaduje efektivní a snadno použitelné metody pro načítání dat z prostředků všech typů. Připojitelné protokoly umožňují vyvíjet aplikace, které používají jedno rozhraní k načítání dat z více protokolů sítě Internet.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Nahrávání a stahování dat z internetového serveru  
 Pro jednoduché transakce <xref:System.Net.WebClient> požadavků a odpovědí poskytuje třída nejjednodušší způsob, jak nahrávat data nebo stahovat data z internetového serveru. **Webový klient** poskytuje metody pro nahrávání a stahování souborů, odesílání a příjem datových proudů a posílání vyrovnávací paměti dat na server a příjem odpovědi. **Webový klient** používá <xref:System.Net.WebRequest> třídy a <xref:System.Net.WebResponse> k tomu, aby provedl skutečná připojení k internetovému prostředku, takže jakýkoli registrovaný připojitelný protokol je k dispozici pro použití.  
  
 Klientské aplikace, které potřebují provádět složitější transakce, vyžadují data ze serverů pomocí třídy **WebRequest** a jejích potomků. **WebRequest** zapouzdřuje podrobnosti o připojení k serveru, posílá požadavek a obdrží odpověď. **WebRequest** je abstraktní třída, která definuje sadu vlastností a metod, které jsou k dispozici pro všechny aplikace, které používají připojitelné protokoly. Následníky **WebRequest**, například <xref:System.Net.HttpWebRequest>, implementují vlastnosti a metody definované **WebRequest** způsobem, který je konzistentní s podkladovým protokolem.  
  
 Třída **WebRequest** vytvoří instance pro následníky **WebRequest** pomocí hodnoty identifikátoru URI předané jeho <xref:System.Net.WebRequest.Create%2A> metodě k určení konkrétní instance odvozené třídy, která se má vytvořit. Aplikace označují, který člen **WebRequest** by měl být použit ke zpracování požadavku registrací konstruktoru následníka s <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metodou.  
  
 Požadavek se provede na prostředek v Internetu voláním <xref:System.Net.WebRequest.GetResponse%2A> metody na **WebRequest**. Metoda **GetResponse** sestaví požadavek specifický pro protokol z vlastností **WebRequest**, vytvoří připojení soketu TCP nebo UDP k serveru a odešle požadavek. V **případě požadavků,** které odesílají data na server, jako jsou <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> požadavky HTTP **post** nebo FTP, poskytuje metoda síťový datový proud, ve kterém se budou data odesílat.  
  
 Metoda **GetResponse** vrací **WebResponse** specifickou pro protokol, který odpovídá **WebRequest.**  
  
 Třída **WebResponse** je také abstraktní třída, která definuje vlastnosti a metody, které jsou k dispozici pro všechny aplikace, které používají připojitelná protokoly. Následníky **WebResponse** implementují tyto vlastnosti a metody pro základní protokol. Třída například implementuje třídu WebResponse pro protokol HTTP. <xref:System.Net.HttpWebResponse>  
  
 Data vrácená serverem se zobrazí aplikaci v datovém proudu vráceném <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metodou. Tento datový proud můžete použít jako kterýkoli jiný, jak je znázorněno v následujícím příkladu.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>Viz také:

- [Síťové programování v rozhraní .NET Framework](index.md)
- [Postupy: Požádat o webovou stránku a načíst výsledky jako datový proud](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [Postupy: Načtení WebResponse konkrétního protokolu, který odpovídá WebRequest](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
