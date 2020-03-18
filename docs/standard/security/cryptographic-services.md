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
ms.openlocfilehash: c1783a578d0b55b0b62a1ffb870802faca97623f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187014"
---
# <a name="cryptographic-services"></a>Šifrovací služby

Veřejné sítě, jako je Internet, neposkytují prostředky pro bezpečnou komunikaci mezi subjekty. Komunikace prostřednictvím těchto sítí je náchylná ke čtení nebo dokonce ke změně neoprávněnými třetími stranami. Kryptografie pomáhá chránit data před zobrazením, poskytuje způsoby, jak zjistit, zda byla data změněna, a pomáhá zajistit bezpečný způsob komunikace prostřednictvím jinak nezabezpečených kanálů. Data mohou být například šifrována pomocí kryptografického algoritmu, přenášena v šifrovaném stavu a později dešifrována zamýšlenou stranou. Pokud třetí strana zachytí šifrovaná data, bude obtížné je rozluštit.

V rozhraní .NET Framework třídy v oboru <xref:System.Security.Cryptography?displayProperty=nameWithType> názvů spravovat mnoho podrobností o kryptografii za vás. Některé jsou obálky pro nespravované rozhraní Api kryptografie společnosti Microsoft (CryptoAPI), zatímco jiné jsou čistě spravované implementace. Nemusíte být odborníkem na kryptografii, abyste používali tyto třídy. Když vytvoříte novou instanci jedné z tříd šifrovacího algoritmu, klíče se automaticky generují pro snadné použití a výchozí vlastnosti jsou co nejbezpečnější a nejbezpečnější.

Tento přehled poskytuje přehled metod a postupů šifrování podporovaných rozhraním .NET Framework, včetně podpory ClickOnce manifestů, sady B a kryptografie nové generace (CNG) zavedené v rozhraní .NET Framework 3.5.

Další informace o kryptografii a o službách, součástech a nástrojích společnosti Microsoft, které umožňují přidat do aplikací kryptografické zabezpečení, naleznete v této dokumentaci v části Win32 a COM Development, Security.

## <a name="cryptographic-primitives"></a>Kryptografická primitiva

V typické situaci, kdy se používá kryptografie, dvě strany (Alice a Bob) komunikují přes nezabezpečený kanál. Alice a Bob chtějí zajistit, aby jejich komunikace zůstala nepochopitelná pro každého, kdo by mohl poslouchat. Navíc vzhledem k tomu, že Alice a Bob jsou ve vzdálených umístěních, Alice musí zajistit, že informace, které obdrží od Boba nebyl změněn nikým během přenosu. Kromě toho se musí ujistit, že informace skutečně pocházejí od Boba a ne od někoho, kdo se vydává za Boba.

Kryptografie se používá k dosažení následujících cílů:

- Důvěrnost: Pomáhá chránit identitu nebo data uživatele před čtením.

- Integrita dat: Pomáhá chránit data před změnami.

- Ověřování: Chcete-li zajistit, aby data pocházela od určité strany.

- Neodvolatelnost: Chcete-li zabránit určité straně v popírání, že odeslala zprávu.

K dosažení těchto cílů můžete k vytvoření kryptografického schématu použít kombinaci algoritmů a postupů označovaných jako kryptografické primitiva. V následující tabulce jsou uvedeny kryptografické primitivy a jejich použití.

|Kryptografická primitivní|Použití|
|-----------------------------|---------|
|Šifrování tajného klíče (symetrická kryptografie)|Provede transformaci dat, aby je nečetly třetí strany. Tento typ šifrování používá jeden sdílený tajný klíč k šifrování a dešifrování dat.|
|Šifrování pomocí veřejného klíče (asymetrická kryptografie)|Provede transformaci dat, aby je nečetly třetí strany. Tento typ šifrování používá k šifrování a dešifrování dat dvojici veřejných a soukromých klíčů.|
|Kryptografické podepisování|Pomáhá ověřit, zda data pocházejí od určité strany vytvořením digitálního podpisu, který je pro tuto stranu jedinečný. Tento proces také používá funkce hash.|
|Kryptografické zachycovací|Mapuje data z libovolné délky na sekvenci bajtů s pevnou délkou. Hashes jsou statisticky jedinečné; různé dvoubajtové sekvence nebude hash na stejnou hodnotu.|

## <a name="secret-key-encryption"></a>Šifrování tajného klíče

Šifrovací algoritmy tajného klíče používají k šifrování a dešifrování dat jeden tajný klíč. Je nutné zabezpečit klíč před přístupem neoprávněných agentů, protože každá strana, která má klíč, jej může použít k dešifrování dat nebo šifrování vlastních dat a prohlašovat, že pochází od vás.

Šifrování tajného klíče se také označuje jako symetrické šifrování, protože stejný klíč se používá pro šifrování a dešifrování. Šifrovací algoritmy tajného klíče jsou velmi rychlé (ve srovnání s algoritmy veřejného klíče) a jsou vhodné pro provádění kryptografických transformací na velkých datových proudech dat. Asymetrické šifrovací algoritmy, jako je RSA, jsou matematicky omezeny v tom, kolik dat mohou šifrovat. Symetrické šifrovací algoritmy obvykle nemají tyto problémy.

Typ algoritmu tajného klíče nazývaný bloková šifra se používá k šifrování jednoho bloku dat najednou. Blokové šifry, jako jsou Standard šifrování dat (DES), TripleDES a Advanced Encryption Standard (AES), kryptograficky transformují vstupní blok *n* bajtů do výstupního bloku šifrovaných bajtů. Pokud chcete šifrovat nebo dešifrovat sekvenci bajtů, musíte to udělat blok po bloku. Protože *n* je malý (8 bajtů pro DES a TripleDES; 16 bajtů [výchozí], 24 bajtů nebo 32 bajtů pro AES), hodnoty dat, které jsou větší než *n* musí být šifrovány jeden blok najednou. Hodnoty dat, které jsou menší než *n,* musí být rozbaleny na *n,* aby mohly být zpracovány.

Jedna jednoduchá forma blokové šifry se nazývá režim elektronického codebooku (ECB). Režim ECB není považován za bezpečný, protože nepoužívá inicializační vektor k inicializaci prvního bloku prostého textu. Pro daný tajný klíč *k*, jednoduchý blok šifra, který nepoužívá inicializační vektor bude šifrovat stejný vstupní blok prostého textu do stejného výstupního bloku šifrovaného textu. Proto pokud máte duplicitní bloky ve vstupním datovém proudu prostého textu, budete mít duplicitní bloky ve výstupním datovém proudu šifrovaný text. Tyto duplicitní výstupní bloky upozorňují neoprávněné uživatele na slabé šifrování, které používalo algoritmy, které mohly být použity, a možné režimy útoku. Režim šifry ECB je proto poměrně zranitelný vůči analýze a v konečném důsledku ke klíčovému objevu.

Třídy blokové šifry, které jsou k dispozici v knihovně základní třídy, používají výchozí režim řetězení nazývaný řetězení bloků šifry (CBC), i když toto výchozí nastavení můžete změnit, pokud chcete.

Cbc šifry překonat problémy spojené s ecb šifry pomocí inicializačního vektoru (IV) k šifrování první blok prostého textu. Každý následující blok prostého textu prochází bitovou výhradní operací OR (`XOR`) s předchozím blokem šifrovaného textu před jeho šifrováním. Každý blok šifrovaného textu je proto závislý na všech předchozích blocích. Při použití tohoto systému nelze k zpětné analýzě klíče použít běžné záhlaví zpráv, které mohou být neoprávněným uživatelům známy.

Jedním ze způsobů, jak ohrozit data, která jsou šifrována pomocí šifry CBC, je provést vyčerpávající vyhledávání všech možných klíčů. V závislosti na velikosti klíče, který se používá k provádění šifrování, je tento druh vyhledávání velmi časově náročný i při použití nejrychlejších počítačů, a proto je neproveditelný. Větší velikosti klíčů je obtížnější rozluštit. Přestože šifrování neznemožňuje protivníkovi teoreticky načíst šifrovaná data, zvyšuje náklady na to. Pokud trvá tři měsíce, než provedete vyčerpávající vyhledávání, abyste získali data, která mají smysl pouze několik dní, je metoda vyčerpávajícího vyhledávání nepraktická.

Nevýhodou šifrování tajného klíče je, že předpokládá, že se dvě strany dohodly na klíči a IV a sdělily své hodnoty. IV není považováno za tajné a může být přenášeno ve formátu prostého textu se zprávou. Klíč však musí být uchován v tajnosti před neoprávněnými uživateli. Z důvodu těchto problémů šifrování tajného klíče se často používá společně s šifrováním veřejného klíče soukromě komunikovat hodnoty klíče a IV.

Za předpokladu, že Alice a Bob jsou dvě strany, které chtějí komunikovat přes nezabezpečený kanál, mohou použít šifrování tajného klíče následujícím způsobem: Alice a Bob se dohodly, že budou používat jeden konkrétní algoritmus (například AES) s určitým klíčem a IV. Alice vytvoří zprávu a vytvoří síťový datový proud (možná pojmenovaný kanál nebo síťový e-mail), na který chcete zprávu odeslat. Dále zašifruje text pomocí klíče a IV a odešle šifrovanou zprávu a IV Bobovi přes intranet. Bob obdrží šifrovaný text a dešifruje jej pomocí IV a dříve dohodnuté ho klíče. Pokud je přenos zachycen, zachycovač nemůže obnovit původní zprávu, protože nezná klíč. V tomto scénáři pouze klíč musí zůstat tajné. V reálném scénáři Alice nebo Bob generuje tajný klíč a používá veřejné klíče (asymetrické) šifrování k přenosu tajného (symetrického) klíče do druhé strany. Další informace o šifrování veřejného klíče naleznete v další části.

Rozhraní .NET Framework poskytuje následující třídy, které implementují šifrovací algoritmy tajného klíče:

- <xref:System.Security.Cryptography.AesManaged>(zavedeno v rámci .NET 3.5).

- <xref:System.Security.Cryptography.DESCryptoServiceProvider>.

- <xref:System.Security.Cryptography.HMACSHA1>(Jedná se technicky o algoritmus tajného klíče, protože představuje ověřovací kód zprávy, který se vypočítá pomocí kryptografické funkce hash v kombinaci s tajným klíčem. Viz [Hodnoty hash](#hash-values)dále v tomto tématu.)

- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RijndaelManaged>.

- <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.

## <a name="public-key-encryption"></a>Šifrování veřejného klíče

Šifrování veřejného klíče používá soukromý klíč, který musí být uchován v tajnosti před neoprávněnými uživateli, a veřejný klíč, který může být zveřejněn komukoli. Veřejný klíč a soukromý klíč jsou matematicky propojeny; data, která jsou zašifrována pomocí veřejného klíče, lze dešifrovat pouze pomocí soukromého klíče a data podepsaná soukromým klíčem lze ověřit pouze pomocí veřejného klíče. Veřejný klíč může být zpřístupněn komukoli; používá se pro šifrování dat, která mají být odeslána držiteli soukromého klíče. Kryptografické algoritmy veřejného klíče jsou také označovány jako asymetrické algoritmy, protože k šifrování dat je vyžadován jeden klíč a k dešifrování dat je vyžadován jiný klíč. Základní kryptografické pravidlo zakazuje opětovné použití klíčů a oba klíče by měly být jedinečné pro každou relaci komunikace. V praxi jsou však asymetrické klíče obecně dlouhodobé.

Dvě strany (Alice a Bob) může používat šifrování veřejného klíče takto: Za prvé, Alice generuje pár veřejného a soukromého klíče. Pokud chce Bob poslat Alici zašifrovanou zprávu, požádá ji o její veřejný klíč. Alice odešle Bobovi svůj veřejný klíč přes nezabezpečenou síť a Bob tento klíč použije k zašifrování zprávy. Bob odešle zašifrovanou zprávu Alici a dešifruje ji pomocí svého soukromého klíče. Pokud Bob obdržel Alice klíč přes nezabezpečený kanál, jako je například veřejná síť, Bob je otevřen man-in-the-middle útoku. Proto musí Bob ověřit u Alice, že má správnou kopii jejího veřejného klíče.

Během přenosu veřejného klíče Alice může neoprávněný agent klíč zachytit. Kromě toho může stejný agent zachytit šifrovanou zprávu od Boba. Agent však nemůže dešifrovat zprávu pomocí veřejného klíče. Zprávu lze dešifrovat pouze pomocí soukromého klíče Alice, který nebyl přenesen. Alice nepoužívá svůj soukromý klíč k šifrování odpovědi na Boba, protože kdokoli s veřejným klíčem může zprávu dešifrovat. Pokud alice chce odeslat zprávu zpět Bobovi, požádá Boba o jeho veřejný klíč a zašifruje její zprávu pomocí tohoto veřejného klíče. Petr pak zprávu dešifruje pomocí přidruženého soukromého klíče.

V tomto scénáři Alice a Bob použít veřejného klíče (asymetrické) šifrování k přenosu tajný (symetrický) klíč a používat šifrování tajného klíče pro zbytek jejich relace.

Následující seznam nabízí porovnání mezi kryptografickými algoritmy veřejného a tajného klíče:

- Kryptografické algoritmy s veřejným klíčem používají pevnou velikost vyrovnávací paměti, zatímco kryptografické algoritmy s tajným klíčem používají vyrovnávací paměť s proměnnou délkou.

- Algoritmy veřejného klíče nelze použít k řetězení dat do datových proudů způsobem, jakým mohou algoritmy tajného klíče, protože lze šifrovat pouze malé množství dat. Proto asymetrické operace nepoužívají stejný model streamování jako symetrické operace.

- Šifrování veřejného klíče má mnohem větší prostor klíčů (rozsah možných hodnot pro klíč) než šifrování tajného klíče. Šifrování veřejného klíče je proto méně náchylné k vyčerpávajícím útokům, které se snaží všechny možné klíče.

- Veřejné klíče lze snadno distribuovat, protože nemusí být zabezpečeny za předpokladu, že existuje nějaký způsob ověření identity odesílatele.

- Některé algoritmy veřejného klíče (například RSA a DSA, ale ne Diffie-Hellman) lze použít k vytvoření digitálních podpisů k ověření identity odesílatele dat.

- Algoritmy veřejného klíče jsou velmi pomalé ve srovnání s algoritmy tajného klíče a nejsou navrženy tak, aby šifrovaly velké množství dat. Algoritmy veřejného klíče jsou užitečné pouze pro přenos velmi malých objemů dat. Šifrování veřejného klíče se obvykle používá k šifrování klíče a IV, které mají být použity algoritmem tajného klíče. Po přenosu klíče a IV se pro zbytek relace používá šifrování tajného klíče.

Rozhraní .NET Framework poskytuje následující třídy, které implementují šifrovací algoritmy veřejného klíče:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDiffieHellman>(základní třída)

- <xref:System.Security.Cryptography.ECDiffieHellmanCng>

- <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey>(základní třída)

- <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction>(základní třída)

- <xref:System.Security.Cryptography.ECDsaCng>

RSA umožňuje šifrování i podepisování, ale DSA lze použít pouze pro podepisování a Diffie-Hellman lze použít pouze pro generování klíčů. Obecně platí, že algoritmy veřejného klíče jsou omezenější v jejich použití než algoritmy soukromého klíče.

## <a name="digital-signatures"></a>Digitální podpisy

Algoritmy veřejného klíče lze také použít k vytvoření digitálních podpisů. Digitální podpisy ověřují identitu odesílatele (pokud důvěřujete veřejnému klíči odesílatele) a pomáhají chránit integritu dat. Pomocí veřejného klíče generovaného Alicí může příjemce dat Alice ověřit, že je Alice odeslala porovnáním digitálního podpisu s daty Alice a veřejným klíčem Alice.

Chcete-li použít kryptografii s veřejným klíčem k digitálnímu podepsání zprávy, Alice nejprve použije algoritmus hash na zprávu k vytvoření výtahu zprávy. Zpráva digest je kompaktní a jedinečné reprezentace dat. Alice pak zašifruje výtah zprávy pomocí svého soukromého klíče a vytvoří svůj osobní podpis. Po obdržení zprávy a podpisu Bob dešifruje podpis pomocí veřejného klíče Alice k obnovení výtahu zprávy a zařazuje zprávu pomocí stejného algoritmu hash, který alice použila. Pokud výtah zprávy, který Petr vypočítá přesně odpovídá zprávu digest přijaté od Alice, Bob je ujištěn, že zpráva pochází od vlastníka soukromého klíče a že data nebyla změněna. Pokud Bob důvěřuje, že Alice je vlastníkem soukromého klíče, ví, že zpráva pochází od Alice.

> [!NOTE]
> Podpis může ověřit kdokoli, protože veřejný klíč odesílatele je všeobecně známo a je obvykle součástí formátu digitálního podpisu. Tato metoda nezachová tajemství zprávy; aby byla zpráva tajná, musí být také zašifrována.

Rozhraní .NET Framework poskytuje následující třídy, které implementují algoritmy digitálního podpisu:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDsa>(základní třída)

- <xref:System.Security.Cryptography.ECDsaCng>

## <a name="hash-values"></a>Hodnoty hash

Algoritmy hash mapují binární hodnoty libovolné délky na menší binární hodnoty pevné délky, známé jako hodnoty hash. Hodnota hash je číselná reprezentace části dat. Pokud hash odstavec prostého textu a změnit i jedno písmeno odstavce, následné hash vytvoří jinou hodnotu. Pokud je hodnota hash kryptograficky silná, její hodnota se výrazně změní. Například pokud jeden bit zprávy se změní, silné hash funkce může produkovat výstup, který se liší o 50 procent. Mnoho vstupních hodnot může hash na stejnou výstupní hodnotu. Je však výpočtově nemožné najít dva odlišné vstupy, které hash na stejnou hodnotu.

Dvě strany (Alice a Bob) může použít funkci hash k zajištění integrity zprávy. Vybrali by algoritmus hash pro podepisování zpráv. Alice by napsat zprávu a potom vytvořit hash této zprávy pomocí vybraného algoritmu. Poté by se řídili jednou z následujících metod:

- Alice odešle zprávu ve formátu prostého textu a zahashovaná zpráva (digitální podpis) Bobovi. Petr přijme a zahasírá zprávu a porovná jeho hodnotu hash s hodnotou hash, kterou obdržel od Alice. Pokud jsou hodnoty hash identické, zpráva nebyla změněna. Pokud hodnoty nejsou identické, zpráva byla změněna poté, co Alice napsal.

  Bohužel tato metoda nestanoví pravost odesílatele. Kdokoli se může vydávat za Alici a poslat zprávu Bobovi. Mohou použít stejný algoritmus hash k podepsání zprávy a vše, co Může Petr určit, je, že zpráva odpovídá jeho podpisu. Tohle je jedna z forem útoku. Další informace naleznete v [tématu Cryptography Next Generation (CNG) Secure Communication Example](https://docs.microsoft.com/previous-versions/cc488018(v=vs.100)).

- Alice odešle zprávu ve formátu prostého textu Bobovi prostředpou nezabezpečeného veřejného kanálu. Odešle zahashované zprávě Bobovi přes zabezpečený soukromý kanál. Petr obdrží zprávu ve formátu prostého textu, zahasíjí ji a porovná hodnotu hash se soukromě vyměněnou hodnotou hash. Pokud se hash shoduje, Bob ví dvě věci:

  - Zpráva nebyla změněna.

  - Odesílatel zprávy (Alice) je autentický.

  Aby tento systém fungoval, musí Alice skrýt svou původní hodnotu hash před všemi stranami kromě Boba.

- Alice odešle zprávu ve formátu prostého textu Bobovi prostředkem nezabezpečeného veřejného kanálu a umístí zahashovou zprávu na veřejně zobrazitelný web.

  Tato metoda zabraňuje falšování zpráv tím, že brání komukoli v úpravě hodnoty hash. Přestože zprávu a její hodnotu hash může číst kdokoli, hodnotu hash může změnit pouze Alice. Útočník, který se chce vydávat za Alici, by vyžadoval přístup k webu Alice.

Žádná z předchozích metod nezabrání někomu ve čtení zpráv Alice, protože jsou přenášeny ve formátu prostého textu. Úplné zabezpečení obvykle vyžaduje digitální podpisy (podepisování zpráv) a šifrování.

Rozhraní .NET Framework poskytuje následující třídy, které implementují algoritmy hash:

- <xref:System.Security.Cryptography.HMACSHA1>.

- <xref:System.Security.Cryptography.MACTripleDES>.

- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RIPEMD160>.

- <xref:System.Security.Cryptography.SHA1Managed>.

- <xref:System.Security.Cryptography.SHA256Managed>.

- <xref:System.Security.Cryptography.SHA384Managed>.

- <xref:System.Security.Cryptography.SHA512Managed>.

- HMAC varianty všech algoritmů Secure Hash Algorithm (SHA), Message Digest 5 (MD5) a RIPEMD-160 algoritmů.

- Implementace CryptoServiceProvider (obálky spravovaného kódu) všech algoritmů SHA.

- Kryptografie nové generace (CNG) implementace všech algoritmů MD5 a SHA.

> [!NOTE]
> V roce 1996 byly objeveny konstrukční nedostatky MD5 a místo toho byl doporučen SHA-1. V roce 2004 byly objeveny další chyby a algoritmus MD5 již není považován za bezpečný. Algoritmus SHA-1 byl také zjištěno, že je nezabezpečené a SHA-2 se nyní doporučuje místo.

## <a name="random-number-generation"></a>Generování náhodných čísel

Generování náhodných čísel je nedílnou součástí mnoha kryptografických operací. Například kryptografické klíče musí být co nejnáhodnější, aby bylo možné je reprodukovat. Generátory kryptografických náhodných čísel musí generovat výstup, který je výpočtově neproveditelný předpovědět s pravděpodobností, která je lepší než jedna polovina. Proto jakákoli metoda předpovídání další výstupní bit nesmí provádět lépe než náhodné hádání. Třídy v rozhraní .NET Framework používají generátory náhodných čísel ke generování kryptografických klíčů.

Třída <xref:System.Security.Cryptography.RNGCryptoServiceProvider> je implementace algoritmu generátoru náhodných čísel.

## <a name="clickonce-manifests"></a>Manifesty ClickOnce

V rozhraní .NET Framework 3.5 umožňují následující třídy kryptografie získat a ověřit informace o podpisech manifestu pro aplikace, které jsou nasazeny pomocí [technologie ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment):

- Třída <xref:System.Security.Cryptography.ManifestSignatureInformation> získá informace o podpisu manifestu <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> při použití jeho metody přetížení.

- <xref:System.Security.ManifestKinds> Výčet můžete použít k určení manifestů k ověření. Výsledek ověření je jednou z <xref:System.Security.Cryptography.SignatureVerificationResult> hodnot výčtu.

- Třída <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> poskytuje kolekci <xref:System.Security.Cryptography.ManifestSignatureInformation> objektů ověřených podpisů jen pro čtení.

 Kromě toho následující třídy poskytují konkrétní informace o podpisu:

- <xref:System.Security.Cryptography.StrongNameSignatureInformation>obsahuje informace o podpisu silného názvu manifestu.

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation>představuje informace o podpisu Authenticode pro manifest.

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation>obsahuje informace o časovém razítku podpisu Authenticode.

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus>poskytuje jednoduchý způsob, jak zkontrolovat, zda je podpis Authenticode důvěryhodný.

## <a name="suite-b-support"></a>Podpora suite B

Rozhraní .NET Framework 3.5 podporuje sadu kryptografických algoritmů sady B sady, kterou publikovala Národní bezpečnostní agentura (NSA). Další informace o sadě Suite B naleznete v [informačním přehledu o kryptografii NSA Suite B](https://www.nsa.gov/what-we-do/information-assurance/).

Jsou zahrnuty následující algoritmy:

- Algoritmus Advanced Encryption Standard (AES) s velikostí klíče 128, 192 a 256 bitů pro šifrování.

- Zabezpečené algoritmy hash SHA-1, SHA-256, SHA-384 a SHA-512 pro hašování. (Poslední tři jsou obecně seskupeny a označovány jako SHA-2.)

- Algoritmus digitálního podpisu eliptické křivky (ECDSA) pomocí křivek 256bitového, 384bitového a 521bitového primárního modulu pro podepisování. Dokumentace NSA konkrétně definuje tyto křivky a nazývá je P-256, P-384 a P-521. Tento algoritmus je <xref:System.Security.Cryptography.ECDsaCng> poskytován třídou. Umožňuje podepsat pomocí soukromého klíče a ověřit podpis pomocí veřejného klíče.

- Eliptický curve Diffie-Hellman (ECDH) algoritmus, pomocí křivky 256-bit, 384-bit, a 521-bit prime moduli pro výměnu klíčů a tajné dohody. Tento algoritmus je <xref:System.Security.Cryptography.ECDiffieHellmanCng> poskytován třídou.

Obálky spravovaného kódu pro implementaci s certifikací FIPS (Federal Information Processing Standard) pro implementace AES, SHA-256, SHA-384 a <xref:System.Security.Cryptography.AesCryptoServiceProvider>SHA-512 jsou k dispozici v nových , <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>, <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>a <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> třídách.

## <a name="cryptography-next-generation-cng-classes"></a>Třídy kryptografie nové generace (CNG)

Třídy kryptografie nové generace (CNG) poskytují spravované obálky kolem nativní funkce CNG. (CNG je náhradou za CryptoAPI.) Tyto třídy mají "Cng" jako součást jejich jména. Centrální třídy obálky CNG <xref:System.Security.Cryptography.CngKey> je třída kontejneru klíčů, která abstrahuje úložiště a použití klíčů CNG. Tato třída umožňuje bezpečně uložit dvojici klíčů nebo veřejný klíč a odkazovat na něj pomocí jednoduchého názvu řetězce. Elliptic křivka <xref:System.Security.Cryptography.ECDsaCng> na základě <xref:System.Security.Cryptography.ECDiffieHellmanCng> podpisu třídy a šifrování třídy můžete použít <xref:System.Security.Cryptography.CngKey> objekty.

Třída <xref:System.Security.Cryptography.CngKey> se používá pro různé další operace, včetně otevírání, vytváření, odstraňování a exportu klíčů. Poskytuje také přístup k popisovači základní klíče pro použití při přímém volání nativních funkcí.

Rozhraní .NET Framework 3.5 také obsahuje řadu podpůrných tříd CNG, například následující:

- <xref:System.Security.Cryptography.CngProvider>udržuje zprostředkovatele úložiště klíčů.

- <xref:System.Security.Cryptography.CngAlgorithm>udržuje algoritmus CNG.

- <xref:System.Security.Cryptography.CngProperty>udržuje často používané vlastnosti klíče.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Kryptografický model](../../../docs/standard/security/cryptography-model.md)|Popisuje, jak je kryptografie implementována v knihovně základních tříd.|
|[Návod: Vytvoření šifrovací aplikace](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Ukazuje základní úlohy šifrování a dešifrování.|
|[Konfigurace šifrovacích tříd](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Popisuje, jak mapovat názvy algoritmů na kryptografické třídy a identifikátory mapových objektů na kryptografický algoritmus.|
