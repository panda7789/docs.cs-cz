---
title: Terminologie zabezpečení WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], terminology
- security glossary [WCF]
- security terms [WCF]
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 72a2ea1393daa7435ae233d1e420cf88b6f5b6af
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649442"
---
# <a name="wcf-security-terminology"></a>Terminologie zabezpečení WCF
Některé o terminologii používané diskuse o zabezpečení mohou být obeznámeni. Toto téma poskytuje krátký vysvětlení některých pojmů pro zabezpečení, ale není určená k poskytování komplexní dokumentaci pro každou položku.  
  
 Další informace o termínů používaných v dokumentaci k Windows Communication Foundation (WCF), najdete v části [základní koncepty Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 seznam řízení přístupu (ACL)  
 Seznam ochranu zabezpečení, která se vztahuje k objektu. (Objekt může být soubor, proces, události nebo něco jinak s popisovač zabezpečení.) Položky v seznamu ACL portu je položky řízení přístupu (ACE). Existují dva typy seznamů ACL: volitelný a systému.  
  
 ověřování  
 Proces ověření, uživatele, počítače, služby nebo procesu je kdo nebo co se vydává.  
  
 autorizace  
 V rámci řízení přístupu a oprávnění k prostředku. Například umožňuje členům v jedné skupině ke čtení souboru, ale umožňuje pouze členy jiné skupiny ke změně souboru.  
  
 certifikát certifikační autority (CA)  
 Určuje, která vydává certifikáty pro ověřování serveru a klienta na servery a klienty, kteří požadují tyto certifikáty certifikační Autority. Protože obsahuje veřejný klíč používaný v digitální podpisy, to se také označuje jako *certifikát podpisu*. Pokud certifikační Autorita je kořenovou autoritou, certifikát certifikační Autority může odkazovat jako *kořenový certifikát*. Někdy také říká *certifikát lokality*.  
  
 Hierarchie certifikačních Autorit  
 Hierarchie certifikačních Autorit obsahuje více certifikačních autorit. Je uspořádán tak, aby každý certifikační Autority je certifikovaný jinou certifikační Autoritou v vyšší úroveň hierarchie až do nejvyšší úrovni hierarchie, označované také jako *kořenová autorita*, je dosaženo.  
  
 certificate  
 Digitálně podepsané prohlášení s informacemi o entitu a veřejný klíč entity, tedy dohromady vazby tyto dva druhy údajů. Certifikát vystaven důvěryhodnou autoritou organizace (nebo entity), volá se, certifikace, po oprávnění ověřila, že entita je který říká, že se že jedná.  
  
 Certifikáty mohou obsahovat různé typy dat. Například certifikát X.509, který obsahuje formát certifikátu a sériové číslo certifikátu, algoritmus použitý k podepsání certifikátu a název certifikační autority, která vydala certifikát, název a veřejný klíč entity žádosti o certifikát a Certifikační autority podpis.  
  
 Úložiště certifikátů  
 Obvykle jsou uloženy trvalé úložiště certifikátů certifikáty, seznamy odvolaných certifikátů (CRL), kde seznamy důvěryhodných certifikátů (CTL). Je však možné, vytvořit a otevřít úložiště certifikátů výhradně v paměti, při práci s certifikáty, které není potřeba umístit do trvalého úložiště.  
  
 deklarace identity  
 Informace předány do jiného používá k navázání identity uživatele z entit. Například uživatelské jméno a heslo token nebo certifikát X.509.  
  
 klientský certifikát  
 Odkazuje na certifikát, který slouží pro ověřování klientů, jako je například ověřování webový prohlížeč na webovém serveru. Když webového prohlížeče klienta se pokusí o přístup k zabezpečené webový server, klient odešle svůj certifikát na server, aby mohla ověřit identitu klienta.  
  
 Přihlašovací údaje  
 Dříve ověřit data přihlášení, které objektu zabezpečení se používá k vytvoření vlastní identity, jako jsou hesla nebo lístek protokolu Kerberos. Přihlašovací údaje se používají k řízení přístupu k prostředkům.  
  
 abstrahovanou dat  
 Datový typ obsahu definovaný pomocí veřejného klíče kryptografické standard (PKCS) #7, který se skládá z libovolného typu dat a zpráva hodnoty hash (přehled) obsah.  
  
 digitální podpis  
 Data, která se sváže s informace odesílané identity uživatele. Digitální podpis může dodávat s jakékoli zprávy, soubor nebo jiné digitálně kódovaného informace nebo přenášet samostatně. Digitální podpisy se používají v prostředí veřejných klíčů a poskytnout integritu a ověřování.  
  
 encoding  
 Proces přeměny data do datového proudu bitů. Kódování je součástí procesu serializace, který převádí data do datového proudu a jedniček.  
  
 pár klíčů Exchange  
 Dvojice veřejného/soukromého klíče použitý k šifrování klíče relace, takže je možné bezpečně uložená a s ostatními uživateli, které si vyměňují.  
  
 hash  
 Pevné velikosti číselnou hodnotu použitím matematických funkcí (viz algoritmus hash) na libovolné množství dat získali. Data obvykle obsahují náhodná data, nazývá *nonce*. Služby a klient přispívat náhodně generované identifikátory exchange ke zvýšení složitosti výsledek. Výsledek je také označován jako *hash*. Odesláním hodnoty hash je bezpečnější než posláním citlivých dat, jako je heslo, i v případě, že heslo je zašifrováno. Hodnota hash odesílatele a příjemce musí shodnout na algoritmu hash a náhodně generované identifikátory tak, aby po přijetí, můžete ověřit hodnotu hash.  
  
 Algoritmus hash  
 Algoritmus používaný k vytvoření hodnoty hash nějakou část dat, jako jsou zprávy nebo relace klíče. Typické algoritmy hash zahrnují MD2, MD4, MD5 a SHA-1.  
  
 Protokol Kerberos  
 Protokol, který definuje způsob interakce klientů se síťovou službou ověřování. Klienti získat lístky z protokolu Kerberos distribuce Center KDC (Key) a představují tyto lístky na servery, když se připojení vytvářejí. Lístky protokolu Kerberos představují přihlašovací údaje k síti klienta.  
  
 místní autority zabezpečení (LSA)  
 Chráněné subsystému, která ověřuje a protokoly uživatelů do místního systému. LSA také udržuje informace o všech aspektech zabezpečení v systému, souhrnně označované jako místní zásady zabezpečení systému.  
  
 Vyjednávání  
 Zprostředkovatel podpory zabezpečení (SSP), který funguje jako aplikační vrstva mezi rozhraní SSPI Security Support Provider Interface () a další zprostředkovatele sdílených služeb. Pokud aplikace zavolá rozhraní SSPI pro přihlášení k síti, můžete zadat zprostředkovatele sdílených služeb ke zpracování požadavku. Pokud aplikace určí `Negotiate`, `Negotiate` analyzuje požadavek a vybere nejlepší zprostředkovatele sdílených služeb ke zpracování požadavku na základě zásad zabezpečení nakonfigurované zákazníka.  
  
 Hodnota Nonce  
 Náhodně generované hodnoty používají k překonání útoky "opakování".  
  
 nepopiratelnosti odpovědnosti  
 Schopnost identifikovat uživatele, kteří provést některé akce, tedy irrefutably zamezením pokusy uživatele o odepřít odpovědnost. Systém může Protokolujte například, ID uživatele při každém odstranění souboru.  
  
 Kryptografie využívající veřejného klíče Standard (PKCS č.)  
 Specifikace vytvářených RSA Data zabezpečení, Inc. ve spolupráci s vývojáři, kteří zabezpečené systémy po celém světě k urychlení nasazení kryptografie využívající veřejný klíč.  
  
 PKCS #7  
 Standardní syntaxe Cryptographic Message. Obecnou syntaxi pro data šifrování, které může použít, jako je například digitálních podpisů a šifrování. Také poskytuje syntaxi pro šíření certifikátů nebo seznam odvolaných certifikátů a další atributy zpráv, jako jsou časová razítka na zprávu.  
  
 ve formátu prostého textu  
 Zpráva, která nejsou šifrována. Zprávy ve formátu prostého textu se někdy označují jako *jako nezašifrovaný text* zprávy.  
  
 oprávnění  
 Práva uživatele k provádění různých operací souvisejících s systému, jako je například vypnutí systému, načítání ovladače nebo systémového času. Přístupový token uživatele obsahuje seznam oprávnění, uživatele nebo uživatele skupiny blokování.  
  
 privátní klíč  
 Tajný polovinu dvojice klíčů používané algoritmus veřejného klíče. Privátní klíče se obvykle používají se zašifrovat symetrického klíče relace, digitálně podepsat zprávy nebo dešifrovat zprávu, která byla dříve zašifrována s odpovídajícím veřejným klíčem. Viz také "veřejný klíč."  
  
 zpracování  
 Kontext zabezpečení, pod kterým je aplikace spuštěna. Kontext zabezpečení je obvykle související s uživatelem, tak všechny aplikace spuštěné v rámci daného procesu převezmou oprávnění a oprávnění vlastnícího uživatele.  
  
 dvojice veřejného/soukromého klíče  
 Sada kryptografických klíčů využívaných pro kryptografii využívající veřejného klíče. Pro každého uživatele, zprostředkovatele kryptografických služeb (CSP) obvykle udržuje dvě veřejného/soukromého klíče dvojice: páru klíčů exchange a pár klíče využívá digitální podpis. Relace relace jsou zachována i párů klíčů.  
  
 veřejný klíč  
 Kryptografický klíč, obvykle používaný k dešifrování klíče relace nebo digitální podpis. Veřejný klíč slouží také k zašifrování zprávy, zajištění, že pouze osoba s odpovídající privátní klíč lze dešifrování zprávy.  
  
 šifrování pomocí veřejného klíče  
 Šifrování, který používá dvojici klíčů, jeden klíč k šifrování dat a další klíč k dešifrování dat Naproti tomu symetrický šifrovací algoritmy, které používají stejný klíč k šifrování a dešifrování. V praxi se obvykle používá kryptografii využívající veřejného klíče k ochraně klíče relace, které používá algoritmus symetrického šifrování. V takovém případě veřejný klíč slouží k šifrování klíče relace, které se pak použil k zašifrování nějaká data, a privátní klíč slouží k dešifrování. Kromě ochrany klíčů relací, kryptografii využívající veřejného klíče může také sloužit k digitálnímu podepisování zprávy (pomocí privátního klíče) a ověřit podpis (pomocí veřejného klíče).  
  
 infrastruktury veřejných klíčů (PKI)  
 Infrastrukturou, která poskytuje integrovaná sada služeb a nástroje pro správu pro vytváření, nasazování a správu aplikací veřejného klíče.  
  
 odmítnutí  
 Umožňuje uživateli falešně odmítat s provést akci při jiné strany nemůže prokázat jinak. Například uživatel, který odstraní soubor a který můžete úspěšně odepřít tak učinili.  
  
 kořenová autorita  
 Certifikační Autorita v horní části hierarchie certifikačních Autorit. Kořenová autorita certifikuje certifikační autority v další úroveň hierarchie.  
  
 Zabezpečené hashovací algoritmus (SHA)  
 Hashovací algoritmus, který generuje zprávy digest. SHA se používá s digitální podpis algoritmus (DSA) v digitální podpis DSS (Standard), mimo jiné. Existují čtyři typy prvků SHA: SHA-1, SHA-256, SHA-384 a SHA-512. SHA-1 vytváří 160bitovou digest. SHA-256, SHA-384 a SHA-512 generovat 256bitový, 384 bitů a hodnoty Digest 512 bitů zprávy, v uvedeném pořadí. SHA byla vyvinuta National Institute of Standards and Technology (NIST) a National Security Agency (NSA).  
  
 Secure Sockets Layer (SSL)  
 Protokol pro komunikaci zabezpečené sítě díky kombinaci klíčová technologie pro veřejné a tajného kódu.  
  
 kontext zabezpečení  
 Atributy zabezpečení nebo pravidla, která jsou momentálně aktivní. Například aktuální uživatel přihlášen k počítači nebo osobní identifikační číslo zadané uživatelem čipové karty. Kontext zabezpečení pro SSPI, je neprůhledný datovou strukturu, která obsahuje data zabezpečení, které jsou relevantní pro připojení, jako je například klíč relace nebo údaj o dobu trvání relace.  
  
 objekt zabezpečení  
 Entita zabezpečení systémem rozpoznán. Objekty zabezpečení může zahrnovat uživateli, stejně jako autonomní procesy.  
  
 Zprostředkovatel podpory zabezpečení (SSP)  
 Dynamická knihovna (DLL), která implementuje rozhraní SSPI tím, že jeden nebo více balíčků zabezpečení dostupné pro aplikace. Každý balíček zabezpečení zajišťuje mapování mezi volání funkcí rozhraní SSPI aplikace a funkce modelu zabezpečení. Balíčky zabezpečení podporují protokoly zabezpečení, jako je například ověřování protokolem Kerberos a Microsoft LAN Manager (LanMan).  
  
 Security Support Provider Interface (SSPI)  
 Obecné rozhraní mezi aplikací transportní vrstvy, jako je například Microsoft vzdálené volání procedur (RPC) a zprostředkovatele zabezpečení, jako je například Windows distributed security. Rozhraní SSPI umožňuje přenos aplikace volání jednoho z několik zprostředkovatelů zabezpečení získat ověřené připojení. Tato volání nevyžadují rozsáhlé znalosti o podrobnosti protokolu zabezpečení.  
  
 Služba tokenů zabezpečení  
 Služby navržené tak vydávat a spravovat vlastní bezpečnostní tokeny (vystavené tokeny) ve scénáři multiservice. Vlastní tokeny jsou obvykle tokeny zabezpečení kontrolní výrazy SAML (Markup Language), zahrnující vlastní přihlašovací údaje.  
  
 certifikát serveru  
 Odkazuje na certifikát, který slouží k ověření serveru, například při ověřování ve webovém serveru do webového prohlížeče. Když webového prohlížeče klienta se pokusí o přístup k zabezpečené webový server, server odešle svůj certifikát do prohlížeče, aby mohla ověřit identitu serveru.  
  
 Relace  
 Výměna zpráv v rámci ochrany jednoduchým šifrovací klíče. Například relace protokolu SSL použít jeden klíč k odeslání více zpráv vpřed a zpět v rámci tohoto klíče.  
  
 klíč relace  
 Náhodně vygenerovaný klíč, který je jednou a potom je zahozen. Klíče relace jsou symetrické (používá se pro šifrování a dešifrování). Jejich odesláním se zprávou, chráněná šifrováním pomocí veřejného klíče z zamýšlený příjemce. Klíč relace se skládá z náhodné číslo přibližně 40 až 2 000 bitů.  
  
 doplňující údaje  
 Použijte přihlašovací údaje pro ověřování objektu zabezpečení na zabezpečení domény ve.  
  
 symetrické šifrování  
 Šifrování, které používá jeden klíč k šifrování a dešifrování. Symetrické šifrování se upřednostňuje v případě velkého objemu dat šifrování. Některé z běžnějších symetrický šifrovací algoritmy jsou RC2, RC4 a šifrování Standard DES (Data).  
  
 Viz také "šifrování s veřejným klíčem."  
  
 Symetrický klíč  
 Jeden klíč slouží k šifrování a dešifrování. Jsou obvykle symetrického klíče relace.  
  
 Token (přístupový token)  
 Přístupový token obsahuje informace o zabezpečení pro relaci přihlášení. Systém vytvoří přístupový token při přihlášení uživatele a každý proces spuštěný jménem uživatele má kopii tohoto tokenu. Token, který identifikuje uživatele, skupiny uživatelů a oprávnění uživatele. Systém používá token pro řízení přístupu k zabezpečeným objektům a ovládání možnosti uživatele můžete provádět různé operace týkající se systému v místním počítači. Existují dva druhy přístupové tokeny, primární a zosobnění.  
  
 přenosové vrstvy  
 Síťové vrstvy, který je zodpovědný za oba kvalitu služeb a přesné doručování informací. Mezi úlohy prováděné v této vrstvě patří Chyba zjišťování a opravy.  
  
 Seznam důvěryhodnosti (seznam důvěryhodných certifikátů nebo seznam CTL)  
 Předdefinované seznam položek, které byly podepsány důvěryhodným entity. Seznam CTL může být cokoli, jako je například seznam hodnot hash certifikátů nebo seznam názvů souborů. Všechny položky v seznamu ověření (schválit) podpisový entity.  
  
 vztah důvěryhodnosti zprostředkovatele  
 Software, který určuje, zda daný soubor je důvěryhodný. Toto rozhodnutí je na základě certifikátu přidruženého k souboru.  
  
 hlavní název uživatele (UPN)  
 Název uživatelského účtu (někdy označovány jako *přihlašovací uživatelské jméno*) a název domény identifikující doménu, ve kterém se nachází uživatelský účet. Toto je standardní využití pro přihlášení k doméně Windows. Formát je: someone@example.com (jako u e-mailovou adresu).  
  
> [!NOTE]
>  Kromě běžného formuláře (UPN) WCF přijímá UPN v podobě nižší úrovně, například cohowinery.com\someone.  
  
 X.509  
 Mezinárodně uznávané standard pro certifikáty, které definuje jejich požadované části.  
  
## <a name="see-also"></a>Viz také  
 [Základní koncepty Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md)  
 [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
