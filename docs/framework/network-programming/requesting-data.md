---
title: Požadavek na Data
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
ms.openlocfilehash: 026912a2dc8a09fb52e0427fc7bf2dbb1d55413a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182811"
---
# <a name="requesting-data"></a>Požadavek na Data
Vývoj aplikací, které běží v distribuované provozní prostředí dnešní Internet vyžaduje metodu efektivní a snadno použitelné pro načítání dat ze všech typů prostředků. Připojitelných protokolů umožňují vyvíjet aplikace, které používají jednotné rozhraní pro načtení dat z více protokolů sítě Internet.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Nahrávání a stahování dat z internetového serveru  
 Pro jednoduché žádosti a odpovědi transakce <xref:System.Net.WebClient> třída poskytuje nejjednodušší metodu pro nahrávání dat do nebo stahování dat z internetového serveru. **Webový klient** poskytuje metody pro nahrávání a stahování souborů, příjem a odesílání datových proudů, vyrovnávací paměť dat na server a přijímání odpovědí. **Webový klient** používá <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy pro skutečné připojení k internetového zdroji, tak žádné registrována připojitelných protokolů je k dispozici pro použití.  
  
 Klientské aplikace, které je potřeba provést složitější data požadavku transakcí ze serverů pomocí **WebRequest** třídy a jejích potomků. **WebRequest** zapouzdřuje informace připojování k serveru, požadavek odesílat a přijímat odpovědi. **WebRequest** je abstraktní třída, která definuje sadu vlastností a metod, které jsou k dispozici pro všechny aplikace, které pomocí připojitelných protokolů. Následníky **WebRequest**, jako například <xref:System.Net.HttpWebRequest>, implementovat vlastnosti a metody definované **WebRequest** způsobem, který je konzistentní se základním protokolu.  
  
 **WebRequest** třídy vytvoří konkrétní instance **WebRequest** následníky, hodnotu identifikátoru URI s použitím předaného do jeho <xref:System.Net.WebRequest.Create%2A> metodou ke zjištění konkrétních odvozených tříd instance má vytvořit. Vyberte aplikace, které **WebRequest** potomkem by měla sloužit ke zpracování požadavku tak, že zaregistrujete potomka konstruktor s <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.  
  
 Vytvoří se požadavek k internetového zdroji voláním <xref:System.Net.WebRequest.GetResponse%2A> metodu **WebRequest**. **GetResponse** metoda vytvoří konkrétní žádosti z vlastností **WebRequest**, vytvoří protokol TCP nebo UDP soketu připojení k serveru a odešle žádost. Pro žádosti, které odesílají data na serveru, např. HTTP **příspěvek** nebo FTP **umístit** požadavků, <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> metoda poskytuje datové proudy sítě ve kterých se mají odeslat data.  
  
 **GetResponse** metoda vrátí hodnotu konkrétního protokol **WebResponse** , který odpovídá **WebRequest.**  
  
 **WebResponse** třídy je také abstraktní třída, která definuje vlastnosti a metody, které jsou k dispozici pro všechny aplikace, které pomocí připojitelných protokolů. **WebResponse** následníky implementovat tyto vlastnosti a metody pro základní protokol. <xref:System.Net.HttpWebResponse> , Například implementuje třída **WebResponse** třídy pro protokol HTTP.  
  
 Data vrácená serverem se zobrazují na aplikaci v stream vrácený poskytovatelem <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metody. Tento datový proud stejně jako jakýkoli jiný, můžete použít, jak je znázorněno v následujícím příkladu.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>Viz také  
 [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Postupy: Vyžádání webové stránky a načtení výsledků jako streamu](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)  
 [Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
