---
title: Ohrožení zabezpečení časování u symetrického dešifrování pomocí odsazení v režimu CBC
description: Zjistěte, jak k detekování a zmírnění chyby zabezpečení časování s Cipher Block Chaining CBC () režim Symetrické dešifrování pomocí odsazení.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 6d8c2593cdbc4bbff2b1507196989282b16aa9a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933897"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Ohrožení zabezpečení časování u symetrického dešifrování pomocí odsazení v režimu CBC

Společnost Microsoft věří, že už nejsou bezpečné dešifrovat data zašifrovaná pomocí šifrování se symetrickým režim Cipher Block Chaining CBC (), při použití ověřitelných odsazení bez první zajištění integrity šifrovaného textu, s výjimkou specifickou okolnosti. Toto posouzení podle aktuálně známé kryptografickém výzkumu. 

## <a name="introduction"></a>Úvod

Útok odsazení oracle je typ útoku proti šifrovaná data, která umožňuje útočníkovi dešifrovat obsah dat, bez znalosti klíč.

Oracle odkazuje "říct" které poskytuje útočník informace o tom, zda je akce, kterou správné nebo ne. Imagine přehrávání panelu nebo karet hry s podřízeným. Když své pro rozpoznávání tváře aktivuje emotikonami velké objemy vzhledem k tomu, že Jana domnívá, že je o aby dobré přesunu, je oracle. Jako protihráč, vám pomůže tento oracle další přesunout odpovídající plán.

Výplň je konkrétní kryptografických období. Některé šifry, které jsou algoritmy používané k šifrování dat, pracovat na bloky dat, ve kterém je každý blok s pevnou velikostí. Není-li data, která chcete šifrovat správnou velikost tak, aby vyplnil bloky, vaše data doplněno, dokud se provádí. Mnoho forem odsazení vyžadují tento odsazení vždy mít k dispozici, i když původní vstup není vhodné velikosti. To umožňuje odsazení vždy bezpečně odebrat po dešifrování.

Sestavení dvě věci, implementaci softwaru se společností oracle odsazení zjistí, zda dešifrovaná data mají platný odsazení. Oracle může být jednoduše vrací hodnotu, která říká "Neplatný odsazení" něco nebo složitější jako trvá zlepšení života na zemi jiný čas ke zpracování platný blok na rozdíl od neplatný blok.

Blokový šifry mají jiné vlastnosti volá režimu, který určuje vztah data v první blok dat v druhé blok, a tak dále. Jednou z nejčastěji používaných režimech je CBC. CBC představuje počáteční náhodných blokovat, známé jako inicializační vektor (IV) a kombinuje předchozí blok s výsledkem statické šifrování, aby ho tak, aby šifrování stejná zpráva se stejným klíčem není vždy vytvořila stejný výstup šifrované.

Útočník může použít odsazení oracle, v kombinaci s jak CBC data strukturovaná, odesílat zprávy o něco změněné kódu, který zpřístupňuje oracle a posílat data, dokud oracle dozví se, je správná data. Z odpovědi může útočník dešifrování zprávy bajt po bajtu.

Moderní počítačových sítí jsou tyto vysoce kvalitní, že útočník může zjistit, velmi malý (méně než 0,1 ms) rozdíly v provádění čas na vzdálených systémů. Aplikace, které jsou za předpokladu, že úspěšná dešifrování může dojít pouze v případě dat nebylo manipulováno se může být zranitelný vůči útokům z nástrojů, které jsou určeny k sledujte rozdíly v úspěšné a neúspěšné dešifrování. Tento rozdíl časování může být v některých jazycích a knihovnách mnohem závažnější než jiné, je nyní předpokládá, že toto je praktické před internetovými útoky pro všechny jazyky a knihovny, když je aplikace odpovědi na chybu vzít v úvahu.

Tento útok spoléhá na schopnost změnit šifrovaná data a výsledek s oracle testu. Jediný způsob, jak plně zmírnění tohoto útoku je zjištění změn k šifrovaným datům a provádět všechny akce na něm odmítnout. K vytvoření podpisu pro data a ověřit podpis před provedením jakékoli operace, které je standardní způsob. Podpis musí být možné ověřit, nemůže být vytvořen uživatelem zlými úmysly, jinak, by přejít šifrovaná data, a potom compute nový podpis podle změněná data. Jeden běžný typ odpovídajícím podpisem se označuje jako ověřovací kód zprávy s klíči hash (metoda HMAC). V tom, že trvá tajný klíč známý jenom na osobu, vytváření HMAC a osobě, ověřování, se liší od kontrolní součet kódu HMAC s. Bez vlastnictví klíče nejde produkovat správné HMAC. Když se zobrazí vaše data, by trvat šifrovaná data, jste a sdílené složky odesílatele, a pak porovnat HMAC odeslali proti ten je vypočítán nezávisle na sobě výpočetní HMAC pomocí tajného klíče. Toto porovnání musí být konstantní čas, jinak jste přidali další zjistitelná oracle, povolení jiného typu útoku.

Stručně řečeno používat, aby bylo vytvořeno CBC blokové šifry bezpečně, musí je zkombinovat s kódu HMAC s (nebo další kontrolu integrity dat), které ověřit pomocí porovnání konstantním času než to zkusíte data dešifrovat. Protože všechny změněné zprávy čekat na stejné množství vytvořilo odpověď, je zabráněno útoku.

## <a name="who-is-vulnerable"></a>Kdo je ohrožené

Toto ohrožení zabezpečení platí pro spravovaný i nativní aplikace, které provádějí své vlastní šifrování a dešifrování. To zahrnuje, například:

- Aplikace, která se zašifruje do souboru cookie pro pozdější dešifrování na serveru.
- Databázové aplikace, která poskytuje možnost uživatelů k vložení dat do tabulky, jejichž sloupce se dešifrují později.
- Aplikace pro přenos dat, která spoléhá na šifrování pomocí sdíleného klíče k ochraně dat během přenosu.
- Aplikace, která šifruje a dešifruje zprávy "vnitřní" tunelu TLS.

Všimněte si, že použití protokolu TLS samostatně nemůže chránit v těchto scénářích.

Ohrožené aplikace:

- Dešifruje data pomocí režimu CBC šifrování s režimem ověřitelný odsazení, jako je například ve formátu PKCS #7 nebo ANSI X.923.
- Provede dešifrování bez nutnosti provést kontrolu integrity dat (prostřednictvím MACU nebo asymetrický digitální podpis).

To platí i pro aplikace založené na abstrakce přes horní těchto primitivních hodnot, jako je například struktura EnvelopedData Cryptographic Message Syntax (PKCS #7/CMS).

## <a name="related-areas-of-concern"></a>Související oblastí zájmu

Výzkum vedlo Microsoft dále se starat o CBC zprávy, které jsou doplněny ISO 10126-ekvivalentem odsazení, když zpráva obsahuje strukturu dobře známé nebo předvídatelný zápatí. Například obsah připravený v části pravidla syntaxe W3C XML šifrování a zpracování doporučení (xmlenc EncryptedXml). Při W3C pokyny k podepisování zpráv pak šifrování považovaná za vhodné v době, doporučuje Microsoft teď vždy provádění šifrování přihlášení pak.

Vývojáři aplikací by měl vždy dávejte ověřovat použitelnost asymetrického podpisu klíče, protože není žádná vlastní důvěryhodný vztah mezi asymetrický klíč a libovolného zprávy.

## <a name="details"></a>Podrobnosti

V minulosti došlo shody, které jsou důležité k šifrování i ověřování důležitých dat, prostředky, jako jsou podpisy HMAC nebo RSA. Má však bylo méně jasné pokyny o tom, jak pořadí operace šifrování a ověřování. Z důvodu chyby podrobně popsané v tomto článku pokyny od Microsoftu je teď vždy používejte paradigma "šifrování then znak". To znamená nejdřív šifrování dat s využitím symetrický klíč a potom výpočetní MAC nebo asymetrického podpisu přes šifrovaného textu (šifrovaná data). Při dešifrování dat, proveďte opačně. Nejprve potvrdit MAC nebo podpis šifrovaného textu a pak ho dešifrovat.

Třída chyby zabezpečení označované jako "padding oracle útoky" označuje existovat více než deset let. Tyto chyby útočníkovi umožnit dešifrovat data zašifrovaná pomocí bloku symetrické algoritmy, například AES a 3DES pomocí více než 4096 pokusů na jednoho datového bloku. Ujistěte se, tyto nedostatky zabezpečení použijte skutečnost, že block šifer se nejčastěji používají s daty ověřitelný odsazení na konci. Bylo zjištěno, že pokud útočník lze manipulovat s šifrovaného textu a zjistěte, zda úmyslné poškozování způsobilo chybu ve formátu odsazení na konci, útočník může data dešifrovat.

Na začátku praktické útoky jsou založené na službách, které vrátí různé chybové kódy na základě na, jestli byl platný, jako je například Chyba zabezpečení technologie ASP.NET odsazení [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070). Společnost Microsoft však nyní věří, že je potřeba provést podobné útoky pomocí pouze rozdíly mezi časování mezi zpracování platný a neplatný odsazení.

Za předpokladu, že podpis používá schéma šifrování a ověření podpisu se provádí s pevnou modul runtime pro danou délku dat (bez ohledu na obsah), můžete ověřit integritu dat bez generování žádné informace Útočník prostřednictvím [kanál ze strany](https://en.wikipedia.org/wiki/Side-channel_attack). Protože kontroly integrity odmítne všechny zmanipulovanou zprávy, je zmírnit hrozby oracle odsazení.

## <a name="guidance"></a>Doprovodné materiály

Především společnost Microsoft doporučuje, aby všechna data, která má důvěrnost musí přenášet přes zabezpečení TLS (Transport Layer), nástupce do vrstvy SSL (Secure Sockets).

Dále analyzujte aplikaci:

- Pochopení přesně jaké při provádění šifrování a se zajišťuje šifrování, jaké platformy a rozhraní API používáte.
- Být jisti, že každé použití na každé úrovni symetrický [algoritmus šifrování bloku](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), jako je AES a 3DES v režimu CBC začlenit použijte kontrolu integrity dat s klíči tajný klíč (asymetrického podpisu HMAC, nebo chcete-li změnit režim šifrování pro [ověření šifrování](https://en.wikipedia.org/wiki/Authenticated_encryption) režimu (AE), jako jsou GCM nebo CCM).

Podle současných výzkumů, obecně předpokládá se, že při ověřování a šifrování kroky jsou provedeny nezávisle pro jiné AE režimy šifrování, ověřování šifrovaný text (šifrování then znaménko) je nejlepší obecných možností. Však neexistuje žádná přitom správnou odpověď kryptografie a této generalizaci není tak dobré, jako řízené Rady od profesionální cryptographer.

Aplikace, které nelze změnit jejich formát zasílání zpráv, ale neověřené dešifrování CBC se doporučuje pro pokus o začlenit způsoby zmírnění rizik, jako:

- Dešifrování bez povolení-li ověřit nebo odebrat odsazení:
  - Žádné odsazení, které byly použity stále je potřeba odebrat nebo ignorovat, přesouváte zatížení do vaší aplikace.
  - Výhoda spočívá v odsazení ověření a odebrání může být zahrnut do další logiku ověření dat aplikace. Pokud odsazení ověření a ověření dat můžete udělat v konstantním času, se snižuje hrozby.
  - Protože délka zjištěné zprávy se změní výklad odsazení, stále informace možná budou časování vyzařováno tento přístup.
- Změňte režim odsazení dešifrování na ISO10126:
  - Odsazení dešifrování ISO10126 je kompatibilní s PKCS7 šifrování odsazení a ANSIX923 šifrování odsazení.
  - Změna režimu snižuje ve znalostní bázi oracle odsazení 1 bajt místo celý blok. Ale pokud má obsah dobře známé zápatí, jako je znak pravé – element XML, útoky související můžete dál k útoku na zbytek zprávy.
  - To také nezabrání obnovení ve formátu prostého textu v situacích, kde může útočník vynucení stejné jako prostý text s posunem jiná zpráva šifrování více než jednou.
- Brána vyhodnocení volání dešifrování Ztlumit signál časování:
  - Výpočet doby uchování musí být minimálně nad rámec maximální množství času, které by pro datový segment, který obsahuje odsazení provést operaci dešifrování.
  - Čas výpočty by mělo být provedeno podle pokynů v [získávání ve vysokém rozlišení časová razítka](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), nikoli pomocí <xref:System.Environment.TickCount?displayProperty=nameWithType> (v souladu s vrácení over nebo přetečení) nebo odečtení dvou časová razítka systému (v souladu s úpravy NTP chyby).
  - Výpočty čas musí být včetně dešifrovací operace, včetně všechny potenciální výjimky spravované nebo aplikací v jazyce C++, nikoli pouze, aby bylo vytvořeno na konci.
  - Pokud úspěch nebo neúspěch byla zjištěna ještě, brána časování je potřeba při jeho platnost vyprší, vrátí hodnotu neúspěch.
- Služby, které provádějí neověřené dešifrování by měl mít nastavené ke zjištění, že má větší "neplatné" zprávy pocházejí monitorování.
  - Berte v úvahu, že tento signál představuje počet falešně pozitivních výsledků (oprávněně poškozená data) i falešně negativní (šíření útoku přes obejít zjišťování dostatečně dlouho).

## <a name="finding-vulnerable-code---native-applications"></a>Hledání zranitelné kód – nativní aplikace

Pro programy vytvořena šifrování Windows: Další knihovny služby nové generace (CNG):

- Volání dešifrování [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), zadání `BCRYPT_BLOCK_PADDING` příznak.
- Popisovač klíče byl inicializován pomocí volání [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) s [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) nastavena na `BCRYPT_CHAIN_MODE_CBC`.
  - Protože `BCRYPT_CHAIN_MODE_CBC` je výchozí nastavení, která měla vliv na kód nemusí mít přiřazené libovolnou hodnotu pro `BCRYPT_CHAINING_MODE`.

Pro programy vytvořené starší kryptografické rozhraní API Windows:

- Volání dešifrování [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) s `Final=TRUE`.
- Popisovač klíče byl inicializován pomocí volání [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) s [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) nastavena na `CRYPT_MODE_CBC`.
  - Protože `CRYPT_MODE_CBC` je výchozí nastavení, která měla vliv na kód nemusí mít přiřazené libovolnou hodnotu pro `KP_MODE`.

## <a name="finding-vulnerable-code---managed-applications"></a>Hledání kódu zranitelné – spravované aplikace

- Dešifrování volání <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> nebo <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> metody <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.
  - To zahrnuje následující odvozené typy v .NET, ale může také obsahovat typy třetích stran:
    - <xref:System.Security.Cryptography.Aes>
    - <xref:System.Security.Cryptography.AesCng>
    - <xref:System.Security.Cryptography.AesCryptoServiceProvider>
    - <xref:System.Security.Cryptography.AesManaged>
    - <xref:System.Security.Cryptography.DES>
    - <xref:System.Security.Cryptography.DESCryptoServiceProvider>
    - <xref:System.Security.Cryptography.RC2>
    - <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
    - <xref:System.Security.Cryptography.Rijndael>
    - <xref:System.Security.Cryptography.RijndaelManaged>
    - <xref:System.Security.Cryptography.TripleDES>
    - <xref:System.Security.Cryptography.TripleDESCng>
    - <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> Nastavenou na <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, nebo <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Protože <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> je výchozí nastavení, která měla vliv na kód může být nikdy přiřazena <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> vlastnost.
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> Nastavenou na <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Protože <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> je výchozí nastavení, která měla vliv na kód může být nikdy přiřazena <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> vlastnost.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Hledání zranitelné kód – syntaxe kryptografické zprávy

Neověřená zpráva CMS EnvelopedData jehož šifrovaný obsah používá režimu CBC AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), (1.3.14.3.2.7) DES, 3DES (1.2.840.113549.3.7) nebo RC2 (1.2.840.113549.3.2) je ohrožené, stejně jako zprávy použití jakékoli jiné algoritmy šifrování bloku v režimu CBC.

Při šifrování datového proudu nejsou náchylný k této konkrétní chyby, společnost Microsoft doporučuje vždy ověřování přes kontrola ContentEncryptionAlgorithm hodnotu data.

Pro spravované aplikace CMS EnvelopedData objekt blob může být zjištěny jako libovolnou hodnotu, která je předána <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.

U nativních aplikací lze zjistit CMS EnvelopedData blob jako libovolná hodnota zadaná pro zpracování CMS prostřednictvím [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) jehož výsledný [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) je `CMSG_ENVELOPED` nebo je popisovač CMS dále odeslané `CMSG_CTRL_DECRYPT` instrukce prostřednictvím [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).

## <a name="vulnerable-code-example---managed"></a>Příklad kódu zranitelné – spravované

Tato metoda načte soubor cookie a dešifruje ji a není žádná kontrola integrity dat je viditelný. Obsah souboru cookie, který je pro čtení touto metodou proto může útoku, uživatel, který přijal nebo útočník, který získal hodnotu zašifrovaného souboru cookie.

```csharp
private byte[] DecryptCookie(string cookieName)
{
    HttpCookie cookie = Request.Cookies[cookieName];

    if (cookie == null)
    {
        return null;
    }

    using (ICryptoTransform decryptor = _aes.CreateDecryptor())
    using (MemoryStream memoryStream = new MemoryStream())
    using (CryptoStream cryptoStream =
        new CryptoStream(memoryStream, decryptor, CryptoStreamMode.Write))
    {
        byte[] readCookie = Convert.FromBase64String(cookie.Value);
        cryptoStream.Write(readCookie, 0, readCookie.Length);
        cryptoStream.FlushFinalBlock();
        return memoryStream.ToArray();
    }
}
```

## <a name="example-code-following-recommended-practices---managed"></a>Následující příklad kódu doporučené postupy – spravované

Následující vzorový kód používá formát nestandardní zprávy z

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

kde `cipher_algorithm_id` a `hmac_algorithm_id` algoritmus identifikátory jsou místní aplikace (nestandardní) reprezentace tyto algoritmy. Tyto identifikátory může dávat smysl v ostatních částech existující protokol zasílání zpráv, nikoli jako úplné zřetězených bytestream

Tento příklad také používá jeden hlavní klíč k odvození šifrovací klíč a klíčem HMAC. To i v zájmu usnadnění práce poskytuje při zapínání jednotlivě označenými aplikace do aplikace s klíči duální a povzbudit udržování dva klíče jako různé hodnoty. Další zaručuje, že klíčem HMAC a šifrovacího klíče nelze získat synchronizována.

Tato ukázka nepřijme <xref:System.IO.Stream> pro šifrování nebo dešifrování. Aktuální využívá formát data jednofázové šifrování obtížné protože `hmac_tag` hodnota předchází šifrovaného textu. Tento formát však byla vybrána, protože všechny prvky pevné velikosti udržuje na začátek jednodušší zajistit analyzátor. V tomto formátu dat je možné, jednofázové dešifrovat, ačkoli implementátora se zobrazí se upozornění GetHashAndReset volání a ověření výsledku před voláním TransformFinalBlock. Streamování šifrování je důležité, jiný režim AE může být vyžadováno.

```csharp
// ==++==
//
//   Copyright (c) Microsoft Corporation.  All rights reserved.
//
//   Shared under the terms of the Microsoft Public License,
//   https://opensource.org/licenses/MS-PL
//
// ==--==

using System;
using System.Diagnostics;
using System.IO;
using System.Runtime.CompilerServices;
using System.Security.Cryptography;

namespace Microsoft.Examples.Cryptography
{
    public enum AeCipher : byte
    {
        Unknown,
        Aes256CbcPkcs7,
    }

    public enum AeMac : byte
    {
        Unknown,
        HMACSHA256,
        HMACSHA384,
    }

    /// <summary>
    /// Provides extension methods to make HashAlgorithm look like .NET Core's
    /// IncrementalHash
    /// </summary>
    internal static class IncrementalHashExtensions
    {
        public static void AppendData(this HashAlgorithm hash, byte[] data)
        {
            hash.TransformBlock(data, 0, data.Length, null, 0);
        }

        public static void AppendData(
            this HashAlgorithm hash,
            byte[] data,
            int offset,
            int length)
        {
            hash.TransformBlock(data, offset, length, null, 0);
        }

        public static byte[] GetHashAndReset(this HashAlgorithm hash)
        {
            hash.TransformFinalBlock(Array.Empty<byte>(), 0, 0);
            return hash.Hash;
        }
    }

    public static partial class AuthenticatedEncryption
    {
        /// <summary>
        /// Use <paramref name="masterKey"/> to derive two keys (one cipher, one HMAC)
        /// to provide authenticated encryption for <paramref name="message"/>.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="message">The message to encrypt</param>
        /// <returns>
        /// A concatenation of
        /// [cipher algorithm+chainmode+padding][mac algorithm][authtag][IV][ciphertext],
        /// suitable to be passed to <see cref="Decrypt"/>.
        /// </returns>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or bigger) value generated
        /// by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>.
        /// This implementation chooses to block deficient inputs by length, but does not
        /// make any attempt at discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase)
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Encrypt(byte[] masterKey, byte[] message)
        {
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (message == null)
                throw new ArgumentNullException(nameof(message));

            // First, choose an encryption scheme.
            AeCipher aeCipher = AeCipher.Aes256CbcPkcs7;

            // Second, choose an authentication (message integrity) scheme.
            //
            // In this example we use the master key length to change from HMACSHA256 to
            // HMACSHA384, but that is completely arbitrary. This mostly represents a
            // "cryptographic needs change over time" scenario.
            AeMac aeMac = masterKey.Length < 48 ? AeMac.HMACSHA256 : AeMac.HMACSHA384;

            // It's good to be able to identify what choices were made when a message was
            // encrypted, so that the message can later be decrypted. This allows for
            // future versions to add support for new encryption schemes, but still be
            // able to read old data. A practice known as "cryptographic agility".
            //
            // This is similar in practice to PKCS#7 messaging, but this uses a
            // private-scoped byte rather than a public-scoped Object IDentifier (OID).
            // Please note that the scheme in this example adheres to no particular
            // standard, and is unlikely to survive to a more complete implementation in
            // the .NET Framework.
            //
            // You may be well-served by prepending a version number byte to this
            // message, but may want to avoid the value 0x30 (the leading byte value for
            // DER-encoded structures such as X.509 certificates and PKCS#7 messages).
            byte[] algorithmChoices = { (byte)aeCipher, (byte)aeMac };
            byte[] iv;
            byte[] cipherText;
            byte[] tag;

            // Using our algorithm choices, open an HMAC (as an authentication tag
            // generator) and a SymmetricAlgorithm which use different keys each derived
            // from the same master key.
            //
            // A custom implementation may very well have distinctly managed secret keys
            // for the MAC and cipher, this example merely demonstrates the master to
            // derived key methodology to encourage key separation from the MAC and
            // cipher keys.
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
                using (ICryptoTransform encryptor = cipher.CreateEncryptor())
                {
                    // Since no IV was provided, a random one has been generated
                    // during the call to CreateEncryptor.
                    //
                    // But note that it only does the auto-generation once. If the cipher
                    // object were used again, a call to GenerateIV would have been
                    // required.
                    iv = cipher.IV;

                    cipherText = Transform(encryptor, message, 0, message.Length);
                }

                // The IV and ciphertest both need to be included in the MAC to prevent
                // tampering.
                //
                // By including the algorithm identifiers, we have technically moved from
                // simple Authenticated Encryption (AE) to Authenticated Encryption with
                // Additional Data (AEAD). By including the algorithm identifiers in the
                // MAC, it becomes harder for an attacker to change them as an attempt to
                // perform a downgrade attack.
                //
                // If you've added a data format version field, it can also be included
                // in the MAC to further inhibit an attacker's options for confusing the
                // data processor into believing the tampered message is valid.
                tagGenerator.AppendData(algorithmChoices);
                tagGenerator.AppendData(iv);
                tagGenerator.AppendData(cipherText);
                tag = tagGenerator.GetHashAndReset();
            }

            // Build the final result as the concatenation of everything except the keys.
            int totalLength =
                algorithmChoices.Length +
                tag.Length +
                iv.Length +
                cipherText.Length;

            byte[] output = new byte[totalLength];
            int outputOffset = 0;

            Append(algorithmChoices, output, ref outputOffset);
            Append(tag, output, ref outputOffset);
            Append(iv, output, ref outputOffset);
            Append(cipherText, output, ref outputOffset);

            Debug.Assert(outputOffset == output.Length);
            return output;
        }

        /// <summary>
        /// Reads a message produced by <see cref="Encrypt"/> after verifying it hasn't
        /// been tampered with.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="cipherText">
        /// The output of <see cref="Encrypt"/>: a concatenation of a cipher ID, mac ID,
        /// authTag, IV, and cipherText.
        /// </param>
        /// <returns>The decrypted content.</returns>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="masterKey"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="cipherText"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="CryptographicException">
        /// <paramref name="cipherText"/> identifies unknown algorithms, is not long
        /// enough, fails a data integrity check, or fails to decrypt.
        /// </exception>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or larger) value
        /// generated by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>. This implementation chooses to
        /// block deficient inputs by length, but doesn't make any attempt at
        /// discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase),
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Decrypt(byte[] masterKey, byte[] cipherText)
        {
            // This example continues the .NET practice of throwing exceptions for
            // failures. If you consider message tampering to be normal (and thus
            // "not exceptional") behavior, you may like the signature
            // bool Decrypt(byte[] messageKey, byte[] cipherText, out byte[] message)
            // better.
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (cipherText == null)
                throw new ArgumentNullException(nameof(cipherText));

            // The format of this message is assumed to be public, so there's no harm in
            // saying ahead of time that the message makes no sense.
            if (cipherText.Length < 2)
            {
                throw new CryptographicException();
            }

            // Use the message algorithm headers to determine what cipher algorithm and
            // MAC algorithm are going to be used. Since the same Key Derivation
            // Functions (KDFs) are being used in Decrypt as Encrypt, the keys are also
            // the same.
            AeCipher aeCipher = (AeCipher)cipherText[0];
            AeMac aeMac = (AeMac)cipherText[1];

            using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                int blockSizeInBytes = cipher.BlockSize / 8;
                int tagSizeInBytes = tagGenerator.HashSize / 8;
                int headerSizeInBytes = 2;
                int tagOffset = headerSizeInBytes;
                int ivOffset = tagOffset + tagSizeInBytes;
                int cipherTextOffset = ivOffset + blockSizeInBytes;
                int cipherTextLength = cipherText.Length - cipherTextOffset;
                int minLen = cipherTextOffset + blockSizeInBytes;

                // Again, the minimum length is still assumed to be public knowledge,
                // nothing has leaked out yet. The minimum length couldn't just be calculated
                // without reading the header.
                if (cipherText.Length < minLen)
                {
                    throw new CryptographicException();
                }

                // It's very important that the MAC be calculated and verified before
                // proceeding to decrypt the ciphertext, as this prevents any sort of
                // information leaking out to an attacker.
                //
                // Don't include the tag in the calculation, though.

                // First, everything before the tag (the cipher and MAC algorithm ids)
                tagGenerator.AppendData(cipherText, 0, tagOffset);

                // Skip the data before the tag and the tag, then read everything that
                // remains.
                tagGenerator.AppendData(
                    cipherText,
                    tagOffset + tagSizeInBytes,
                    cipherText.Length - tagSizeInBytes - tagOffset);

                byte[] generatedTag = tagGenerator.GetHashAndReset();

                // The time it took to get to this point has so far been a function only
                // of the length of the data, or of non-encrypted values (e.g. it could
                // take longer to prepare the *key* for the HMACSHA384 MAC than the
                // HMACSHA256 MAC, but the algorithm choice wasn't a secret).
                //
                // If the verification of the authentication tag aborts as soon as a
                // difference is found in the byte arrays then your program may be
                // acting as a timing oracle which helps an attacker to brute-force the
                // right answer for the MAC. So, it's very important that every possible
                // "no" (2^256-1 of them for HMACSHA256) be evaluated in as close to the
                // same amount of time as possible. For this, we call CryptographicEquals
                if (!CryptographicEquals(
                    generatedTag,
                    0,
                    cipherText,
                    tagOffset,
                    tagSizeInBytes))
                {
                    // Assuming every tampered message (of the same length) took the same
                    // amount of time to process, we can now safely say
                    // "this data makes no sense" without giving anything away.
                    throw new CryptographicException();
                }

                // Restore the IV into the symmetricAlgorithm instance.
                byte[] iv = new byte[blockSizeInBytes];
                Buffer.BlockCopy(cipherText, ivOffset, iv, 0, iv.Length);
                cipher.IV = iv;

                using (ICryptoTransform decryptor = cipher.CreateDecryptor())
                {
                    return Transform(
                        decryptor,
                        cipherText,
                        cipherTextOffset,
                        cipherTextLength);
                }
            }
        }

        private static byte[] Transform(
            ICryptoTransform transform,
            byte[] input,
            int inputOffset,
            int inputLength)
        {
            // Many of the implementations of ICryptoTransform report true for
            // CanTransformMultipleBlocks, and when the entire message is available in
            // one shot this saves on the allocation of the CryptoStream and the
            // intermediate structures it needs to properly chunk the message into blocks
            // (since the underlying stream won't always return the number of bytes
            // needed).
            if (transform.CanTransformMultipleBlocks)
            {
                return transform.TransformFinalBlock(input, inputOffset, inputLength);
            }

            // If our transform couldn't do multiple blocks at once, let CryptoStream
            // handle the chunking.
            using (MemoryStream messageStream = new MemoryStream())
            using (CryptoStream cryptoStream =
                new CryptoStream(messageStream, transform, CryptoStreamMode.Write))
            {
                cryptoStream.Write(input, inputOffset, inputLength);
                cryptoStream.FlushFinalBlock();
                return messageStream.ToArray();
            }
        }

        /// <summary>
        /// Open a properly configured <see cref="SymmetricAlgorithm"/> conforming to the
        /// scheme identified by <paramref name="aeCipher"/>.
        /// </summary>
        /// <param name="aeCipher">The cipher mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// A SymmetricAlgorithm object with the right key, cipher mode, and padding
        /// mode; or <c>null</c> on unknown algorithms.
        /// </returns>
        private static SymmetricAlgorithm GetCipher(AeCipher aeCipher, byte[] masterKey)
        {
            SymmetricAlgorithm symmetricAlgorithm;

            switch (aeCipher)
            {
                case AeCipher.Aes256CbcPkcs7:
                    symmetricAlgorithm = Aes.Create();
                    // While 256-bit, CBC, and PKCS7 are all the default values for these
                    // properties, being explicit helps comprehension more than it hurts
                    // performance.
                    symmetricAlgorithm.KeySize = 256;
                    symmetricAlgorithm.Mode = CipherMode.CBC;
                    symmetricAlgorithm.Padding = PaddingMode.PKCS7;
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            //
            // Since none of the symmetric encryption algorithms currently in .NET
            // support key sizes greater than 256-bit, we can use HMACSHA256 with
            // NIST SP 800-108 5.1 (Counter Mode KDF) to derive a value that is
            // no smaller than the key size, then Array.Resize to trim it down as
            // needed.

            using (HMAC hmac = new HMACSHA256(masterKey))
            {
                // i=1, Label=ASCII(cipher)
                byte[] cipherKey = hmac.ComputeHash(
                    new byte[] { 1, 99, 105, 112, 104, 101, 114 });

                // Resize the array to the desired keysize. KeySize is in bits,
                // and Array.Resize wants the length in bytes.
                Array.Resize(ref cipherKey, symmetricAlgorithm.KeySize / 8);

                symmetricAlgorithm.Key = cipherKey;
            }

            return symmetricAlgorithm;
        }

        /// <summary>
        /// Open a properly configured <see cref="HMAC"/> conforming to the scheme
        /// identified by <paramref name="aeMac"/>.
        /// </summary>
        /// <param name="aeMac">The message authentication mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// An HMAC object with the proper key, or <c>null</c> on unknown algorithms.
        /// </returns>
        private static HMAC GetMac(AeMac aeMac, byte[] masterKey)
        {
            HMAC hmac;

            switch (aeMac)
            {
                case AeMac.HMACSHA256:
                    hmac = new HMACSHA256();
                    break;
                case AeMac.HMACSHA384:
                    hmac = new HMACSHA384();
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            // Since the output size of the HMAC is the same as the ideal key size for
            // the HMAC, we can use the master key over a fixed input once to perform
            // NIST SP 800-108 5.1 (Counter Mode KDF):
            hmac.Key = masterKey;

            // i=1, Context=ASCII(MAC)
            byte[] newKey = hmac.ComputeHash(new byte[] { 1, 77, 65, 67 });

            hmac.Key = newKey;
            return hmac;
        }

        // A simple helper method to ensure that the offset (writePos) always moves
        // forward with new data.
        private static void Append(byte[] newData, byte[] combinedData, ref int writePos)
        {
            Buffer.BlockCopy(newData, 0, combinedData, writePos, newData.Length);
            writePos += newData.Length;
        }

        /// <summary>
        /// Compare the contents of two arrays in an amount of time which is only
        /// dependent on <paramref name="length"/>.
        /// </summary>
        /// <param name="a">An array to compare to <paramref name="b"/>.</param>
        /// <param name="aOffset">
        /// The starting position within <paramref name="a"/> for comparison.
        /// </param>
        /// <param name="b">An array to compare to <paramref name="a"/>.</param>
        /// <param name="bOffset">
        /// The starting position within <paramref name="b"/> for comparison.
        /// </param>
        /// <param name="length">
        /// The number of bytes to compare between <paramref name="a"/> and
        /// <paramref name="b"/>.</param>
        /// <returns>
        /// <c>true</c> if both <paramref name="a"/> and <paramref name="b"/> have
        /// sufficient length for the comparison and all of the applicable values are the
        /// same in both arrays; <c>false</c> otherwise.
        /// </returns>
        /// <remarks>
        /// An "insufficient data" <c>false</c> response can happen early, but otherwise
        /// a <c>true</c> or <c>false</c> response take the same amount of time.
        /// </remarks>
        [MethodImpl(MethodImplOptions.NoInlining | MethodImplOptions.NoOptimization)]
        private static bool CryptographicEquals(
            byte[] a,
            int aOffset,
            byte[] b,
            int bOffset,
            int length)
        {
            Debug.Assert(a != null);
            Debug.Assert(b != null);
            Debug.Assert(length >= 0);

            int result = 0;

            if (a.Length - aOffset < length || b.Length - bOffset < length)
            {
                return false;
            }

            unchecked
            {
                for (int i = 0; i < length; i++)
                {
                    // Bitwise-OR of subtraction has been found to have the most
                    // stable execution time.
                    //
                    // This cannot overflow because bytes are 1 byte in length, and
                    // result is 4 bytes.
                    // The OR propagates all set bytes, so the differences are only
                    // present in the lowest byte.
                    result = result | (a[i + aOffset] - b[i + bOffset]);
                }
            }

            return result == 0;
        }
    }
}
```
