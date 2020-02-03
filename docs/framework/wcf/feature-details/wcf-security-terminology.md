---
title: Terminologie zabezpečení WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], terminology
- security glossary [WCF]
- security terms [WCF]
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
ms.openlocfilehash: 6751513b72f732bd7392de11a203467a9ead1bce
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743355"
---
# <a name="wcf-security-terminology"></a>Terminologie zabezpečení WCF
Některá z terminologie, která se používá, když je diskuze o zabezpečení možná neznámá. Toto téma obsahuje krátká vysvětlení některých bezpečnostních podmínek, ale není určena k poskytnutí komplexní dokumentace pro každou položku.  
  
 Další informace o pojmech používaných v dokumentaci k Windows Communication Foundation (WCF) najdete v tématu [základní koncepty Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 seznam řízení přístupu (ACL)  
 Seznam ochrany zabezpečení, které se vztahují k objektu. (Objekt může být soubor, proces, událost nebo cokoli jiného, co má popisovač zabezpečení.) Položka v seznamu ACL je položka řízení přístupu (ACE). Existují dva typy seznamů ACL: volitelné a systémové.  
  
 ověřování  
 Proces ověření, jestli se jedná o uživatele, počítač, službu nebo proces.  
  
 autorizace  
 Řízení přístupu k prostředku a oprávnění k němu. Například umožnění, aby členové jedné skupiny mohli číst soubor, ale umožňují pouze členům jiné skupiny upravovat soubor.  
  
 certifikát certifikační autority (CA)  
 Identifikuje certifikační autoritu, která vydává certifikáty pro ověřování serveru a klienta, na servery a klienty, kteří požadují tyto certifikáty. Protože obsahuje veřejný klíč, který se používá v digitálních podpisech, označuje se také jako *certifikát podpisu*. Pokud je certifikační autorita kořenovou autoritou, může se certifikát certifikační autority označovat jako *kořenový certifikát*. Někdy se také označuje jako *certifikát webu*.  
  
 Hierarchie certifikační autority  
 Hierarchie certifikační autority obsahuje několik certifikačních autorit. Je uspořádána tak, že je dosaženo maximálního počtu CERTIFIKAČNÍch autorit jiné certifikační autority v vyšší úrovni hierarchie až do nejvyšší úrovně v hierarchii, která se označuje také jako *Kořenová autorita*.  
  
 certifikát  
 Digitálně podepsaný příkaz, který obsahuje informace o entitě a veřejném klíči entity, takže tyto dva druhy informací propojuje. Certifikát je vydán důvěryhodnou organizací (neboli entitou), která se označuje jako certifikační autorita, poté, co autorita ověří, že se jedná o subjekt, který je vyjadřuje.  
  
 Certifikáty mohou obsahovat různé typy dat. Například certifikát X. 509 zahrnuje formát certifikátu, sériové číslo certifikátu, algoritmus použitý k podepsání certifikátu, název certifikační autority, která certifikát vystavila, název a veřejný klíč entity požadující certifikát. a podpis certifikační autority.  
  
 úložiště certifikátů  
 Obvykle se jedná o trvalé úložiště, ve kterém jsou uložené certifikáty, seznamy odvolaných certifikátů (CRL) a seznamy důvěryhodných certifikátů (CTL). Je ale možné vytvořit a otevřít úložiště certifikátů výhradně v paměti při práci s certifikáty, které není nutné ukládat do trvalého úložiště.  
  
 claims  
 Informace předané z jedné entity do druhé, která se používá k vytvoření identity odesilatele. Například uživatelské jméno a token hesla nebo certifikát X. 509.  
  
 certifikát klienta  
 Odkazuje na certifikát používaný pro ověřování klientů, jako je například ověřování webového prohlížeče na webovém serveru. Když se klient webového prohlížeče pokusí o přístup k zabezpečenému webovému serveru, klient odešle svůj certifikát serveru, aby mohl ověřit identitu klienta.  
  
 přihlašovací údaje  
 Dříve ověřená přihlašovací data, která objekt zabezpečení používá k vytvoření vlastní identity, jako je například heslo nebo lístek protokolu Kerberos. Pověření slouží k řízení přístupu k prostředkům.  
  
 data ve Digest  
 Typ obsahu definovaný pomocí standardu PKCS (Public Key Cryptographic Standard) #7, který se skládá z libovolného typu dat plus hodnota hash (Digest) obsahu.  
  
 Digitální podpis  
 Data, která váže identitu odesilatele k odesílaným informacím. Digitální podpis může být součástí libovolné zprávy, souboru nebo jiné digitálně kódované informace nebo se přenáší samostatně. Digitální podpisy se používají v prostředích veřejných klíčů a poskytují služby ověřování a integrity.  
  
 encoding  
 Proces přepínání dat do datového proudu bitů. Kódování je součástí procesu serializace, který převádí data na datový proud a nuly.  
  
 pár klíčů pro výměnu  
 Pár veřejného a privátního klíče sloužící k šifrování klíčů relace tak, aby bylo možné je bezpečně uložit a vyměňovat s ostatními uživateli.  
  
 hash  
 Číselná hodnota pevné velikosti získaná použitím matematické funkce (viz algoritmus hash) na libovolný objem dat. Data obvykle zahrnují náhodná data, která se označují jako *hodnota nonce*. Hodnoty nonce systému Exchange pro službu i klienta přispívají k zvýšení složitosti výsledku. Výsledek je také označován jako *Digest zprávy*. Odeslání hodnoty hash je bezpečnější než posílání citlivých dat, jako je heslo, i když je heslo šifrované. Odesílatel a příjemce hodnoty hash musí souhlasit s algoritmem hash a náhodně tak, aby po přijetí bylo možné ověřit hodnotu hash.  
  
 algoritmus hash  
 Algoritmus, který slouží k vytvoření hodnoty hash některých částí dat, jako je například zpráva nebo klíč relace. Mezi typické algoritmy hash patří MD2, MD4, MD5 a SHA-1.  
  
 Protokol Kerberos  
 Protokol, který definuje, jak klienti komunikují se službou ověřování v síti. Klienti získávají lístky z protokolu Kerberos služba KDC (Key Distribution Center) (KDC) a při navázání připojení prezentují tyto lístky na servery. Lístky protokolu Kerberos reprezentují síťová pověření klienta.  
  
 místní úřad zabezpečení (LSA)  
 Chráněný podsystém, který ověřuje a zapisuje uživatele do místního systému. LSA také uchovává informace o všech aspektech místního zabezpečení v systému, které se souhrnně označují jako místní zásady zabezpečení systému.  
  
 Mluví  
 Zprostředkovatel podpory zabezpečení (SSP), který funguje jako aplikační vrstva mezi rozhraním SSPI (Security Support Provider Interface) a jiným zprostředkovatelem sdílených služeb. Když aplikace zavolá rozhraní SSPI, aby se přihlásila k síti, může určit zprostředkovatele sdílených služeb pro zpracování žádosti. Pokud aplikace určí `Negotiate`, `Negotiate` analyzuje požadavek a vybere nejlepší SSP pro zpracování požadavku na základě zásad zabezpečení nakonfigurovaných zákazníkem.  
  
 nonce  
 Náhodně generovaná hodnota, která se používá k přepřipraveným útokům "opakované přehrání".  
  
 nepopiratelnosti odpovědnosti  
 Možnost identifikovat uživatele, kteří provedli určité akce, a irrefutably tak, že uživatel zamítne zodpovědnost. Systém může například protokolovat ID uživatele při každém odstranění souboru.  
  
 PKCS (Public Key Cryptography Standard)  
 Specifikace, které vytvořila technologie RSA Data Security, Inc. ve spolupráci s vývojáři zabezpečení systémů po celém světě, aby se urychlilo nasazení kryptografie s veřejným klíčem.  
  
 #7 PKCS  
 Standard syntaxe kryptografických zpráv. Obecná syntaxe pro data, na která lze použít kryptografii, například digitální podpisy a šifrování. Obsahuje také syntaxi pro rozšiřování certifikátů nebo seznamů odvolaných certifikátů a dalších atributů zpráv, jako jsou například časová razítka, do zprávy.  
  
 prostý  
 Zpráva, která není zašifrována. Zprávy ve formátu prostého textu jsou někdy označovány jako zprávy *nešifrovaných* zpráv.  
  
 Privilege  
 Právo uživatele provádět různé operace související se systémem, jako je vypnutí systému, načítání ovladačů zařízení nebo změna systémového času. Přístupový token uživatele obsahuje seznam oprávnění, která uživatel nebo skupiny uživatelů drží.  
  
 privátní klíč  
 Tajná polovina páru klíčů použitého v algoritmu veřejného klíče. Privátní klíče se obvykle používají k šifrování symetrického klíče relace, k digitálnímu podepisování zprávy nebo k dešifrování zprávy, která byla zašifrována s odpovídajícím veřejným klíčem. Viz také "veřejný klíč".  
  
 process  
 Kontext zabezpečení, pod nímž je aplikace spuštěna. Kontext zabezpečení je obvykle přidružen k uživateli, takže všechny aplikace spuštěné v rámci daného procesu přebírají oprávnění a oprávnění vlastnícího uživatele.  
  
 pár veřejného a privátního klíče  
 Sada kryptografických klíčů, která se používá pro kryptografii s veřejným klíčem. Pro každého uživatele obvykle udržuje zprostředkovatel kryptografických služeb (CSP) dva páry veřejného a privátního klíče: pár klíčů Exchange a pár klíčů digitálního podpisu. Obě dvojice klíčů jsou zachované z relace do relace.  
  
 veřejný klíč  
 Kryptografický klíč, který se obvykle používá při dešifrování klíče relace nebo digitálního podpisu. Veřejný klíč lze také použít k zašifrování zprávy, což zaručuje, že zpráva může dešifrovat pouze osoba s odpovídajícím privátním klíčem.  
  
 šifrování veřejného klíče  
 Šifrování, které používá pár klíčů, jeden klíč k šifrování dat a druhý klíč k dešifrování dat. Naproti tomu algoritmy symetrického šifrování, které používají stejný klíč pro šifrování i dešifrování. V praxi se obvykle používá kryptografie využívající veřejný klíč k ochraně klíče relace, který používá algoritmus symetrického šifrování. V takovém případě se veřejný klíč použije k zašifrování klíče relace, který se pak použil k šifrování některých dat a privátní klíč se použije k dešifrování. Kromě ochrany klíčů relace se může kryptografie s veřejným klíčem používat také k digitálnímu podepisování zprávy (pomocí privátního klíče) a k ověření podpisu (pomocí veřejného klíče).  
  
 Infrastruktura veřejných klíčů (PKI)  
 Infrastruktura poskytující integrovanou sadu služeb a nástrojů pro správu pro vytváření, nasazování a správu aplikací veřejného klíče.  
  
 popírání odpovědnosti  
 Schopnost uživatele nepravdivě odepřít provedení akce, zatímco jiné strany nemůžou jinak prokázat. Například uživatel, který odstraní soubor a který se k tomu může úspěšně zamítnout.  
  
 Kořenová autorita  
 CA v horní části hierarchie certifikační autority. Kořenová autorita potvrzuje certifikační autority v další úrovni hierarchie.  
  
 Algoritmus SHA (Secure Hash Algorithm)  
 Algoritmus hash, který generuje výtah zprávy. SHA se používá společně s algoritmem DSA (Digital Signature) v standardu DSS (Digital Signature Standard), a to mimo jiné. Existují čtyři odrůdy algoritmu SHA: SHA-1, SHA-256, SHA-384 a SHA-512. SHA-1 generuje 160 zpráv. SHA-256, SHA-384 a SHA-512 256 generují v uvedeném pořadí 16bitové, 384 a 512 bitů zpráv. Služba SHA byla vyvinuta národním institutem standardů a technologií (NIST) a národním bezpečnostním úřadem (National Security Agency).  
  
 SSL (Secure Sockets Layer) (SSL)  
 Protokol pro zabezpečenou síťovou komunikaci pomocí kombinace technologie veřejného a tajného klíče.  
  
 kontext zabezpečení  
 Atributy zabezpečení nebo pravidla, která jsou v současné době platná. Například aktuální uživatel přihlášený k počítači nebo osobní identifikační číslo zadané uživatelem čipové karty. V případě SSPI je kontextem zabezpečení neprůhledná datová struktura, která obsahuje data zabezpečení relevantní pro připojení, jako je například klíč relace nebo označení doby trvání relace.  
  
 objekt zabezpečení  
 Entita rozpoznaná systémem zabezpečení. Objekty zabezpečení mohou zahrnovat lidské uživatele i autonomní procesy.  
  
 Zprostředkovatel podpory zabezpečení (SSP)  
 Dynamická knihovna (DLL), která implementuje rozhraní SSPI tím, že pro aplikace zpřístupní jeden nebo více balíčků zabezpečení. Každý balíček zabezpečení poskytuje mapování mezi voláními funkcí SSPI aplikace a skutečnými funkcemi modelu zabezpečení. Balíčky zabezpečení podporují protokoly zabezpečení, jako je ověřování pomocí protokolu Kerberos a Microsoft LAN Manager (LanMan).  
  
 Rozhraní SSPI (Security Support Provider Interface)  
 Společné rozhraní mezi aplikacemi na úrovni přenosu, jako je například vzdálené volání procedur (RPC) společnosti Microsoft a poskytovatelé zabezpečení, jako je například distribuované zabezpečení systému Windows. Rozhraní SSPI umožňuje, aby aplikace přenosu vyvolala nějakého z několika poskytovatelů zabezpečení, aby získala ověřované připojení. Tato volání nevyžadují rozsáhlé znalosti podrobností protokolu zabezpečení.  
  
 Služba tokenů zabezpečení  
 Služby navržené pro vydávání a správu vlastních tokenů zabezpečení (vydaných tokenů) ve scénáři s více službami. Vlastní tokeny jsou obvykle tokeny SAML (Security Assert Markup Language), které zahrnují vlastní přihlašovací údaje.  
  
 certifikát serveru  
 Odkazuje na certifikát používaný k ověřování serveru, jako je například ověřování webového serveru ve webovém prohlížeči. Když se klient webového prohlížeče pokusí o přístup k zabezpečenému webovému serveru, server odešle svůj certifikát do prohlížeče, aby mohl ověřit identitu serveru.  
  
 jednání  
 Výměna zpráv v rámci ochrany jedné části materiálu klíčů. Například relace SSL používají jeden klíč k posílání více zpráv v rámci tohoto klíče a zpátky do něj.  
  
 klíč relace  
 Náhodně vygenerovaný klíč, který se používá jednou a pak se zahodí. Klíče relace jsou symetrické (slouží k šifrování i dešifrování). Jsou odesílány se zprávou chráněným šifrováním pomocí veřejného klíče od zamýšleného příjemce. Klíč relace se skládá z náhodného čísla přibližně 40 až 2 000 bitů.  
  
 doplňkové přihlašovací údaje  
 Přihlašovací údaje pro použití při ověřování objektu zabezpečení vůči cizím doménám zabezpečení.  
  
 symetrické šifrování  
 Šifrování, které používá jeden klíč pro šifrování i dešifrování. Při šifrování velkých objemů dat je upřednostňováno symetrické šifrování. Mezi nejběžnější algoritmy symetrického šifrování patří RC2, RC4 a Standard DES (Data Encryption Standard).  
  
 Viz také "šifrování veřejných klíčů".  
  
 symetrický klíč  
 Jeden klíč, který se používá pro šifrování i dešifrování. Klíče relace jsou obvykle symetrické.  
  
 token (přístupový token)  
 Přístupový token obsahuje bezpečnostní informace pro přihlašovací relaci. Systém vytvoří přístupový token, když se uživatel přihlásí a každý proces spuštěný jménem uživatele má kopii tohoto tokenu. Token identifikuje uživatele, skupiny uživatelů a oprávnění uživatele. Systém používá token k řízení přístupu k zabezpečeným objektům a k řízení schopnosti uživatele provádět různé operace související se systémem v místním počítači. Existují dva typy přístupových tokenů, primární a zosobnění.  
  
 Transportní vrstva  
 Síťová vrstva, která je zodpovědná za kvalitu služby a přesné doručování informací. Mezi úkoly provedenými v této vrstvě je detekce a oprava chyb.  
  
 seznam důvěryhodných certifikátů (seznam důvěryhodných certifikátů nebo CTL)  
 Předdefinovaný seznam položek, které byly podepsány důvěryhodnou entitou. Seznam CTL může být cokoli, jako je například seznam hodnot hash certifikátů nebo seznam názvů souborů. Všechny položky v seznamu jsou ověřeny (schváleny) podpisovou entitou.  
  
 zprostředkovatel důvěryhodnosti  
 Software, který rozhoduje, zda je daný soubor důvěryhodný Toto rozhodnutí vychází z certifikátu přidruženého k souboru.  
  
 hlavní název uživatele (UPN)  
 Název uživatelského účtu (někdy označovaný jako *přihlašovací jméno uživatele*) a název domény identifikující doménu, ve které se uživatelský účet nachází. Toto je standardní použití pro přihlášení k doméně systému Windows. Formát je: someone@example.com (jako u e-mailové adresy).  
  
> [!NOTE]
> Kromě standardního formuláře hlavního názvu uživatele (UPN) WCF přijímá hlavní názvy uživatelů (UPN) ve formě nižší úrovně, například cohowinery. com\someone.  
  
 X.509  
 Mezinárodní uznávaný standard pro certifikáty, které definují jejich požadované části.  
  
## <a name="see-also"></a>Viz také

- [Základní koncepty Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md)
- [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
