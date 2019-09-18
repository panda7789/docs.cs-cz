---
title: Model deklarovaných identit
ms.date: 03/30/2017
ms.assetid: 4a96a9af-d980-43be-bf91-341a23401431
author: BrucePerlerMS
ms.openlocfilehash: c09d3e177d8b0638f0260b76c163bf668235db29
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045528"
---
# <a name="claims-based-identity-model"></a>Model deklarovaných identit
Při vytváření aplikací pracujících s deklaracemi je identita uživatele ve vaší aplikaci reprezentována jako sada deklarací. Jednou deklarací může být jméno uživatele, další může být e-mailová adresa. Princip spočívá v tom, že je nakonfigurován externí systém identit, který vaší aplikaci poskytuje vše, co pro každou žádost potřebuje o uživateli vědět, a současně pomocí kryptografických metod zaručuje, že přijatá data identity pocházejí z důvěryhodného zdroje.  
  
 Používání tohoto modelu nesmírně zjednodušuje jednotné přihlašování a aplikace již nemusí zodpovídat za následující činnosti:  
  
- Ověřování uživatelů  
  
- Ukládání uživatelských účtů a hesel  
  
- Vyhledávání podrobností identit uživatelů pomocí volání podnikové adresářové služby  
  
- Integrace se systémy identit z jiných platforem nebo od jiných společností  
  
 V rámci tohoto modelu provádí aplikace rozhodnutí týkající se identity na základě deklarací poskytovaných systémem, který uživatele ověřil. Může se jednat o cokoli, od jednoduchého přizpůsobení aplikace pomocí křestního jména uživatele až po povolení přístupu k vyšší úrovni funkcí a prostředků aplikace.  
  
 Toto téma poskytuje následující informace:  
  
- [Úvod do identity založené na deklaracích](claims-based-identity-model.md#BKMK_1)  
  
- [Základní scénář pro model identity založený na deklaracích](claims-based-identity-model.md#BKMK_2)  
  
<a name="BKMK_1"></a>   
## <a name="introduction-to-claims-based-identity"></a>Představení deklarovaných identit  
 Následující terminologie a koncepce vám pomohou pochopit tuto novou architekturu identit.  
  
### <a name="identity"></a>Identita  
 Pro účely popisu programovacího modelu v rámci Windows Identity Foundation (WIF) použijeme termín "identita", který představuje sadu atributů, které popisují uživatele nebo jinou entitu v systému, který chcete zabezpečit.  
  
### <a name="claim"></a>Deklarace  
 Deklaraci identity si můžete představit jako část informací o identitě, jako je jméno, e-mailová adresa, věk, členství v roli Sales (prodej). Čím více deklarací vaše aplikace obdrží, tím více toho budete o uživateli vědět. Možná vás zajímá, proč se jedná o "deklarace", spíše než "atributy", jako by se běžně používaly v popisech podnikových adresářů. Důvod souvisí se způsobem doručení. V tomto modelu nevyhledává aplikace atributy uživatele v adresáři. Namísto toho uživatel poskytuje aplikaci deklarace a aplikace tyto deklarace zkoumá. Každou deklaraci vystavuje vystavitel, přičemž deklarace má stejnou důvěryhodnost jako její vystavitel. Deklarace od řadiče domény vaší společnosti má například větší důvěryhodnost než deklarace od samotného uživatele. WIF představuje deklarace s <xref:System.Security.Claims.Claim> typem, který <xref:System.Security.Claims.Claim.Issuer%2A> má vlastnost, která umožňuje zjistit, kdo tuto deklaraci vystavil.  
  
### <a name="security-token"></a>Token zabezpečení  
 Spolu s žádostí poskytuje uživatel vaší aplikaci sadu deklarací. Ve webové službě se tyto deklarace přenášejí v záhlaví zabezpečení obálky SOAP. Ve webové aplikaci využívající prohlížeč přicházejí deklarace z prohlížeče uživatele prostřednictvím metody POST protokolu HTTP a mohou být následně uloženy do mezipaměti v souboru cookie, pokud aplikace potřebuje pracovat s relacemi. Bez ohledu na způsob jejich doručení musejí být deklarace serializovány, a právě zde se uplatňují tokeny zabezpečení. Token zabezpečení je serializovaná sada deklarací, kterou digitálně podepsala vystavující autorita. Podpis je důležitý, protože poskytuje záruku, že vám uživatel jednoduše neposlal balík deklarací, které sám vytvořil. V situacích, kdy postačuje nízká úroveň zabezpečení a používání kryptografie je zbytečné nebo nevhodné, můžete používat nepodepsané tokeny, ale toto téma tento scénář nepopisuje.  
  
 Jednou ze základních funkcí technologie WIF je možnost vytvářet a číst tokeny zabezpečení. Technologie WIF a rozhraní .NET Framework zastanou všechnu kryptografickou práci a vaší aplikaci předloží sadu deklarací, které si může přečíst.  
  
### <a name="issuing-authority"></a>Vystavující autorita  
 Existuje celá řada různých typů vystavujících autorit, od řadičů domény, které vystavují lístky protokolu Kerberos, až po certifikační autority, které vystavují certifikáty X.509, ale toto téma popisuje konkrétní typ autority, která vystavuje tokeny zabezpečení obsahující deklarace. Vystavující autorita je webová aplikace nebo webová služba, která umí vystavovat tokeny zabezpečení. Musí mít dostatek znalostí, aby dokázala vystavovat správné deklarace pro cílovou předávající stranu a uživatele, který žádost podává. Může také zodpovídat za interakci s úložišti informací o uživatelích za účelem vyhledání deklarací a ověření samotných uživatelů.  
  
 Vystavující autorita, kterou si zvolíte, hraje ústřední roli ve vašem řešení identity. Tím, že ověřování přesunete mimo svou aplikaci a budete se namísto toho spoléhat na deklarace, předáváte zodpovědnost této autoritě a žádáte ji, aby uživatele ověřovala za vás.  
  
### <a name="security-token-service-sts"></a>Služba tokenů zabezpečení (STS)  
 Služba tokenů zabezpečení (STS) je komponenta služby, která vytváří, podepisuje a vystavuje tokeny zabezpečení v souladu s protokoly WS-Trust a WS-Federation. Implementace těchto protokolů vyžaduje velké množství práce, ale technologie WIF odvádí všechnu tuto práci za vás. Díky tomu je zprovoznění služby STS velmi snadné, i když nejste odborníkem na tyto protokoly. Můžete použít předem vytvořenou službu STS, jako je například [Služba Active Directory® Federation Services (AD FS) 2,0](https://go.microsoft.com/fwlink/?LinkID=247516), Cloud STS, jako je [Windows Azure Access Control Service (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517), nebo pokud chcete vydávat vlastní tokeny nebo zajistit vlastní ověřování nebo autorizaci. pomocí WIF můžete vytvořit vlastní STS. Technologie WIF umožňuje snadno vytvořit vlastní službu STS.  
  
### <a name="relying-party-application"></a>Aplikace předávající strany  
 Když vytváříte aplikaci, která se spoléhá na deklarace, vytváříte aplikaci předávající strany. Mezi synonyma pro RP patří "aplikace pracující s deklaracemi" a "aplikace založená na deklaracích". Předávající stranou mohou být webové aplikace i webové služby. Aplikace předávající strany používá tokeny vystavené službou STS a extrahuje z tokenů deklarace, které používá pro úkoly související s identitami. Technologie WIF nabízí funkce, které pomáhají vytvářet aplikace předávající strany.  
  
### <a name="standards"></a>Standardy  
 Pro zajištění vzájemné funkční spolupráce používá předešlý scénář několik standardů WS-*. Zásady jsou načítány s použitím standardu WS-MetadataExchange a samotná struktura zásad musí odpovídat specifikaci WS-Policy. Služba STS zveřejňuje koncové body implementující specifikaci WS-Trust, která popisuje, jak žádat o tokeny zabezpečení a jak je přijímat. Většina STS dnes vydává tokeny naformátované pomocí Security Assertion Markup Language (SAML). Jazyk SAML je slovník XML s podporou v celém odvětví, který umožňuje reprezentovat deklarace tak, aby byla zajištěna vzájemná funkční spolupráce. V případě používání více platforem také umožňuje komunikovat se službou STS na zcela jiné platformě a dosáhnout jednotného přihlašování napříč všemi aplikacemi bez ohledu na platformu.  
  
### <a name="browser-based-applications"></a>Aplikace využívající prohlížeč  
 Model deklarovaných identit nemusejí používat jen inteligentní klienti. Mohou ho používat i aplikace využívající prohlížeč (označované také jako pasivní klienti). Způsob fungování popisuje následující scénář.  
  
 Uživatel nejprve přejde v prohlížeči na webovou aplikaci pracující s deklaracemi (aplikaci předávající strany). Webová aplikace přesměruje prohlížeč na službu STS, aby mohl být uživatel ověřen. Služba STS je hostována v jednoduché webové aplikaci, která přečte příchozí žádost, ověří uživatele pomocí standardních mechanismů protokolu HTTP a poté vytvoří token SAML a zašle odpověď s kódem jazyka JavaScript, který vyvolá metodu HTTP POST, pomocí níž je token SAML odeslán zpět předávající straně. Data přenášená pomocí metody POST obsahují deklarace, které si předávající strana vyžádala. V tomto okamžiku předávající strana často zabalí deklarace do souboru cookie, aby uživatel nemusel být přesměrován pro každou žádost.  
  
<a name="BKMK_2"></a>   
## <a name="basic-scenario-for-a-claims-based-identity-model"></a>Základní scénář pro model deklarovaných identit  
 Následuje příklad systému založeného na deklaracích.  
  
 ![Předávající tok ověřování partnerů](./media/conc-relying-partner-processc.png "conc_relying_partner_processc")  
  
 Tento diagram znázorňuje web (aplikace předávající strany, RP), který byl nakonfigurován, aby pro ověřování používal technologii WIF, a klienta, webový prohlížeč, který chce tento web používat.  
  
1. Když neověřený uživatel požádá o stránku, jejich prohlížeč se přesměruje na stránky zprostředkovatele identity (IdP).  
  
2. IdP vyžaduje, aby uživatel měl k dispozici své přihlašovací údaje, jako je uživatelské jméno/heslo nebo ověřování pomocí protokolu Kerberos.  
  
3. IdP vydá token zpátky do, který se vrátí do prohlížeče.  
  
4. Nyní bude prohlížeč přesměrován zpět na původně požadovanou stránku, kde technologie WIF určí, zda token splňuje požadavky pro přístup ke stránce. Pokud ano, je vystaven soubor cookie pro vytvoření relace, aby ověřování nemuselo probíhat víc než jedenkrát, a řízení je předáno aplikaci.
