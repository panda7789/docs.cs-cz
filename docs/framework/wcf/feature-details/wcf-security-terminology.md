---
title: "Terminologie zabezpečení WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF], terminology
- security glossary [WCF]
- security terms [WCF]
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 352615238d95cf02788cf88ef412a11ffd2faf37
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="wcf-security-terminology"></a>Terminologie zabezpečení WCF
Může být obeznámeni některé z technologiím použitým když hovoříte o zabezpečení. Toto téma poskytuje krátké vysvětlení některých termínů zabezpečení, ale není určená k poskytování komplexní dokumentaci pro každou položku.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] termínů používaných v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dokumentaci najdete v tématu [základní Windows Communication Foundation koncepty](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 seznam řízení přístupu (ACL)  
 Seznam ochranu zabezpečení, která se vztahuje k objektu. (Objekt může být soubor, procesů, události či něco jinak museli popisovač zabezpečení.) Položku v seznamu ACL je položka řízení přístupu (ACE). Existují dva typy seznamů řízení přístupu: volitelný a systému.  
  
 ověřování  
 Proces pro ověření, že uživatel, počítač nebo procesu je kdo nebo co se vydává.  
  
 autorizace  
 V rámci řízení přístupu a práva k prostředku. Například povolení členy skupiny jeden pro čtení souboru, ale umožňuje pouze členy jiné skupiny ke změně souboru.  
  
 certifikát certifikační autority (CA)  
 Identifikuje certifikační Autoritu, která vydává certifikáty pro ověřování serveru a klienta pro servery a klienty, kteří požadují tyto certifikáty. Protože obsahuje veřejný klíč používaný v digitální podpisy, ho se také označuje jako *certifikát podpisu*. Pokud je Certifikační autorita kořenové, může se označovat certifikátu certifikační Autority jako *kořenový certifikát*. Někdy také říká *certifikát webu*.  
  
 Hierarchie certifikačních Autorit  
 Hierarchie certifikačních autorit obsahuje několik certifikačních autorit. Je uspořádán tak, aby každá CA je certifikát od jiného certifikačního úřadu vyšší úrovni hierarchie až do nejvyšší úrovně hierarchie, také známé jako *kořenová autorita*, je dostupný.  
  
 certificate  
 Digitálně podepsaných příkaz, který obsahuje informace o entitě a veřejný klíč entity, proto tyto dvě údaje společně vazby. Po autorita ověřil, že tato entita je kdo ho informacemi o tom, že se že jedná, je certifikát vystavený důvěryhodnou organizaci (nebo entity), nazývá certifikační autoritou.  
  
 Certifikáty mohou obsahovat různé typy dat. Například certifikát X.509 obsahuje formát certifikátu, sériové číslo certifikátu, algoritmus použitý k podepsání certifikátu, název certifikační autority, která vydala certifikát, název a veřejný klíč entity žádosti o certifikát a podpis Certifikační autority.  
  
 úložiště certifikátů  
 Obvykle jsou uloženy trvalé úložiště certifikátů certifikáty, seznamy odvolaných certifikátů (CRL), kde seznamy důvěryhodných certifikátů (CTL). Je však možné, vytvořte a otevřete úložiště certifikátů výhradně v paměti při práci s certifikáty, které není potřeba uvedení v trvalém úložišti.  
  
 Deklarace identity  
 Informace předány jednu entitu do jiného použijí k vytvoření identity uživatele. Například uživatelské jméno a heslo token nebo certifikát X.509.  
  
 Certifikát klienta  
 Odkazuje na certifikátu používaného pro ověřování klientů, jako je například ověřování webový prohlížeč na webovém serveru. Když klientský webový prohlížeč pokusí o přístup k zabezpečeným webový server, klient odešle svůj certifikát serveru tak, aby ji k ověření identity klienta.  
  
 přihlašovací údaje  
 Dřív ověření přihlášení data, která používá objekt zabezpečení a vytvořit tak vlastní identitu, například heslo nebo lístek protokolu Kerberos. Přihlašovací údaje slouží k řízení přístupu k prostředkům.  
  
 Natrávený dat  
 Datový typ obsahu definované veřejný klíč kryptografických standard (PKCS) #7, které se skládá z libovolného typu dat a hodnotu hash zprávy (digest) obsahu.  
  
 digitální podpis  
 Data, která se sváže s odesílané informace identity uživatele. Digitální podpis může dodávat s jakékoli zprávy, soubor nebo jiné digitálně kódovaného informace nebo přenést samostatně. Digitální podpisy se používají v prostředí veřejných klíčů a poskytuje služby ověřování a integrity.  
  
 encoding  
 Proces zapnutí data do datového proudu bitů. Kódování je součástí serializace proces, který převádí data do datového proudu a jedniček.  
  
 pár klíčů Exchange  
 Páru veřejného a privátního klíče RSA použitý k šifrování klíče relace tak, aby bylo možné bezpečně uložená a vyměňují s ostatními uživateli.  
  
 hash  
 Pevné velikosti číselnou hodnotu aplikací matematické funkce (viz algoritmus hash) na libovolné množství dat získat. Data obvykle obsahují náhodná data, označuje jako *hodnotu nonce*. Služby a klienta přispívat náhodně generované identifikátory exchange zvýšit složitost výsledku. Výsledkem je také označován jako *hodnota hash*. Odesílání hodnotu hash je bezpečnější než odesílání citlivých dat, jako například heslo, i v případě, že heslo je zašifrováno. Hodnota hash odesílatele a příjemce, musíte souhlasit na algoritmu hash a náhodně generované identifikátory tak, aby po přijetí, můžete ověřit hodnotu hash.  
  
 algoritmus hash  
 Algoritmus sloužící k vytvoření hodnoty hash některé část dat, jako jsou zprávy nebo relace klíče. Typické algoritmy hash zahrnují MD2, MD4, MD5 a SHA-1.  
  
 Protokol Kerberos  
 Protokol, který definuje způsob interakce klientů s služby ověřování sítě. Klienti získat lístky z protokolu Kerberos Center KDC (Key Distribution) a představují těchto lístků na servery, když se připojení vytvářejí. Lístky protokolu Kerberos představují přihlašovací údaje k síti klienta.  
  
 místní úřad zabezpečení (LSA)  
 Chráněný podsystém, který ověřuje a přihlašuje uživatele k místního systému. LSA také udržuje informace o všech aspektech místního zabezpečení v systému, společně označované jako místní zásady zabezpečení systému.  
  
 Vyjednávání  
 Zprostředkovatel podpory zabezpečení (SSP), který funguje jako vrstva aplikací od jiných SSP rozhraní SSPI (Security Support Provider Interface). Pokud aplikace zavolá rozhraní SSPI pro přihlášení k síti, může však určovat zprostředkovatele sdílených služeb pro zpracování požadavku. Pokud aplikace určí `Negotiate`, `Negotiate` analyzuje požadavek a vybere nejlepší zprostředkovatele sdílených služeb pro zpracování požadavku na základě zásad zabezpečení nakonfigurované zákazníka.  
  
 hodnotu Nonce  
 Náhodně generované hodnoty používá k "opakování" útoky.  
  
 nepopiratelnosti odpovědnosti  
 Možnost k identifikaci uživatelů, kteří provést určité akce, proto irrefutably zamezením pokusy uživatele o odepřít zodpovědnost. Například může systém protokolu ID uživatele, vždy, když někdo odstraní nějaký soubor.  
  
 Kryptografie využívající veřejného klíče Standard (PKCS č.)  
 Specifikace vyprodukované RSA Data Security, Inc. ve spolupráci s vývojáři zabezpečených systémů po celém světě chcete-li zrychlit nasazení šifrování veřejného klíče.  
  
 PKCS #7  
 Standard Cryptographic Message Syntax Standard. Obecná syntaxe pro data, která šifrování může použít, jako jsou například digitálních podpisů a šifrování. Poskytuje také syntaxe pro šíření certifikáty nebo seznamy odvolaných certifikátů a další atributy, zprávu, například časová razítka ke zprávě.  
  
 ve formátu prostého textu  
 Zpráva, která nejsou šifrována. Zprávy ve formátu prostého textu se někdy označují jako *nezašifrovaný text* zprávy.  
  
 privilege  
 Práva uživatele k provedení různých operací souvisejících s systému, například vypínání systému, načítání ovladače zařízení nebo změně systémového času. Přístupový token uživatele obsahuje seznam oprávnění, že uživatel nebo uživatele skupiny uchování.  
  
 privátní klíč  
 Tajný polovina pár klíčů použít v algoritmu veřejného klíče. Soukromé klíče jsou obvykle používány k šifrování symetrického klíče relace, digitálně podepsat zprávu nebo zprávu, která byla zašifrována pomocí odpovídající veřejný klíč pro dešifrování. Viz také "veřejný klíč."  
  
 zpracování  
 Kontext zabezpečení, pod kterým je aplikace spuštěna. Kontext zabezpečení je obvykle související s uživatelem, tak všechny aplikace spuštěné v rámci dané proces trvat na oprávnění a oprávnění vlastnícím uživatele.  
  
 pár veřejného a privátního klíče  
 Sada kryptografických klíčů používaných pro kryptografie využívající veřejného klíče. Pro každého uživatele, zprostředkovatele kryptografických služeb (CSP) obvykle udržuje dvě dvojice veřejných/privátních klíčů: dvojici klíčů exchange a pár klíčů digitální podpis. Relace relace jsou zachována i páry klíčů.  
  
 veřejný klíč  
 Kryptografický klíč, který obvykle používaný k dešifrování klíče relace nebo digitální podpis. Veřejný klíč slouží také k šifrování zpráv, která zaručí, že pouze osoba s odpovídající privátní klíč může dešifrování zprávy.  
  
 šifrování pomocí veřejného klíče  
 Šifrování, který používá dvojici klíčů, jeden klíč k šifrování dat a další klíč pro dešifrování dat. Naproti tomu symetrický šifrovací algoritmy, které používají stejné klíče pro šifrování a dešifrování. V praxi se obvykle používá kryptografie využívající veřejného klíče k ochraně klíče relace, které používá algoritmus symetrického šifrování. V takovém případě veřejný klíč slouží k šifrování klíče relace, které se pak používá k šifrování některá data a privátní klíč se používá k dešifrování. Kromě ochrany klíče relace, může kryptografie využívající veřejného klíče použít také k digitálnímu podepisování zprávu (pomocí soukromého klíče) a ověřit podpis (pomocí veřejného klíče).  
  
 Infrastruktury veřejných klíčů (PKI)  
 Infrastrukturou, která poskytuje integrované sadu služeb a nástroje pro správu pro vytváření, nasazování a správě aplikací veřejného klíče.  
  
 popírání odpovědnosti  
 Možnost uživatele nesprávně Odepřít má provést akce v průběhu jiné strany nelze prokázat, jinak hodnota. Například uživatel, který odstraní soubor a který můžete úspěšně odepřít tak učinili.  
  
 kořenová autorita  
 Certifikační Autority v horní části hierarchie certifikačních autorit. Kořenovou autoritou potvrzuje certifikační autority v další úroveň v hierarchii.  
  
 Algoritmus Hash SHA (SHA)  
 Algoritmus hash, který generuje hodnota hash. SHA se používá s digitální podpis algoritmus (DSA) v standardní DSS (Digital Signature), mimo jiné. Existují čtyři typy SHA: SHA-1, SHA-256, SHA-384 a SHA-512. SHA-1 generuje 160bitovou hodnotu hash. Algoritmus SHA-256, SHA-384 a SHA-512 generovat 256 bitů, 384 bitů a hodnoty Digest 512bitové zprávy, v uvedeném pořadí. SHA byla vyvinuta podle národního institutu standardů a technologie (NIST) a National zabezpečení agentura (NSA).  
  
 Secure Sockets Layer (SSL)  
 Protokol pro komunikaci zabezpečené sítě prostřednictvím technologie veřejné a tajný klíč.  
  
 kontext zabezpečení  
 Atributy zabezpečení nebo pravidla, která je aktuálně použito. Například aktuální uživatel přihlášený k počítači, nebo osobní identifikační číslo, zadané uživatelem čipové karty. Kontext zabezpečení pro rozhraní SSPI, je neprůhledného datová struktura, která obsahuje data zabezpečení, které jsou relevantní pro připojení, jako je například klíč relace nebo údajem o dobu trvání relace.  
  
 objekt zabezpečení  
 Entity zabezpečení systému rozpoznat. Objekty zabezpečení může obsahovat lidského uživatelé, jakož i autonomního procesy.  
  
 Zprostředkovatel podpory zabezpečení (SSP)  
 Dynamická knihovna (DLL), který implementuje rozhraní SSPI tím, že jeden nebo více balíčků zabezpečení dostupné pro aplikace. Každý balíček zabezpečení poskytuje mapování mezi volání funkcí rozhraní SSPI aplikace a funkce skutečného zabezpečení model. Balíčky zabezpečení podporovat protokoly zabezpečení, jako je například ověřování protokolem Kerberos a Microsoft LAN Manager (LanMan).  
  
 Rozhraní poskytovatele podpory zabezpečení (SSPI)  
 Společné rozhraní mezi aplikací transportní vrstvy, jako je například Microsoft vzdáleného volání procedur (RPC) a poskytovatelé zabezpečení, například Windows distributed security. Rozhraní SSPI umožňuje přenos aplikace volání jednoho několik poskytovatelů zabezpečení získat ověřené připojení. Tyto volání nevyžadují rozsáhlé znalosti o podrobnosti o protokol zabezpečení.  
  
 služby tokenů zabezpečení  
 Služby navržená tak, aby vydávat a spravovat tokeny zabezpečení vlastní (vystavené tokeny) v případě multiservice. Vlastní tokeny jsou obvykle tokeny zabezpečení kontrolní výrazy Markup Language (SAML), které zahrnují vlastní pověření.  
  
 certifikát serveru  
 Odkazuje na certifikát používaný k ověření serveru, jako je například ověřování webového serveru do webového prohlížeče. Když klientský webový prohlížeč pokusí o přístup k zabezpečeným webový server, server odešle svůj certifikát do prohlížeče tak, aby ji ověřit identitu serveru.  
  
 Relace  
 Výměnou zpráv pod ochranu jediný klíčový materiál. Relace SSL je třeba použít jeden klíč odeslat více zpráv a zpět pod tímto klíčem.  
  
 klíč relace  
 Náhodně generovaný klíč, který je použit jednou a potom je zahozen. Klíče relace jsou symetrické (používá se pro šifrování a dešifrování). Se odešlou se zprávou, chráněná šifrováním pomocí veřejného klíče z zamýšlený příjemce. Klíč relace se skládá z náhodné číslo přibližně 40 až 2 000 bitů.  
  
 dodatečné přihlašovací údaje  
 Přihlašovací údaje pro použití v ověřování objekt zabezpečení k doménám cizí zabezpečení.  
  
 symetrické šifrování  
 Šifrování, která používá jeden klíč pro šifrování a dešifrování. Při šifrování velkých objemů dat je upřednostňovaný symetrického šifrování. Některé z běžnějších algoritmy symetrického šifrování jsou RC2 RC4 a Data Encryption (Standard DES).  
  
 Viz také "veřejný šifrovací klíč."  
  
 Symetrický klíč  
 Jeden klíč používaný k šifrování a dešifrování. Jsou obvykle symetrického klíče relace.  
  
 Token (přístupový token)  
 Přístupový token obsahuje informace o zabezpečení pro relace přihlášení. Systém vytvoří přístupový token při přihlášení uživatele a každý proces spuštěný jménem uživatele má kopii token. Token identifikuje uživatele, skupiny uživatele a oprávnění uživatele. Systém použije token řídit přístup k zabezpečitelným objektům a ovládání možnosti uživatele k provedení různých operací souvisejících s systému v místním počítači. Existují dva druhy přístupových tokenů, primární a zosobnění.  
  
 přenosové vrstvy  
 Vrstva sítě, která je zodpovědná za obou kvality služeb a přesná doručení informací. Mezi úlohy prováděné v této vrstvě jsou rozpoznávání a opravy chyb.  
  
 Seznam důvěryhodnosti (seznam důvěryhodných certifikátů nebo seznam CTL)  
 Předdefinované seznam položek, které byly podepsány důvěryhodným subjektem. Seznam důvěryhodných certifikátů může být jakýkoli, jako je například seznam hodnot hash certifikátů nebo seznam názvů souborů. Všechny položky v seznamu, se ověřují (schválení) podpisový entita.  
  
 vztah důvěryhodnosti zprostředkovatele  
 Software, který rozhodne, zda je daný soubor důvěryhodný. Toto rozhodnutí je založena na spojených se souborem certifikátu.  
  
 Hlavní název uživatele (UPN)  
 Název uživatelského účtu (někdy označovány jako *přihlašovací uživatelské jméno*) a název domény určujícího doménu, ve kterém se nachází uživatelský účet. Toto je standardní použití pro přihlášení k doméně systému Windows. Formát je: someone@example.com (jako u e-mailovou adresu).  
  
> [!NOTE]
>  Kromě standardní UPN formuláře [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přijímá UPN v podobě nižší úrovně, například cohowinery.com\someone.  
  
 X.509  
 Mezinárodní úrovni rozpoznaný standard pro certifikáty definující jejich požadované součásti.  
  
## <a name="see-also"></a>Viz také  
 [Základní koncepty Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md)  
 [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
