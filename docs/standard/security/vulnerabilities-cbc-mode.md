---
title: Ohrožení zabezpečení časování s režimu CBC Symetrické dešifrování pomocí odsazení
description: Zjistěte, jak zjišťovat a zmírňovat ohrožení zabezpečení časování s Cipher Block Chaining CBC režimu Symetrické dešifrování pomocí odsazení.
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: a07acbb943c430f6e26bec44f55a5c84306da513
ms.sourcegitcommit: 73a662360bbe2f43c19aca1fbcc2565025c60cd8
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2018
ms.locfileid: "35327268"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Ohrožení zabezpečení časování s režimu CBC Symetrické dešifrování pomocí odsazení

Společnosti Microsoft, podle aktuálně známé kryptografickém výzkumu se považuje za, s výjimkou velmi konkrétní okolností už bezpečné dešifrovat data šifrují s režimem Cipher Block Chaining CBC symetrického šifrování, pokud byl ověřitelný odsazení použít bez první zajistíte integritu šifrovaný text.

## <a name="introduction"></a>Úvod

Útoku odsazení oracle je typ útoku proti šifrovaná data, která umožňuje útočník dešifrovat obsah data, aniž by věděly, klíč.

Oracle odkazuje "říct" které dává útočník informace o tom, zda akci, kterou jste provedením jejich správné nebo ne. Představte si přehrávání panelu nebo karty hry s podřízeným. Pokud svůj vzhled rozsvítí s velký smajlíka vzhledem k tomu, že se domnívá, že uživatel je o aby dobrý přesunu, která je oracle. Jako protihráče, můžete tento oracle plánování vaší další přesunutí správně.

Odsazení je konkrétní kryptografických období. Některé šifry, které jsou algoritmy používané k šifrování dat, fungovat na bloky dat, kde je každý blok s pevnou velikostí. Pokud data chcete šifrovat není správnou velikost k vyplnění na bloky, vaše data doplněno dokud dělá. Mnoho forem odsazení vyžadují tento odsazení vždy nacházet, i když původní vstup byl správnou velikost. To umožňuje odsazení vždy bezpečně odeberou při dešifrování.

Připravuje umístění dvě věci softwaru implementace s oracle odsazení zjistí, zda dešifrovaná data má platný odsazení. Oracle může být jednoduché, vrátí hodnotu, která říká "Neplatný odsazení" něco nebo něco složitější jako měřitelný výkon různých doba zpracování platný blok oproti bloku neplatný.

Blokový šifry mít jinou vlastnost s názvem režimu, který určuje vztah dat v prvním bloku k datům ve druhé blok, a tak dále. Jeden z režimů nejčastěji používané je CBC. CBC uvádí počáteční náhodné bloku známé jako inicializační vektor (IV) a kombinuje k předchozímu bloku s výsledkem statické šifrování, aby bylo tak, že šifrování stejná zpráva se stejným klíčem není vždy vytvořila stejný šifrované výstup.

Útočník může použít odsazení oracle, v kombinaci s struktury CBC dat, mírně změněné zprávy poslat kód, který zveřejňuje oracle a zachovat odesílání dat, dokud se sdělením, oracle je správná data. Z této odpovědi může útočník dešifrování zprávy bajtů podle bajtů.

Moderní počítače sítě jsou takové vysoké kvality, že útočník může zjistit velmi malé (méně než 0,1 ms) rozdíly v provádění čas na vzdálené systémy. Aplikace, které jsou za předpokladu, že úspěšné dešifrování může dojít pouze v případě dat nebylo manipulováno může být zranitelný vůči útokům z nástroje, které jsou navržené tak, abyste viděli rozdíly v úspěšné a neúspěšné dešifrování. Tento rozdíl časování může být v některých jazycích nebo knihovny větších než jiná, nyní předpokládá se toto je praktické hrozbu pro všechny jazyky a knihovny, když je aplikace odpověď selhání vzít v úvahu.

Tento útok spoléhá na možnost změnit šifrovaných dat a testování výsledků oracle. Jediný způsob, jak plně zmírnit útok je detekovat změny k šifrovaným datům a odmítnout na něm provádět žádné akce. Standardním způsobem k tomu je k vytvoření podpisu pro data a ověření této podpis před provedením jakékoli operace. Podpis musí být ověřitelný, nemůže být vytvořený útočník, jinak se by přejít šifrovaná data, a potom výpočetní nový podpis podle změněná data. Jeden běžný typ odpovídajícím podpisem se označuje jako ověřovací kód zprávy keyed-hash (HMAC). HMAC se liší od kontrolní součet v, že trvá tajný klíč známý jenom osobě generovala HMAC a osobě, její ověřování. Bez vlastní klíč nelze vytvořit správný HMAC. Jakmile se zobrazí vaše data, můžete provést šifrovaná data, nezávisle výpočetní HMAC pomocí tajný klíč můžete a sdílenou složku odesílatele, a potom porovnat HMAC odešlou proti ten je počítaný. Toto porovnání musí být konstantní čas, jinak jste přidali další rozpoznat oracle, povolení jiný typ útoku.

V souhrnu používat vyplní CBC bloku šifry bezpečně, je nutné zkombinovat s HMAC s klíčem (nebo jiné kontrolu integrity dat), který můžete ověřit pomocí porovnání konstantní čas a teprve potom zkusili data dešifrovat. Vzhledem k tomu, že všechny zprávy změněna využít současně velikost k vytvoření odpovědi, je-li vypnuto útoku.

## <a name="who-is-vulnerable"></a>Kdo je snadno napadnutelný

Toto ohrožení zabezpečení se vztahuje na spravovaná a nativní aplikace, které fungují vlastní šifrování a dešifrování. To zahrnuje, například:

- Aplikace, která zašifruje do souboru cookie pro novější dešifrování na serveru.
- Databáze aplikace, která poskytuje možnosti pro uživatele k vložení dat do tabulky, jejichž sloupce se dešifrují později.
- Aplikace pro přenos dat, která využívá šifrování pomocí sdílený klíč k ochraně dat během přenosu.
- Aplikace, který šifruje a dešifruje zprávy "vnitřních" tunelu TLS.

Mějte na paměti, který používá protokol TLS samostatně nemusí chránit v těchto scénářích.

K citlivé aplikaci:

- Dešifruje data pomocí režimu CBC šifrování s režimem ověřitelný odsazení, jako je například PKCS #7 nebo ANSI X.923.
- Provede dešifrování bez nutnosti provést kontrolu integrity dat (prostřednictvím MAC nebo digitální podpis asymetrické).

To platí také pro aplikace nástavbou abstrakce v horní části tyto základní prvky, jako je například struktura EnvelopedData Cryptographic Message Syntax (PKCS #7/CMS).

## <a name="related-areas-of-concern"></a>Související oblastí zájmu

Research vedlo Microsoft se další starat o CBC zprávy, které se vyplní ISO 10126-ekvivalentem odsazení při zpráva má struktura dobře známé nebo předvídatelný zápatí stránky. Například obsah připravit v části pravidla W3C XML šifrování syntaxe a zpracování doporučení (xmlenc, EncryptedXml). Zatímco pokyny W3C podepsat zprávu pak šifrování byl v době považuje za vhodné, Microsoft teď doporučuje vždy to šifrovat přihlašovací potom.

Vývojáři aplikace musí být vždy s vědomím ověření použitelnost klíčem asymetrické podpis není žádný vztah důvěry vyplývajících mezi asymetrický klíč a libovolný zprávy.

## <a name="details"></a>Podrobnosti

V minulosti došlo konsenzu, který je důležité k šifrování i ověřování důležitých dat, prostředky, jako je například HMAC nebo RSA podpisů. Ale musí být menší jasné pokyny, jak pořadí operace šifrování a ověřování. Z důvodu chyby zabezpečení, popsané v tomto článku pokyny společnosti Microsoft nyní je vždy nutné použít zlepší "šifrování potom přihlášení". To znamená nejprve šifrování dat pomocí symetrického klíče, a poté výpočetním MAC nebo asymetrický podpis přes šifrovaný text (šifrovaná data). K dešifrování dat, proveďte naopak. Nejprve zkontrolujte MAC nebo podpis šifrovaný text a potom ho dešifrovat.

Třída chyb zabezpečení, které označuje jako "odsazení oracle útoky" známé existovat více než deset let. Tyto chyby zabezpečení útočníkovi umožnit dešifrovat data zašifrovaná pomocí bloku symetrické algoritmy, například šifrování AES a 3DES, pomocí více než 4096 pokusů za datového bloku. Ujistěte se, tyto chyby zabezpečení použijte skutečnost, že blokovat šifry nejčastěji používaných s daty ověřitelný odsazení na konci. Bylo zjištěno, že pokud útočník můžete manipulovat s ciphertext a zjistit, jestli manipulaci způsobilo chybu ve formátu odsazení na konci, útočník může data dešifrovat.

Standardně jsou praktické útoky založené na služby, které by návratové kódy jiné chyby, které jsou založené na tom, zda byl platný, jako je například ohrožení zabezpečení ASP.NET odsazení [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx). Však Microsoft teď dochází k závěru, že je potřeba provést podobné útoky pomocí pouze rozdíly v časování mezi zpracování platné a neplatné odsazení.

Za předpokladu, že schéma šifrování používá podpis a ověření podpisu se provádí s pevnou runtime pro dané délky dat (bez ohledu na obsah), můžete ověřit integritu dat bez generování žádné informace Útočník prostřednictvím [straně kanál](https://en.wikipedia.org/wiki/Side-channel_attack). Vzhledem k tomu, že kontrola integrity odmítne všechny zmanipulovanou zprávy, zmírnit hrozby oracle odsazení.

## <a name="guidance"></a>Doprovodné materiály

Především společnost Microsoft doporučuje, aby žádná data, která má důvěrnost musí přenášet přes zabezpečení TLS (Transport Layer), nástupcem do vrstvy SSL (Secure Sockets).

V dalším kroku analyzujte aplikace:

- Rady pro pochopení přesněji jaké šifrování, provádění a probíhá zajišťuje šifrování, jaké platformy a rozhraní API používáte.
- Se ujistěte, zda každý využití v jednotlivých vrstvách služby symetrický [bloku šifrovací algoritmus](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), jako například šifrování AES a 3DES v režimu CBC začlenit použití kontrolu integrity dat s klíči tajný klíč (asymetrické podpis, klíčem HMAC, nebo chcete-li změnit režim šifrovací [ověřený šifrování](https://en.wikipedia.org/wiki/Authenticated_encryption) režimu (AE), jako je například GCM nebo CCM).

Podle aktuální research, obecně předpokládá se, že při ověřování a šifrování kroky se provádí nezávisle bez AE režimy šifrování, ověřování šifrovaný text (šifrování potom podepsání) lze nejvhodnější Obecné možnosti. Však neexistuje žádná univerzálně správnou odpověď na šifrování a tento generalizace není dosahovat směrovanou Rady, jak z professional cryptographer.

Aplikace, které se nepodařilo změnit jejich zasílání zpráv formátu ale provést neověřené CBC dešifrování se doporučuje pokusí začlenit způsoby zmírnění rizik, jako:

- Dešifrování bez povolení-li ověřit nebo odebrat odsazení:
  - Všechny odsazení, které bylo použito stále je nutné odebrat nebo ignorovat, přesouváte zatížení do vaší aplikace.
  - Výhodou je, že ověření odsazení a odebrání lze začlenit do jiné logiku ověření dat aplikace. Pokud v čase konstantní lze provést ověření odsazení a ověření dat, se snižuje riziko, že.
  - Vzhledem k tomu, že se výklad odsazení změní délka dosahovaný zprávy, je stále možné časování informace vygenerované z tohoto přístupu.
- Změňte režim odsazení dešifrování ISO10126:
  - Odsazení dešifrování ISO10126 je kompatibilní s PKCS7 šifrování odsazení a odsazení ANSIX923 šifrování.
  - Změna režimu snižuje znalosti oracle odsazení do 1 bajtů místo celý blok. Ale pokud obsah obsahuje dobře známé zápatí stránky, jako je například ukončovací XML element může dál související útoky vůči útokům rest zprávy.
  - To také nezabrání obnovení ve formátu prostého textu v situacích, kdy útočník může coerce stejné jako prostý text k zašifrování vícekrát s posunem jiná zpráva.
- Vyhodnocení volání dešifrování Ztlumit časování signál brány:
  - Výpočet doby uchování musí mít minimálně nad maximální množství času, které by pro datový segment, který obsahuje odsazení provést operaci dešifrování.
  - Čas výpočty by mělo být provedeno podle pokynů v [získávání s vysokým rozlišením časová razítka](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), nikoli pomocí <xref:System.Environment.TickCount?displayProperty=nameWithType> (přičemž podléhá kumulativní přes nebo přetečení) nebo odečtením dvě časová razítka systému (přičemž podléhá úpravu NTP chyby).
  - Výpočty čas musí být včetně dešifrovací operace, včetně všechny potenciální výjimky v spravované nebo aplikací C++, ne jenom odsazenou na konci.
  - Pokud úspěch nebo neúspěch byla zjištěna ještě, časování brány musí vrátit selhání při jeho platnost vyprší.
- Služby, které fungují neověřené dešifrování by měl mít zavedené ke zjištění, zda velké množství "neplatný" zprávy zase monitorování.
  - Berte v úvahu, že tento signál představuje falešně pozitivních (legálně poškozená data) a výsledkům (rozšíří útoku přes dostatečně dlouhou dobu obejít zjišťování).

## <a name="finding-vulnerable-code---native-applications"></a>Hledání kódu citlivé - nativních aplikací

Pro programy, které jsou vytvořeny kryptografický modul systému Windows: Knihovna generace (CNG):

- Dešifrování volání je [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), zadání `BCRYPT_BLOCK_PADDING` příznak.
- Popisovač klíče byla inicializována voláním [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) s [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) nastavena na `BCRYPT_CHAIN_MODE_CBC`.
  - Vzhledem k tomu `BCRYPT_CHAIN_MODE_CBC` je výchozí nastavení ovlivněných kód nesmí mít přiřazeno žádnou hodnotu pro `BCRYPT_CHAINING_MODE`.

Pro programy vytvořené starší kryptografické rozhraní API systému Windows:

- Dešifrování volání je [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) s `Final=TRUE`.
- Popisovač klíče byla inicializována voláním [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) s [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) nastavena na `CRYPT_MODE_CBC`.
  - Vzhledem k tomu `CRYPT_MODE_CBC` je výchozí nastavení ovlivněných kód nesmí mít přiřazeno žádnou hodnotu pro `KP_MODE`.

## <a name="finding-vulnerable-code---managed-applications"></a>Hledání kódu citlivé - spravované aplikace

- Dešifrování volání je <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> nebo <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> metody na <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.
  - To zahrnuje následující typy odvozené v rámci .NET, ale může také zahrnovat typy třetí strany:
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
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> Byla nastavena na <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, nebo <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Vzhledem k tomu <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> je výchozí nastavení ovlivněných kódu může nikdy přiřadili <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> vlastnost.
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> Byla nastavena na <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Vzhledem k tomu <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> je výchozí nastavení ovlivněných kódu může nikdy přiřadili <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> vlastnost.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Hledání kódu citlivé - syntaxe kryptografických zpráv

Neověřená zpráva CMS EnvelopedData jejichž šifrovaný obsah používá režimu CBC šifrování DES (1.3.14.3.2.7), AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), algoritmus 3DES (1.2.840.113549.3.7) nebo RC2 (1.2.840.113549.3.2) je snadno napadnutelný, stejně jako zprávy pomocí jakékoli jiné šifrovací algoritmy bloku v režimu CBC.

Když datový proud šifry nejsou náchylné k této konkrétní chyby, společnost Microsoft doporučuje, vždy ověřování data přes zkontrolujete ContentEncryptionAlgorithm hodnota.

Pro spravované aplikace, CMS EnvelopedData, blob může být zjištěna jako jakoukoli hodnotu, která je předána <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.

Pro nativní aplikace, bude možné zjišťovat objekt blob CMS EnvelopedData jako libovolná hodnota zadaná pro popisovač CMS prostřednictvím [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) jejichž výsledná [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) je `CMSG_ENVELOPED` nebo je popisovač CMS později odeslané `CMSG_CTRL_DECRYPT` instrukce prostřednictvím [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).

## <a name="vulnerable-code-example---managed"></a>Příklad citlivé kódu - spravované

Tato metoda přečte soubor cookie a dešifruje ji a žádné kontrolu integrity dat je viditelná. Obsah souboru cookie, který je pro čtení, tato metoda může být proto napadení uživatel, který ji obdržela, nebo jakékoli útočník, který má získat hodnotu šifrovaného souboru cookie.

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

## <a name="example-code-following-recommended-practices---managed"></a>Následující příklad kódu doporučené postupy - spravované

Následující vzorový kód používá formát nestandardní zprávy z

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

kde `cipher_algorithm_id` a `hmac_algorithm_id` místní aplikace (nestandardní) reprezentace tyto algoritmy jsou algoritmus identifikátory. Tyto identifikátory může mít smysl v dalších částí vaší existující zasílání zpráv protokolu místo jako úplné zřetězených bytestream.

Tento příklad také používá jeden hlavní klíč odvození šifrovací klíč a klíčem HMAC s klíčem. To se i pro potřeby poskytuje pro vypnutí samostatně keyed aplikace do aplikace s klíči duální a podporovat zachování dva klíče jako různé hodnoty. Další zaručuje, že mimo synchronizace nelze získat HMAC klíč a šifrovací klíč.

Tato ukázka nepřijímá <xref:System.IO.Stream> pro šifrování nebo dešifrování. Aktuální díky formátu dat jeden průchodu šifrování obtížné protože `hmac_tag` hodnotu předchází šifrovaný text. Tento formát však jste vybrali, protože všechny prvky pevné velikosti udržuje na začátku zachovat analyzátor jednodušší. Díky tento formát dat je možné, jeden průchodu dešifrování, i když je implementátor cautioned volání GetHashAndReset a ověřit před voláním TransformFinalBlock výsledek. Pokud streamování šifrování je důležité, může se vyžadovat jiný režim AE.

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
