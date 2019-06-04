---
title: Šifrovací služby
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework]
- pattern of derived class inheritance
- digital signatures
- asymmetric cryptographic algorithms
- digital signatures, public-key systems
- public keys
- decryption [.NET Framework]
- private keys
- MAC algorithms
- cryptographic algorithms
- private keys, overview
- encryption [.NET Framework]
- security [.NET Framework], encryption
- cryptographic services
- symmetric cryptographic algorithms
- hash
- message authentication codes
- derived class inheritance
- cryptography [.NET Framework], about
- random number generation
ms.assetid: f96284bc-7b73-44b5-ac59-fac613ad09f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa05fe1e170a0285df73d179ef39db6301059ac8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490960"
---
# <a name="cryptographic-services"></a>Šifrovací služby

<a name="top"></a> Veřejné sítě, jako je Internet se neposkytuje způsob zabezpečenou komunikaci mezi entitami. Komunikace v těchto sítích je náchylné ke čtení nebo dokonce i změnit neoprávněné třetími stranami. Šifrování pomáhá chránit data před zobrazením, poskytuje způsoby, jak zjistit, zda byla data změněna, a pomáhá zajistit zabezpečený způsob komunikace přes jinak nezabezpečené kanály. Například data může být zašifrovaný pomocí algoritmu, přenášet do šifrovaného stavu a později dešifrovat určenou stranou. Pokud třetích stran zachycuje šifrovaná data, bude obtížné je dešifrovat.

V rozhraní .NET Framework, třídy v <xref:System.Security.Cryptography?displayProperty=nameWithType> obor názvů spravovat mnoho podrobností kryptografie za vás. Některé jsou obálky pro nespravované Microsoft Cryptography API (rozhraní CryptoAPI), zatímco jiné jsou čistě spravovaná implementace. Nemusíte být odborníky na kryptografii k použití těchto tříd. Při vytváření nové instance jednoho šifrování třídy algoritmus klíče jsou automaticky generované pro snadné použití a výchozí vlastnosti jsou bezpečné a co nevíce zabezpečený.

Tento přehled obsahuje souhrn metody šifrování a postupy podporované rozhraním .NET Framework, včetně manifesty ClickOnce, Suite B a kryptografické služby nové generace (CNG) podporu zavedena v rozhraní .NET Framework 3.5.

Tento přehled obsahuje následující části:

- [Cryptographic Primitives](#primitives)

- [Šifrování tajného klíče](#secret_key)

- [Šifrování s veřejným klíčem](#public_key)

- [Digitální podpisy](#digital_signatures)

- [Hodnoty hash](#hash_values)

- [Náhodné generování čísel](#random_numbers)

- [Manifesty ClickOnce](#clickonce)

- [Podpora Suite B](#suite_b)

- [Související témata](#related_topics)

Další informace o šifrování a služeb Microsoftu, komponenty a nástroje, které vám umožní přidat kryptografické zabezpečení pro vaše aplikace najdete v systému Win32 a COM Development sekci zabezpečení v této dokumentaci.

<a name="primitives"></a>

## <a name="cryptographic-primitives"></a>Kryptografické primitiv

V typické situace, ve kterém se používá šifrování obě strany (Alice a Bob) komunikaci přes nezabezpečený kanál. Alice a Bob chcete zajistit, aby jejich komunikace zůstal Nesrozumitelná každý, kdo může naslouchat. Navíc vzhledem k tomu, že Alice a Bob jsou ve vzdálených umístěních, Alice musí zajistit, že informace, které se od Boba přijde nebyl změněn kdokoli během přenosu. Kromě toho také musí zajistit, že informace skutečně pocházejí od Boba a ne z někoho, kdo je zosobňující Bob.

Šifrování se používá k naplnění následujících cílů:

- Důvěrnost: Chcete-li zabránit čtená data nebo identity uživatele.

- Integrita dat: Chcete-li chránit data před změnou.

- Ověřování: K zajištění, že data pochází od určitého výrobce.

- Nepopiratelnost odpovědnosti: Zabránit konkrétní stran odepření, byla odeslána zpráva.

K dosažení těchto cílů, slouží k vytvoření kryptografických schémat kombinaci algoritmů a postupy, které jsou známé jako kryptografické primitiv. V následující tabulce jsou uvedeny kryptografické primitiv a jejich použití.

|Kryptografická primitiva|Použití|
|-----------------------------|---------|
|Šifrování tajného klíče (symetrického šifrování)|Provede transformaci na data před čtením třetím stranám. Tento typ šifrování používá jediný sdílený tajný klíč k šifrování a dešifrování dat.|
|Šifrování s veřejným klíčem (asymetrické šifrování)|Provede transformaci na data před čtením třetím stranám. Tento typ šifrování používá k šifrování a dešifrování dat dvojice veřejného/soukromého klíče.|
|Kryptografický podpis|Pomáhá ověřit, že data pochází z určité skupiny tak, že vytvoříte digitální podpis, který je jedinečný pro tuto skupinu. Tento proces také používá funkce hash.|
|Kryptografické hodnoty hash|Mapuje data z jakékoli délky na sekvenci bajtů pevné délky. Hodnoty hash jsou statisticky jedinečný.; jiné pořadí dvoubajtový nebude na stejnou hodnotu hash.|

[Zpět na začátek](#top)

<a name="secret_key"></a>

## <a name="secret-key-encryption"></a>Šifrování tajného klíče

Algoritmy šifrování tajného klíče šifrování a dešifrování dat pomocí jednoho tajný klíč. Klíč z přístup neoprávněné agenty musí zabezpečit, protože každá strana, která má klíč můžete použít pro data dešifrovat nebo šifrovat vlastní data, nárokování, že pochází od vás.

Šifrování tajného klíče je také označovány jako symetrického šifrování, protože se používá stejný klíč k šifrování a dešifrování. Algoritmy šifrování tajného klíče jsou velmi rychlé zpracování (ve srovnání s algoritmy veřejného klíče) a jsou vhodné pro provedení kryptografické transformace na velkých datových proudů. Asymetrických šifrovacích algoritmů třeba RSA, jsou omezeny matematicky v tom, kolik dat můžete šifrovat. Algoritmy šifrování se symetrickým obvykle není nutné tyto problémy.

Typ tajného klíče algoritmu volá bloková šifra se používá k šifrování jeden blok dat v čase. Blokové šifry, jako je Standard DES (Data Encryption), TripleDES, a Advanced Encryption (Standard AES), kryptograficky transformují vstupní blok *n* bajtů do výstupního bloku šifrovaných bajtů. Pokud chcete šifrovat nebo dešifrovat sekvenci bajtů, je nutné provést blok po bloku. Protože *n* je malá (8 bajtů pro algoritmus DES a TripleDES, 16 bajtů [výchozí], 24 bajtů nebo 32 bajtů pro algoritmus AES), datových hodnot, které jsou větší než *n* musela být šifrovaná jeden blok najednou. Hodnoty dat, které jsou menší než *n* musí rozbalí se *n* zpracování.

Jednoduchá forma bloková šifra se nazývá režim electronic codebook (ECB). Režim ECB se nepovažuje za bezpečnou, protože nepoužívá inicializační vektor k inicializaci prvního bloku ve formátu prostého textu. Pro daný tajný klíč *k*, bude jednoduchá bloková šifra, která nepoužívá inicializační vektor bude šifrovat stejný vstupní blok prostého textu do stejného výstupního bloku šifrovaného textu. Proto pokud váš datový proud ve formátu prostého textu vstupu obsahuje duplicitní bloky, budete mít duplicitní bloky v výstupní datový proud šifrovaného textu. Tyto bloky duplicitním výstupem výstrah neoprávněným uživatelům slabé šifrování používá algoritmy, které byly použity a možné režimy útoku. Režim šifrování ECB proto je poměrně snadno napadnutelný analýzy a nakonec klíč zjišťování.

Třídy blokové šifry, které jsou k dispozici v knihovně základních tříd pomocí řetězení režim s názvem bloků šifer řetězení CBC (), i když toto výchozí nastavení můžete změnit, pokud chcete výchozí hodnotu.

CBC šifrování překonat problémy spojené se ECB šifry pomocí inicializační vektor (IV) k šifrování první blok prostého textu. Každý další blok prostého textu při bitový exkluzivní operátor OR (`XOR`) operace u předchozího bloku šifrovaného textu předtím, než je šifrovaný. Každý blok šifrovaného textu je proto závisí na všechny předchozí bloky. Pokud je tento systém záhlaví použit, běžné zpráv, které může být známé neoprávněný uživatel nemůže být umožňuje provádět zpětnou analýzu klíč.

Jedním ze způsobů k ohrožení dat, která je zašifrovaný pomocí CBC šifer s nižší sílou je provést během důkladného prohledání objektu všechny možné klíče. V závislosti na velikosti klíč, který se používá k provádění šifrování tento druh vyhledávání je velmi časově náročné, dokonce i nejrychlejší počítačů a proto je nemožné. Větší velikosti klíče jsou obtížnější dekódovat. I když šifrování není znemožnit teoreticky pro nežádoucí osobu načíst šifrovaná data, zvýšit náklady na to. Pokud trvá tří měsíců provádět během důkladného prohledání data, která má smysl pouze pro několik dní, během důkladného prohledání metodou je nepraktické.

Nevýhodou šifrování tajného klíče je, že předpokládá, že obě strany mají dohodnutou klíč a vektor IV a předávají jejich hodnoty. Vektor IV se nepovažuje za tajného kódu a může být přenášen ve formátu prostého textu se zprávou. Ale klíč musí být udržen v tajnosti před neoprávněnými uživateli. Kvůli těmto problémům šifrování tajného klíče se často používá společně s veřejným klíčem šifrování komunikovat soukromě hodnoty klíč a vektor IV.

Za předpokladu, že Alice a Bob se dvěma stranami, které chcete komunikovat přes nezabezpečený kanál, můžou používat šifrování tajného klíče následujícím způsobem: Alice a Bob svůj souhlas s konkrétním klíč a vektor IV používat jeden konkrétní algoritmus (například standard AES). Alice vytvoří zprávu a vytváří datový proud sítě (třeba pojmenovaného kanálu nebo sítě e-mail s) na základě které chcete odeslat zprávu. V dalším kroku Jana zašifruje text pomocí klíč a vektor IV a odešle zašifrovanou zprávu a vektor IV Bob prostřednictvím sítě intranet. Bob obdrží šifrovaného textu a dešifruje ji pomocí vektor IV a dříve dohodnutých klíč. Pokud je přenos, sběrač nelze obnovit původní zprávu, protože nezná klíč. V tomto scénáři musí zůstat pouze klíč tajného kódu. Ve scénáři reálného světa Alice a Bob vygeneruje tajný klíč a šifrování veřejného klíče (asymetricky) používá k přenosu tajných kódů (symetrického) klíče na druhou stranu. Další informace o šifrování s veřejným klíčem najdete v další části.

Rozhraní .NET Framework poskytuje následující třídy, které implementují algoritmy šifrování tajného klíče:

- <xref:System.Security.Cryptography.AesManaged> (zavedena v rozhraní .NET Framework 3.5).

- <xref:System.Security.Cryptography.DESCryptoServiceProvider>.

- <xref:System.Security.Cryptography.HMACSHA1> (To je technicky algoritmu tajného klíče, protože představuje ověřovací kód zprávy, které se počítá pomocí funkce kryptografická hodnota hash v kombinaci s tajným klíčem. Zobrazit [hodnoty Hash](#hash_values)dále v tomto tématu.)

- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RijndaelManaged>.

- <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.

[Zpět na začátek](#top)

<a name="public_key"></a>

## <a name="public-key-encryption"></a>Šifrování s veřejným klíčem

Šifrování s veřejným klíčem používá soukromý klíč, který musí být udržen v tajnosti před neoprávněnými uživateli a veřejného klíče, který lze zveřejnit všem uživatelům. Veřejný klíč a soukromý klíč matematicky propojenou; data, která je zašifrovaná pomocí veřejného klíče, mohou ho dešifrovat jenom s privátním klíčem, a data, která je podepsaná pomocí soukromého klíče můžete ověřit pouze pomocí veřejného klíče. Veřejný klíč může být k dispozici všem uživatelům; používá se pro šifrování dat k odeslání do držitele privátní klíč. Veřejného klíče kryptografické algoritmy jsou také známé jako asymetrické algoritmy, protože jeden z nich je potřeba šifrovat data a jiný klíč se vyžaduje k dešifrování dat. Základní pravidlo kryptografických zakazuje opětovné použití klíčů a oba klíče musí být jedinečná pro každou relaci komunikace. V praxi, jsou však obvykle dlouhodobé asymetrické klíče.

Obě strany (Alice a Bob) mohou použít šifrování s veřejným klíčem následujícím způsobem: Nejprve Alice vytvoří pár veřejného a privátního klíče. Pokud Bob chce odeslat Alice zašifrovanou zprávu, požádá ji pro svůj veřejný klíč. Alice odešle Bob veřejného klíče v nezabezpečené síti a Bob použije tento klíč k šifrování zpráv. Zašifrovanou zprávu: Bob pošle Alici, a Jana dešifruje ji pomocí vlastního soukromého klíče. Pokud Bob obdržel Alice klíč přes nezabezpečený kanál, jako je například veřejnou síť, Bob je otevřená pro útok man-in-the-middle. Proto musíte Bob ověřit pomocí Alice, že má správnou kopii svůj veřejný klíč.

Během přenosu Alice veřejný klíč může zachytit neoprávněný agent klíč. Kromě toho stejný agent, kterého může zachytit zašifrovanou zprávu od Boba. Agenta však nemůže dešifrování zprávy s veřejným klíčem. Zpráva může dešifrovat jenom s privátním klíčem Alice, který nebyl bylo přeneseno. Alice svůj privátní klíč k šifrování zprávy s odpovědí Bobovi nepoužívá, protože každý, kdo má veřejný klíč může dešifrování zprávy. Alice chce, aby se pro odeslání zprávy zpět uživateli, že Bob vyzve k zadání jeho veřejný klíč a šifruje své zprávy pomocí veřejného klíče. Bob dešifruje pak zprávy pomocí jeho přidružený privátní klíč.

V tomto scénáři Alice a Bob šifrování veřejného klíče (asymetricky) pro přenos tajných kódů (symetrického) klíče a tajného klíče šifrování pro zbývající část jeho relace.

Následující seznam nabízí porovnání veřejného klíče a tajného klíče kryptografické algoritmy:

- Kryptografické algoritmy veřejného klíče použít vyrovnávací paměť pevné velikosti, že kryptografické algoritmy tajného klíče používat do vyrovnávací paměti proměnné délky.

- Algoritmy veřejného klíče nelze použít na řetězec data společně do datových proudů způsob, jakým lze algoritmy tajného klíče, protože pouze malé množství dat mohou být zašifrovaná. Asymetrické operace proto nepoužívejte stejný model streamování jako symetrický operace.

- Šifrování veřejného klíče má mnohem větší keyspace (rozsah možných hodnot pro klíč) než šifrování tajného klíče. Proto je méně náchylný k vyčerpávající útoků, které se pokoušejí všechny možné klíče šifrování s veřejným klíčem.

- Veřejné klíče se snadno distribuovat, protože nemají být zabezpečené, za předpokladu, že existuje způsob, chcete-li ověřit totožnost odesílatele.

- Některé algoritmy veřejného klíče (např. RSA a DSA, ale ne Diffie-Hellman) slouží k vytváření digitálních podpisů, chcete-li ověřit totožnost odesílatele data.

- Algoritmy veřejného klíče jsou velmi pomalé ve srovnání s algoritmy tajného klíče a nejsou určeny k zašifrování velké objemy dat. Jsou užitečné pouze pro přenos velmi malé množství dat algoritmy veřejného klíče. Šifrování s veřejným klíčem se obvykle používá k šifrování klíč a vektor IV použije algoritmus tajný klíč. Po přenesení klíč a vektor IV šifrování tajného klíče se používá pro zbytek relace.

Rozhraní .NET Framework poskytuje následující třídy, které implementují algoritmy šifrování s veřejným klíčem:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDiffieHellman> (základní třídy)

- <xref:System.Security.Cryptography.ECDiffieHellmanCng>

- <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey> (základní třídy)

- <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction> (základní třídy)

- <xref:System.Security.Cryptography.ECDsaCng>

RSA umožňuje šifrování a podepisování, ale DSA lze použít pouze pro podepisování a Diffie-Hellman lze použít pouze pro generování klíčů. Obecně platí algoritmy veřejného klíče jsou limitovanější v jejich použití než algoritmy soukromého klíče.

[Zpět na začátek](#top)

<a name="digital_signatures"></a>

## <a name="digital-signatures"></a>Digitální podpisy

Veřejný klíč algoritmy lze také tvoří digitální podpisy. Digitální podpisy ověřit totožnost odesílatele (v případě, že důvěřujete odesílatele veřejný klíč) a chránit integritu dat. Pomocí veřejného klíče generované Alice, příjemce dat Alice můžete ověřit, že Alice je odeslání porovnáním digitální podpis k datům uživatele Jaroslava a veřejný klíč od Alice.

Použití kryptografie využívající veřejný klíč k podepsání zprávy, Alice nejprve platí pro zpráva, kterou chcete vytvořit hodnota hash algoritmu hash. Hodnota hash je kompaktní a jedinečný reprezentace data. Hodnota hash Alice potom šifruje s jeho privátním klíčem k vytvoření své osobní podpisu. Při přijetí zprávy a podpis, dešifruje Bob podpis pomocí veřejného klíče uživatele Jaroslava obnovení zpráv pomocí stejné hashovacího algoritmu, který používá Alice hodnoty hash a hodnoty hash. Pokud hodnota hash, která vypočítá Bob přesně odpovídá hodnota hash přijatých od Alice, Bob jistotu, že zpráva pochází od vlastníka privátního klíče a nebyl změněn data. Pokud Bob vztahy důvěryhodnosti, že Alice je vlastník privátního klíče, ví, že zpráva pochází od Alice.

> [!NOTE]
> Podpis můžete ověřit kdokoli, protože veřejného klíče odesílatele je společné znalosti a je obvykle součástí formátu digitální podpis. Tato metoda nezachovává tajemství zprávy. pro zprávy být tajný se musí také být zašifrován.

Rozhraní .NET Framework poskytuje následující třídy, které implementují algoritmy digitální podpis:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDsa> (základní třídy)

- <xref:System.Security.Cryptography.ECDsaCng>

 [Zpět na začátek](#top)

<a name="hash_values"></a>

## <a name="hash-values"></a>Hodnoty hash

Hashovacích algoritmů mapování binárních hodnot libovolné délky na menší binárních hodnot pevné délky, známé jako hodnoty hash. Číselné vyjádření část dat je hodnota hash. Pokud hodnotu hash odstavce ve formátu prostého textu a změníte ještě jedno písmeno odstavce, vytvoří následující hodnoty hash jinou hodnotu. Pokud je hodnota hash kryptograficky silnou, jeho hodnota se změní výrazně. Například pokud se změní část zprávy silné hashovací funkci může vytvořit výstup, který se liší o 50 procent. Počet vstupních hodnot může stejné výstupní hodnotu hash. Je však výpočetně najít dva odlišné vstupy tuto hodnotu hash na stejnou hodnotu.

Obě strany (Alice a Bob) použít k zajištění integrity zprávy funkce hash. Vyberou by hashovací algoritmus jejich zprávy. Alice by zapsat zprávu a pak vytvoří hodnotu hash této zprávy s použitím vybrané algoritmus. Jejich by postupujte podle jednoho z následujících metod:

- Alice odesílá do zprávy ve formátu prostého textu a hodnotu hash zprávy (digitální podpis). Bob obdrží hashuje zprávu a porovnává jeho hodnotu hash pro hodnotu hash, který obdržel od Alice. Pokud jsou hodnoty hash stejné, zpráva nebyla změněna. Pokud hodnoty nejsou shodné, zprávy byl změněn po ho napsal Alice.

    Tato metoda však nevytváří pravosti odesílatele. Kdokoli na nich může zosobnit Alice a Bob odešlete zprávu. Můžou použít stejný algoritmus hash a podepisování jejich zpráva a všechno, co můžete určit Bob je, že zpráva odpovídá jeho podpis. Toto je jedna podoba útok man-in-the-middle. Další informace najdete v tématu [kryptografické služby nové generace (CNG) zabezpečené komunikace příklad](https://docs.microsoft.com/previous-versions/cc488018(v=vs.100)).

- Alice odešle zprávu ve formátu prostého textu Bob přes nezabezpečený kanál veřejné. Odešle hodnotu hash zprávy uživateli přes zabezpečený kanál privátní. Bob obdrží zprávu ve formátu prostého textu, rozdělí a porovná součet hash soukromě výměně hodnotou hash. Pokud se klíče hash shodují, Bob ví dvě věci:

    - Zpráva nebyla změněna.

    - Odesílatel zprávy (Alice) je platná.

    Pro tento systém fungovat musí skrýt Alice ze všech stran, s výjimkou Bob její původní hodnotu hash.

- Alice odešle zprávu ve formátu prostého textu Bob přes nezabezpečený kanál veřejné a umístí hodnotu hash zprávy na svůj veřejně přístupný webový server.

    Tato metoda zabraňuje v manipulaci se zprávami tak, že všem uživatelům zabrání změně hodnoty hash. I když každý lze číst zprávy a jeho hodnotu hash, hodnota hash může změnit pouze Alice. Útočník, který chce zosobnit Alice potřeboval by přístup k webovému serveru Alice.

Žádná z předchozích metod zabrání někdo čtení zprávy od Alice, protože se přenáší ve formátu prostého textu. Úplné zabezpečení zpravidla vyžaduje, aby digitální podpisy (podepisování zpráv) a šifrování.

Rozhraní .NET Framework poskytuje následující třídy, které implementují algoritmy hash:

- <xref:System.Security.Cryptography.HMACSHA1>.

- <xref:System.Security.Cryptography.MACTripleDES>.

- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RIPEMD160>.

- <xref:System.Security.Cryptography.SHA1Managed>.

- <xref:System.Security.Cryptography.SHA256Managed>.

- <xref:System.Security.Cryptography.SHA384Managed>.

- <xref:System.Security.Cryptography.SHA512Managed>.

- Varianty HMAC všechny algoritmy zabezpečení hashovací algoritmus (SHA), Message Digest 5 (MD5) a RIPEMD 160.

- CryptoServiceProvider implementace všechny algoritmy SHA (spravovaný kód obálky).

- Kryptografie generace (CNG) implementace všech algoritmů MD5 a SHA.

> [!NOTE]
> V roce 1996 byly zjištěny chyby návrhu MD5 a SHA-1 se doporučuje místo. V 2004 další chyby byly zjištěny a algoritmus MD5 se už nepovažuje za bezpečný. Být nezabezpečené také byla nalezena algoritmus SHA-1 a SHA-2 je teď doporučujeme místo toho.

[Zpět na začátek](#top)

<a name="random_numbers"></a>

## <a name="random-number-generation"></a>Náhodné generování čísel

Náhodné generování čísel je nedílnou součástí mnoha kryptografické operace. Například kryptografické klíče musí být jako náhodné, jak je to možné, tak, aby se reprodukovat. Kryptografické generátorů náhodných čísel musí generovat výstup, který je výpočetně odhadnout pravděpodobnost, že je obecně lepší než polovinu. Proto jakékoli metody objektu předpověď Další bit výstup nesmí mít lepší výkon než náhodných opakovaně uhodnout. Třídy v rozhraní .NET Framework pomocí generátorů náhodných čísel pro generování kryptografických klíčů.

<xref:System.Security.Cryptography.RNGCryptoServiceProvider> Třída je implementací algoritmu generátor náhodných čísel.

[Zpět na začátek](#top)

<a name="clickonce"></a>

## <a name="clickonce-manifests"></a>Manifesty ClickOnce

V [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], následující šifrovacích tříd umožňují získat a zkontrolovat informace o manifestu podpisy pro aplikace, které jsou nasazeny pomocí [technologie ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment):

- <xref:System.Security.Cryptography.ManifestSignatureInformation> Třídy získává informace o podpisu manifestu při použití jeho <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> přetížení metody.

- Můžete použít <xref:System.Security.ManifestKinds> výčet určit, které manifesty ověření. Výsledek ověření je jedním z <xref:System.Security.Cryptography.SignatureVerificationResult> hodnot výčtu.

- <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> Třída poskytuje kolekci jen pro čtení <xref:System.Security.Cryptography.ManifestSignatureInformation> objekty ověřených podpisů.

 Navíc následující třídy poskytují informace o konkrétní podpisu:

- <xref:System.Security.Cryptography.StrongNameSignatureInformation> Obsahuje informace o podpisu silného názvu pro manifest.

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation> představuje informace o podpisu Authenticode pro manifest.

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation> obsahuje informace o časové razítko na podpis Authenticode.

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus> poskytuje jednoduchý způsob, jak zkontrolovat, zda je důvěryhodný podpis Authenticode.

[Zpět na začátek](#top)

<a name="suite_b"></a>

## <a name="suite-b-support"></a>Podpora Suite B

[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Podporuje sady Suite B kryptografické algoritmy, které jsou publikovány National Security Agency (NSA). Další informace o Suite B, najdete v článku [NSA Suite B kryptografie fakt Sheet](https://www.nsa.gov/what-we-do/information-assurance/).

Tyto algoritmy jsou zahrnuty:

- Pokročilé algoritmus standardu šifrování (AES) s velikostí klíče 128, 192 a 256 bitů pro šifrování.

- Pro vytvoření hodnoty hash zabezpečení hashovací algoritmy SHA-1, SHA-256, SHA-384 a SHA-512. (Poslední tři jsou obecně seskupené dohromady a označovány jako SHA-2.)

- Křivky digitální podpis algoritmů ECDSA (Elliptic), pomocí křivky 256 bitů, 384 bitů a 521-bit 521bitů primárního modulu pro podepisování. Dokumentace NSA speciálně definuje tyto křivky a je volá p-256, p-384 a p-521. Tento algoritmus poskytuje <xref:System.Security.Cryptography.ECDsaCng> třídy. Umožňuje vám přihlášení s privátním klíčem a ověřit podpis s veřejným klíčem.

- Eliptické křivky Diffie-Hellman (ECDH) algoritmus, pomocí křivky 256 bitů, 384 bitů a 521-bit 521bitů primárního modulu pro výměnu klíčů a tajných kódů smlouvy. Tento algoritmus poskytuje <xref:System.Security.Cryptography.ECDiffieHellmanCng> třídy.

Spravovaný kód obálky pro federální informace o zpracování Standard (FIPS) certified implementace AES, SHA-256, SHA-384 a SHA-512 jsou dostupná na novém <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>, <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>, a <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> třídy.

[Zpět na začátek](#top)

<a name="cng"></a>

## <a name="cryptography-next-generation-cng-classes"></a>Další generace (CNG) třídy šifrování

Kryptografické služby nové generace (CNG) třídy poskytují spravovaná obálka kolem nativní funkce CNG. (CNG je náhradou rozhraní CryptoAPI.) Tyto třídy mají "Cng" jako součást jejich názvy. Z centrální na obálkové třídy CNG je <xref:System.Security.Cryptography.CngKey> třída kontejneru, který abstrahuje úložiště a použití klíčů CNG klíčů. Tato třída umožňuje bezpečně dvojici klíčů nebo veřejný klíč a na něj odkazovat pomocí názvu jednoduchým řetězcem. Na eliptické založené na křivku <xref:System.Security.Cryptography.ECDsaCng> Třída podpisu a <xref:System.Security.Cryptography.ECDiffieHellmanCng> pomocí tříd šifrování <xref:System.Security.Cryptography.CngKey> objekty.

<xref:System.Security.Cryptography.CngKey> Třída se používá pro celou řadu dalších operací, včetně otevření, vytváření, odstraňování a export klíčů. Poskytuje také přístup k podkladové popisovač klíče pro použití při volání nativních funkcí přímo.

[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Také zahrnuje celou řadu pomocných tříd CNG, jako je následující:

- <xref:System.Security.Cryptography.CngProvider> udržuje zprostředkovatele úložiště klíčů.

- <xref:System.Security.Cryptography.CngAlgorithm> udržuje CNG algoritmus.

- <xref:System.Security.Cryptography.CngProperty> udržuje často používané vlastnosti klíče.

[Zpět na začátek](#top)

<a name="related_topics"></a>

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Kryptografický model](../../../docs/standard/security/cryptography-model.md)|Popisuje, jak je implementovaná šifrování v knihovně základních tříd.|
|[Návod: Vytvoření šifrovací aplikace](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Ukazuje základní úlohy pro šifrování a dešifrování.|
|[Konfigurace šifrovacích tříd](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Popisuje způsob mapování názvů algoritmů na třídy šifrování a mapování identifikátorů objektů na kryptografický algoritmus.|
