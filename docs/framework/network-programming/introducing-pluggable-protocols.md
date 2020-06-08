---
title: Úvod k připojitelným protokolům
description: Seznamte se s připojenými protokoly, které podporují vývoj aplikací využívajících internetové prostředky bez ohledu na podrobnosti protokolu používané prostředky.
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
ms.openlocfilehash: 0bc2d0d005e50b04aff360866a146f6fe6b0ea02
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502350"
---
# <a name="introducing-pluggable-protocols"></a>Úvod k připojitelným protokolům
Microsoft .NET Framework poskytuje vrstvenou, rozšiřitelnou a spravovanou implementaci internetových služeb, které se dají snadno a rychle integrovat do vašich aplikací. Třídy přístupu k Internetu v <xref:System.Net> <xref:System.Net.Sockets> oborech názvů a je možné použít k implementaci webových i internetových aplikací.  
  
## <a name="internet-applications"></a>Internetové aplikace  
 Internetové aplikace je možné klasifikovat široce do dvou druhů: klientských aplikací, které vyžadují informace a serverové aplikace, které reagují na žádosti o informace od klientů. Klasický internetový klient-server je webová aplikace, kde uživatelé používají prohlížeče k přístupu k dokumentům a dalším datům uloženým na webových serverech po celém světě.  
  
 Aplikace nejsou omezeny pouze na jednu z těchto rolí; známý aplikační server střední vrstvy například reaguje na žádosti od klientů vyžádáním dat z jiného serveru. v takovém případě funguje jako server i klient.  
  
 Klientská aplikace vytvoří požadavek určením požadovaného internetového prostředku a komunikačního protokolu, který se má použít pro požadavek a odpověď. V případě potřeby klient také poskytuje veškerá další data potřebná k dokončení žádosti, jako je umístění proxy serveru nebo ověřovací informace (uživatelské jméno, heslo atd.). Jakmile je žádost vytvořená, žádost se dá odeslat na server.  
  
## <a name="identifying-resources"></a>Identifikace prostředků  
 .NET Framework používá identifikátor URI (Uniform Resource Identifier) k identifikaci požadovaného internetového prostředku a komunikačního protokolu. Identifikátor URI se skládá alespoň ze tří a případně čtyř, fragmentů: identifikátor schématu, který identifikuje komunikační protokol pro požadavek a odpověď. identifikátor serveru, který se skládá buď s názvem hostitele DNS (Domain Name System), nebo s adresou TCP, která jednoznačně identifikuje server na internetu; Identifikátor cesty, který vyhledá požadované informace na serveru. a nepovinný řetězec dotazu, který předává informace z klienta na server. Identifikátor URI `http://www.contoso.com/whatsnew.aspx?date=today` se například skládá z identifikátoru schématu `http` , identifikátoru serveru `www.contoso.com` , cesty `/whatsnew.aspx` a řetězce dotazu `?date=today` .  
  
 Poté, co server obdrží požadavek a zpracoval odpověď, vrátí odpověď klientské aplikaci. Odpověď obsahuje doplňkové informace, jako je například typ obsahu (nezpracovaný text nebo XML data).  
  
## <a name="requests-and-responses-in-the-net-framework"></a>Žádosti a odpovědi v .NET Framework  
 .NET Framework používá konkrétní třídy k poskytnutí tří informací potřebných pro přístup k prostředkům Internetu prostřednictvím modelu požadavků a odpovědí: <xref:System.Uri> třída, která obsahuje identifikátor URI vyhledaných internetových prostředků; <xref:System.Net.WebRequest> třída, která obsahuje požadavek na prostředek a <xref:System.Net.WebResponse> třídu, která poskytuje kontejner pro příchozí odpověď.  
  
 Klientské aplikace vytvářejí `WebRequest` instance předáním identifikátoru URI síťového prostředku do <xref:System.Net.WebRequest.Create%2A> metody. Tato statická metoda vytvoří `WebRequest` pro konkrétní protokol, jako je například http. `WebRequest`Vrácený vrátí přístup k vlastnostem, které řídí jak požadavek na server, tak přístup k datovému proudu, který je odeslán po provedení žádosti. <xref:System.Net.WebRequest.GetResponse%2A>Metoda na `WebRequest` straně odesílá požadavek z klientské aplikace na server identifikovaný v identifikátoru URI. V případech, kdy odpověď může být zpožděna, je možné požadavek provést asynchronně pomocí <xref:System.Net.WebRequest.BeginGetResponse%2A> metody na **WebRequest**a odpověď může být vrácena později pomocí <xref:System.Net.WebRequest.EndGetResponse%2A> metody.  
  
 Metody **GetResponse** a **EndGetResponse** vracejí **WebResponse** , který poskytuje přístup k datům vráceným serverem. Vzhledem k tomu, že tato data jsou k dispozici žádající aplikaci jako datový proud <xref:System.Net.WebResponse.GetResponseStream%2A> metodou, je možné ji použít v aplikaci kdekoli, kde jsou použity datové streamy.  
  
 Třídy **WebRequest** a **WebResponse** jsou základem protokolů připojení – implementace síťových služeb, které umožňují vyvíjet aplikace, které používají internetové prostředky, aniž byste se museli starat o konkrétní podrobnosti protokolu, který jednotlivé prostředky používají. Odvozené třídy **WebRequest** jsou registrovány s třídou **WebRequest** za účelem správy podrobností o tom, že skutečná připojení k prostředkům sítě Internet.  
  
 Například <xref:System.Net.HttpWebRequest> Třída spravuje podrobnosti o připojení k internetovému prostředku pomocí protokolu HTTP. Ve výchozím nastavení, když metoda **WebRequest. Create** NALEZNE identifikátor URI, který začíná řetězcem http: nebo https: (identifikátory protokolu pro http a zabezpečený protokol HTTP), vrácený objekt **WebRequest** lze použít tak, jak je, nebo může být přetypovat k **HttpWebRequest** pro přístup k vlastnostem specifickým pro protokol. Ve většině případů poskytuje **WebRequest** všechny informace potřebné k vytvoření žádosti.  
  
 Jakýkoli protokol, který může být reprezentován jako transakce žádosti nebo odpovědi, lze použít v rámci **WebRequest**. Třídy specifické pro protokol můžete odvodit z **WebRequest** a **WebResponse** a pak je zaregistrovat pro použití v aplikaci se statickou <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metodou.  
  
 Pokud je vyžadována autorizace klienta pro požadavky na Internet, <xref:System.Net.WebRequest.Credentials%2A> vlastnost **WebRequest** poskytne potřebné přihlašovací údaje. Tyto přihlašovací údaje můžou být jednoduché dvojici název/heslo pro základní ověřování HTTP nebo Digest nebo název/heslo nebo doména nastavené pro ověřování protokolem NTLM nebo Kerberos. Jedna sada přihlašovacích údajů může být uložena v <xref:System.Net.NetworkCredential> instanci nebo může být v instanci současně uloženo více sad <xref:System.Net.CredentialCache> . **CredentialCache** používá identifikátor URI žádosti a schéma ověřování, které server podporuje k určení přihlašovacích údajů, které se mají odeslat na server.  
  
## <a name="simple-requests-with-webclient"></a>Jednoduché požadavky s webovým klientem  
 Pro aplikace, které potřebují provádět jednoduché požadavky na internetové prostředky, <xref:System.Net.WebClient> poskytuje třída běžné metody pro nahrávání dat nebo stahování dat z internetového serveru. **Webový klient** spoléhá na třídu **WebRequest** za účelem poskytnutí přístupu k internetovým prostředkům; Proto třída **WebClient** může používat jakýkoli registrovaný protokol k připojení.  
  
 Pro aplikace, které nemůžou používat model požadavků a odpovědí, nebo pro aplikace, které potřebují naslouchat v síti, a také požadavky na odesílání, obor názvů **System .NET. Sockets** poskytuje <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener> třídy, a <xref:System.Net.Sockets.UdpClient> . Tyto třídy zpracovávají podrobnosti o vytváření připojení pomocí různých přenosových protokolů a zpřístupňují síťové připojení k aplikaci jako datový proud.  
  
 Vývojáři, kteří znají rozhraní Windows Sockets nebo kteří potřebují ovládací prvek poskytnutý programováním na úrovni soketu, zjistí, že třídy **System .NET. Socket** vyhovují jejich potřebám. Třídy **System .NET. Sockets** jsou přechodovým bodem ze spravovaného do nativního kódu v rámci tříd **System.NET** . Ve většině případů třídy **System .NET. Sockets** zařazovat data do jejich protějšků systému Windows 32 a také vycházejí z nezbytných kontrol zabezpečení.  
  
## <a name="see-also"></a>Viz také:

- [Programování připojitelných protokolů](programming-pluggable-protocols.md)
- [Síťové programování v rozhraní .NET Framework](index.md)
- [Ukázky programování sítě](network-programming-samples.md)
