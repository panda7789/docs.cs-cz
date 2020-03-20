---
title: Úvod k připojitelným protokolům
ms.date: 03/30/2017
helpviewer_keywords:
- data requests, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- URI
- Windows Sockets
- request/response model
- sending data, pluggable protocols
- pluggable protocols
- WebClient class, about WebClient class
- pluggable protocols, about pluggable protocols
- Internet, pluggable protocols
- path identifiers
- Uniform Resource Identifier
- application development [.NET Framework], pluggable protocols
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
- server identifiers
- scheme identifiers
ms.assetid: 4b48e22d-e4e5-48f0-be80-d549bda97415
ms.openlocfilehash: 72b47b8159f9f6f0dc3a19c5cbf94335507d9e7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047864"
---
# <a name="introducing-pluggable-protocols"></a>Úvod k připojitelným protokolům
Rozhraní Microsoft .NET Framework poskytuje vrstvenou, rozšiřitelnou a spravovanou implementaci internetových služeb, kterou lze rychle a snadno integrovat do vašich aplikací. Třídy přístupu <xref:System.Net> k <xref:System.Net.Sockets> Internetu v oborech názvů a lze použít k implementaci webových i internetových aplikací.  
  
## <a name="internet-applications"></a>Internetové aplikace  
 Internetové aplikace lze rozdělit do dvou druhů: klientské aplikace, které požadují informace a serverové aplikace, které reagují na požadavky klientů na informace. Klasická internetová klient-serverová aplikace je World Wide Web, kde lidé používají prohlížeče pro přístup k dokumentům a dalším datům uloženým na webových serverech po celém světě.  
  
 Aplikace nejsou omezeny pouze na jednu z těchto rolí; například známý aplikační server střední vrstvy reaguje na požadavky klientů vyžádáním dat z jiného serveru, v takovém případě funguje jako server i jako klient.  
  
 Klientská aplikace provede požadavek identifikací požadovaného internetového prostředku a komunikačního protokolu, který se má použít pro požadavek a odpověď. V případě potřeby klient také poskytuje další data potřebná k dokončení požadavku, například informace o umístění proxy serveru nebo ověřování (uživatelské jméno, heslo a tak dále). Po vytvoření požadavku může být požadavek odeslán na server.  
  
## <a name="identifying-resources"></a>Identifikace zdrojů  
 Rozhraní .NET Framework používá identifikátor URI (Uniform Resource Identifier) k identifikaci požadovaného internetového prostředku a komunikačního protokolu. Identifikátor URI se skládá z nejméně tří a případně čtyř fragmentů: identifikátorschématu, který identifikuje komunikační protokol pro požadavek a odpověď; identifikátor serveru, který se skládá buď z názvu hostitele DNS (Domain Name System) nebo adresy TCP, která jednoznačně identifikuje server v Internetu; identifikátor cesty, který vyhledá požadované informace na serveru; a volitelný řetězec dotazu, který předává informace z klienta na server. Identifikátor `http://www.contoso.com/whatsnew.aspx?date=today` URI se například skládá `http`z identifikátoru `www.contoso.com`schématu `/whatsnew.aspx`, identifikátoru `?date=today`serveru , cesty a řetězce dotazu .  
  
 Poté, co server obdržel požadavek a zpracoval odpověď, vrátí odpověď klientské aplikaci. Odpověď obsahuje doplňující informace, například typ obsahu (například nezpracovaný text nebo data XML).  
  
## <a name="requests-and-responses-in-the-net-framework"></a>Požadavky a odpovědi v rozhraní .NET Framework  
 Rozhraní .NET Framework používá určité třídy k poskytnutí tří částí informací potřebných <xref:System.Uri> pro přístup k internetovým prostředkům prostřednictvím modelu požadavku a odpovědi: třídy, která obsahuje identifikátor URI internetového prostředku, který hledáte; <xref:System.Net.WebRequest> třída, která obsahuje požadavek na prostředek; a <xref:System.Net.WebResponse> třídy, která poskytuje kontejner pro příchozí odpověď.  
  
 Klientské `WebRequest` aplikace vytvářejí instance předáním identifikátoru <xref:System.Net.WebRequest.Create%2A> URI síťového prostředku metodě. Tato statická `WebRequest` metoda vytvoří pro konkrétní protokol, například HTTP. Vrácená `WebRequest` funkce poskytuje přístup k vlastnostem, které řídí požadavek na server a přístup k datovému proudu, který je odeslán při požadavku. Metoda <xref:System.Net.WebRequest.GetResponse%2A> na `WebRequest` odešle požadavek z klientské aplikace na server identifikovaný v identifikátoru URI. V případech, ve kterých může být odpověď zpožděna, může <xref:System.Net.WebRequest.BeginGetResponse%2A> být požadavek proveden asynchronně pomocí metody na **WebRequest**a odpověď může být vrácena později pomocí <xref:System.Net.WebRequest.EndGetResponse%2A> metody.  
  
 **GetResponse** a **EndGetResponse** Metody vrátí **WebResponse,** který poskytuje přístup k datům vráceným serverem. Vzhledem k tomu, že tato data jsou <xref:System.Net.WebResponse.GetResponseStream%2A> poskytována žádající aplikaci jako datový proud metodou, lze je použít v aplikaci kdekoli datové proudy.  
  
 Třídy **WebRequest** a **WebResponse** jsou základem připojitelných protokolů , což je implementace síťových služeb, která umožňuje vyvíjet aplikace, které používají internetové prostředky bez obav o konkrétní podrobnosti protokolu, který každý prostředek používá. Potomek **třídy WebRequest** jsou registrovány s **WebRequest** třídy pro správu podrobností o vytváření skutečných připojení k internetovým prostředkům.  
  
 Jako příklad třídy <xref:System.Net.HttpWebRequest> spravuje podrobnosti o připojení k prostředku Internetu pomocí protokolu HTTP. Ve výchozím nastavení, když **metoda WebRequest.Create** narazí na identifikátor URI, který začíná "http:" nebo "https:" (identifikátory protokolu pro protokol HTTP a zabezpečené HTTP), **webový požadavek,** který je vrácen, může být použit tak, jak je, nebo může být typecast na **HttpWebRequest** pro přístup k vlastnostem specifickým pro protokol. Ve většině případů **WebRequest** poskytuje všechny potřebné informace pro podání požadavku.  
  
 Libovolný protokol, který může být reprezentován jako transakce požadavku a odpovědi, lze použít v **aplikaci WebRequest**. Třídy specifické pro protokol můžete odvodit z **WebRequest** a **WebResponse** a pak je zaregistrovat pro použití aplikací statickou <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metodou.  
  
 Pokud je vyžadována autorizace klienta pro požadavky na Internet, <xref:System.Net.WebRequest.Credentials%2A> vlastnost **WebRequest** poskytuje potřebná pověření. Tato pověření mohou být jednoduchý majek název/heslo pro základní ověřování HTTP nebo digest nebo název/heslo/doména nastavená pro ověřování NTLM nebo Kerberos. Jednu sadu přihlašovacích údajů <xref:System.Net.NetworkCredential> lze uložit v instanci nebo <xref:System.Net.CredentialCache> více sad lze uložit současně v instanci. **Mezipaměť Pověření** používá identifikátor URI požadavku a schéma ověřování, které server podporuje, k určení pověření, která mají být odeslána na server.  
  
## <a name="simple-requests-with-webclient"></a>Jednoduché požadavky s webovým klientem  
 Pro aplikace, které potřebují jednoduché požadavky na <xref:System.Net.WebClient> internetové prostředky, třída poskytuje běžné metody pro nahrávání dat nebo stahování dat z internetového serveru. **Webový klient** spoléhá na třídu **WebRequest** a poskytuje přístup k internetovým prostředkům. proto **třída WebClient** může použít libovolný registrovaný připojitelný protokol.  
  
 Pro aplikace, které nemohou používat model požadavku/odpovědi, nebo pro aplikace, které potřebují naslouchat v síti a odesílat <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>požadavky, <xref:System.Net.Sockets.UdpClient> poskytuje obor názvů **System.Net.Sockets** třídy , , a. Tyto třídy zpracovávají podrobnosti o vytváření připojení pomocí různých přenosových protokolů a vystavit síťové připojení k aplikaci jako datový proud.  
  
 Vývojáři obeznámení s rozhraním Windows Sockets nebo ti, kteří potřebují ovládací prvek poskytovaný programováním na úrovni soketu, zjistí, že **třídy System.Net.Sockets** splňují jejich potřeby. Třídy **System.Net.Sockets** jsou přechodovým bodem ze spravovaného nanativního kódu v rámci **System.Net** tříd. Ve většině případů **System.Net.Sockets třídy** zařazování dat do jejich 32bitové protějšky systému Windows, stejně jako zpracování všech nezbytných kontrol zabezpečení.  
  
## <a name="see-also"></a>Viz také

- [Programování připojitelných protokolů](programming-pluggable-protocols.md)
- [Síťové programování v rozhraní .NET Framework](index.md)
- [Ukázky programování sítě](network-programming-samples.md)
