---
title: Ohrožení zabezpečení při dešifrování CBC
description: Naučte se, jak detekovat a zmírnit omezení chyb časování pomocí symetrického dešifrování režimu CBC (Cipher-Block-Chaining) pomocí odsazení.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 1d570cf3da197e7af5c1a1ab4e4df0d21f2cb2d7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347232"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Ohrožení zabezpečení časování u symetrického dešifrování pomocí odsazení v režimu CBC

Společnost Microsoft se domnívá, že již není bezpečná k dešifrování dat šifrovaných pomocí režimu CBC (Cipher-Block-Chaining) symetrického šifrování, pokud bylo použito ověřitelné odsazení bez předchozího zadání integrity šifrovaného textu, s výjimkou konkrétního žádný. Tento odhad je založen na aktuálně známém kryptografickém výzkumu. 

## <a name="introduction"></a>Úvod

Útok typu Oracle pro vyplňování je typ útoku proti šifrovaným datům, který umožňuje útočníkovi dešifrovat obsah dat bez znalosti klíče.

Oracle odkazuje na "Řekněte", který poskytuje útočníkovi informace o tom, zda je akce, kterou spouštíte, správná nebo ne. Představte si, že budete hrát desku nebo karetní hru s podřízeným. Když se tváře s velkým úsměvem, protože si domníváme, že se chystá, aby se zajistil dobrý pohyb, je to Oracle. Jako protihráč může použít tento Oracle k naplánování dalšího přesunu.

Odsazení je konkrétní kryptografické podmínky. Některá šifry, které jsou algoritmy používané k šifrování vašich dat, fungují na blocích dat, kde každý blok má pevně danou velikost. Pokud data, která chcete zašifrovat, nemají správnou velikost pro vyplnění bloků, vaše data se doplní, dokud to neudělá. Mnoho forem odsazení vyžaduje, aby bylo odsazení vždy k dispozici, i když původní vstup měl správnou velikost. To umožňuje, aby se výplň vždy bezpečně odebrala při dešifrování.

Implementace těchto dvou věcí společně s doplňováním Oracle odhalí, zda má dešifrovaná data platné odsazení. Oracle může být něco jednoduchého, protože vrací hodnotu, která říká "Neplatné odsazení", nebo něco složitějšího, jako by bylo možné zpracovat platný blok na rozdíl od neplatného bloku.

Šifry založené na bloku mají jinou vlastnost, která se nazývá režim, který určuje vztah mezi daty v prvním bloku a daty ve druhém bloku atd. Jedním z nejčastěji používaných režimů je CBC. CBC zavádí počáteční náhodný blok, který se označuje jako inicializační vektor (IV), a zkombinuje předchozí blok s výsledkem statického šifrování, aby se zajistilo, že šifrování stejné zprávy se stejným klíčem nikdy nevytvoří stejný šifrovaný výstup.

Útočník může použít výplň Oracle, a to v kombinaci s tím, jak jsou CBC data strukturovaná, aby odesílaly mírně změněné zprávy do kódu, který zveřejňuje Oracle, a dál odesílá data, dokud je Oracle neupozorní, že data jsou správná. Od této odpovědi může útočník dešifrovat bajt po bajtu.

Moderní počítačové sítě mají takovou vysokou kvalitu, kterou může útočník detekovat velmi malými rozdíly (méně než 0,1 ms) v době provádění ve vzdálených systémech. Aplikace, u kterých se předpokládá, že úspěšné dešifrování může nastat jenom v případě, že data nebyla zfalšována, můžou být zranitelná vůči útokům z nástrojů, které jsou navržené tak, aby sledovaly rozdíly v úspěšném a neúspěšném dešifrování. I když tento časový rozdíl může být v některých jazycích nebo knihovnách důležitější než jiné, je to pro všechny jazyky a knihovny v případě, že je odezva aplikace na selhání v úvahu, to je praktická hrozba.

Tento útok se spoléhá na možnost změnit šifrovaná data a otestovat výsledek pomocí Oracle. Jediným způsobem, jak plně zmírnit útok, je zjistit změny šifrovaných dat a odmítnout na ni provádět jakékoli akce. Standardní způsob, jak to provést, je vytvořit podpis pro data a ověřit podpis před provedením jakékoli operace. Podpis musí být ověřitelný, nemůže ho vytvořit útočník, jinak změní šifrovaná data a pak vypočítá nový podpis na základě změněných dat. Jeden běžný typ odpovídající signatury se označuje jako ověřovací kód zprávy hash s klíčem (HMAC). HMAC se liší od kontrolního součtu v tom, že přebírá tajný klíč, známý jenom pro osobu, která vyrábí HMAC a osoba ji ověřuje. Bez použití klíče nemůžete vytvořit správné HMAC. Když obdržíte data, zašifrujte zašifrovaná data, nezávisle COMPUTE HMAC pomocí tajného klíče a sdílené složky odesílatele a pak porovnejte HMAC, která se poslala oproti vypočítanému. Toto porovnání musí být konstantní čas, jinak jste přidali další zjistitelnou databázi Oracle umožňující jiný typ útoku.

Aby bylo možné bezpečně použít doplněné šifrované šifry CBC, je nutné je kombinovat s HMAC (nebo jinou kontrolou integrity dat), kterou ověříte s použitím porovnání konstantního času, než se pokusíte data dešifrovat. Vzhledem k tomu, že všechny změněné zprávy přebírají stejnou dobu jako odpověď, útok se zabrání.

## <a name="who-is-vulnerable"></a>Kdo je ohrožen

Tato chyba zabezpečení se týká spravovaných i nativních aplikací, které provádějí vlastní šifrování a dešifrování. Patří sem například:

- Aplikace, která šifruje soubor cookie pro pozdější dešifrování na serveru.
- Databázová aplikace, která uživatelům umožňuje vkládat data do tabulky, jejíž sloupce jsou později dešifrovány.
- Aplikace pro přenos dat, která spoléhá na šifrování pomocí sdíleného klíče k ochraně dat při přenosu.
- Aplikace, která šifruje a dešifruje zprávy "v rámci" tunelu TLS.

Upozorňujeme, že při použití samotného TLS se v těchto scénářích neochrání.

Zranitelná aplikace:

- Dešifruje data pomocí režimu šifry CBC s ověřitelným režimem odsazení, jako je PKCS # 7 nebo ANSI X. 923.
- Provede dešifrování bez provedení kontroly integrity dat (přes MAC nebo asymetrický digitální podpis).

To platí také pro aplikace postavené na abstrakcích přes tyto primitivní prvky, jako je například syntaxe kryptografické zprávy (PKCS # 7/CMS) EnvelopedData struktura.

## <a name="related-areas-of-concern"></a>Související oblasti k obavám

Výzkum vedla společnost Microsoft o další obavy o CBCch zprávách, které jsou doplněny odpovídajícím odsazením ISO 10126, když má zpráva dobře známou nebo předvídatelné struktury zápatí. Například obsah připravený v rámci pravidel syntaxe šifrování W3C XML a doporučení pro zpracování (xmlenc, EncryptedXml). I když pokyny W3C pro podepsání zprávy se pak považují za vhodné, Microsoft teď doporučuje vždycky zašifrovat a podepsat.

Vývojáři aplikací by měli vždy vědomi ověření použitelnosti asymetrického klíče podpisu, protože mezi asymetrickým klíčem a libovolnou zprávou neexistuje vztah důvěryhodnosti.

## <a name="details"></a>Podrobnosti

Historicky jsme dosáhli konsensu, že je důležité šifrovat a ověřovat důležitá data pomocí prostředků, jako jsou například HMAC nebo podpis RSA. V takovém případě však existuje méně jasných pokynů pro sekvencování operací šifrování a ověřování. V souvislosti s touto chybou v tomto článku jsou teď pokyny Microsoftu k tomu, abyste vždycky použili paradigma "šifrovat a pak-podepsat". To znamená, že nejprve Šifrujte data pomocí symetrického klíče a pak vypočítáte klíč MAC nebo asymetrický podpis přes šifrovaný text (šifrovaná data). Při dešifrování dat proveďte reverzní. Nejdřív potvrďte adresu MAC nebo podpis šifrovaného textu a pak ho dešifrujte.

V případě více než 10 let bylo známo, že existují třídy chyb zabezpečení, které jsou známy jako "útoky Oracle pro vyplňování". Tyto chyby zabezpečení umožňují útočníkovi dešifrovat data zašifrovaná pomocí symetrických blokových algoritmů, jako jsou AES a 3DES, s využitím maximálně 4096ch pokusů na blok dat. Tato ohrožení zabezpečení využívají skutečnost, že se na konci často používají data blokující šifry s ověřitelnými daty odsazení. Bylo zjištěno, že pokud útočník může manipulovat s šifrovaným datovým časem a zjistit, zda manipulace způsobila chybu ve formátu odsazení na konci, může útočník data dešifrovat.

Zpočátku byly praktické útoky založené na službách, které vrátily různé kódy chyb na základě toho, jestli bylo odsazení platné, jako je například zranitelnost ASP.NET [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070). Společnost Microsoft se však nyní domnívá, že je praktické provádět podobné útoky pouze v případě, že je mezi nimi platné a neplatné odsazení.

Za předpokladu, že šifrovací schéma používá podpis a že se pro danou délku dat (bez ohledu na obsah) provádí ověření podpisu s pevným modulem runtime, může být integrita dat ověřena bez vygenerování jakýchkoli informací útočníkem přes [postranní kanál](https://en.wikipedia.org/wiki/Side-channel_attack). Vzhledem k tomu, že kontrola integrity odmítne jakékoli neoprávněné zprávy, dojde k omezení hrozby Oracle pro odsazení.

## <a name="guidance"></a>Doprovodné materiály

A především společnost Microsoft doporučuje, aby všechna data, která mají důvěrné požadavky, byla přenášena přes protokol TLS (Transport Layer Security), nástupce SSL (Secure Sockets Layer) (SSL).

Dále proveďte analýzu aplikace na:

- Přesné pochopení toho, jaké šifrování provádíte a jaké šifrování poskytují platformy a rozhraní API, které používáte.
- Ujistěte se, že každé použití v každé vrstvě [algoritmu symetrického bloku šifrování](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), jako je AES a 3DES, v režimu CBC zahrnuje použití kontroly integrity dat tajných klíčů (asymetrický podpis, HMAC nebo ke změně režimu šifry na [ověřený šifrovací](https://en.wikipedia.org/wiki/Authenticated_encryption) režim (AE), jako je například GCM nebo ccm).

V závislosti na aktuálním výzkumu se obecně předpokládá, že pokud jsou kroky ověřování a šifrování prováděny nezávisle na jiných režimech šifrování, ověřování šifrovaných informací (šifrování a podepsání) je nejlepší volbou. Neexistuje však žádná platná odpověď na šifrování a tato generalizace není stejně vhodná jako směrná Rada od profesního cryptographeru.

Aplikace, které nemůžou měnit formát zpráv, ale provádějí neověřené dešifrování CBC, by se měly doporučit při pokusu o začlenit rizika, jako jsou:

- Dešifrovat bez povolení dešifry pro ověření nebo odebrání odsazení:
  - Všechna předplatná, která byla použita stále, je nutné odebrat nebo ignorovat, přesunete zatížení do aplikace.
  - Výhodou je, že ověření a odebrání odsazení lze začlenit do jiné logiky ověřování dat aplikace. Pokud se ověření odsazení a ověření dat dá provést v konstantním čase, dojde k omezení hrozby.
  - Vzhledem k tomu, že výklad odsazení změní vnímanou délku zprávy, mohou být stále informace o časování vydávané z tohoto přístupu.
- Změňte režim odsazení dešifrování na ISO10126:
  - OdISO10126 dešifrování je kompatibilní s odsazením šifrování PKCS7 i s odsazením ANSIX923 šifrování.
  - Změna režimu omezí znalosti od Oracle odsazení od celého bloku. Pokud však obsah obsahuje dobře známé zápatí, jako je například uzavírací element XML, mohou související útoky pokračovat v útoku na zbytek zprávy.
  - To také nebrání v situacích, kdy by útočník mohl převést stejný prostý text, aby byl několikrát zašifrovaný pomocí jiného posunu zprávy.
- Brána vyhodnocuje vyhodnocení volání dešifrování a ztlumení signálu časování:
  - Výpočet doby blokování musí obsahovat minimum, než je maximální doba, po kterou by měla operace dešifrování platit pro jakýkoliv datový segment, který obsahuje odsazení.
  - Časové výpočty by se měly provádět v souladu s pokyny pro [získání časových razítek s vysokým rozlišením](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), ne pomocí <xref:System.Environment.TickCount?displayProperty=nameWithType> (v rámci převzetí/přetečení) nebo odečtením dvou systémových časových razítek (v závislosti na chybách při úpravách NTP).
  - Časová období musí být zahrnutá do dešifrovací operace, včetně všech potenciálních výjimek ve C++ spravovaných nebo aplikací, a ne jenom na konci.
  - Pokud se zatím zjistila úspěch nebo neúspěch, musí časová brána při vypršení platnosti vracet chybu.
- Služby, které provádějí neověřené dešifrování, by měly mít k dispozici monitorování, aby bylo možné zjistit, že se nejedná o neplatnou zprávu.
  - Mějte na paměti, že tento signál ponese falešně pozitivní (legitimně poškozená data) a falešně negativní výsledek (za dostatečně dlouhou dobu šíří útok na obcházení).

## <a name="finding-vulnerable-code---native-applications"></a>Hledání chybných nativních aplikací kódu

Pro programy vytvořené proti knihovně Windows Cryptography: Next Generation (CNG):

- Dešifrovací volání je [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), určení příznaku `BCRYPT_BLOCK_PADDING`.
- Obslužná rutina klíče byla inicializována voláním [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) s [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) nastavenou na `BCRYPT_CHAIN_MODE_CBC`.
  - Vzhledem k tomu, že `BCRYPT_CHAIN_MODE_CBC` je výchozí, ovlivněný kód nemusí mít přiřazenou žádnou hodnotu pro `BCRYPT_CHAINING_MODE`.

Pro programy vytvořené proti staršímu rozhraní API Windows pro šifrování:

- Dešifrovací volání je [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) pomocí `Final=TRUE`.
- Obslužná rutina klíče byla inicializována voláním [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) s [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) nastavenou na `CRYPT_MODE_CBC`.
  - Vzhledem k tomu, že `CRYPT_MODE_CBC` je výchozí, ovlivněný kód nemusí mít přiřazenou žádnou hodnotu pro `KP_MODE`.

## <a name="finding-vulnerable-code---managed-applications"></a>Hledání ohrožených aplikací spravovaných kódem

- Dešifrovací volání je <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> nebo <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> metody na <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.
  - To zahrnuje následující odvozené typy v rozhraní .NET, ale mohou také zahrnovat typy třetích stran:
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
- Vlastnost <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> byla nastavena na <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>nebo <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Vzhledem k tomu, že <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> je výchozí, ovlivněný kód nemusí nikdy mít přiřazenou vlastnost <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>.
- Vlastnost <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> byla nastavena na hodnotu <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Vzhledem k tomu, že <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> je výchozí, ovlivněný kód nemusí nikdy mít přiřazenou vlastnost <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Hledání zranitelného kódu – syntaxe kryptografické zprávy

Neověřená zpráva CMS EnvelopedData, jejíž šifrovaný obsah používá režim CBC AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) nebo RC2 (1.2.840.113549.3.2), je zranitelná a také zprávy používající jakékoli jiné algoritmy blokového šifrování v režimu CBC.

I když nejsou šifry streamů náchylné k této konkrétní chybě zabezpečení, společnost Microsoft doporučuje vždycky ověřovat data prostřednictvím kontroly hodnoty ContentEncryptionAlgorithm.

U spravovaných aplikací se dá EnvelopedData objekt BLOB CMS zjistit jako libovolná hodnota, která se předává do <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.

U nativních aplikací se dá EnvelopedData objekt BLOB CMS zjistit jako jakákoli hodnota poskytnutá popisovači CMS prostřednictvím [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) , jehož výsledná [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) je `CMSG_ENVELOPED`, nebo popisovač CMS se později pošle `CMSG_CTRL_DECRYPT` instrukcí prostřednictvím [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).

## <a name="vulnerable-code-example---managed"></a>Příklad zranitelného kódu – spravováno

Tato metoda přečte soubor cookie a dešifruje a nezobrazuje se žádná kontrola integrity dat. Proto může být obsah souboru cookie, který je čten touto metodou, napaden uživatelem, který ji přijal, nebo jakýmkoli útočníkem, který získal hodnotu šifrovaného souboru cookie.

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

## <a name="example-code-following-recommended-practices---managed"></a>Příklad kódu pro následující doporučené postupy – spravováno

Následující vzorový kód používá nestandardní formát zprávy.

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

kde identifikátory algoritmu `cipher_algorithm_id` a `hmac_algorithm_id` jsou místní (nestandardní) reprezentace těchto algoritmů. Tyto identifikátory můžou v jiných částech vašeho stávajícího protokolu pro zasílání zpráv smysl místo jako nebytestreamně zřetězené.

V tomto příkladu se k odvození šifrovacího klíče a klíče HMAC používá jeden hlavní klíč. Tato možnost je poskytována jako pohodlí pro zapnutí jednorázové aplikace v aplikaci s dvojitou konvencí a pro povýšení uchování těchto dvou klíčů jako různých hodnot. Dále zaručuje, že klíče HMAC a šifrovací klíč nebudou synchronizovány.

Tato ukázka nepřijímá <xref:System.IO.Stream> pro šifrování ani dešifrování. Aktuální formát dat je obtížné složit šifrování, protože hodnota `hmac_tag` předchází šifrovanému textu. Tento formát byl však vybrán, protože udržuje všechny prvky pevné velikosti na začátku, aby byl analyzátor jednodušší. S tímto formátem dat je možné provést dešifrování jedním průchodem, i když je implementátor opatrní při volání GetHashAndReset a ověřit výsledek před voláním TransformFinalBlock. Pokud je šifrování streamování důležité, může se vyžadovat jiný režim AE.

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
