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
ms.openlocfilehash: 213a714a04c31954b0091071b0625449916d154d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146911"
---
# <a name="introducing-pluggable-protocols"></a>Úvod k připojitelným protokolům
Rozhraní Microsoft .NET Framework poskytuje vícevrstvou, rozšiřitelnou a spravovatelnou implementaci internetových služeb, které je možné integrovat se rychle a snadno do svých aplikací. Přístup k Internetu tříd v <xref:System.Net> a <xref:System.Net.Sockets> obory názvů slouží k implementaci založeného na webu i internetových aplikací.  
  
## <a name="internet-applications"></a>Internetové aplikace  
 Internetové aplikace je možné rozdělit do dvou typů široce: klientské aplikace, které požadují informace a serverové aplikace, které reagují na požadavky na informace z klientů. Klasické aplikaci klient server Internet je World Wide Web, kde uživatelé používají prohlížeč pro přístup k dokumentům a další data uložená na webových serverů po celém světě.  
  
 Aplikace nejsou omezeny pouze k jedné z těchto rolí; například známé aplikace střední vrstvy serveru reaguje na požadavky klientů o vyžádání dat z jiného serveru, v takovém případě funguje jako server a klienta.  
  
 Klientská aplikace odešle požadavek určením požadovaný prostředek Internet a komunikační protokol pro žádost a odpověď. V případě potřeby klient také poskytuje všechny další data potřebná k dokončení požadavku, jako je například proxy umístění nebo ověřovací údaje (uživatelské jméno, heslo atd.). Jakmile je vytvořen požadavek, můžete žádost odeslána na server.  
  
## <a name="identifying-resources"></a>Identifikace prostředků  
 Rozhraní .NET Framework používá k identifikaci požadovaný Internet zdrojů a komunikační protokol identifikátorem URI (Uniform Resource). Identifikátor URI se skládá z alespoň tři a případně čtyři, fragmenty: identifikátor schématu, která identifikuje komunikační protokol pro žádost a odpověď; Identifikátor serveru, který se skládá z názvu systému DNS (Domain Name) hostitele nebo adresu TCP, který jednoznačně identifikuje server na Internetu. identifikátor cesty, který vyhledá požadované informace na serveru. a volitelný řetězec dotazu, který předává informace od klienta k serveru. Například identifikátor URI `http://www.contoso.com/whatsnew.aspx?date=today` identifikátor schématu se skládá ze `http`, identifikátor serveru `www.contoso.com`, cesta `/whatsnew.aspx`a řetězce dotazu `?date=today`.  
  
 Po server obdržel požadavek a zpracovat odpověď, vrací odpověď klientské aplikaci. Odpověď obsahuje doplňující informace, jako je například typ obsahu (nezpracovaný text nebo data XML, třeba).  
  
## <a name="requests-and-responses-in-the-net-framework"></a>Požadavky a odpovědi v rozhraní .NET Framework  
 Rozhraní .NET Framework používá určité třídy k poskytování tři druhy informací potřebných pro přístup k internetovým prostředkům prostřednictvím modelu žádostí a odpovědí: <xref:System.Uri> třídu, která obsahuje identifikátor URI prostředku Internet hledáte; <xref:System.Net.WebRequest>třídu, která obsahuje žádost o prostředku. a <xref:System.Net.WebResponse> třídu, která poskytuje kontejner pro příchozí odpovědi.  
  
 Vytvoření klientské aplikace `WebRequest` instance předáním identifikátor URI prostředku sítě <xref:System.Net.WebRequest.Create%2A> metody. Tato statická metoda vytvoří `WebRequest` pro určitý protokol, jako je například HTTP. `WebRequest` , Který je vrácen poskytuje přístup k vlastnosti, které řídí požadavek na serveru i přístup k datový proud, který se odešle, když se požadavek. <xref:System.Net.WebRequest.GetResponse%2A> Metodu `WebRequest` odesílá žádost z klientské aplikace na server identifikované v identifikátoru URI. V případech, ve kterých můžou být zpožděné odpověď na žádost provádět asynchronně pomocí <xref:System.Net.WebRequest.BeginGetResponse%2A> metodu na **WebRequest**, a odpovědi lze vrátit na pozdější čas pomocí <xref:System.Net.WebRequest.EndGetResponse%2A> metody.  
  
 **GetResponse** a **EndGetResponse** metody vrací **WebResponse** , který poskytuje přístup k datům vrácená serverem. Protože tato data se poskytuje s žádající aplikací jako datový proud pomocí <xref:System.Net.WebResponse.GetResponseStream%2A> metoda, je možné v aplikaci, kdekoli se používají datové proudy.  
  
 **WebRequest** a **WebResponse** třídy jsou základem připojitelných protokolů – implementace síťových služeb, která umožňuje vyvíjet aplikace, které používají internetové prostředky bez byste se museli starat o konkrétních podrobností protokolu, který používá každého prostředku. Odvozené třídy **WebRequest** jsou registrované **WebRequest** třídy spravovat podrobnosti o vytvoření skutečné připojení k internetovým prostředkům.  
  
 Například <xref:System.Net.HttpWebRequest> třída spravuje podrobnosti o připojení internetového zdroji pomocí protokolu HTTP. Ve výchozím nastavení když **WebRequest.Create** metoda zaznamená identifikátor URI, který začíná "http:" nebo "https:" (protokol identifikátory pro protokol HTTP a zabezpečený protokol HTTP), **WebRequest** , která je vrácena, může sloužit jako je, nebo ho můžete přetypovat na **HttpWebRequest** pro přístup k vlastnostem specifickým pro protokol. Ve většině případů **WebRequest** poskytuje všechny potřebné informace pro požadavku.  
  
 Libovolný protokol, který může být reprezentována jako transakce žádostí a odpovědí můžete použít v **WebRequest**. Lze odvodit z třídy pro konkrétní **WebRequest** a **WebResponse** a zaregistrujte je pro použití aplikací s statické <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metody.  
  
 Pokud klient autorizaci pro požadavky na Internetu je potřeba, <xref:System.Net.WebRequest.Credentials%2A> vlastnost **WebRequest** poskytne potřebné přihlašovací údaje. Tyto přihlašovací údaje můžou být pár jednoduchých jméno/heslo pro základní HTTP nebo ověřování hodnotou hash nebo jméno/heslo nebo doméně nastavení pro ověřování protokolů NTLM nebo Kerberos. Jednu sadu přihlašovacích údajů můžou být uložené v <xref:System.Net.NetworkCredential> instance nebo více sad mohou být uloženy v současně <xref:System.Net.CredentialCache> instance. **CredentialCache** používá identifikátoru URI požadavku a schéma ověřování, který server podporuje rozhodnout, jaké přihlašovací údaje pro odesílání na server.  
  
## <a name="simple-requests-with-webclient"></a>Jednoduché požadavky s webovým klientem přes  
 Pro aplikace, které je potřeba provést jednoduché požadavky na internetové prostředky <xref:System.Net.WebClient> třída poskytuje běžné metody pro nahrávání dat do nebo stahování dat z internetového serveru. **Webový klient** spoléhá na **WebRequest** třídy a zajistit tak přístup k internetovým prostředkům; proto **WebClient** třídu můžete použít jakýkoli protokol registrované modulární.  
  
 Pro aplikace, které nelze použít model žádost odpověď, nebo pro aplikace, které potřebují k naslouchat na síti také odesílat požadavky **System.Net.Sockets** obor názvů poskytuje <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>a <xref:System.Net.Sockets.UdpClient> třídy. Tyto třídy zpracování podrobností o připojení pomocí různé přenosové protokoly a vystavit síťové připojení k aplikaci jako datový proud.  
  
 Vývojáři, kteří znají rozhraní Windows Sockets nebo uživatelům, kteří potřebují poskytnuté programování na úrovni soketu ovládací prvek, který najdete **System.Net.Sockets** třídy podle jejich potřeb. **System.Net.Sockets** třídy jsou bod přechod ze spravované do nativního kódu v rámci **System.Net** třídy. Ve většině případů **System.Net.Sockets** třídy zařazování dat do jejich protějšky Windows 32-bit, jakož i zpracování žádné nezbytná bezpečnostní kontroly.  
  
## <a name="see-also"></a>Viz také  
 [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Ukázky práce se sítí pro .NET v Galerie kódu na webu MSDN](https://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)
