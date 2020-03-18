---
title: Chyba zabezpečení dešifrování CBC
description: Zjistěte a zmírníte chyby zabezpečení časování pomocí režimu Cipher-Block-Chaining (CBC) symetrickédešifrování pomocí odsazení.
ms.date: 06/12/2018
author: blowdart
ms.openlocfilehash: 47520ea4c9c7d0ef4d79378c93c6ce1f2ba7dd6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186100"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="a74af-103">Ohrožení zabezpečení časování u symetrického dešifrování pomocí odsazení v režimu CBC</span><span class="sxs-lookup"><span data-stu-id="a74af-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="a74af-104">Společnost Microsoft se domnívá, že již není bezpečné dešifrovat data šifrovaná pomocí režimu šifrování symetrického šifrování cipher-Block-Chaining (CBC), pokud bylo použito ověřitelné odsazení, aniž by byla nejprve zajištěna integrita šifrovaného textu, s výjimkou velmi specifických Okolností.</span><span class="sxs-lookup"><span data-stu-id="a74af-104">Microsoft believes that it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext, except for very specific circumstances.</span></span> <span data-ttu-id="a74af-105">Tento rozsudek je založen na v současné době známém kryptografickém výzkumu.</span><span class="sxs-lookup"><span data-stu-id="a74af-105">This judgement is based on currently known cryptographic research.</span></span>

## <a name="introduction"></a><span data-ttu-id="a74af-106">Úvod</span><span class="sxs-lookup"><span data-stu-id="a74af-106">Introduction</span></span>

<span data-ttu-id="a74af-107">Odsazení oracle útok je typ útoku proti šifrovaná data, která umožňuje útočníkovi dešifrovat obsah dat, aniž by věděl klíč.</span><span class="sxs-lookup"><span data-stu-id="a74af-107">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="a74af-108">Věštec odkazuje na "tell", který poskytuje útočníkinformace o tom, zda akce, kterou provádí, je správná, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="a74af-108">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="a74af-109">Představte si, že hrajete deskovou nebo karetní hru s dítětem.</span><span class="sxs-lookup"><span data-stu-id="a74af-109">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="a74af-110">Když se jejich tvář rozsvítí s velkým úsměvem, protože si myslí, že se chystají udělat dobrý krok, je to věštec.</span><span class="sxs-lookup"><span data-stu-id="a74af-110">When their face lights up with a big smile because they think they're about to make a good move, that's an oracle.</span></span> <span data-ttu-id="a74af-111">Ty, jako protivník, můžeš použít tuto věštkyni k tomu, abys vhodně naplánoval svůj další krok.</span><span class="sxs-lookup"><span data-stu-id="a74af-111">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="a74af-112">Odsazení je specifický kryptografický termín.</span><span class="sxs-lookup"><span data-stu-id="a74af-112">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="a74af-113">Některé šifry, což jsou algoritmy používané k šifrování dat, pracují na blocích dat, kde každý blok má pevnou velikost.</span><span class="sxs-lookup"><span data-stu-id="a74af-113">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="a74af-114">Pokud data, která chcete zašifrovat, nemají správnou velikost pro vyplnění bloků, budou data doplněna, dokud se tak nestane.</span><span class="sxs-lookup"><span data-stu-id="a74af-114">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="a74af-115">Mnoho forem odsazení vyžaduje, aby odsazení vždy přítomen, i v případě, že původní vstup byl správné velikosti.</span><span class="sxs-lookup"><span data-stu-id="a74af-115">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="a74af-116">To umožňuje odsazení vždy bezpečně odstranit po dešifrování.</span><span class="sxs-lookup"><span data-stu-id="a74af-116">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="a74af-117">Uvedení dvě věci dohromady, implementace softwaru s odsazení oracle odhalí, zda dešifrovaná data má platné odsazení.</span><span class="sxs-lookup"><span data-stu-id="a74af-117">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="a74af-118">Oracle může být něco tak jednoduchého jako vrácení hodnoty, která říká, že "Neplatné odsazení" nebo něco složitějšího, jako je užívání měřitelně odlišný čas pro zpracování platného bloku na rozdíl od neplatného bloku.</span><span class="sxs-lookup"><span data-stu-id="a74af-118">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="a74af-119">Šifry založené na bloku mají jinou vlastnost, nazývanou režim, která určuje vztah dat v prvním bloku k datům v druhém bloku a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a74af-119">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="a74af-120">Jedním z nejčastěji používaných režimů je CBC.</span><span class="sxs-lookup"><span data-stu-id="a74af-120">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="a74af-121">CBC zavádí počáteční náhodný blok, známý jako inicializační vektor (IV) a kombinuje předchozí blok s výsledkem statického šifrování tak, aby byl takový, že šifrování stejné zprávy pomocí stejného klíče nevytváří vždy stejný šifrovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="a74af-121">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="a74af-122">Útočník může použít odsazení oracle, v kombinaci s tím, jak cbc data jsou strukturována, posílat mírně změněné zprávy do kódu, který zpřístupňuje oracle a udržet odesílání dat, dokud oracle řekne jim, že data jsou správná.</span><span class="sxs-lookup"><span data-stu-id="a74af-122">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="a74af-123">Z této odpovědi může útočník dešifrovat bajt zprávy bajtem.</span><span class="sxs-lookup"><span data-stu-id="a74af-123">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="a74af-124">Moderní počítačové sítě jsou tak kvalitní, že útočník dokáže detekovat velmi malé (méně než 0,1 ms) rozdíly v době provádění ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="a74af-124">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span><span data-ttu-id="a74af-125">Aplikace, které předpokládají, že úspěšné dešifrování může dojít pouze v případě, že data nebyla zfalšována s může být náchylné k útoku z nástrojů, které jsou navrženy tak, aby sledovat rozdíly v úspěšné a neúspěšné dešifrování.</span><span class="sxs-lookup"><span data-stu-id="a74af-125"> Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="a74af-126">Zatímco tento rozdíl časování může být významnější v některých jazycích nebo knihovnách než jiné, nyní se předpokládá, že se jedná o praktickou hrozbu pro všechny jazyky a knihovny, když je zohledněna odpověď aplikace na selhání.</span><span class="sxs-lookup"><span data-stu-id="a74af-126">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="a74af-127">Tento útok závisí na schopnosti změnit šifrovaná data a otestovat výsledek s oracle.</span><span class="sxs-lookup"><span data-stu-id="a74af-127">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="a74af-128">Jediným způsobem, jak plně zmírnit útok, je zjistit změny šifrovaných dat a odmítnout na něm provést jakékoli akce.</span><span class="sxs-lookup"><span data-stu-id="a74af-128">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="a74af-129">Standardní způsob, jak to provést, je vytvořit podpis pro data a ověřit tento podpis před provedením všech operací.</span><span class="sxs-lookup"><span data-stu-id="a74af-129">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="a74af-130">Podpis musí být ověřitelný, nemůže být vytvořen útočníkem, jinak by změnil šifrovaná data a poté vypočítal nový podpis na základě změněných dat.</span><span class="sxs-lookup"><span data-stu-id="a74af-130">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="a74af-131">Jeden běžný typ příslušného podpisu se označuje jako kód ověřování zpráv hash (HMAC).</span><span class="sxs-lookup"><span data-stu-id="a74af-131">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="a74af-132">HMAC se liší od kontrolního součtu v tom, že trvá tajný klíč, známý pouze osobě vyrábějící HMAC a osobě, která jej ověřuje.</span><span class="sxs-lookup"><span data-stu-id="a74af-132">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="a74af-133">Bez držení klíče, nemůžete produkovat správné HMAC.</span><span class="sxs-lookup"><span data-stu-id="a74af-133">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="a74af-134">Když obdržíte data, vezmete šifrovaná data, nezávisle vypočítáte HMAC pomocí tajného klíče, který vy a sdílená sdílená odesílatel, a pak porovnáte HMAC, který poslali, s tím, který jste vypočítali.</span><span class="sxs-lookup"><span data-stu-id="a74af-134">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="a74af-135">Toto porovnání musí být konstantní čas, jinak jste přidali další zjistitelné oracle, což umožňuje jiný typ útoku.</span><span class="sxs-lookup"><span data-stu-id="a74af-135">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="a74af-136">Stručně řečeno, chcete-li bezpečně používat polstrované šifry bloků CBC, musíte je kombinovat s HMAC (nebo jinou kontrolou integrity dat), kterou ověříte pomocí porovnání konstantního času před pokusem o dešifrování dat.</span><span class="sxs-lookup"><span data-stu-id="a74af-136">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="a74af-137">Vzhledem k tomu, že všechny změněné zprávy trvat stejné množství času k vytvoření odpovědi, útok je zabráněno.</span><span class="sxs-lookup"><span data-stu-id="a74af-137">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="a74af-138">Kdo je zranitelný</span><span class="sxs-lookup"><span data-stu-id="a74af-138">Who is vulnerable</span></span>

<span data-ttu-id="a74af-139">Tato chyba zabezpečení se vztahuje na spravované i nativní aplikace, které provádějí vlastní šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="a74af-139">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="a74af-140">To zahrnuje například:</span><span class="sxs-lookup"><span data-stu-id="a74af-140">This includes, for example:</span></span>

- <span data-ttu-id="a74af-141">Aplikace, která šifruje soubor cookie pro pozdější dešifrování na serveru.</span><span class="sxs-lookup"><span data-stu-id="a74af-141">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="a74af-142">Databázová aplikace, která uživatelům umožňuje vkládat data do tabulky, jejíž sloupce jsou později dešifrovány.</span><span class="sxs-lookup"><span data-stu-id="a74af-142">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="a74af-143">Aplikace pro přenos dat, která závisí na šifrování pomocí sdíleného klíče k ochraně dat při přenosu.</span><span class="sxs-lookup"><span data-stu-id="a74af-143">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="a74af-144">Aplikace, která šifruje a dešifruje zprávy "uvnitř" tunelu TLS.</span><span class="sxs-lookup"><span data-stu-id="a74af-144">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="a74af-145">Všimněte si, že použití TLS sám nemusí chránit vás v těchto scénářích.</span><span class="sxs-lookup"><span data-stu-id="a74af-145">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="a74af-146">Zranitelná aplikace:</span><span class="sxs-lookup"><span data-stu-id="a74af-146">A vulnerable application:</span></span>

- <span data-ttu-id="a74af-147">Dešifruje data pomocí režimu šifrování CBC s ověřitelným režimem odsazení, například PKCS#7 nebo ANSI X.923.</span><span class="sxs-lookup"><span data-stu-id="a74af-147">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="a74af-148">Provádí dešifrování bez provedení kontroly integrity dat (pomocí MAC nebo asymetrického digitálního podpisu).</span><span class="sxs-lookup"><span data-stu-id="a74af-148">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="a74af-149">To platí také pro aplikace postavené na vrcholu abstrakce nad tyto primitiv, jako je například syntaxe kryptografické zprávy (PKCS # 7/CMS) EnvelopedData struktury.</span><span class="sxs-lookup"><span data-stu-id="a74af-149">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="a74af-150">Související oblasti zájmu</span><span class="sxs-lookup"><span data-stu-id="a74af-150">Related areas of concern</span></span>

<span data-ttu-id="a74af-151">Výzkum vedl Microsoft k dalšímu znepokojení nad zprávami CBC, které jsou doplněny odsazením ekvivalentu ISO 10126, pokud má zpráva známou nebo předvídatelnou strukturu zápatí.</span><span class="sxs-lookup"><span data-stu-id="a74af-151">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="a74af-152">Například obsah připravený podle pravidel w3c XML encryption syntaxe a zpracování doporučení (xmlenc, EncryptedXml).</span><span class="sxs-lookup"><span data-stu-id="a74af-152">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="a74af-153">Zatímco W3C pokyny k podpisu zprávy pak šifrovat bylo považováno za vhodné v té době, Microsoft nyní doporučuje vždy dělat šifrovat-pak podepsat.</span><span class="sxs-lookup"><span data-stu-id="a74af-153">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="a74af-154">Vývojáři aplikací by měli mít vždy na paměti ověření použitelnosti klíče asymetrického podpisu, protože neexistuje žádný vlastní vztah důvěryhodnosti mezi asymetrickým klíčem a libovolnou zprávou.</span><span class="sxs-lookup"><span data-stu-id="a74af-154">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="a74af-155">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a74af-155">Details</span></span>

<span data-ttu-id="a74af-156">Historicky došlo ke shodě, že je důležité šifrovat a ověřovat důležitá data pomocí prostředků, jako jsou podpisy HMAC nebo RSA.</span><span class="sxs-lookup"><span data-stu-id="a74af-156">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="a74af-157">Nicméně, tam byl méně jasné pokyny, jak sekvencovat operace šifrování a ověřování.</span><span class="sxs-lookup"><span data-stu-id="a74af-157">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="a74af-158">Vzhledem k chybě zabezpečení popsané v tomto článku, Pokyny společnosti Microsoft je nyní vždy používat "šifrovat-pak-podepsat" paradigma.</span><span class="sxs-lookup"><span data-stu-id="a74af-158">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="a74af-159">To znamená nejprve šifrovat data pomocí symetrického klíče, pak vypočítat MAC nebo asymetrický podpis přes šifrovaný text (šifrovaná data).</span><span class="sxs-lookup"><span data-stu-id="a74af-159">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="a74af-160">Při dešifrování dat proveďte opačný.</span><span class="sxs-lookup"><span data-stu-id="a74af-160">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="a74af-161">Nejprve potvrďte MAC nebo podpis šifrovacího textu a poté jej dešifrujte.</span><span class="sxs-lookup"><span data-stu-id="a74af-161">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="a74af-162">O třídě zranitelných míst známé jako "vycpávky oracle útoků" je známo, že existují již více než 10 let.</span><span class="sxs-lookup"><span data-stu-id="a74af-162">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="a74af-163">Tyto chyby zabezpečení umožňují útočníkovi dešifrovat data šifrovaná symetrickými blokovými algoritmy, jako jsou AES a 3DES, pomocí maximálně 4096 pokusů na blok dat.</span><span class="sxs-lookup"><span data-stu-id="a74af-163">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="a74af-164">Tyto chyby zabezpečení využívají skutečnosti, že blokové šifry se nejčastěji používají s ověřitelnými daty odsazení podle náhlážních dat na konci.</span><span class="sxs-lookup"><span data-stu-id="a74af-164">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="a74af-165">Bylo zjištěno, že pokud útočník může manipulovat s šifrovaný text a zjistit, zda manipulace způsobila chybu ve formátu odsazení na konci, útočník může dešifrovat data.</span><span class="sxs-lookup"><span data-stu-id="a74af-165">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="a74af-166">Zpočátku byly praktické útoky založeny na službách, které by vracely různé kódy chyb na základě toho, zda je odsazení platné, například ASP.NET zranitelnost [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span><span class="sxs-lookup"><span data-stu-id="a74af-166">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span></span> <span data-ttu-id="a74af-167">Společnost Microsoft se však nyní domnívá, že je praktické provádět podobné útoky pouze pomocí rozdílů v časování mezi zpracováním platného a neplatného odsazení.</span><span class="sxs-lookup"><span data-stu-id="a74af-167">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="a74af-168">Za předpokladu, že schéma šifrování používá podpis a že ověření podpisu je prováděno s pevným časem runtime po danou délku dat (bez ohledu na obsah), lze integritu dat ověřit bez vyzařování jakýchkoli informací útočníkovi prostřednictvím [bočního kanálu](https://en.wikipedia.org/wiki/Side-channel_attack).</span><span class="sxs-lookup"><span data-stu-id="a74af-168">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="a74af-169">Vzhledem k tomu, že kontrola integrity odmítne všechny zfalšované zprávy, je zmírněna hrozba odsazení oracle.</span><span class="sxs-lookup"><span data-stu-id="a74af-169">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="a74af-170">Doprovodné materiály</span><span class="sxs-lookup"><span data-stu-id="a74af-170">Guidance</span></span>

<span data-ttu-id="a74af-171">V první řadě společnost Microsoft doporučuje, aby všechna data, která má důvěrnost potřeby být přenášeny přes zabezpečení transportní vrstvy (TLS), následník ssl (SSL).</span><span class="sxs-lookup"><span data-stu-id="a74af-171">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="a74af-172">Dále analyzujte aplikaci takto:</span><span class="sxs-lookup"><span data-stu-id="a74af-172">Next, analyze your application to:</span></span>

- <span data-ttu-id="a74af-173">Pochopte přesně, jaké šifrování provádíte a jaké šifrování poskytují platformy a api, která používáte.</span><span class="sxs-lookup"><span data-stu-id="a74af-173">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="a74af-174">Ujistěte se, že každé použití v každé vrstvě algoritmu symetrické [blokové šifry](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), například AES a 3DES, v režimu CBC zahrnuje použití kontroly integrity dat s tajným klíčem (asymetrický podpis, HMAC nebo pro změnu režimu šifrování na [režim ověřeného šifrování](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE), jako je GCM nebo CCM).</span><span class="sxs-lookup"><span data-stu-id="a74af-174">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="a74af-175">Na základě aktuálního výzkumu se obecně předpokládá, že pokud jsou kroky ověřování a šifrování prováděny nezávisle pro režimy šifrování bez AE, je ověřování šifrovaného textu (šifrování-pak-sign) nejlepší obecnou volbou.</span><span class="sxs-lookup"><span data-stu-id="a74af-175">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="a74af-176">Neexistuje však žádná univerzální odpověď na kryptografii a toto zobecnění není tak dobré jako pokyny od profesionálního kryptografa.</span><span class="sxs-lookup"><span data-stu-id="a74af-176">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="a74af-177">Aplikace, které nemohou změnit formát zasílání zpráv, ale provádět neověřené cbc dešifrování se doporučuje, aby se pokusili začlenit skutečnosti snižující závažnost rizika, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="a74af-177">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="a74af-178">Dešifrujte, aniž byste dešifrovači povolili ověření nebo odebrání odsazení:</span><span class="sxs-lookup"><span data-stu-id="a74af-178">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="a74af-179">Jakékoli odsazení, které bylo použito, je stále třeba odebrat nebo ignorovat, přesouváte zátěž do aplikace.</span><span class="sxs-lookup"><span data-stu-id="a74af-179">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="a74af-180">Výhodou je, že ověření a odebrání odsazení lze začlenit do jiné logiky ověřování dat aplikace.</span><span class="sxs-lookup"><span data-stu-id="a74af-180">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="a74af-181">Pokud lze ověření odsazení a ověření dat provést v konstantním čase, hrozba se sníží.</span><span class="sxs-lookup"><span data-stu-id="a74af-181">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="a74af-182">Vzhledem k tomu, že interpretace odsazení změní vnímanou délku zprávy, může být stále časování informace vyzařované z tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="a74af-182">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="a74af-183">Změňte režim odsazení dešifrování na ISO10126:</span><span class="sxs-lookup"><span data-stu-id="a74af-183">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="a74af-184">Dešifrovací polstrování ISO10126 je kompatibilní s šifrovacím polstrováním PKCS7 a odsazením šifrování ANSIX923.</span><span class="sxs-lookup"><span data-stu-id="a74af-184">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="a74af-185">Změna režimu snižuje odsazení oracle znalosti na 1 bajt místo celého bloku.</span><span class="sxs-lookup"><span data-stu-id="a74af-185">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="a74af-186">Pokud však má obsah dobře známé zápatí, například uzavírací element XML, související útoky mohou pokračovat v útoku na zbytek zprávy.</span><span class="sxs-lookup"><span data-stu-id="a74af-186">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="a74af-187">To také nezabrání obnovení ve formátu prostého textu v situacích, kdy útočník může domluvit stejný prostý text, který má být šifrován vícekrát s jiným posunem zprávy.</span><span class="sxs-lookup"><span data-stu-id="a74af-187">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="a74af-188">Brána vyhodnocení dešifrování volání tlumit časování signál:</span><span class="sxs-lookup"><span data-stu-id="a74af-188">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="a74af-189">Výpočty doby blokování musí mít minimální hodnotu přesahující maximální dobu, po kterou by dešifrovací operace trvala pro libovolný datový segment, který obsahuje odsazení.</span><span class="sxs-lookup"><span data-stu-id="a74af-189">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="a74af-190">Časové výpočty by měly být prováděny podle pokynů v [získávání časových razítek s vysokým rozlišením](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), nikoli pomocí <xref:System.Environment.TickCount?displayProperty=nameWithType> (s výhradou převrácení / přetečení) nebo odečtením dvou systémových časových razítek (s výhradou chyb úprav NTP).</span><span class="sxs-lookup"><span data-stu-id="a74af-190">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="a74af-191">Časové výpočty musí zahrnovat dešifrovací operaci včetně všech možných výjimek ve spravovaných aplikacích nebo aplikacích jazyka C++, které nejsou pouze doplněny do konce.</span><span class="sxs-lookup"><span data-stu-id="a74af-191">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="a74af-192">Pokud úspěch nebo neúspěch byl ještě určen, časování brány musí vrátit selhání po vypršení jeho platnosti.</span><span class="sxs-lookup"><span data-stu-id="a74af-192">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="a74af-193">Služby, které provádějí neověřené dešifrování by měl mít monitorování na místě zjistit, že záplava "neplatné" zprávy prošel.</span><span class="sxs-lookup"><span data-stu-id="a74af-193">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="a74af-194">Mějte na paměti, že tento signál nese jak falešně pozitivní výsledky (legitimně poškozená data), tak falešné negativy (šíření útoku po dostatečně dlouhou dobu, aby se vyhnul detekci).</span><span class="sxs-lookup"><span data-stu-id="a74af-194">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="a74af-195">Hledání ohroženého kódu – nativní aplikace</span><span class="sxs-lookup"><span data-stu-id="a74af-195">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="a74af-196">Pro programy vytvořené v porovnání s kryptografií systému Windows: Knihovna nové generace (CNG):</span><span class="sxs-lookup"><span data-stu-id="a74af-196">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="a74af-197">Dešifrování volání je [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), zadání `BCRYPT_BLOCK_PADDING` příznaku.</span><span class="sxs-lookup"><span data-stu-id="a74af-197">The decryption call is to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="a74af-198">Popisovač klíče byl inicializován voláním [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) s [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) nastavena na `BCRYPT_CHAIN_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="a74af-198">The key handle has been initialized by calling [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) with [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="a74af-199">Vzhledem k tomu, `BCRYPT_CHAIN_MODE_CBC` že je výchozí, `BCRYPT_CHAINING_MODE`nemusí být ovlivněný kód přiřazena žádná hodnota pro .</span><span class="sxs-lookup"><span data-stu-id="a74af-199">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="a74af-200">Pro programy vytvořené podle staršího kryptografického rozhraní API systému Windows:</span><span class="sxs-lookup"><span data-stu-id="a74af-200">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="a74af-201">Dešifrování volání je [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) s `Final=TRUE`.</span><span class="sxs-lookup"><span data-stu-id="a74af-201">The decryption call is to [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) with `Final=TRUE`.</span></span>
- <span data-ttu-id="a74af-202">Popisovač klíče byl inicializován voláním [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) s [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) nastavena na `CRYPT_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="a74af-202">The key handle has been initialized by calling [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) with [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="a74af-203">Vzhledem k tomu, `CRYPT_MODE_CBC` že je výchozí, `KP_MODE`nemusí být ovlivněný kód přiřazena žádná hodnota pro .</span><span class="sxs-lookup"><span data-stu-id="a74af-203">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="a74af-204">Hledání ohroženého kódu – spravované aplikace</span><span class="sxs-lookup"><span data-stu-id="a74af-204">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="a74af-205">Volání dešifrování je <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> na metody <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> or <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>na .</span><span class="sxs-lookup"><span data-stu-id="a74af-205">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="a74af-206">To zahrnuje následující odvozené typy v rámci rozhraní .NET, ale může také zahrnovat typy třetích stran:</span><span class="sxs-lookup"><span data-stu-id="a74af-206">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="a74af-207">Vlastnost <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> byla nastavena <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>na <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType> <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, nebo .</span><span class="sxs-lookup"><span data-stu-id="a74af-207">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="a74af-208">Vzhledem k tomu, <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> že je <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> výchozí, ohrožený kód pravděpodobně nikdy nepřiřadil vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a74af-208">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="a74af-209">Vlastnost <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> byla nastavena na<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a74af-209">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="a74af-210">Vzhledem k tomu, <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> že je <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> výchozí, ohrožený kód pravděpodobně nikdy nepřiřadil vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a74af-210">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="a74af-211">Hledání ohroženého kódu – syntaxe kryptografické zprávy</span><span class="sxs-lookup"><span data-stu-id="a74af-211">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="a74af-212">Neověřená zpráva CMS EnvelopedData, jejíž šifrovaný obsah používá režim CBC amonného (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) nebo RC2 (1.2.840.113549.3.2) je zranitelné, stejně jako zprávy pomocí jiných algoritmů blokové šifry v režimu CBC.</span><span class="sxs-lookup"><span data-stu-id="a74af-212">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="a74af-213">Zatímco šifry datového proudu nejsou náchylné k této konkrétní chybě zabezpečení, společnost Microsoft doporučuje vždy ověřování dat přes kontrolu ContentEncryptionAlgorithm hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a74af-213">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="a74af-214">U spravovaných aplikací lze objekt blob CMS EnvelopedData <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>zjistit jako libovolnou hodnotu, která je předána společnosti .</span><span class="sxs-lookup"><span data-stu-id="a74af-214">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="a74af-215">Pro nativní aplikace cms envelopedData objekt blob může být detekován jako libovolná hodnota poskytnutá popisovači CMS prostřednictvím [CryptMsgUpdate,](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) jehož výsledný [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) je `CMSG_ENVELOPED` a/nebo popisovač CMS je později odeslán `CMSG_CTRL_DECRYPT` a instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span><span class="sxs-lookup"><span data-stu-id="a74af-215">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) whose resulting [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="a74af-216">Příklad ohroženého kódu – spravováno</span><span class="sxs-lookup"><span data-stu-id="a74af-216">Vulnerable code example - managed</span></span>

<span data-ttu-id="a74af-217">Tato metoda přečte soubor cookie a dešifruje jej a není viditelná žádná kontrola integrity dat.</span><span class="sxs-lookup"><span data-stu-id="a74af-217">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="a74af-218">Obsah souboru cookie, který je přečten touto metodou, může být proto napaden uživatelem, který jej obdržel, nebo útočníkem, který získal zašifrovanou hodnotu souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="a74af-218">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="a74af-219">Příklad kódu následujícího po doporučených postupech – spravováno</span><span class="sxs-lookup"><span data-stu-id="a74af-219">Example code following recommended practices - managed</span></span>

<span data-ttu-id="a74af-220">Následující ukázkový kód používá nestandardní formát zpráv</span><span class="sxs-lookup"><span data-stu-id="a74af-220">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="a74af-221">kde `cipher_algorithm_id` identifikátory a `hmac_algorithm_id` algoritmu jsou lokální (nestandardní) reprezentace těchto algoritmů.</span><span class="sxs-lookup"><span data-stu-id="a74af-221">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="a74af-222">Tyto identifikátory může mít smysl v jiných částech existující protokol zasílání zpráv namísto jako holý zřetězený bytestream.</span><span class="sxs-lookup"><span data-stu-id="a74af-222">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="a74af-223">Tento příklad také používá jeden hlavní klíč k odvození šifrovacího klíče i klíče HMAC.</span><span class="sxs-lookup"><span data-stu-id="a74af-223">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="a74af-224">To je k dispozici jak pro použití singly-keyed aplikace do aplikace s dvěma klávesami a podporovat zachování dvou klíčů jako různé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a74af-224">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="a74af-225">Dále zaručuje, že klíč HMAC a šifrovací klíč se nemohou dostat ze synchronizace.</span><span class="sxs-lookup"><span data-stu-id="a74af-225">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="a74af-226">Tato ukázka <xref:System.IO.Stream> nepřijímá šifrování nebo dešifrování.</span><span class="sxs-lookup"><span data-stu-id="a74af-226">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="a74af-227">Aktuální formát dat ztěžuje jednoprůchodové `hmac_tag` šifrování, protože hodnota předchází šifrovanému textu.</span><span class="sxs-lookup"><span data-stu-id="a74af-227">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="a74af-228">Tento formát byl však vybrán, protože udržuje všechny prvky pevné velikosti na začátku zachovat analyzátor jednodušší.</span><span class="sxs-lookup"><span data-stu-id="a74af-228">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="a74af-229">S tímto formátem dat je možné jednoprůchodové dešifrování, i když implementátor je upozorněn na volání GetHashAndReset a ověřit výsledek před voláním TransformFinalBlock.</span><span class="sxs-lookup"><span data-stu-id="a74af-229">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="a74af-230">Pokud je důležité šifrování datových proudů, může být vyžadován jiný režim AE.</span><span class="sxs-lookup"><span data-stu-id="a74af-230">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
