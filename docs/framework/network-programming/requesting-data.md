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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047317"
---
# <a name="requesting-data"></a>Žádosti o data
Vývoj aplikací, které běží v distribuovaném provozním prostředí dnešního Internetu, vyžaduje efektivní a snadno použitelnou metodu pro načítání dat z prostředků všech typů. Připojitelné protokoly umožňují vyvíjet aplikace, které používají jediné rozhraní k načtení dat z více internetových protokolů.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Nahrávání a stahování dat z internetového serveru  
 Pro jednoduché transakce požadavků a <xref:System.Net.WebClient> odpovědí poskytuje třída nejjednodušší metodu pro nahrávání dat nebo stahování dat z internetového serveru. **WebClient** poskytuje metody pro nahrávání a stahování souborů, odesílání a přijímání datových proudů a odesílání vyrovnávací paměti dat na server a příjem odpovědi. **WebClient** používá <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> třídy a k navazování skutečných připojení k internetovému prostředku, takže je k dispozici libovolný registrovaný připojitelný protokol.  
  
 Klientské aplikace, které potřebují provádět složitější transakce, vyžadují data ze serverů používajících třídu **WebRequest** a její následníky. **WebRequest** zapouzdřuje podrobnosti o připojení k serveru, odeslání požadavku a přijetí odpovědi. **WebRequest** je abstraktní třída, která definuje sadu vlastností a metod, které jsou k dispozici pro všechny aplikace, které používají připojitelné protokoly. Následovníci **WebRequest**, <xref:System.Net.HttpWebRequest>například implementovat vlastnosti a metody definované **WebRequest** způsobem, který je konzistentní s podkladovým protokolem.  
  
 Třída **WebRequest** vytvoří instance potomků **WebRequest** specifické pro protokol pomocí hodnoty <xref:System.Net.WebRequest.Create%2A> identifikátoru URI předané jeho metodě k určení konkrétní instance odvozené třídy, kterou chcete vytvořit. Aplikace označují, který **potomek WebRequest** by měl být použit ke zpracování <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> požadavku registrací konstruktoru potomka pomocí metody.  
  
 Požadavek je podán a internetová <xref:System.Net.WebRequest.GetResponse%2A> prostředek voláním metody na **WebRequest**. Metoda **GetResponse** vytvoří požadavek specifický pro protokol z vlastností **aplikace WebRequest**, vytvoří připojení soketu TCP nebo UDP k serveru a odešle požadavek. Pro požadavky, které odesílají data na server, například HTTP <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> **Post** nebo FTP **Put** požadavky, metoda poskytuje síťový datový proud, ve kterém chcete odeslat data.  
  
 Metoda **GetResponse** vrátí **webovou odezvu** specifickou pro protokol, která odpovídá **požadavku WebRequest.**  
  
 Třída **WebResponse** je také abstraktní třída, která definuje vlastnosti a metody, které jsou k dispozici všem aplikacím, které používají připojitelné protokoly. **Následovníci WebResponse** implementují tyto vlastnosti a metody pro základní protokol. Třída <xref:System.Net.HttpWebResponse> například implementuje třídu **WebResponse** pro protokol HTTP.  
  
 Data vrácená serverem jsou prezentována aplikaci v <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> datovém proudu vráceném metodou. Tento datový proud můžete použít jako každý jiný, jak je znázorněno v následujícím příkladu.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>Viz také

- [Síťové programování v rozhraní .NET Framework](index.md)
- [Postupy: Vyžádání webové stránky a načtení výsledků jako streamu](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
