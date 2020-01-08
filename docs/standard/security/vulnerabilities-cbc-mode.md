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
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="ed0b7-103">Ohrožení zabezpečení časování u symetrického dešifrování pomocí odsazení v režimu CBC</span><span class="sxs-lookup"><span data-stu-id="ed0b7-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="ed0b7-104">Společnost Microsoft se domnívá, že již není bezpečná k dešifrování dat šifrovaných pomocí režimu CBC (Cipher-Block-Chaining) symetrického šifrování, pokud bylo použito ověřitelné odsazení bez předchozího zadání integrity šifrovaného textu, s výjimkou konkrétního žádný.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-104">Microsoft believes that it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext, except for very specific circumstances.</span></span> <span data-ttu-id="ed0b7-105">Tento odhad je založen na aktuálně známém kryptografickém výzkumu.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-105">This judgement is based on currently known cryptographic research.</span></span> 

## <a name="introduction"></a><span data-ttu-id="ed0b7-106">Úvod</span><span class="sxs-lookup"><span data-stu-id="ed0b7-106">Introduction</span></span>

<span data-ttu-id="ed0b7-107">Útok typu Oracle pro vyplňování je typ útoku proti šifrovaným datům, který umožňuje útočníkovi dešifrovat obsah dat bez znalosti klíče.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-107">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="ed0b7-108">Oracle odkazuje na "Řekněte", který poskytuje útočníkovi informace o tom, zda je akce, kterou spouštíte, správná nebo ne.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-108">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="ed0b7-109">Představte si, že budete hrát desku nebo karetní hru s podřízeným.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-109">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="ed0b7-110">Když se tváře s velkým úsměvem, protože si domníváme, že se chystá, aby se zajistil dobrý pohyb, je to Oracle.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-110">When her face lights up with a big smile because she thinks she's about to make a good move, that's an oracle.</span></span> <span data-ttu-id="ed0b7-111">Jako protihráč může použít tento Oracle k naplánování dalšího přesunu.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-111">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="ed0b7-112">Odsazení je konkrétní kryptografické podmínky.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-112">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="ed0b7-113">Některá šifry, které jsou algoritmy používané k šifrování vašich dat, fungují na blocích dat, kde každý blok má pevně danou velikost.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-113">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="ed0b7-114">Pokud data, která chcete zašifrovat, nemají správnou velikost pro vyplnění bloků, vaše data se doplní, dokud to neudělá.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-114">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="ed0b7-115">Mnoho forem odsazení vyžaduje, aby bylo odsazení vždy k dispozici, i když původní vstup měl správnou velikost.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-115">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="ed0b7-116">To umožňuje, aby se výplň vždy bezpečně odebrala při dešifrování.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-116">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="ed0b7-117">Implementace těchto dvou věcí společně s doplňováním Oracle odhalí, zda má dešifrovaná data platné odsazení.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-117">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="ed0b7-118">Oracle může být něco jednoduchého, protože vrací hodnotu, která říká "Neplatné odsazení", nebo něco složitějšího, jako by bylo možné zpracovat platný blok na rozdíl od neplatného bloku.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-118">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="ed0b7-119">Šifry založené na bloku mají jinou vlastnost, která se nazývá režim, který určuje vztah mezi daty v prvním bloku a daty ve druhém bloku atd.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-119">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="ed0b7-120">Jedním z nejčastěji používaných režimů je CBC.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-120">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="ed0b7-121">CBC zavádí počáteční náhodný blok, který se označuje jako inicializační vektor (IV), a zkombinuje předchozí blok s výsledkem statického šifrování, aby se zajistilo, že šifrování stejné zprávy se stejným klíčem nikdy nevytvoří stejný šifrovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-121">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="ed0b7-122">Útočník může použít výplň Oracle, a to v kombinaci s tím, jak jsou CBC data strukturovaná, aby odesílaly mírně změněné zprávy do kódu, který zveřejňuje Oracle, a dál odesílá data, dokud je Oracle neupozorní, že data jsou správná.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-122">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="ed0b7-123">Od této odpovědi může útočník dešifrovat bajt po bajtu.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-123">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="ed0b7-124">Moderní počítačové sítě mají takovou vysokou kvalitu, kterou může útočník detekovat velmi malými rozdíly (méně než 0,1 ms) v době provádění ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-124">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span><span data-ttu-id="ed0b7-125"> Aplikace, u kterých se předpokládá, že úspěšné dešifrování může nastat jenom v případě, že data nebyla zfalšována, můžou být zranitelná vůči útokům z nástrojů, které jsou navržené tak, aby sledovaly rozdíly v úspěšném a neúspěšném dešifrování.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-125"> Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="ed0b7-126">I když tento časový rozdíl může být v některých jazycích nebo knihovnách důležitější než jiné, je to pro všechny jazyky a knihovny v případě, že je odezva aplikace na selhání v úvahu, to je praktická hrozba.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-126">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="ed0b7-127">Tento útok se spoléhá na možnost změnit šifrovaná data a otestovat výsledek pomocí Oracle.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-127">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="ed0b7-128">Jediným způsobem, jak plně zmírnit útok, je zjistit změny šifrovaných dat a odmítnout na ni provádět jakékoli akce.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-128">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="ed0b7-129">Standardní způsob, jak to provést, je vytvořit podpis pro data a ověřit podpis před provedením jakékoli operace.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-129">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="ed0b7-130">Podpis musí být ověřitelný, nemůže ho vytvořit útočník, jinak změní šifrovaná data a pak vypočítá nový podpis na základě změněných dat.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-130">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="ed0b7-131">Jeden běžný typ odpovídající signatury se označuje jako ověřovací kód zprávy hash s klíčem (HMAC).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-131">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="ed0b7-132">HMAC se liší od kontrolního součtu v tom, že přebírá tajný klíč, známý jenom pro osobu, která vyrábí HMAC a osoba ji ověřuje.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-132">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="ed0b7-133">Bez použití klíče nemůžete vytvořit správné HMAC.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-133">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="ed0b7-134">Když obdržíte data, zašifrujte zašifrovaná data, nezávisle COMPUTE HMAC pomocí tajného klíče a sdílené složky odesílatele a pak porovnejte HMAC, která se poslala oproti vypočítanému.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-134">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="ed0b7-135">Toto porovnání musí být konstantní čas, jinak jste přidali další zjistitelnou databázi Oracle umožňující jiný typ útoku.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-135">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="ed0b7-136">Aby bylo možné bezpečně použít doplněné šifrované šifry CBC, je nutné je kombinovat s HMAC (nebo jinou kontrolou integrity dat), kterou ověříte s použitím porovnání konstantního času, než se pokusíte data dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-136">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="ed0b7-137">Vzhledem k tomu, že všechny změněné zprávy přebírají stejnou dobu jako odpověď, útok se zabrání.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-137">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="ed0b7-138">Kdo je ohrožen</span><span class="sxs-lookup"><span data-stu-id="ed0b7-138">Who is vulnerable</span></span>

<span data-ttu-id="ed0b7-139">Tato chyba zabezpečení se týká spravovaných i nativních aplikací, které provádějí vlastní šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-139">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="ed0b7-140">Patří sem například:</span><span class="sxs-lookup"><span data-stu-id="ed0b7-140">This includes, for example:</span></span>

- <span data-ttu-id="ed0b7-141">Aplikace, která šifruje soubor cookie pro pozdější dešifrování na serveru.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-141">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="ed0b7-142">Databázová aplikace, která uživatelům umožňuje vkládat data do tabulky, jejíž sloupce jsou později dešifrovány.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-142">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="ed0b7-143">Aplikace pro přenos dat, která spoléhá na šifrování pomocí sdíleného klíče k ochraně dat při přenosu.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-143">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="ed0b7-144">Aplikace, která šifruje a dešifruje zprávy "v rámci" tunelu TLS.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-144">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="ed0b7-145">Upozorňujeme, že při použití samotného TLS se v těchto scénářích neochrání.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-145">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="ed0b7-146">Zranitelná aplikace:</span><span class="sxs-lookup"><span data-stu-id="ed0b7-146">A vulnerable application:</span></span>

- <span data-ttu-id="ed0b7-147">Dešifruje data pomocí režimu šifry CBC s ověřitelným režimem odsazení, jako je PKCS # 7 nebo ANSI X. 923.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-147">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="ed0b7-148">Provede dešifrování bez provedení kontroly integrity dat (přes MAC nebo asymetrický digitální podpis).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-148">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="ed0b7-149">To platí také pro aplikace postavené na abstrakcích přes tyto primitivní prvky, jako je například syntaxe kryptografické zprávy (PKCS # 7/CMS) EnvelopedData struktura.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-149">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="ed0b7-150">Související oblasti k obavám</span><span class="sxs-lookup"><span data-stu-id="ed0b7-150">Related areas of concern</span></span>

<span data-ttu-id="ed0b7-151">Výzkum vedla společnost Microsoft o další obavy o CBCch zprávách, které jsou doplněny odpovídajícím odsazením ISO 10126, když má zpráva dobře známou nebo předvídatelné struktury zápatí.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-151">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="ed0b7-152">Například obsah připravený v rámci pravidel syntaxe šifrování W3C XML a doporučení pro zpracování (xmlenc, EncryptedXml).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-152">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="ed0b7-153">I když pokyny W3C pro podepsání zprávy se pak považují za vhodné, Microsoft teď doporučuje vždycky zašifrovat a podepsat.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-153">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="ed0b7-154">Vývojáři aplikací by měli vždy vědomi ověření použitelnosti asymetrického klíče podpisu, protože mezi asymetrickým klíčem a libovolnou zprávou neexistuje vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-154">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="ed0b7-155">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ed0b7-155">Details</span></span>

<span data-ttu-id="ed0b7-156">Historicky jsme dosáhli konsensu, že je důležité šifrovat a ověřovat důležitá data pomocí prostředků, jako jsou například HMAC nebo podpis RSA.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-156">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="ed0b7-157">V takovém případě však existuje méně jasných pokynů pro sekvencování operací šifrování a ověřování.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-157">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="ed0b7-158">V souvislosti s touto chybou v tomto článku jsou teď pokyny Microsoftu k tomu, abyste vždycky použili paradigma "šifrovat a pak-podepsat".</span><span class="sxs-lookup"><span data-stu-id="ed0b7-158">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="ed0b7-159">To znamená, že nejprve Šifrujte data pomocí symetrického klíče a pak vypočítáte klíč MAC nebo asymetrický podpis přes šifrovaný text (šifrovaná data).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-159">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="ed0b7-160">Při dešifrování dat proveďte reverzní.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-160">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="ed0b7-161">Nejdřív potvrďte adresu MAC nebo podpis šifrovaného textu a pak ho dešifrujte.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-161">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="ed0b7-162">V případě více než 10 let bylo známo, že existují třídy chyb zabezpečení, které jsou známy jako "útoky Oracle pro vyplňování".</span><span class="sxs-lookup"><span data-stu-id="ed0b7-162">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="ed0b7-163">Tyto chyby zabezpečení umožňují útočníkovi dešifrovat data zašifrovaná pomocí symetrických blokových algoritmů, jako jsou AES a 3DES, s využitím maximálně 4096ch pokusů na blok dat.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-163">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="ed0b7-164">Tato ohrožení zabezpečení využívají skutečnost, že se na konci často používají data blokující šifry s ověřitelnými daty odsazení.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-164">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="ed0b7-165">Bylo zjištěno, že pokud útočník může manipulovat s šifrovaným datovým časem a zjistit, zda manipulace způsobila chybu ve formátu odsazení na konci, může útočník data dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-165">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="ed0b7-166">Zpočátku byly praktické útoky založené na službách, které vrátily různé kódy chyb na základě toho, jestli bylo odsazení platné, jako je například zranitelnost ASP.NET [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-166">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span></span> <span data-ttu-id="ed0b7-167">Společnost Microsoft se však nyní domnívá, že je praktické provádět podobné útoky pouze v případě, že je mezi nimi platné a neplatné odsazení.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-167">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="ed0b7-168">Za předpokladu, že šifrovací schéma používá podpis a že se pro danou délku dat (bez ohledu na obsah) provádí ověření podpisu s pevným modulem runtime, může být integrita dat ověřena bez vygenerování jakýchkoli informací útočníkem přes [postranní kanál](https://en.wikipedia.org/wiki/Side-channel_attack).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-168">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="ed0b7-169">Vzhledem k tomu, že kontrola integrity odmítne jakékoli neoprávněné zprávy, dojde k omezení hrozby Oracle pro odsazení.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-169">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="ed0b7-170">Doprovodné materiály</span><span class="sxs-lookup"><span data-stu-id="ed0b7-170">Guidance</span></span>

<span data-ttu-id="ed0b7-171">A především společnost Microsoft doporučuje, aby všechna data, která mají důvěrné požadavky, byla přenášena přes protokol TLS (Transport Layer Security), nástupce SSL (Secure Sockets Layer) (SSL).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-171">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="ed0b7-172">Dále proveďte analýzu aplikace na:</span><span class="sxs-lookup"><span data-stu-id="ed0b7-172">Next, analyze your application to:</span></span>

- <span data-ttu-id="ed0b7-173">Přesné pochopení toho, jaké šifrování provádíte a jaké šifrování poskytují platformy a rozhraní API, které používáte.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-173">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="ed0b7-174">Ujistěte se, že každé použití v každé vrstvě [algoritmu symetrického bloku šifrování](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), jako je AES a 3DES, v režimu CBC zahrnuje použití kontroly integrity dat tajných klíčů (asymetrický podpis, HMAC nebo ke změně režimu šifry na [ověřený šifrovací](https://en.wikipedia.org/wiki/Authenticated_encryption) režim (AE), jako je například GCM nebo ccm).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-174">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="ed0b7-175">V závislosti na aktuálním výzkumu se obecně předpokládá, že pokud jsou kroky ověřování a šifrování prováděny nezávisle na jiných režimech šifrování, ověřování šifrovaných informací (šifrování a podepsání) je nejlepší volbou.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-175">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="ed0b7-176">Neexistuje však žádná platná odpověď na šifrování a tato generalizace není stejně vhodná jako směrná Rada od profesního cryptographeru.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-176">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="ed0b7-177">Aplikace, které nemůžou měnit formát zpráv, ale provádějí neověřené dešifrování CBC, by se měly doporučit při pokusu o začlenit rizika, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="ed0b7-177">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="ed0b7-178">Dešifrovat bez povolení dešifry pro ověření nebo odebrání odsazení:</span><span class="sxs-lookup"><span data-stu-id="ed0b7-178">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="ed0b7-179">Všechna předplatná, která byla použita stále, je nutné odebrat nebo ignorovat, přesunete zatížení do aplikace.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-179">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="ed0b7-180">Výhodou je, že ověření a odebrání odsazení lze začlenit do jiné logiky ověřování dat aplikace.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-180">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="ed0b7-181">Pokud se ověření odsazení a ověření dat dá provést v konstantním čase, dojde k omezení hrozby.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-181">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="ed0b7-182">Vzhledem k tomu, že výklad odsazení změní vnímanou délku zprávy, mohou být stále informace o časování vydávané z tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-182">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="ed0b7-183">Změňte režim odsazení dešifrování na ISO10126:</span><span class="sxs-lookup"><span data-stu-id="ed0b7-183">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="ed0b7-184">OdISO10126 dešifrování je kompatibilní s odsazením šifrování PKCS7 i s odsazením ANSIX923 šifrování.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-184">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="ed0b7-185">Změna režimu omezí znalosti od Oracle odsazení od celého bloku.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-185">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="ed0b7-186">Pokud však obsah obsahuje dobře známé zápatí, jako je například uzavírací element XML, mohou související útoky pokračovat v útoku na zbytek zprávy.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-186">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="ed0b7-187">To také nebrání v situacích, kdy by útočník mohl převést stejný prostý text, aby byl několikrát zašifrovaný pomocí jiného posunu zprávy.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-187">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="ed0b7-188">Brána vyhodnocuje vyhodnocení volání dešifrování a ztlumení signálu časování:</span><span class="sxs-lookup"><span data-stu-id="ed0b7-188">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="ed0b7-189">Výpočet doby blokování musí obsahovat minimum, než je maximální doba, po kterou by měla operace dešifrování platit pro jakýkoliv datový segment, který obsahuje odsazení.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-189">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="ed0b7-190">Časové výpočty by se měly provádět v souladu s pokyny pro [získání časových razítek s vysokým rozlišením](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), ne pomocí <xref:System.Environment.TickCount?displayProperty=nameWithType> (v rámci převzetí/přetečení) nebo odečtením dvou systémových časových razítek (v závislosti na chybách při úpravách NTP).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-190">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="ed0b7-191">Časová období musí být zahrnutá do dešifrovací operace, včetně všech potenciálních výjimek ve C++ spravovaných nebo aplikací, a ne jenom na konci.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-191">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="ed0b7-192">Pokud se zatím zjistila úspěch nebo neúspěch, musí časová brána při vypršení platnosti vracet chybu.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-192">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="ed0b7-193">Služby, které provádějí neověřené dešifrování, by měly mít k dispozici monitorování, aby bylo možné zjistit, že se nejedná o neplatnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-193">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="ed0b7-194">Mějte na paměti, že tento signál ponese falešně pozitivní (legitimně poškozená data) a falešně negativní výsledek (za dostatečně dlouhou dobu šíří útok na obcházení).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-194">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="ed0b7-195">Hledání chybných nativních aplikací kódu</span><span class="sxs-lookup"><span data-stu-id="ed0b7-195">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="ed0b7-196">Pro programy vytvořené proti knihovně Windows Cryptography: Next Generation (CNG):</span><span class="sxs-lookup"><span data-stu-id="ed0b7-196">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="ed0b7-197">Dešifrovací volání je [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), určení příznaku `BCRYPT_BLOCK_PADDING`.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-197">The decryption call is to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="ed0b7-198">Obslužná rutina klíče byla inicializována voláním [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) s [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) nastavenou na `BCRYPT_CHAIN_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-198">The key handle has been initialized by calling [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) with [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="ed0b7-199">Vzhledem k tomu, že `BCRYPT_CHAIN_MODE_CBC` je výchozí, ovlivněný kód nemusí mít přiřazenou žádnou hodnotu pro `BCRYPT_CHAINING_MODE`.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-199">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="ed0b7-200">Pro programy vytvořené proti staršímu rozhraní API Windows pro šifrování:</span><span class="sxs-lookup"><span data-stu-id="ed0b7-200">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="ed0b7-201">Dešifrovací volání je [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) pomocí `Final=TRUE`.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-201">The decryption call is to [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) with `Final=TRUE`.</span></span>
- <span data-ttu-id="ed0b7-202">Obslužná rutina klíče byla inicializována voláním [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) s [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) nastavenou na `CRYPT_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-202">The key handle has been initialized by calling [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) with [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="ed0b7-203">Vzhledem k tomu, že `CRYPT_MODE_CBC` je výchozí, ovlivněný kód nemusí mít přiřazenou žádnou hodnotu pro `KP_MODE`.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-203">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="ed0b7-204">Hledání ohrožených aplikací spravovaných kódem</span><span class="sxs-lookup"><span data-stu-id="ed0b7-204">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="ed0b7-205">Dešifrovací volání je <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> nebo <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> metody na <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-205">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="ed0b7-206">To zahrnuje následující odvozené typy v rozhraní .NET, ale mohou také zahrnovat typy třetích stran:</span><span class="sxs-lookup"><span data-stu-id="ed0b7-206">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="ed0b7-207">Vlastnost <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> byla nastavena na <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>nebo <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-207">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="ed0b7-208">Vzhledem k tomu, že <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> je výchozí, ovlivněný kód nemusí nikdy mít přiřazenou vlastnost <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-208">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="ed0b7-209">Vlastnost <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> byla nastavena na hodnotu <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ed0b7-209">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="ed0b7-210">Vzhledem k tomu, že <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> je výchozí, ovlivněný kód nemusí nikdy mít přiřazenou vlastnost <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-210">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="ed0b7-211">Hledání zranitelného kódu – syntaxe kryptografické zprávy</span><span class="sxs-lookup"><span data-stu-id="ed0b7-211">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="ed0b7-212">Neověřená zpráva CMS EnvelopedData, jejíž šifrovaný obsah používá režim CBC AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) nebo RC2 (1.2.840.113549.3.2), je zranitelná a také zprávy používající jakékoli jiné algoritmy blokového šifrování v režimu CBC.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-212">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="ed0b7-213">I když nejsou šifry streamů náchylné k této konkrétní chybě zabezpečení, společnost Microsoft doporučuje vždycky ověřovat data prostřednictvím kontroly hodnoty ContentEncryptionAlgorithm.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-213">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="ed0b7-214">U spravovaných aplikací se dá EnvelopedData objekt BLOB CMS zjistit jako libovolná hodnota, která se předává do <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-214">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="ed0b7-215">U nativních aplikací se dá EnvelopedData objekt BLOB CMS zjistit jako jakákoli hodnota poskytnutá popisovači CMS prostřednictvím [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) , jehož výsledná [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) je `CMSG_ENVELOPED`, nebo popisovač CMS se později pošle `CMSG_CTRL_DECRYPT` instrukcí prostřednictvím [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span><span class="sxs-lookup"><span data-stu-id="ed0b7-215">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) whose resulting [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="ed0b7-216">Příklad zranitelného kódu – spravováno</span><span class="sxs-lookup"><span data-stu-id="ed0b7-216">Vulnerable code example - managed</span></span>

<span data-ttu-id="ed0b7-217">Tato metoda přečte soubor cookie a dešifruje a nezobrazuje se žádná kontrola integrity dat.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-217">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="ed0b7-218">Proto může být obsah souboru cookie, který je čten touto metodou, napaden uživatelem, který ji přijal, nebo jakýmkoli útočníkem, který získal hodnotu šifrovaného souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-218">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="ed0b7-219">Příklad kódu pro následující doporučené postupy – spravováno</span><span class="sxs-lookup"><span data-stu-id="ed0b7-219">Example code following recommended practices - managed</span></span>

<span data-ttu-id="ed0b7-220">Následující vzorový kód používá nestandardní formát zprávy.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-220">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="ed0b7-221">kde identifikátory algoritmu `cipher_algorithm_id` a `hmac_algorithm_id` jsou místní (nestandardní) reprezentace těchto algoritmů.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-221">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="ed0b7-222">Tyto identifikátory můžou v jiných částech vašeho stávajícího protokolu pro zasílání zpráv smysl místo jako nebytestreamně zřetězené.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-222">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="ed0b7-223">V tomto příkladu se k odvození šifrovacího klíče a klíče HMAC používá jeden hlavní klíč.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-223">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="ed0b7-224">Tato možnost je poskytována jako pohodlí pro zapnutí jednorázové aplikace v aplikaci s dvojitou konvencí a pro povýšení uchování těchto dvou klíčů jako různých hodnot.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-224">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="ed0b7-225">Dále zaručuje, že klíče HMAC a šifrovací klíč nebudou synchronizovány.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-225">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="ed0b7-226">Tato ukázka nepřijímá <xref:System.IO.Stream> pro šifrování ani dešifrování.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-226">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="ed0b7-227">Aktuální formát dat je obtížné složit šifrování, protože hodnota `hmac_tag` předchází šifrovanému textu.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-227">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="ed0b7-228">Tento formát byl však vybrán, protože udržuje všechny prvky pevné velikosti na začátku, aby byl analyzátor jednodušší.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-228">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="ed0b7-229">S tímto formátem dat je možné provést dešifrování jedním průchodem, i když je implementátor opatrní při volání GetHashAndReset a ověřit výsledek před voláním TransformFinalBlock.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-229">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="ed0b7-230">Pokud je šifrování streamování důležité, může se vyžadovat jiný režim AE.</span><span class="sxs-lookup"><span data-stu-id="ed0b7-230">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
