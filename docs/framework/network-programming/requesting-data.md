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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 166a076eae69b351248bc67570cdaf50b43ab95c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396295"
---
# <a name="requesting-data"></a>Požadavek na Data
Vývoj aplikací, které běží v distribuované provozní prostředí dnešní Internetu vyžaduje metodu efektivní, snadno použitelné pro načítání dat ze všech typů prostředků. Modulární protokoly umožňují vyvíjet aplikace, které pomocí jediného rozhraní k načtení dat z více internetových protokolech.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Nahrávání a stahování dat z internetového serveru  
 Pro jednoduché požadavku a odpovědi transakce <xref:System.Net.WebClient> třída poskytuje nejsnazší pro nahrávání dat nebo stahování dat z internetového serveru. **Webový klient** poskytuje metody pro odesílání a stahování souborů, přijímající a odesílající datové proudy, vyrovnávací paměť dat na server a přijímání odpověď. **Webový klient** používá <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> je k dispozici pro použití třídy aby skutečné připojení k Internetu, takže všechny registrované modulární protokol.  
  
 Klientských aplikací, které je třeba, aby složitější data požadavku transakcí ze serverů pomocí **WebRequest** třídy a jeho následníky. **WebRequest** zapouzdří podrobnosti o připojení k serveru, odesílání požadavku a přijetí odpovědi. **WebRequest** je abstraktní třída, která definuje sadu vlastností a metod, které jsou k dispozici pro všechny aplikace, které používají modulární protokoly. Následníků **WebRequest**, jako například <xref:System.Net.HttpWebRequest>, implementovat vlastnosti a metody definované **WebRequest** způsobem, který je v souladu s základního protokolu.  
  
 **WebRequest** třída vytváří instance specifické pro protokol **WebRequest** následníky, pomocí hodnoty identifikátoru URI předaný jeho <xref:System.Net.WebRequest.Create%2A> metoda určení konkrétní odvozené třídy instance pro vytvoření. Vyberte aplikace, které **WebRequest** následník se má použít k má požadavek zpracovat tak, že zaregistrujete následník konstruktor s <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metoda.  
  
 Žádosti se k internetového zdroji voláním <xref:System.Net.WebRequest.GetResponse%2A> metodu **WebRequest**. **GetResponse** metoda vytvoří žádost specifické pro protokol z vlastností **WebRequest**, vytvoří soketu připojení TCP nebo UDP na server a odešle žádost. Pro požadavky, které odesílají data na server, jako je například HTTP **Post** nebo FTP **Put** požadavky, <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> metoda poskytuje datový proud sítě, ve kterém se má odeslat data.  
  
 **GetResponse** metoda vrátí hodnotu konkrétního protokolu **WebResponse** odpovídající **WebRequest.**  
  
 **WebResponse** třída je také abstraktní třída, která definuje vlastnosti a metody, které jsou k dispozici pro všechny aplikace, které používají modulární protokoly. **WebResponse** následníky implementovat tyto vlastnosti a metody pro základní protokol. <xref:System.Net.HttpWebResponse> Například třída implementuje **WebResponse** třídy pro protokol HTTP.  
  
 Data vrácená serverem jsou zobrazena na aplikaci v datový proud vrácený <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> metoda. Tento datový proud stejně jako jakýkoli jiný, můžete použít, jak je znázorněno v následujícím příkladu.  
  
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
