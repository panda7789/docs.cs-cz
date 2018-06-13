---
title: Představení modulární protokoly
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ef674855d1b9d6538e08ea2bb95f1f63e602d61d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396387"
---
# <a name="introducing-pluggable-protocols"></a>Představení modulární protokoly
Rozhraní Microsoft .NET Framework poskytuje implementaci vrstev, rozšiřitelný a spravovaných služeb Internetu, které může být integrovaná rychle a snadno do svých aplikací. Přístup k Internetu třídy v <xref:System.Net> a <xref:System.Net.Sockets> obory názvů lze použít k implementaci webové i internetové aplikace.  
  
## <a name="internet-applications"></a>Internetové aplikace  
 Internetové aplikace můžete rozdělit široce do dva typy: klientské aplikace, které požadují informace a serverové aplikace, které reagují na požadavky informace od klientů. Classic Internetové aplikace klient server je World Wide Web, kde se používá prohlížeče na přístup k dokumentům a další data uložená na webových serverech po celém světě.  
  
 Aplikace nejsou omezeny pouze jedna z těchto rolí; například známé střední vrstvy aplikační server odpovídá na požadavky od klientů žádajícího data z jiného serveru v takovém případě funguje jako server a klienta.  
  
 Klientská aplikace odešle požadavek určením požadovaný prostředek Internet a komunikační protokol, který chcete použít pro žádosti a odpovědi. V případě potřeby klienta poskytuje také všechny další data potřebná pro dokončení požadavku, jako je například umístění nebo ověřování informace o proxy serveru (uživatelské jméno, heslo a tak dále). Jakmile požadavek je vytvořen, můžete být požadavek odeslán do serveru.  
  
## <a name="identifying-resources"></a>Identifikujete zdroje  
 Rozhraní .NET Framework identifikátor URI (Uniform Resource) používá k identifikaci požadovaný protokol prostředků a komunikace Internetu. Identifikátor URI se skládá z nejméně tři a případně čtyři, fragmenty: identifikátor schématu, která identifikuje komunikační protokol pro žádosti a odpovědi; Identifikátor serveru, který se skládá z názvu hostitele systému DNS (Domain Name) nebo adresu TCP, který jedinečně identifikuje server na Internetu. identifikátor cesty, která vyhledá požadované informace na serveru. a volitelný řetězec dotazu, který předává informace od klienta k serveru. Například identifikátor URI "http://www.contoso.com/whatsnew.aspx?date=today" se skládá z identifikátor schéma "http", server identifikátor "www.contoso.com", cesta k "/ whatsnew.aspx" a řetězce dotazu "? datum dnes =".  
  
 Po server má žádost přijme a zpracuje odpověď, vrátí odpověď na klientské aplikace. Odpověď obsahuje doplňující informace, například typ obsahu (nezpracovaný text nebo data XML, např.).  
  
## <a name="requests-and-responses-in-the-net-framework"></a>Požadavky a odpovědi v rozhraní .NET Framework  
 Rozhraní .NET Framework používá k poskytování tři údaje informace požadované pro přístup k internetovým prostředkům prostřednictvím modelu požadavků a odpovědí určité třídy: <xref:System.Uri> třídy, která obsahuje identifikátor URI prostředku Internet hledáte; <xref:System.Net.WebRequest>třída, která obsahuje žádost o prostředek; a <xref:System.Net.WebResponse> třídy, která poskytuje kontejner pro příchozí odpovědi.  
  
 Vytvoření klientských aplikací `WebRequest` instance předáním identifikátor URI k síťovému prostředku <xref:System.Net.WebRequest.Create%2A> metoda. Tato metoda statické vytvoří `WebRequest` pro určitý protokol, jako je například HTTP. `WebRequest` , Se vrátí, poskytuje přístup k vlastnosti, které řídí požadavek na server i přístup k datový proud odeslaný při zadání požadavku. <xref:System.Net.WebRequest.GetResponse%2A> Metodu `WebRequest` odešle žádost od aplikace klienta k serveru identifikovat v identifikátoru URI. V případech, ve kterých může být zpoždění odpovědi, žádost můžete provést pomocí asynchronně <xref:System.Net.WebRequest.BeginGetResponse%2A> metodu **WebRequest**, a mohou být vráceny odpovědi na pozdější dobu pomocí <xref:System.Net.WebRequest.EndGetResponse%2A> metoda.  
  
 **GetResponse** a **EndGetResponse** metody vrací **WebResponse** , který poskytuje přístup k datům vrácená serverem. Protože tato data se poskytuje s žádající aplikací jako datový proud pomocí <xref:System.Net.WebResponse.GetResponseStream%2A> metoda, lze v aplikaci, kdekoli se používají datové proudy.  
  
 **WebRequest** a **WebResponse** třídy jsou základem modulární protokoly – implementace síťových služeb, která umožňuje vyvíjet aplikace, které používají prostředků z Internetu bez starostí o konkrétní podrobnosti o protokolu, který používá každého prostředku. Odvozené třídy **WebRequest** jsou registrované **WebRequest** třídy ke správě podrobnosti o skutečné připojení k internetovým prostředkům.  
  
 Jako příklad <xref:System.Net.HttpWebRequest> třída spravuje podrobnosti o připojení k Internetu prostředku pomocí protokolu HTTP. Ve výchozím nastavení když **WebRequest.Create** metoda zaznamená identifikátor URI, který začíná "http:" nebo "https:" (protokol identifikátorů pro protokol HTTP a zabezpečený protokol HTTP), **WebRequest** , je vrácen lze použít jako je, nebo může být přiřazení typu k **HttpWebRequest** pro přístup k vlastnostem protokolu specifické. Ve většině případů **WebRequest** poskytuje všechny potřebné informace pro vytváření požadavku.  
  
 Libovolný protokol, který může být reprezentován jako transakce požadavků a odpovědí lze použít v **WebRequest**. Odvozujete specifické třídy z **WebRequest** a **WebResponse** a registrujte je pro použití aplikací s statických <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metoda.  
  
 Pokud klient autorizaci pro požadavky na Internetu je nutné, <xref:System.Net.WebRequest.Credentials%2A> vlastnost **WebRequest** poskytuje potřebné přihlašovací údaje. Tyto přihlašovací údaje mohou být pár jednoduchých jméno a heslo pro základní HTTP nebo ověřování hodnotou hash nebo jméno/heslo nebo domény nastavte pro ověřování protokolem NTLM nebo Kerberos. Jedna sada pověření mohou být uloženy ve <xref:System.Net.NetworkCredential> instance nebo více sad mohou být uloženy současně ve <xref:System.Net.CredentialCache> instance. **CredentialCache** používá identifikátor URI požadavku a schéma ověřování, který server podporuje k určení pověření k odeslání na server.  
  
## <a name="simple-requests-with-webclient"></a>Jednoduché požadavky s webovým klientem přes  
 Pro aplikace, které musí být jednoduché požadavky na internetové prostředky <xref:System.Net.WebClient> třída poskytuje běžné metody pro odesílání dat do nebo stahování dat z internetového serveru. **Webový klient** spoléhá na **WebRequest** třída poskytnout přístup k internetovým prostředkům; proto **WebClient** třídy můžete použít jakýkoli registrovaný modulární protokol.  
  
 Pro aplikace, které nelze použít model žádosti a odpovědi, nebo pro aplikace, které potřebují naslouchat na síti a také odesílat požadavky **System.Net.Sockets** obor názvů obsahuje <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>a <xref:System.Net.Sockets.UdpClient> třídy. Tyto třídy zpracovávají údaje o připojení pomocí různé přenosové protokoly a zpřístupňují síťové připojení k aplikaci pomocí datového proudu.  
  
 Vývojáři, kteří znají rozhraní Windows Sockets nebo ty, kteří potřebují ovládacího prvku poskytované programování na úrovni soketu se stát, že **System.Net.Sockets** třídy podle jejich potřeb. **System.Net.Sockets** třídy jsou bod přechod ze spravovaných do nativního kódu v rámci **System.Net** třídy. Ve většině případů **System.Net.Sockets** třídy zařazování dat do jejich protějšky v systému Windows 32-bit, jakož i zpracování kontroluje všechny potřeby zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Ukázky sítě pro .NET na galerie kódů MSDN](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)
