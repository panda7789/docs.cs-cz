---
title: Šifrovací služby
description: Přečtěte si přehled metod šifrování a postupů podporovaných rozhraním .NET, jako jsou manifesty ClickOnce, Suite B, podpora kryptografické služby nové generace (CNG) &.
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
ms.openlocfilehash: 701dce82669395743c884a613512bfadc06c91b3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596329"
---
# <a name="cryptographic-services"></a>Šifrovací služby

Veřejné sítě, jako je Internet, neposkytují způsob zabezpečené komunikace mezi entitami. Komunikace přes tyto sítě je náchylná ke čtení nebo dokonce úpravám neoprávněnými třetími stranami. Kryptografie pomáhá chránit data před zobrazením, poskytuje způsoby, jak zjistit, zda byla data upravena, a pomáhá zajistit zabezpečený způsob komunikace v jiném nezabezpečeném kanálu. Data mohou být například šifrována pomocí kryptografického algoritmu, přenášena v zašifrovaném stavu a později dešifrována zamýšlenou stranou. Pokud třetí strana zachytí zašifrovaná data, bude obtížné je dešifrovat.

V .NET Framework třídy v <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů spravují mnoho podrobností kryptografie za vás. Některé jsou obálky pro nespravované rozhraní CryptoAPI (Microsoft Cryptography API), zatímco jiné jsou čistě spravované implementace. Pro použití těchto tříd nemusíte být odborníkem na kryptografii. Když vytváříte novou instanci jedné z tříd šifrovacího algoritmu, klíče se generují automaticky pro snadné použití a výchozí vlastnosti jsou co nejbezpečnější a bezpečné.

Tento přehled obsahuje souhrn metod a postupů šifrování podporovaných .NET Framework, včetně manifestů ClickOnce, Suite B a podpory kryptografie nové generace (CNG) představené v .NET Framework 3,5.

Další informace o kryptografii a o službách, součástech a nástrojích společnosti Microsoft, které vám umožní přidat kryptografické zabezpečení do aplikací, naleznete v části vývoj Win32 a COM, zabezpečení této dokumentace.

## <a name="cryptographic-primitives"></a>Kryptografické primitivy

V typické situaci, kdy se používá kryptografie, dvě strany (Alice a Bob) komunikují přes nezabezpečený kanál. Alice a Bob chtějí zajistit, aby jejich komunikace zůstala nesrozumitelná pro kohokoli, kdo může naslouchat. Vzhledem k tomu, že Alice a Bob jsou ve vzdálených umístěních, Alice musí zajistit, aby informace, které obdrží od Boba, nebyly během přenosu změněny kýmkoli. Kromě toho musí mít jistotu, že informace skutečně pocházejí od Boba a nikoli od někoho, kdo zosobňuje Boba.

Kryptografie se používá k dosažení následujících cílů:

- Důvěrné: slouží k ochraně před čtením identity uživatele nebo dat.

- Integrita dat: pro lepší ochranu dat před změnou.

- Ověřování: zajistí, že data pocházejí z konkrétní strany.

- Neodmítnutí: Pokud chcete zabránit určité straně v odepření, že poslali zprávu.

Pro dosažení těchto cílů můžete použít kombinaci algoritmů a postupů známých jako kryptografické primitivy k vytvoření kryptografického schématu. V následující tabulce jsou uvedeny kryptografické primitivy a jejich použití.

|Kryptografická primitiva|Použití|
|-----------------------------|---------|
|Šifrování tajného klíče (symetrické kryptografie)|Provede transformaci dat za účelem zachování jejich čtení třetími stranami. Tento typ šifrování používá jediný sdílený tajný klíč k šifrování a dešifrování dat.|
|Šifrování veřejného klíče (asymetrické šifrování)|Provede transformaci dat za účelem zachování jejich čtení třetími stranami. Tento typ šifrování používá k šifrování a dešifrování dat dvojici veřejného a privátního klíče.|
|Kryptografické podepisování|Pomáhá ověřit, jestli data pocházejí z konkrétní strany vytvořením digitálního podpisu, který je pro danou stranu jedinečný. Tento proces také používá funkce hash.|
|Kryptografické hodnoty hash|Mapuje data z libovolné délky na bajtovou sekvenci s pevnou délkou. Hodnoty hash jsou statisticky jedinečné; jiná posloupnost dvou bajtů nebude mít hodnotu hash na stejnou hodnotu.|

## <a name="secret-key-encryption"></a>Šifrování tajného klíče

Šifrovací algoritmy tajného klíče používají pro šifrování a dešifrování dat jeden tajný klíč. Klíč musíte zabezpečit od přístupu neautorizovanými agenty, protože kterákoli z nich, který klíč obsahuje, ho může použít k dešifrování vašich dat nebo k šifrování svých vlastních dat. Tato deklarace vzniklá od vás.

Šifrování tajného klíče se také označuje jako symetrické šifrování, protože se ke šifrování a dešifrování používá stejný klíč. Šifrovací algoritmy tajného klíče jsou velmi rychlé (ve srovnání s algoritmy veřejného klíče) a jsou vhodné pro provádění kryptografických transformací velkých proudů dat. Asymetrické šifrovací algoritmy, jako je RSA, jsou omezené matematicky v množství dat, která můžou šifrovat. Algoritmy symetrického šifrování obvykle nemají tyto problémy.

Typ algoritmu tajného klíče, který se nazývá Block šifra, se používá k šifrování jednoho bloku dat najednou. Blokové šifry, jako je DES (Data Encryption Standard), TripleDES a standard AES (Advanced Encryption Standard) (AES), kryptograficky transformují vstupní blok *n* bajtů do výstupního bloku šifrovaných bajtů. Chcete-li zašifrovat nebo dešifrovat sekvenci bajtů, je nutné ji zablokovat blokem. Vzhledem k tomu, že *n* je malé (8 bajtů pro des a TripleDES; 16 bajtů [výchozí], 24 bajtů nebo 32 bajtů pro AES), hodnoty dat větší než *n* musí být zašifrované po jednom bloku. Hodnoty dat, které jsou menší než *n* , musí být rozšířeny na *n* , aby je bylo možné zpracovat.

Jedna jednoduchá forma bloku Block je označována jako Codebook režim elektronického šifrování (ECB). Režim ECB není považován za zabezpečený, protože nepoužívá inicializační vektor k inicializaci prvního bloku prostého textu. Pro daný tajný klíč *k*, jednoduchá bloková šifra, která nepoužívá inicializační vektor, zašifruje stejný vstupní blok prostého textu do stejného výstupního bloku šifrovaného textu. Proto pokud máte duplicitní bloky ve vstupním datovém proudu prostého textu, budete mít ve svém výstupním streamu šifrovaných dat duplicitní bloky. Tyto duplicitní výstupní bloky upozorňují neoprávněné uživatele na slabé šifrování při použití algoritmů, které mohly být zaměstnány, a možných způsobů útoku. Režim šifry ECB je proto poměrně zranitelný za účelem analýzy a nakonec pro zjišťování klíčů.

Třídy blokové šifry, které jsou k dispozici v knihovně základních tříd, používají výchozí režim zřetězení s názvem cipher-Blocking Chaining (CBC), i když můžete změnit toto výchozí nastavení, pokud chcete.

CBC šifry překonat problémy spojené s šiframi ECB pomocí inicializačního vektoru (IV) k šifrování prvního bloku prostého textu. Každý následující blok prostého textu v případě, že `XOR` před jeho zašifrováním projde logickou a () operaci s předchozím blokem šifrovaného textu. Každý blok šifrovaného textu je proto závislý na všech předchozích blocích. Při použití tohoto systému se běžná záhlaví zpráv, která mohou být známá neoprávněným uživatelům, nelze použít k zpětnou analýzu klíče.

Jedním ze způsobů, jak ohrozit data zašifrovaná pomocí CBC šifry, je provést důkladné prohledávání každého možného klíče. V závislosti na velikosti klíče, který se používá k šifrování, je tento druh hledání velmi časově náročný pomocí i nejrychlejších počítačů, a proto je neproveditelný. Větší velikosti klíčů je obtížné dešifrovat. I když při šifrování není teoreticky nemožné, aby nežádoucí osoba načetla šifrovaná data, vyvolají to náklady. Pokud se po uplynutí tří měsíců provede vyčerpávající hledání, aby se načetla data, která jsou smysluplná jenom několik dní, je metoda podrobného vyhledávání nepraktická.

Nevýhodou šifrování tajného klíče je to, že se obě strany dohodly na klíči a IV a sdělily jejich hodnoty. Velikost IV není považována za tajnou a je možné ji přenést do prostého textu se zprávou. Klíč se ale musí uchovávat jako tajný klíč od neautorizovaných uživatelů. Z důvodu těchto problémů se šifrování tajného klíče často používá společně s šifrováním veřejného klíče pro soukromou komunikaci hodnot klíče a IV.

Za předpokladu, že Alice a Bob jsou dvě strany, které chtějí komunikovat přes nezabezpečený kanál, můžou použít šifrování tajného klíče takto: Alice a Bob souhlasí, že používají jeden konkrétní algoritmus (například AES) s určitým klíčem a IV. Alice vytvoří zprávu a vytvoří síťový datový proud (například pojmenovaný kanál nebo síťový e-mail), na který se má zpráva poslat. V dalším kroku šifruje text pomocí klíče a IV a pošle šifrovanou zprávu a IV k Bobovi přes intranet. Bob obdrží zašifrovaný text a dešifruje ho pomocí IV a dřív souhlasil na klíči. Pokud je přenos zachycen, zachytávací modul nemůže obnovit původní zprávu, protože neznají klíč. V tomto scénáři musí být klíč v tajnosti. Ve scénáři reálného světa buď Alice, nebo Bob vygeneruje tajný klíč a pomocí šifrování veřejného klíče (asymetrického klíče) přenáší tajný klíč (symetrický) na druhou stranu. Další informace o šifrování veřejného klíče najdete v další části.

.NET Framework poskytuje následující třídy, které implementují šifrovací algoritmy tajného klíče:

- <xref:System.Security.Cryptography.AesManaged>(zavedeno v .NET Framework 3,5).

- <xref:System.Security.Cryptography.DESCryptoServiceProvider>.

- <xref:System.Security.Cryptography.HMACSHA1>(To je technicky klíč tajného klíče, protože představuje ověřovací kód zprávy vypočtený pomocí kryptografické funkce hash kombinované s tajným klíčem. Viz [hodnoty hash](#hash-values)dále v tomto tématu.)

- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RijndaelManaged>.

- <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.

## <a name="public-key-encryption"></a>Šifrování veřejného klíče

Šifrování s veřejným klíčem používá privátní klíč, který se musí uchovávat jako tajný klíč od neautorizovaných uživatelů a veřejný klíč, který je možné zveřejnit pro kohokoli. Veřejný klíč a soukromý klíč jsou matematicky propojeny; data zašifrovaná pomocí veřejného klíče lze dešifrovat pouze pomocí privátního klíče a data, která jsou podepsána pomocí privátního klíče, lze ověřit pouze pomocí veřejného klíče. Veřejný klíč může být zpřístupněn všem uživatelům; slouží k šifrování dat, která se mají zasílat do uchování privátního klíče. Kryptografické algoritmy veřejného klíče jsou známé také jako asymetrické algoritmy, protože pro šifrování dat je vyžadován jeden klíč a k dešifrování dat je vyžadován další klíč. Základní kryptografické pravidlo zakazuje opakované použití klíče a oba klíče by měly být pro každou relaci komunikace jedinečné. Nicméně v praxi jsou asymetrické klíče všeobecně dlouhodobé.

Dvě strany (Alice a Bob) můžou používat šifrování pomocí veřejného klíče takto: nejdřív Alice vygeneruje pár veřejného a privátního klíče. Pokud Bob chce odeslat Alici šifrovanou zprávu, požádá o jeho veřejný klíč. Alice pošle Bobovi svůj veřejný klíč přes nezabezpečenou síť a Bob použije tento klíč k zašifrování zprávy. Bob pošle šifrovanou zprávu Alici a dešifruje ji pomocí jejího privátního klíče. Pokud Bob přijal klíč Alice přes nezabezpečený kanál, jako je například veřejná síť, Bob je otevřený útok prostředníkem. Proto musí Bob ověřit s Alicí, že má správnou kopii jejího veřejného klíče.

Během přenosu veřejného klíče Alice může klíč zachytit neautorizovaný agent. Kromě toho může stejný agent zachytit šifrovanou zprávu od Boba. Agent ale nemůže dešifrovat zprávu pomocí veřejného klíče. Zpráva může být dešifrována pouze s privátním klíčem Alice, který nebyl přenesen. Alice nepoužívá svůj privátní klíč k šifrování zprávy s odpovědí Bobovi, protože kdokoli s veřejným klíčem by mohl zprávu dešifrovat. Pokud Alice chce poslat zprávu zpět Bobovi, požádá Bob o jeho veřejný klíč a zašifruje jeho zprávu pomocí tohoto veřejného klíče. Bob pak dešifruje zprávu pomocí jejího přidruženého privátního klíče.

V tomto scénáři Alice a Bob používá šifrování veřejného klíče (asymetrické) k přenosu tajného (symetrického) klíče a pro zbytek relace používá šifrování tajného klíče.

Následující seznam obsahuje porovnání kryptografických algoritmů veřejného klíče a tajného klíče:

- Kryptografické algoritmy veřejného klíče používají pevnou velikost vyrovnávací paměti, zatímco kryptografické algoritmy tajného klíče používají vyrovnávací paměť s proměnlivou délkou.

- Algoritmy veřejného klíče nelze použít k zřetězení dat společně do datových proudů, jako jsou algoritmy tajného klíče, protože je možné šifrovat pouze malé objemy dat. Proto asymetrické operace nepoužívají stejný model streamování jako symetrické operace.

- Šifrování veřejného klíče má mnohem větší prostor (rozsah možných hodnot pro klíč) než šifrování tajného klíče. Proto je šifrování veřejného klíče méně náchylné k vyčerpávajícím útokům, které se pokoušejí o každý možný klíč.

- Veřejné klíče se snadno distribuují, protože není nutné je zabezpečit, pokud k tomu existuje nějaký způsob, jak ověřit identitu odesilatele.

- Některé algoritmy veřejného klíče (například RSA a DSA, ale ne Diffie-Hellman) se dají použít k vytvoření digitálních podpisů, které ověřují identitu odesilatele dat.

- Algoritmy veřejného klíče jsou ve srovnání s algoritmy tajného klíče velmi pomalé a nejsou navržené k šifrování velkých objemů dat. Algoritmy veřejného klíče jsou užitečné jenom pro přenos velmi malých objemů dat. Šifrování pomocí veřejného klíče se obvykle používá k šifrování klíče a IV pro použití algoritmem tajného klíče. Po přesunu klíče a IV se pro zbytek relace použije šifrování tajného klíče.

.NET Framework poskytuje následující třídy, které implementují šifrovací algoritmy veřejného klíče:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDiffieHellman>(základní třída)

- <xref:System.Security.Cryptography.ECDiffieHellmanCng>

- <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey>(základní třída)

- <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction>(základní třída)

- <xref:System.Security.Cryptography.ECDsaCng>

RSA umožňuje šifrování i podepisování, ale DSA se dá použít jenom pro podepisování a Diffie-Hellman se dá použít jenom pro generování klíče. Obecně platí, že algoritmy veřejného klíče jsou více omezené při jejich použití než algoritmy privátního klíče.

## <a name="digital-signatures"></a>Digitální podpisy

Algoritmy veřejného klíče se dají použít i k vytvoření digitálních podpisů. Digitální podpisy ověřují identitu odesilatele (Pokud důvěřujete veřejnému klíči odesílatele) a zajistíte ochranu integrity dat. Pomocí veřejného klíče vygenerovaného Alicí může příjemce dat Alice ověřit, že je Alice poslala porovnáním digitálního podpisu s daty Alice a veřejným klíčem Alice.

Chcete-li použít kryptografii veřejného klíče k digitálnímu podpisu zprávy, Alice nejprve pro zprávu použije algoritmus hash k vytvoření výtahu zprávy. Hodnota Digest zprávy je kompaktní a jedinečná reprezentace dat. Alice pak zašifruje výtah zprávy pomocí jeho privátního klíče a vytvoří svůj osobní podpis. Po přijetí zprávy a podpisu Bob dešifruje podpis pomocí veřejného klíče Alice pro obnovení výtahu zprávy a hodnotu hash zprávy pomocí stejného algoritmu hash, který Alice použila. Pokud se výtah zprávy, který Bob počítá, přesně shoduje se výtahem zprávy přijatým od Alice, je zaručeno, že zpráva pochází od držitele privátního klíče a že data nebyla změněna. Pokud Bob důvěřuje, že Alice je držitelem privátního klíče, ví, že zpráva pochází od Alice.

> [!NOTE]
> Podpis může být ověřený kýmkoli, protože veřejný klíč odesílatele je běžnou znalostí a obvykle je zahrnutý ve formátu digitálního podpisu. Tato metoda nezachovává tajnost zprávy; zpráva, která má být tajná, musí být také zašifrovaná.

.NET Framework poskytuje následující třídy, které implementují algoritmy digitálního podpisu:

- <xref:System.Security.Cryptography.DSACryptoServiceProvider>

- <xref:System.Security.Cryptography.RSACryptoServiceProvider>

- <xref:System.Security.Cryptography.ECDsa>(základní třída)

- <xref:System.Security.Cryptography.ECDsaCng>

## <a name="hash-values"></a>Hodnoty hash

Algoritmy hash mapují binární hodnoty libovolné délky na menší binární hodnoty s pevnou délkou, označované jako hodnoty hash. Hodnota hash je numerická reprezentace části dat. Pokud zadáte hodnotu hash v podobě prostého textu a změníte dokonce i jedno písmeno odstavce, další hodnota hash vytvoří jinou hodnotu. Pokud je hash kryptograficky silný, jeho hodnota se významně změní. Například pokud je jeden bit zprávy změněn, silná funkce hash může vytvořit výstup, který se liší o 50 procent. Mnoho vstupních hodnot může mít hodnotu hash na stejnou výstupní hodnotu. Je ale výpočetně neproveditelný, aby bylo možné najít dvě odlišné vstupy, které se hash shodují se stejnou hodnotou.

Dvě strany (Alice a Bob) můžou použít funkci hash k zajištění integrity zprávy. Vybraly algoritmus hash pro podepsání svých zpráv. Alice by napsala zprávu a pak vytvořila hodnotu hash této zprávy pomocí vybraného algoritmu. Pak by pak následovaly jednu z následujících metod:

- Alice pošle zprávu nešifrovaného textu a zatřiďovací zprávu (digitální podpis) Bobovi. Bob obdrží a vytvoří hodnotu hash zprávy a porovná hodnotu hash s hodnotou hash, kterou obdržel od Alice. Pokud jsou hodnoty hash identické, zpráva se nezměnila. Pokud hodnoty nejsou shodné, zpráva se po jejím zapsání nezměnila.

  Tato metoda bohužel nevytváří pravost odesilatele. Kdokoli může zosobnit Alici a poslat zprávu Bobovi. Můžou použít stejný algoritmus hash k podepsání své zprávy a všichni Bob můžou určit, že se zpráva shoduje s jejím podpisem. Jedná se o jednu formu útoku prostředníkem. Další informace najdete v tématu [Příklad zabezpečené komunikace CNG (Cryptography Next Generation)](https://docs.microsoft.com/previous-versions/cc488018(v=vs.100)).

- Alice pošle zprávu nešifrovaného textu Bobovi přes nezabezpečený veřejný kanál. Pošle zprávu hash Bobovi přes zabezpečený privátní kanál. Bob obdrží zprávu ve formátu prostého textu, vytvoří hodnotu hash a porovná hodnotu hash s soukromou vyměněnou hodnotou hash. Pokud se hodnoty hash shodují, Bob zná dvě věci:

  - Zpráva se nezměnila.

  - Odesílatel zprávy (Alice) je pravý.

  Aby tento systém fungoval, musí skrýt jeho původní hodnotu hash ze všech stran kromě Boba.

- Alice pošle zprávu nešifrovaného textu Bobovi přes nezabezpečený veřejný kanál a umístí do jejího veřejně dostupného webu zprávu s hodnotou hash.

  Tato metoda brání manipulaci se zprávou tím, že brání komukoli v úpravě hodnoty hash. I když může být zpráva a její hodnota hash přečtena kýmkoli, hodnota hash může být změněna pouze Alicí. Útočník, který chce zosobnit Alici, by vyžadoval přístup k webu Alice.

Žádná z předchozích metod nebrání někomu v čtení zpráv Alice, protože jsou přenášeny ve formátu prostého textu. Úplné zabezpečení obvykle vyžaduje digitální podpisy (podepisování zpráv) a šifrování.

.NET Framework poskytuje následující třídy, které implementují algoritmy hash:

- <xref:System.Security.Cryptography.HMACSHA1>.

- <xref:System.Security.Cryptography.MACTripleDES>.

- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.

- <xref:System.Security.Cryptography.RIPEMD160>.

- <xref:System.Security.Cryptography.SHA1Managed>.

- <xref:System.Security.Cryptography.SHA256Managed>.

- <xref:System.Security.Cryptography.SHA384Managed>.

- <xref:System.Security.Cryptography.SHA512Managed>.

- Varianty HMAC všech algoritmů SHA (Secure Hash Algorithm), MD5 (Message Digest 5) a RIPEMD-160.

- Implementace CryptoServiceProvider (obálky spravovaného kódu) všech algoritmů SHA.

- Implementace kryptografie nové generace (CNG) pro všechny algoritmy MD5 a SHA.

> [!NOTE]
> Chyby návrhu MD5 byly zjištěny v 1996 a místo toho byly doporučeny SHA-1. V 2004 byly zjištěny další chyby a algoritmus MD5 již není považován za zabezpečený. Algoritmus SHA-1 byl také zjištěn jako nezabezpečený a místo toho se doporučuje SHA-2.

## <a name="random-number-generation"></a>Náhodné generování čísel

Generování náhodného čísla je celé řady kryptografických operací. Například kryptografické klíče musí být co nejnáhodný, aby bylo možné je znovu rekládat. Generátory náhodných náhodných čísel musí generovat výstup, který je výpočetně nevhodný pro předpověď pravděpodobnosti, která je lepší než jedna polovina. Proto jakákoli metoda předpovědi dalšího výstupního bitu nesmí vylepšit více než náhodné odhadování. Třídy v .NET Framework používají generátory náhodných čísel ke generování kryptografických klíčů.

<xref:System.Security.Cryptography.RNGCryptoServiceProvider>Třída je implementací algoritmu generátoru náhodných čísel.

## <a name="clickonce-manifests"></a>Manifesty ClickOnce

V .NET Framework 3,5 následující kryptografické třídy umožňují získat a ověřit informace o signaturách manifestu pro aplikace, které jsou nasazeny pomocí [technologie ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment):

- <xref:System.Security.Cryptography.ManifestSignatureInformation>Třída získává informace o podpisu manifestu při použití <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> přetížení metody.

- Pomocí <xref:System.Security.ManifestKinds> výčtu můžete určit, které manifesty se mají ověřit. Výsledkem ověření je jedna z <xref:System.Security.Cryptography.SignatureVerificationResult> hodnot výčtu.

- <xref:System.Security.Cryptography.ManifestSignatureInformationCollection>Třída poskytuje kolekci <xref:System.Security.Cryptography.ManifestSignatureInformation> objektů ověřovaných podpisů, které jsou jen pro čtení.

 Kromě toho následující třídy poskytují konkrétní informace o podpisu:

- <xref:System.Security.Cryptography.StrongNameSignatureInformation>obsahuje informace o podpisu silného názvu pro manifest.

- <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation>představuje informace o podpisu Authenticode pro manifest.

- <xref:System.Security.Cryptography.X509Certificates.TimestampInformation>obsahuje informace o časovém razítku podpisu Authenticode.

- <xref:System.Security.Cryptography.X509Certificates.TrustStatus>poskytuje jednoduchý způsob, jak ověřit, zda je podpis Authenticode důvěryhodný.

## <a name="suite-b-support"></a>Podpora Suite B

.NET Framework 3,5 podporuje Suite B sadu kryptografických algoritmů publikovaných národním bezpečnostním úřadem (National Security Agency). Další informace o Suite B najdete v [listu faktu Suite B kryptografie](https://www.nsa.gov/what-we-do/information-assurance/).

K dispozici jsou tyto algoritmy:

- Algoritmus standard AES (Advanced Encryption Standard) (AES) s velikostí klíčů 128, 192, a 256 bitů pro šifrování.

- Algoritmy SHA-1, SHA-256, SHA-384 a SHA-512 pro algoritmus hash. (Poslední tři jsou obecně seskupené dohromady a označují se jako SHA-2.)

- Algoritmus ECDSA (s eliptickou křivkou digitálního podpisu), který při podepisování používá křivky 256 bitů, 384 bitů a 521-bit. Dokumentace k bezpečnostnímu orgánu konkrétně definuje tyto křivky a volá je P-256, P-384 a P-521. Tento algoritmus je poskytován <xref:System.Security.Cryptography.ECDsaCng> třídou. Umožňuje vám podepsat privátní klíč a ověřit podpis pomocí veřejného klíče.

- Algoritmus ECDH s eliptickou křivkou (ECDH), který používá křivky 256 bitů, 384 bitů a 521-bit pro výměnu klíčů a tajnou adresu. Tento algoritmus je poskytován <xref:System.Security.Cryptography.ECDiffieHellmanCng> třídou.

Obálka spravovaného kódu pro implementace standardu FIPS (Federal Information Processing Standard) s certifikací AES, SHA-256, SHA-384 a SHA-512 jsou k dispozici v <xref:System.Security.Cryptography.AesCryptoServiceProvider> nových <xref:System.Security.Cryptography.SHA256CryptoServiceProvider> <xref:System.Security.Cryptography.SHA384CryptoServiceProvider> třídách,, a <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> .

## <a name="cryptography-next-generation-cng-classes"></a>Třídy kryptografie nové generace (CNG)

Třídy kryptografie nové generace (CNG) poskytují spravovanou obálku kolem nativních funkcí CNG. (CNG je náhradou pro rozhraní CryptoAPI.) Tyto třídy mají v rámci svých názvů "CNG". Základem základních tříd CNG je <xref:System.Security.Cryptography.CngKey> Třída kontejnerů klíčů, která vyabstrakce úložiště a použití klíčů CNG. Tato třída umožňuje bezpečně uložit dvojici klíčů nebo veřejný klíč a odkazovat na ni pomocí jednoduchého názvu řetězce. Třída podpisu založená na eliptické křivce <xref:System.Security.Cryptography.ECDsaCng> a <xref:System.Security.Cryptography.ECDiffieHellmanCng> Třída šifrování může používat <xref:System.Security.Cryptography.CngKey> objekty.

<xref:System.Security.Cryptography.CngKey>Třída se používá pro celou řadu dalších operací, včetně otevírání, vytváření, odstraňování a exportování klíčů. Poskytuje také přístup k základnímu popisovači klíče, který se použije při přímém volání nativních funkcí.

.NET Framework 3,5 obsahuje také řadu podporovaných tříd CNG, například následující:

- <xref:System.Security.Cryptography.CngProvider>udržuje poskytovatele úložiště klíčů.

- <xref:System.Security.Cryptography.CngAlgorithm>udržuje algoritmus CNG.

- <xref:System.Security.Cryptography.CngProperty>uchovává často používané vlastnosti klíče.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Kryptografický model](cryptography-model.md)|Popisuje, jak je kryptografie implementována v knihovně základní třídy.|
|[Návod: Vytvoření šifrovací aplikace](walkthrough-creating-a-cryptographic-application.md)|Ukazuje základní úlohy šifrování a dešifrování.|
|[Konfigurace šifrovacích tříd](../../framework/configure-apps/configure-cryptography-classes.md)|Popisuje způsob mapování názvů algoritmů na kryptografické třídy a mapování identifikátorů objektů na kryptografický algoritmus.|
