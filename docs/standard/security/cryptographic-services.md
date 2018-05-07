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
- decryptioin [.NET Framework]
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
ms.openlocfilehash: f8193932deac3854b07085cba9faac76e68c4da8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cryptographic-services"></a>Šifrovací služby
<a name="top"></a> Veřejných sítích, jako je Internet není pro zajištění zabezpečené komunikace mezi entitami. Komunikace v těchto sítích je náchylný ke čtení nebo dokonce upravovat neoprávněným třetím stranám. Šifrování pomáhá chránit data před zobrazením, poskytuje způsoby, jak zjistit, zda nedošlo ke změně dat, a pomáhá poskytovat zabezpečenou komunikaci přes jinak nezabezpečené kanály. Například data mohou být šifrují pomocí šifrovacího algoritmu, přenesen šifrovaného stavu a později dešifrovat určenou stranou. Pokud třetích stran zabrání šifrovaná data, bude obtížné dekódovat.  
  
 V rozhraní .NET Framework, třídy v <xref:System.Security.Cryptography?displayProperty=nameWithType> obor názvů spravovat mnoho podrobností kryptografie pro vás. Některé jsou obálek pro nespravované Microsoft Cryptography API (rozhraní CryptoAPI), zatímco jiné jsou čistě spravované implementace. Nemusíte být odborník v kryptografii k použití těchto tříd. Když vytvoříte novou instanci jednoho z šifrovací algoritmus třídy, klíče jsou vytvořeny automaticky pro snadné použití a výchozí vlastnosti jsou bezpečné a co nejvíce zabezpečené.  
  
 Tento přehled obsahuje souhrn metody šifrování a postupy podporované rozhraním .NET Framework, včetně ClickOnce manifestů, Suite B, a podporu Kryptografické služby nové generace (CNG) uvedené v systémech [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  
  
 Tento přehled obsahuje následující části:  
  
-   [Kryptografické primitivní elementy.](#primitives)  
  
-   [Šifrování tajného klíče](#secret_key)  
  
-   [Šifrování veřejného klíče](#public_key)  
  
-   [Digitální podpisy](#digital_signatures)  
  
-   [Hodnoty hash](#hash_values)  
  
-   [Náhodné generování čísel](#random_numbers)  
  
-   [Manifesty ClickOnce](#clickonce)  
  
-   [Podpora standardu Suite B](#suite_b)  
  
-   [Související témata](#related_topics)  
  
 Další informace o šifrování a o služby společnosti Microsoft, komponenty a nástroje, které vám umožní přidat kryptografické zabezpečení pro aplikace najdete v části Win32 a COM vývoj, zabezpečení části této dokumentace.  
  
<a name="primitives"></a>   
## <a name="cryptographic-primitives"></a>Kryptografické primitivní elementy.  
 V typické situaci, kde se používá šifrování obě strany (Alice a Bob) komunikovat přes nezabezpečený kanál. Alice a Bob chtít zajistit, aby jejich komunikace zůstala nesrozumitelná každý, kdo může naslouchání. Kromě toho protože Alice a Bob jsou ve vzdálených umístěních, Alice musí Ujistěte se, že informace, které uživatel obdrží od Boba nebyl změněn libovolný uživatel během přenosu. Kromě toho také musí zajistit, že informace skutečně pocházejí z Bob a ne od uživatele, který zosobňuje Bob.  
  
 Šifrování se používá k dosažení těchto cílů:  
  
-   Důvěrnost: K ochraně identity uživatele nebo data z načítán.  
  
-   Integrita dat: K ochraně dat před změnou.  
  
-   Ověřování: K zajištění toho, že data pocházejí od určité skupiny.  
  
-   Non odvolatelnost: Zabránit konkrétní strany odepření, že odešlou zprávy.  
  
 K dosažení těchto cílů, slouží k vytvoření kryptografických schémat kombinaci algoritmy a postupy, které jsou známé jako kryptografických primitiv. Následující tabulka uvádí kryptografických primitiva a jejich použití.  
  
|Kryptografické primitivní|Použití|  
|-----------------------------|---------|  
|Šifrování tajného klíče (symetrické šifrování)|Provádí transformaci dat zabránit jeho načítán třetích stran. Tento typ šifrování používá jediný sdílený tajný klíč k šifrování a dešifrování dat.|  
|Šifrování veřejného klíče (asymetrické šifrování)|Provádí transformaci dat zabránit jeho načítán třetích stran. Tento typ šifrování používá k šifrování a dešifrování dat pár veřejného a privátního klíče.|  
|Kryptografický podpis|Pomáhá ověřit, že data pocházejí od určité skupiny tak, že vytvoříte digitální podpis, který je jedinečný pro tuto skupinu. Tento proces také používá funkce hash.|  
|Kryptografické hodnoty hash|Mapuje dat z jakékoli délky pořadí bajtů pevnou délkou. Hodnoty hash jsou statisticky jedinečné; různé dvoubajtovou sekvenci nebude na stejnou hodnotu hash.|  
  
 [Zpět na začátek](#top)  
  
<a name="secret_key"></a>   
## <a name="secret-key-encryption"></a>Šifrování tajného klíče  
 Algoritmy šifrování tajného klíče pomocí jednoho tajný klíč k šifrování a dešifrování dat. Je nutné zabezpečit klíč z přístupu neoprávněnými agenty, protože jakékoli strany, který má klíč můžete použít k dešifrování dat nebo šifrování svá vlastní data deklaraci identity, že pochází od vás.  
  
 Šifrování tajného klíče jsou také označovány jako symetrického šifrování, protože stejný klíč se používá pro šifrování a dešifrování. Algoritmy šifrování tajného klíče jsou velmi rychlé (ve srovnání s algoritmy veřejného klíče) a je výhodné pro provedení kryptografické transformace na velkých datových proudů. Asymetrické šifrování algoritmů, například RSA jsou omezené matematicky v tom, kolik dat můžete šifrovat. Symetrický šifrovací algoritmy obvykle nemají těchto problémů.  
  
 Typ volat bloku šifrovací algoritmus tajného klíče se používá k šifrování jeden blok dat najednou. Bloky šifer, jako je například Standard DES (Data Encryption), TripleDES, a Advanced Encryption (Standard AES), kryptograficky transformují vstupní blok *n* bajtů do výstupního bloku zašifrovaných bajtů. Pokud chcete zašifrovat nebo dešifrovat sekvenci bajtů, je nutné provést blok po bloku. Protože *n* je malý (8 bajtů pro DES a TripleDES; 16 bajtů [výchozí], bajtů 24 nebo 32 bajtů pro AES), hodnot dat, které jsou větší než *n* musela být šifrovaná jeden blok v čase. Hodnot dat, které jsou menší než *n* potřeba rozšířit tak, aby *n* ke zpracování.  
  
 Jednoduché formu šifrování bloku se nazývá režim electronického (ECB). Režim ECB se nepovažuje za bezpečnou, protože nepoužívá inicializační vektor k chybě při inicializaci prvního bloku prostého textu. Pro daný tajný klíč *tisíc*, šifrovací jednoduchý blok, který nepoužívá inicializační vektor zašifruje stejný vstupní blok prostého textu do stejného bloku výstup šifrovaného textu. Proto pokud máte duplicitní bloky v datovém proudu vaše vstupní ve formátu prostého textu, bude mít duplicitní bloky ve vaší výstupního datového proudu ciphertext. Tyto duplicitní výstupní bloky výstrahy neoprávněným uživatelům slabé šifrování používá algoritmy, které byly použity a možné způsoby útoku. Režim šifrování ECB je proto velmi citlivé na analýzy a nakonec, klíče zjišťování.  
  
 Třídy šifry bloku, které jsou k dispozici v knihovně základní třída použijte výchozí řetězení režim se označuje jako bloků šifer šifer (CBC), i když toto výchozí nastavení můžete změnit, pokud chcete.  
  
 CBC šifry překonávají problémy spojené se ECB šifry s použitím inicializační vektor (IV) pro šifrování prvního bloku prostého textu. Každý další blok ve formátu prostého textu zde nevyskytlo bitový exkluzivní OR (`XOR`) operaci s předchozím blokem předtím, než je zašifrovaná. Každý blok šifrovaného textu je proto závisí na všech předchozích bloků. Při tomto systému je použit, běžné zpráva hlavičky, které může být známé neoprávněný uživatel nemůže být umožňuje provádět zpětnou analýzu klíč.  
  
 Jedním ze způsobů ohrozit data, která je šifrován CBC šifrování je vyčerpávající vyhledávání každého možného klíče. V závislosti na velikosti klíče, který se používá k šifrování tento typ vyhledávání je velmi časově náročný i nejrychlejší počítače a je proto je nemožné. Větší velikosti klíče jsou obtížnější dekódovat. I když šifrování neprovede teoreticky znemožňuje, aby nežádoucí osoba načíst šifrovaná data, zvýšit náklady na to. Pokud trvá tři měsíce provádět důkladné prohledání načíst data, která má smysl pouze pro několik dní, je důkladné prohledání metoda nepraktické.  
  
 Nevýhodou šifrování tajného klíče je, že předpokládá, že obě strany mají dohodnutou klíč a IV a oznamovat jejich hodnot. IV se nepovažuje tajného klíče se dá přenést v podobě prostého textu se zprávou. Ale klíč musí utajení před neoprávněnými uživateli. Z důvodu tyto problémy šifrování tajného klíče se často používá spolu s šifrování veřejného klíče pro hodnoty klíče a IV soukromě komunikaci.  
  
 Za předpokladu, že Alice a Bob se dvěma stranami, které chcete komunikovat přes nezabezpečený kanál, můžou používat šifrování tajného klíče následujícím způsobem: Alice a Bob souhlas s používat jeden konkrétní algoritmus (například AES) s konkrétním klíčem a IV. Alice vytvoří zprávu a vytvoří datový proud sítě (možná pojmenovaného kanálu nebo síť e-mailu), na které se mají odeslat zprávu. V dalším kroku se šifruje text pomocí klíče a IV a odešle zprávy zašifrované a IV Bobovi prostřednictvím intranetu. Robert obdrží šifrovaný text a dešifruje ji pomocí IV a dříve dohodnutého klíče. Pokud je přenos zachycen, lze sběrač nelze obnovit na původní zprávu, protože nezná klíč. V tomto scénáři musí zůstat tajný pouze klíč. Ve scénáři skutečných Alice a Bob generuje tajný klíč a šifrování veřejného klíče (asymetrického) používá k přenosu tajný klíč (symetrického) druhé straně. Další informace o šifrování veřejného klíče najdete v další části.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Obsahuje následující třídy, které implementují algoritmy šifrování tajného klíče:  
  
-   <xref:System.Security.Cryptography.AesManaged> (počínaje [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]).  
  
-   <xref:System.Security.Cryptography.DESCryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.HMACSHA1> (Toto je technicky algoritmu tajného klíče, protože představuje ověřovací kód zprávy, která se vypočítává pomocí kryptografické hodnoty hash funkce v kombinaci s tajným klíčem. V tématu [hodnoty Hash](#hash_values)dál v tomto tématu.)  
  
-   <xref:System.Security.Cryptography.RC2CryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.RijndaelManaged>.  
  
-   <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>.  
  
 [Zpět na začátek](#top)  
  
<a name="public_key"></a>   
## <a name="public-key-encryption"></a>Šifrování veřejného klíče  
 Šifrování veřejného klíče používá privátní klíč, který musí být udržovány tajný před neoprávněnými uživateli a veřejný klíč, který lze zveřejnit všem uživatelům. Veřejný klíč a soukromý klíč jsou matematicky spojeny; data, která je šifrován veřejný klíč může dešifrovat jenom s privátním klíčem a data, která je podepsaná pomocí soukromého klíče můžete ověřit pouze s veřejným klíčem. Veřejný klíč může být dostupné všem; použije se pro šifrování dat k odeslání do držitel privátní klíč. Kryptografické algoritmy veřejného klíče se také nazývají asymetrických algoritmů, protože jeden klíč je nutný pro šifrování dat a k dešifrování dat je požadován jiný klíč. Základní kryptografické pravidlo zakazuje opětovné použití klíčů a oba klíče musí být jedinečný. pro každou relaci komunikace. V praxi, jsou však obvykle dlohotrvající asymetrické klíče.  
  
 Obě strany (Alice a Bob) mohou použít šifrování veřejného klíče následujícím způsobem: nejdřív Alice generuje pár veřejného a privátního klíče. Pokud Bob chce poslat Alici šifrované zprávy, požádá ji pro svůj veřejný klíč. Alice odesílá Bobovi svůj veřejný klíč nezabezpečené síti a Bob používá tento klíč k šifrování zpráv. Šifrované zprávy: Bob pošle Alici, a Jana dešifruje ji pomocí vlastního soukromého klíče. Pokud Bob obdržel klíč Alice přes nezabezpečený kanál, jako je například veřejnou síť, Bob je otevřený pro útok man-in-the-middle. Proto musí Bob ověřit u Alice, že má správné kopie svůj veřejný klíč.  
  
 Během přenosu veřejného klíče Alice může neoprávněný agent zachytit klíč. Kromě toho stejný agent může zachytit šifrovanou zprávu od Boba. Agenta však nemůže dešifrovat zprávu s veřejným klíčem. Zpráva může dešifrovat jenom se od Alice privátní klíč, který není přenášen. Alice nepoužívá svůj privátní klíč k šifrování odpovědi Bobovi, protože každý, kdo má veřejný klíč může zprávu dešifrovat. Pokud Alice chce poslat zpět do Bob, uživatel požádá o jeho veřejný klíč Bob a šifruje své zprávy pomocí tohoto veřejný klíč. Bob poté dešifruje zprávy pomocí jeho přidružený privátní klíč.  
  
 V tomto scénáři Alice a Bob použít šifrování veřejného klíče (asymetrického) pro přenos tajný klíč (symetrického) a použít šifrování tajného klíče pro zbytek jejich relace.  
  
 Následující seznam nabízí porovnání mezi veřejného klíče a tajné klíče kryptografické algoritmy:  
  
-   Kryptografické algoritmy veřejného klíče pomocí vyrovnávací paměť pevné velikosti, zatímco kryptografické algoritmy tajný klíč používat proměnlivou délkou vyrovnávací paměti.  
  
-   Algoritmy veřejného klíče nelze použít k řetězu dat společně do datových proudů způsob, jakým může algoritmy tajného klíče, protože jenom malé množství dat mohou být šifrována. Asymetrické operace tedy nepoužívejte stejný model streamování jako symetrické operace.  
  
-   Šifrování veřejného klíče má mnohem větší keyspace (rozsahu možných hodnot pro klíč) než šifrování tajného klíče. Šifrování veřejného klíče je proto méně náchylný k vyčerpávající útoků, které každý možné zkratku vyzkoušejte.  
  
-   Veřejné klíče se dají snadno distribuovat, protože nemají být zabezpečené, za předpokladu, že existuje nějaký způsob ověření identity odesílatele.  
  
-   Některé algoritmy veřejného klíče (například RSA a DSA, ale není Diffie-Hellman) slouží k vytvoření digitálních podpisů k ověření identity odesílatele data.  
  
-   Algoritmy veřejného klíče jsou velmi pomalé ve srovnání s algoritmy tajného klíče a nejsou určeny k zašifrování velkých objemů dat. Algoritmy veřejného klíče jsou užitečné pouze pro přenos velmi malé množství dat. Šifrování veřejného klíče se obvykle používá k šifrování klíče a IV použije algoritmem tajný klíč. Po přenesení klíče a IV šifrování tajného klíče se používá pro zbytek relace.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Obsahuje následující třídy, které implementují veřejného klíče šifrovací algoritmy:  
  
-   <xref:System.Security.Cryptography.DSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.ECDiffieHellman> (základní třída)  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanCng>  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanCngPublicKey> (základní třída)  
  
-   <xref:System.Security.Cryptography.ECDiffieHellmanKeyDerivationFunction> (základní třída)  
  
-   <xref:System.Security.Cryptography.ECDsaCng>  
  
 RSA umožňuje šifrování a podepisování, ale DSA lze použít pouze pro podepisování a Diffie-Hellman lze použít pouze pro generování klíče. Obecně platí algoritmy veřejného klíče jsou více omezeny v jejich použití než algoritmy soukromého klíče.  
  
 [Zpět na začátek](#top)  
  
<a name="digital_signatures"></a>   
## <a name="digital-signatures"></a>Digitální podpisy  
 Algoritmy veřejného klíče můžete použít také pro vytvoření digitálních podpisů. Digitální podpisy ověření identity odesílatele (v případě, že důvěřujete odesílatele veřejného klíče) a chránit integritu dat. Pomocí veřejného klíče generované Alici, příjemce dat od Alice můžete ověřit, že Alice ji odeslala tak, že porovnáte digitálního podpisu dat Alice a veřejný klíč Alice.  
  
 Chcete-li digitálně podepsat zprávu pomocí veřejného klíče, Alice nejprve platí algoritmus hash pro zpráva, kterou chcete vytvořit hodnota hash. Hodnota hash je compact a jedinečný reprezentace data. Hodnota hash Alice potom šifruje s jeho privátním klíčem k vytvoření svého osobního podpisu. Po přijetí zprávy a podpisu, Bob dešifruje podpis pomocí veřejného klíče Alice obnovení hodnoty hash a hodnoty hash zprávy pomocí stejné algoritmu hash, který používá Alice. Pokud hodnota hash, kterou Bob vypočítá přesně odpovídá hodnota hash přijal od Alice, Bob jistotu, že zpráva pochází od vlastníka soukromého klíče a nezměnil data. Pokud Bob důvěřuje, že Alice je vlastník privátního klíče, ví, že zpráva byla přijata od Alice.  
  
> [!NOTE]
>  Podpis můžete ověřit pomocí každý, kdo, protože odesílatele veřejný klíč se obecné znalosti a je typicky zahrnuté ve formátu digitální podpis. Tato metoda není zachována utajení zprávy; zprávy tajné je nutné šifrovat.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Poskytuje následující třídy, které implementují algoritmy digitálního podpisu:  
  
-   <xref:System.Security.Cryptography.DSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider>  
  
-   <xref:System.Security.Cryptography.ECDsa> (základní třída)  
  
-   <xref:System.Security.Cryptography.ECDsaCng>  
  
 [Zpět na začátek](#top)  
  
<a name="hash_values"></a>   
## <a name="hash-values"></a>Hodnoty hash  
 Algoritmy hash mapování binární hodnoty o libovolné délce na menší binární hodnoty pevné délky, označuje jako hodnoty hash. Číselné vyjádření část dat je hodnota hash. Pokud hodnotu hash odstavce ve formátu prostého textu a změnit i písmeno odstavce, následná hodnota hash vytvoří jinou hodnotu. Pokud je hodnota hash kryptograficky silnou, jeho hodnota se změní výrazně. Například pokud se jeden bit zprávy změnil, silné hash funkce může způsobit výstup, který se liší o 50 procent. Může mnoho vstupní hodnoty hash na stejnou hodnotu výstup. Je však rovněž nemožné najít dva odlišné vstupy tuto hodnotu hash na stejnou hodnotu.  
  
 Obě strany (Alice a Bob) může použít k zajištění integrity zprávy funkce hash. Měli by vybrat algoritmus hash pro podepsání jejich zpráv. Alice by zapsat zprávu a pak vytvořte pomocí vybraného algoritmu hash této zprávy. Měli by pak postupovat jednu z následujících metod:  
  
-   Alice odesílá do zprávy ve formátu prostého textu a hodnotu hash zprávy (digitální podpis). Bob obdrží hashuje zprávy a porovnává hodnotu hash s hodnotou, kterou obdržel od Alice hodnotě hash. Pokud jsou hodnoty hash shodné, zpráva nebyla změněna. Pokud tyto hodnoty nebudou stejné, zpráva byla změněna po ho napsal Alice.  
  
     Tato metoda bohužel nevytváří pravost odesílatele. Každý, kdo může zosobnit Alice a odeslání zprávy do Bob. Používají stejnou algoritmus hash k podepsání své zprávy a všechny, které můžete určit Bob se, zda zpráva odpovídá jeho podpis. Toto je jednu formu útok man-in-the-middle. V tématu [NIB: Příklad zabezpečené komunikace Kryptografické služby nové generace (CNG)](https://msdn.microsoft.com/library/8048e94e-054a-417b-87c6-4f5e26710e6e) Další informace.  
  
-   Alice odešle zprávu ve formátu prostého textu Bobovi přes nezabezpečený kanál veřejné. Odešle hodnotu hash zprávy Bobovi přes zabezpečený kanál privátní. Robert obdrží zprávu ve formátu prostého textu, rozdělí a porovná součet hash k soukromě výměně hash. Pokud se klíče hash shodují, Bob ví dvě věci:  
  
    -   Zpráva nebyla změněna.  
  
    -   Odesílatel zprávy (Alice) je platná.  
  
     Pro tento systém fungovat musí Alice skrýt její původní hodnotu hash ze všech stran s výjimkami Bob.  
  
-   Alice odešle zprávu ve formátu prostého textu Bobovi přes nezabezpečený kanál veřejné a umístí hodnotu hash zprávy na jeho veřejně přístupný webový server.  
  
     Tato metoda zabraňuje zpráva manipulaci tak, že každý, kdo brání úpravy hodnoty hash. I když každý lze číst zprávy a jeho hodnota hash, hodnota hash může změnit pouze Alice. Útočník, který chce Alici zosobnit by vyžadují přístup k webovému serveru Alice.  
  
 Žádná z výše uvedených metod zabrání někdo čtení zprávy od Alice, protože jsou přenášeny ve formátu prostého textu. Úplné zabezpečení obvykle vyžaduje digitální podpisy (podepisování zpráv) a šifrování.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Obsahuje následující třídy, které implementují algoritmy hash:  
  
-   <xref:System.Security.Cryptography.HMACSHA1>.  
  
-   <xref:System.Security.Cryptography.MACTripleDES>.  
  
-   <xref:System.Security.Cryptography.MD5CryptoServiceProvider>.  
  
-   <xref:System.Security.Cryptography.RIPEMD160>.  
  
-   <xref:System.Security.Cryptography.SHA1Managed>.  
  
-   <xref:System.Security.Cryptography.SHA256Managed>.  
  
-   <xref:System.Security.Cryptography.SHA384Managed>.  
  
-   <xref:System.Security.Cryptography.SHA512Managed>.  
  
-   Varianty HMAC všech algoritmů Secure Hash Algorithm (SHA), Message Digest 5 (MD5) a RIPEMD-160.  
  
-   CryptoServiceProvider implementace všechny algoritmy SHA (spravovaný kód obálky).  
  
-   Cryptography Next Generation (CNG) implementace všech algoritmů MD5 a SHA.  
  
> [!NOTE]
>  V 1996 byly zjištěny chyby návrhu MD5 a SHA-1 se doporučuje místo toho. V 2004 byly zjištěny další chyby a algoritmus MD5 je už považované za bezpečné. Algoritmus SHA-1 také byl nalezen nejsou zabezpečené a SHA-2 je nyní vhodné místo.  
  
 [Zpět na začátek](#top)  
  
<a name="random_numbers"></a>   
## <a name="random-number-generation"></a>Náhodné generování čísel  
 Náhodné generování čísel je nedílnou součástí mnoho kryptografických operací. Například kryptografické klíče musí být jako náhodné nejblíže tak, aby se reprodukovat. Kryptografické generátory náhodných čísel musí generovat výstup, který je rovněž neumožňuje předpovědět pravděpodobnost, že je lepší, než polovinu. Proto jakákoli metoda předpovědi dalšího výstupního bitu nesmí provádět lepší než náhodné hádání. Třídy v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] používají generátory náhodných čísel ke generování šifrovacích klíčů.  
  
 <xref:System.Security.Cryptography.RNGCryptoServiceProvider> Třída je implementací algoritmu generátoru náhodných čísel.  
  
 [Zpět na začátek](#top)  
  
<a name="clickonce"></a>   
## <a name="clickonce-manifests"></a>Manifesty ClickOnce  
 V [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], následující třídy kryptografie umožňují získat a ověřte informace o podpisech manifestu pro aplikace, které jsou nasazeny pomocí [technologie ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment):  
  
-   <xref:System.Security.Cryptography.ManifestSignatureInformation> Třída získává informace o podpisu manifestu při použití jeho <xref:System.Security.Cryptography.ManifestSignatureInformation.VerifySignature%2A> přetížení metody.  
  
-   Můžete použít <xref:System.Security.ManifestKinds> výčtu k určení, které manifesty ověření. Výsledek ověřování je jedním z <xref:System.Security.Cryptography.SignatureVerificationResult> hodnot výčtu.  
  
-   <xref:System.Security.Cryptography.ManifestSignatureInformationCollection> Třída poskytuje kolekci jen pro čtení <xref:System.Security.Cryptography.ManifestSignatureInformation> objekty ověřených podpisů.  
  
 Kromě toho následující třídy poskytují informace o konkrétní podpisu:  
  
-   <xref:System.Security.Cryptography.StrongNameSignatureInformation> Obsahuje informace o podpis silného názvu pro manifest.  
  
-   <xref:System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation> představuje informace o podpisu Authenticode pro manifest.  
  
-   <xref:System.Security.Cryptography.X509Certificates.TimestampInformation> obsahuje informace o časového razítka na podpis Authenticode.  
  
-   <xref:System.Security.Cryptography.X509Certificates.TrustStatus> poskytuje jednoduchý způsob, jak zkontrolovat, zda je důvěryhodný podpis Authenticode.  
  
 [Zpět na začátek](#top)  
  
<a name="suite_b"></a>   
## <a name="suite-b-support"></a>Podpora standardu Suite B  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Podporuje sady Suite B kryptografických algoritmů, které jsou publikovány National zabezpečení agentura (NSA). Další informace o Suite B, najdete v článku [NSA Suite B Cryptography fakt Sheet](https://www.nsa.gov/what-we-do/information-assurance/).  
  
 Zahrnují se tyto algoritmy:  
  
-   Rozšířené algoritmus standardu šifrování (AES) s velikostí klíče 128, 192, a 256 bitů pro šifrování.  
  
-   Zabezpečené algoritmy Hash SHA-1, SHA-256, SHA-384 a SHA-512 pro použití algoritmu hash. (Poslední tři jsou obecně seskupeny dohromady a označovat jako SHA-2.)  
  
-   Eliptické křivky digitální podpis algoritmus (ECDSA), pomocí křivek 256 bitů, 384 bitů a bitů 521 521bitů primárního modulu pro podepisování. Dokumentace NSA konkrétně definuje tyto křivky a je volá p-256, 384 a 521. Tento algoritmus je poskytován <xref:System.Security.Cryptography.ECDsaCng> třídy. Umožňuje přihlásit s privátním klíčem a ověřit podpis pomocí veřejného klíče.  
  
-   Elliptic Curve Diffie-Hellman (ECDH) algoritmus pomocí křivek 256 bitů, 384 bitů a bitů 521 521bitů primárního modulu pro výměnu klíčů a tajnou dohodu. Tento algoritmus je poskytován <xref:System.Security.Cryptography.ECDiffieHellmanCng> třídy.  
  
 Obálky spravovaného kódu pro Federal Information Processing Standard (FIPS) certifikované implementace AES, SHA-256, SHA-384 a SHA-512 jsou k dispozici v nové <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.SHA256CryptoServiceProvider>, <xref:System.Security.Cryptography.SHA384CryptoServiceProvider>, a <xref:System.Security.Cryptography.SHA512CryptoServiceProvider> třídy.  
  
 [Zpět na začátek](#top)  
  
<a name="cng"></a>   
## <a name="cryptography-next-generation-cng-classes"></a>Další nové generace (CNG) třídy šifrování  
 Třídy Kryptografické služby nové generace (CNG) poskytují spravovanou obálku kolem nativních funkcí CNG. (CNG je náhradou rozhraní CryptoAPI.) Tyto třídy mají "Cng" jako součást jejich názvy. Centrální pro obálky tříd CNG je <xref:System.Security.Cryptography.CngKey> třída kontejneru, která abstrahuje úložiště a použití klíčů CNG klíčů. Tato třída umožňuje bezpečně uložit pár klíčů nebo veřejný klíč a na ni odkazuje pomocí jednoduchého řetězec názvu. Na eliptické křivky mohutnosti na základě <xref:System.Security.Cryptography.ECDsaCng> podpis – třída a <xref:System.Security.Cryptography.ECDiffieHellmanCng> šifrování třídu můžete použít <xref:System.Security.Cryptography.CngKey> objekty.  
  
 <xref:System.Security.Cryptography.CngKey> Třída se používá pro celou řadu dalších operací, včetně otevírání, vytváření, odstraňování a export klíčů. Také poskytuje přístup k podkladové popisovač klíče pro použití při volání nativních funkcí přímo.  
  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Také zahrnuje celou řadu pomocných tříd CNG, jako jsou následující:  
  
-   <xref:System.Security.Cryptography.CngProvider> udržuje zprostředkovatele úložiště klíčů.  
  
-   <xref:System.Security.Cryptography.CngAlgorithm> udržuje CNG algoritmus.  
  
-   <xref:System.Security.Cryptography.CngProperty> udržuje často používané vlastnosti klíče.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Kryptografický model](../../../docs/standard/security/cryptography-model.md)|Popisuje způsob implementace kryptografie v knihovně základní třídy.|  
|[Návod: Vytvoření šifrovací aplikace](../../../docs/standard/security/walkthrough-creating-a-cryptographic-application.md)|Ukazuje základní úlohy šifrování a dešifrování.|  
|[Konfigurace šifrovacích tříd](../../../docs/framework/configure-apps/configure-cryptography-classes.md)|Popisuje, jak k mapování názvů algoritmů na třídy kryptografických a mapování identifikátorů objektů kryptografickým algoritmům.|
