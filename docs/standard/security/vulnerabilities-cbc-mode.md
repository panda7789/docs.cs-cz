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
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="df57b-103">Ohrožení zabezpečení časování s režimu CBC Symetrické dešifrování pomocí odsazení</span><span class="sxs-lookup"><span data-stu-id="df57b-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="df57b-104">Společnosti Microsoft, podle aktuálně známé kryptografickém výzkumu se považuje za, s výjimkou velmi konkrétní okolností už bezpečné dešifrovat data šifrují s režimem Cipher Block Chaining CBC symetrického šifrování, pokud byl ověřitelný odsazení použít bez první zajistíte integritu šifrovaný text.</span><span class="sxs-lookup"><span data-stu-id="df57b-104">Microsoft, based on currently known cryptographic research, believes that, except for very specific circumstances, it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext.</span></span>

## <a name="introduction"></a><span data-ttu-id="df57b-105">Úvod</span><span class="sxs-lookup"><span data-stu-id="df57b-105">Introduction</span></span>

<span data-ttu-id="df57b-106">Útoku odsazení oracle je typ útoku proti šifrovaná data, která umožňuje útočník dešifrovat obsah data, aniž by věděly, klíč.</span><span class="sxs-lookup"><span data-stu-id="df57b-106">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="df57b-107">Oracle odkazuje "říct" které dává útočník informace o tom, zda akci, kterou jste provedením jejich správné nebo ne.</span><span class="sxs-lookup"><span data-stu-id="df57b-107">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="df57b-108">Představte si přehrávání panelu nebo karty hry s podřízeným.</span><span class="sxs-lookup"><span data-stu-id="df57b-108">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="df57b-109">Pokud svůj vzhled rozsvítí s velký smajlíka vzhledem k tomu, že se domnívá, že uživatel je o aby dobrý přesunu, která je oracle.</span><span class="sxs-lookup"><span data-stu-id="df57b-109">When her face lights up with a big smile because she thinks she's about to make a good move, that's an oracle.</span></span> <span data-ttu-id="df57b-110">Jako protihráče, můžete tento oracle plánování vaší další přesunutí správně.</span><span class="sxs-lookup"><span data-stu-id="df57b-110">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="df57b-111">Odsazení je konkrétní kryptografických období.</span><span class="sxs-lookup"><span data-stu-id="df57b-111">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="df57b-112">Některé šifry, které jsou algoritmy používané k šifrování dat, fungovat na bloky dat, kde je každý blok s pevnou velikostí.</span><span class="sxs-lookup"><span data-stu-id="df57b-112">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="df57b-113">Pokud data chcete šifrovat není správnou velikost k vyplnění na bloky, vaše data doplněno dokud dělá.</span><span class="sxs-lookup"><span data-stu-id="df57b-113">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="df57b-114">Mnoho forem odsazení vyžadují tento odsazení vždy nacházet, i když původní vstup byl správnou velikost.</span><span class="sxs-lookup"><span data-stu-id="df57b-114">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="df57b-115">To umožňuje odsazení vždy bezpečně odeberou při dešifrování.</span><span class="sxs-lookup"><span data-stu-id="df57b-115">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="df57b-116">Připravuje umístění dvě věci softwaru implementace s oracle odsazení zjistí, zda dešifrovaná data má platný odsazení.</span><span class="sxs-lookup"><span data-stu-id="df57b-116">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="df57b-117">Oracle může být jednoduché, vrátí hodnotu, která říká "Neplatný odsazení" něco nebo něco složitější jako měřitelný výkon různých doba zpracování platný blok oproti bloku neplatný.</span><span class="sxs-lookup"><span data-stu-id="df57b-117">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="df57b-118">Blokový šifry mít jinou vlastnost s názvem režimu, který určuje vztah dat v prvním bloku k datům ve druhé blok, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="df57b-118">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="df57b-119">Jeden z režimů nejčastěji používané je CBC.</span><span class="sxs-lookup"><span data-stu-id="df57b-119">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="df57b-120">CBC uvádí počáteční náhodné bloku známé jako inicializační vektor (IV) a kombinuje k předchozímu bloku s výsledkem statické šifrování, aby bylo tak, že šifrování stejná zpráva se stejným klíčem není vždy vytvořila stejný šifrované výstup.</span><span class="sxs-lookup"><span data-stu-id="df57b-120">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="df57b-121">Útočník může použít odsazení oracle, v kombinaci s struktury CBC dat, mírně změněné zprávy poslat kód, který zveřejňuje oracle a zachovat odesílání dat, dokud se sdělením, oracle je správná data.</span><span class="sxs-lookup"><span data-stu-id="df57b-121">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="df57b-122">Z této odpovědi může útočník dešifrování zprávy bajtů podle bajtů.</span><span class="sxs-lookup"><span data-stu-id="df57b-122">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="df57b-123">Moderní počítače sítě jsou takové vysoké kvality, že útočník může zjistit velmi malé (méně než 0,1 ms) rozdíly v provádění čas na vzdálené systémy.</span><span class="sxs-lookup"><span data-stu-id="df57b-123">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span> <span data-ttu-id="df57b-124">Aplikace, které jsou za předpokladu, že úspěšné dešifrování může dojít pouze v případě dat nebylo manipulováno může být zranitelný vůči útokům z nástroje, které jsou navržené tak, abyste viděli rozdíly v úspěšné a neúspěšné dešifrování.</span><span class="sxs-lookup"><span data-stu-id="df57b-124">Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="df57b-125">Tento rozdíl časování může být v některých jazycích nebo knihovny větších než jiná, nyní předpokládá se toto je praktické hrozbu pro všechny jazyky a knihovny, když je aplikace odpověď selhání vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="df57b-125">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="df57b-126">Tento útok spoléhá na možnost změnit šifrovaných dat a testování výsledků oracle.</span><span class="sxs-lookup"><span data-stu-id="df57b-126">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="df57b-127">Jediný způsob, jak plně zmírnit útok je detekovat změny k šifrovaným datům a odmítnout na něm provádět žádné akce.</span><span class="sxs-lookup"><span data-stu-id="df57b-127">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="df57b-128">Standardním způsobem k tomu je k vytvoření podpisu pro data a ověření této podpis před provedením jakékoli operace.</span><span class="sxs-lookup"><span data-stu-id="df57b-128">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="df57b-129">Podpis musí být ověřitelný, nemůže být vytvořený útočník, jinak se by přejít šifrovaná data, a potom výpočetní nový podpis podle změněná data.</span><span class="sxs-lookup"><span data-stu-id="df57b-129">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="df57b-130">Jeden běžný typ odpovídajícím podpisem se označuje jako ověřovací kód zprávy keyed-hash (HMAC).</span><span class="sxs-lookup"><span data-stu-id="df57b-130">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="df57b-131">HMAC se liší od kontrolní součet v, že trvá tajný klíč známý jenom osobě generovala HMAC a osobě, její ověřování.</span><span class="sxs-lookup"><span data-stu-id="df57b-131">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="df57b-132">Bez vlastní klíč nelze vytvořit správný HMAC.</span><span class="sxs-lookup"><span data-stu-id="df57b-132">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="df57b-133">Jakmile se zobrazí vaše data, můžete provést šifrovaná data, nezávisle výpočetní HMAC pomocí tajný klíč můžete a sdílenou složku odesílatele, a potom porovnat HMAC odešlou proti ten je počítaný.</span><span class="sxs-lookup"><span data-stu-id="df57b-133">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="df57b-134">Toto porovnání musí být konstantní čas, jinak jste přidali další rozpoznat oracle, povolení jiný typ útoku.</span><span class="sxs-lookup"><span data-stu-id="df57b-134">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="df57b-135">V souhrnu používat vyplní CBC bloku šifry bezpečně, je nutné zkombinovat s HMAC s klíčem (nebo jiné kontrolu integrity dat), který můžete ověřit pomocí porovnání konstantní čas a teprve potom zkusili data dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="df57b-135">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="df57b-136">Vzhledem k tomu, že všechny zprávy změněna využít současně velikost k vytvoření odpovědi, je-li vypnuto útoku.</span><span class="sxs-lookup"><span data-stu-id="df57b-136">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="df57b-137">Kdo je snadno napadnutelný</span><span class="sxs-lookup"><span data-stu-id="df57b-137">Who is vulnerable</span></span>

<span data-ttu-id="df57b-138">Toto ohrožení zabezpečení se vztahuje na spravovaná a nativní aplikace, které fungují vlastní šifrování a dešifrování.</span><span class="sxs-lookup"><span data-stu-id="df57b-138">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="df57b-139">To zahrnuje, například:</span><span class="sxs-lookup"><span data-stu-id="df57b-139">This includes, for example:</span></span>

- <span data-ttu-id="df57b-140">Aplikace, která zašifruje do souboru cookie pro novější dešifrování na serveru.</span><span class="sxs-lookup"><span data-stu-id="df57b-140">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="df57b-141">Databáze aplikace, která poskytuje možnosti pro uživatele k vložení dat do tabulky, jejichž sloupce se dešifrují později.</span><span class="sxs-lookup"><span data-stu-id="df57b-141">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="df57b-142">Aplikace pro přenos dat, která využívá šifrování pomocí sdílený klíč k ochraně dat během přenosu.</span><span class="sxs-lookup"><span data-stu-id="df57b-142">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="df57b-143">Aplikace, který šifruje a dešifruje zprávy "vnitřních" tunelu TLS.</span><span class="sxs-lookup"><span data-stu-id="df57b-143">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="df57b-144">Mějte na paměti, který používá protokol TLS samostatně nemusí chránit v těchto scénářích.</span><span class="sxs-lookup"><span data-stu-id="df57b-144">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="df57b-145">K citlivé aplikaci:</span><span class="sxs-lookup"><span data-stu-id="df57b-145">A vulnerable application:</span></span>

- <span data-ttu-id="df57b-146">Dešifruje data pomocí režimu CBC šifrování s režimem ověřitelný odsazení, jako je například PKCS #7 nebo ANSI X.923.</span><span class="sxs-lookup"><span data-stu-id="df57b-146">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="df57b-147">Provede dešifrování bez nutnosti provést kontrolu integrity dat (prostřednictvím MAC nebo digitální podpis asymetrické).</span><span class="sxs-lookup"><span data-stu-id="df57b-147">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="df57b-148">To platí také pro aplikace nástavbou abstrakce v horní části tyto základní prvky, jako je například struktura EnvelopedData Cryptographic Message Syntax (PKCS #7/CMS).</span><span class="sxs-lookup"><span data-stu-id="df57b-148">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="df57b-149">Související oblastí zájmu</span><span class="sxs-lookup"><span data-stu-id="df57b-149">Related areas of concern</span></span>

<span data-ttu-id="df57b-150">Research vedlo Microsoft se další starat o CBC zprávy, které se vyplní ISO 10126-ekvivalentem odsazení při zpráva má struktura dobře známé nebo předvídatelný zápatí stránky.</span><span class="sxs-lookup"><span data-stu-id="df57b-150">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="df57b-151">Například obsah připravit v části pravidla W3C XML šifrování syntaxe a zpracování doporučení (xmlenc, EncryptedXml).</span><span class="sxs-lookup"><span data-stu-id="df57b-151">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="df57b-152">Zatímco pokyny W3C podepsat zprávu pak šifrování byl v době považuje za vhodné, Microsoft teď doporučuje vždy to šifrovat přihlašovací potom.</span><span class="sxs-lookup"><span data-stu-id="df57b-152">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="df57b-153">Vývojáři aplikace musí být vždy s vědomím ověření použitelnost klíčem asymetrické podpis není žádný vztah důvěry vyplývajících mezi asymetrický klíč a libovolný zprávy.</span><span class="sxs-lookup"><span data-stu-id="df57b-153">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="df57b-154">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="df57b-154">Details</span></span>

<span data-ttu-id="df57b-155">V minulosti došlo konsenzu, který je důležité k šifrování i ověřování důležitých dat, prostředky, jako je například HMAC nebo RSA podpisů.</span><span class="sxs-lookup"><span data-stu-id="df57b-155">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="df57b-156">Ale musí být menší jasné pokyny, jak pořadí operace šifrování a ověřování.</span><span class="sxs-lookup"><span data-stu-id="df57b-156">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="df57b-157">Z důvodu chyby zabezpečení, popsané v tomto článku pokyny společnosti Microsoft nyní je vždy nutné použít zlepší "šifrování potom přihlášení".</span><span class="sxs-lookup"><span data-stu-id="df57b-157">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="df57b-158">To znamená nejprve šifrování dat pomocí symetrického klíče, a poté výpočetním MAC nebo asymetrický podpis přes šifrovaný text (šifrovaná data).</span><span class="sxs-lookup"><span data-stu-id="df57b-158">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="df57b-159">K dešifrování dat, proveďte naopak.</span><span class="sxs-lookup"><span data-stu-id="df57b-159">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="df57b-160">Nejprve zkontrolujte MAC nebo podpis šifrovaný text a potom ho dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="df57b-160">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="df57b-161">Třída chyb zabezpečení, které označuje jako "odsazení oracle útoky" známé existovat více než deset let.</span><span class="sxs-lookup"><span data-stu-id="df57b-161">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="df57b-162">Tyto chyby zabezpečení útočníkovi umožnit dešifrovat data zašifrovaná pomocí bloku symetrické algoritmy, například šifrování AES a 3DES, pomocí více než 4096 pokusů za datového bloku.</span><span class="sxs-lookup"><span data-stu-id="df57b-162">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="df57b-163">Ujistěte se, tyto chyby zabezpečení použijte skutečnost, že blokovat šifry nejčastěji používaných s daty ověřitelný odsazení na konci.</span><span class="sxs-lookup"><span data-stu-id="df57b-163">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="df57b-164">Bylo zjištěno, že pokud útočník můžete manipulovat s ciphertext a zjistit, jestli manipulaci způsobilo chybu ve formátu odsazení na konci, útočník může data dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="df57b-164">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="df57b-165">Standardně jsou praktické útoky založené na služby, které by návratové kódy jiné chyby, které jsou založené na tom, zda byl platný, jako je například ohrožení zabezpečení ASP.NET odsazení [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span><span class="sxs-lookup"><span data-stu-id="df57b-165">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span></span> <span data-ttu-id="df57b-166">Však Microsoft teď dochází k závěru, že je potřeba provést podobné útoky pomocí pouze rozdíly v časování mezi zpracování platné a neplatné odsazení.</span><span class="sxs-lookup"><span data-stu-id="df57b-166">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="df57b-167">Za předpokladu, že schéma šifrování používá podpis a ověření podpisu se provádí s pevnou runtime pro dané délky dat (bez ohledu na obsah), můžete ověřit integritu dat bez generování žádné informace Útočník prostřednictvím [straně kanál](https://en.wikipedia.org/wiki/Side-channel_attack).</span><span class="sxs-lookup"><span data-stu-id="df57b-167">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="df57b-168">Vzhledem k tomu, že kontrola integrity odmítne všechny zmanipulovanou zprávy, zmírnit hrozby oracle odsazení.</span><span class="sxs-lookup"><span data-stu-id="df57b-168">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="df57b-169">Doprovodné materiály</span><span class="sxs-lookup"><span data-stu-id="df57b-169">Guidance</span></span>

<span data-ttu-id="df57b-170">Především společnost Microsoft doporučuje, aby žádná data, která má důvěrnost musí přenášet přes zabezpečení TLS (Transport Layer), nástupcem do vrstvy SSL (Secure Sockets).</span><span class="sxs-lookup"><span data-stu-id="df57b-170">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="df57b-171">V dalším kroku analyzujte aplikace:</span><span class="sxs-lookup"><span data-stu-id="df57b-171">Next, analyze your application to:</span></span>

- <span data-ttu-id="df57b-172">Rady pro pochopení přesněji jaké šifrování, provádění a probíhá zajišťuje šifrování, jaké platformy a rozhraní API používáte.</span><span class="sxs-lookup"><span data-stu-id="df57b-172">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="df57b-173">Se ujistěte, zda každý využití v jednotlivých vrstvách služby symetrický [bloku šifrovací algoritmus](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), jako například šifrování AES a 3DES v režimu CBC začlenit použití kontrolu integrity dat s klíči tajný klíč (asymetrické podpis, klíčem HMAC, nebo chcete-li změnit režim šifrovací [ověřený šifrování](https://en.wikipedia.org/wiki/Authenticated_encryption) režimu (AE), jako je například GCM nebo CCM).</span><span class="sxs-lookup"><span data-stu-id="df57b-173">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="df57b-174">Podle aktuální research, obecně předpokládá se, že při ověřování a šifrování kroky se provádí nezávisle bez AE režimy šifrování, ověřování šifrovaný text (šifrování potom podepsání) lze nejvhodnější Obecné možnosti.</span><span class="sxs-lookup"><span data-stu-id="df57b-174">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="df57b-175">Však neexistuje žádná univerzálně správnou odpověď na šifrování a tento generalizace není dosahovat směrovanou Rady, jak z professional cryptographer.</span><span class="sxs-lookup"><span data-stu-id="df57b-175">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="df57b-176">Aplikace, které se nepodařilo změnit jejich zasílání zpráv formátu ale provést neověřené CBC dešifrování se doporučuje pokusí začlenit způsoby zmírnění rizik, jako:</span><span class="sxs-lookup"><span data-stu-id="df57b-176">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="df57b-177">Dešifrování bez povolení-li ověřit nebo odebrat odsazení:</span><span class="sxs-lookup"><span data-stu-id="df57b-177">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="df57b-178">Všechny odsazení, které bylo použito stále je nutné odebrat nebo ignorovat, přesouváte zatížení do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="df57b-178">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="df57b-179">Výhodou je, že ověření odsazení a odebrání lze začlenit do jiné logiku ověření dat aplikace.</span><span class="sxs-lookup"><span data-stu-id="df57b-179">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="df57b-180">Pokud v čase konstantní lze provést ověření odsazení a ověření dat, se snižuje riziko, že.</span><span class="sxs-lookup"><span data-stu-id="df57b-180">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="df57b-181">Vzhledem k tomu, že se výklad odsazení změní délka dosahovaný zprávy, je stále možné časování informace vygenerované z tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="df57b-181">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="df57b-182">Změňte režim odsazení dešifrování ISO10126:</span><span class="sxs-lookup"><span data-stu-id="df57b-182">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="df57b-183">Odsazení dešifrování ISO10126 je kompatibilní s PKCS7 šifrování odsazení a odsazení ANSIX923 šifrování.</span><span class="sxs-lookup"><span data-stu-id="df57b-183">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="df57b-184">Změna režimu snižuje znalosti oracle odsazení do 1 bajtů místo celý blok.</span><span class="sxs-lookup"><span data-stu-id="df57b-184">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="df57b-185">Ale pokud obsah obsahuje dobře známé zápatí stránky, jako je například ukončovací XML element může dál související útoky vůči útokům rest zprávy.</span><span class="sxs-lookup"><span data-stu-id="df57b-185">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="df57b-186">To také nezabrání obnovení ve formátu prostého textu v situacích, kdy útočník může coerce stejné jako prostý text k zašifrování vícekrát s posunem jiná zpráva.</span><span class="sxs-lookup"><span data-stu-id="df57b-186">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="df57b-187">Vyhodnocení volání dešifrování Ztlumit časování signál brány:</span><span class="sxs-lookup"><span data-stu-id="df57b-187">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="df57b-188">Výpočet doby uchování musí mít minimálně nad maximální množství času, které by pro datový segment, který obsahuje odsazení provést operaci dešifrování.</span><span class="sxs-lookup"><span data-stu-id="df57b-188">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="df57b-189">Čas výpočty by mělo být provedeno podle pokynů v [získávání s vysokým rozlišením časová razítka](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), nikoli pomocí <xref:System.Environment.TickCount?displayProperty=nameWithType> (přičemž podléhá kumulativní přes nebo přetečení) nebo odečtením dvě časová razítka systému (přičemž podléhá úpravu NTP chyby).</span><span class="sxs-lookup"><span data-stu-id="df57b-189">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="df57b-190">Výpočty čas musí být včetně dešifrovací operace, včetně všechny potenciální výjimky v spravované nebo aplikací C++, ne jenom odsazenou na konci.</span><span class="sxs-lookup"><span data-stu-id="df57b-190">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="df57b-191">Pokud úspěch nebo neúspěch byla zjištěna ještě, časování brány musí vrátit selhání při jeho platnost vyprší.</span><span class="sxs-lookup"><span data-stu-id="df57b-191">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="df57b-192">Služby, které fungují neověřené dešifrování by měl mít zavedené ke zjištění, zda velké množství "neplatný" zprávy zase monitorování.</span><span class="sxs-lookup"><span data-stu-id="df57b-192">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="df57b-193">Berte v úvahu, že tento signál představuje falešně pozitivních (legálně poškozená data) a výsledkům (rozšíří útoku přes dostatečně dlouhou dobu obejít zjišťování).</span><span class="sxs-lookup"><span data-stu-id="df57b-193">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="df57b-194">Hledání kódu citlivé - nativních aplikací</span><span class="sxs-lookup"><span data-stu-id="df57b-194">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="df57b-195">Pro programy, které jsou vytvořeny kryptografický modul systému Windows: Knihovna generace (CNG):</span><span class="sxs-lookup"><span data-stu-id="df57b-195">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="df57b-196">Dešifrování volání je [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), zadání `BCRYPT_BLOCK_PADDING` příznak.</span><span class="sxs-lookup"><span data-stu-id="df57b-196">The decryption call is to [BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="df57b-197">Popisovač klíče byla inicializována voláním [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) s [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) nastavena na `BCRYPT_CHAIN_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="df57b-197">The key handle has been initialized by calling [BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx) with [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="df57b-198">Vzhledem k tomu `BCRYPT_CHAIN_MODE_CBC` je výchozí nastavení ovlivněných kód nesmí mít přiřazeno žádnou hodnotu pro `BCRYPT_CHAINING_MODE`.</span><span class="sxs-lookup"><span data-stu-id="df57b-198">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="df57b-199">Pro programy vytvořené starší kryptografické rozhraní API systému Windows:</span><span class="sxs-lookup"><span data-stu-id="df57b-199">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="df57b-200">Dešifrování volání je [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) s `Final=TRUE`.</span><span class="sxs-lookup"><span data-stu-id="df57b-200">The decryption call is to [CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx) with `Final=TRUE`.</span></span>
- <span data-ttu-id="df57b-201">Popisovač klíče byla inicializována voláním [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) s [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) nastavena na `CRYPT_MODE_CBC`.</span><span class="sxs-lookup"><span data-stu-id="df57b-201">The key handle has been initialized by calling [CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx) with [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="df57b-202">Vzhledem k tomu `CRYPT_MODE_CBC` je výchozí nastavení ovlivněných kód nesmí mít přiřazeno žádnou hodnotu pro `KP_MODE`.</span><span class="sxs-lookup"><span data-stu-id="df57b-202">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="df57b-203">Hledání kódu citlivé - spravované aplikace</span><span class="sxs-lookup"><span data-stu-id="df57b-203">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="df57b-204">Dešifrování volání je <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> nebo <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> metody na <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df57b-204">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="df57b-205">To zahrnuje následující typy odvozené v rámci .NET, ale může také zahrnovat typy třetí strany:</span><span class="sxs-lookup"><span data-stu-id="df57b-205">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="df57b-206"><xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> Byla nastavena na <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, nebo <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df57b-206">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="df57b-207">Vzhledem k tomu <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> je výchozí nastavení ovlivněných kódu může nikdy přiřadili <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="df57b-207">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="df57b-208"><xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> Byla nastavena na <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="df57b-208">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="df57b-209">Vzhledem k tomu <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> je výchozí nastavení ovlivněných kódu může nikdy přiřadili <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="df57b-209">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="df57b-210">Hledání kódu citlivé - syntaxe kryptografických zpráv</span><span class="sxs-lookup"><span data-stu-id="df57b-210">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="df57b-211">Neověřená zpráva CMS EnvelopedData jejichž šifrovaný obsah používá režimu CBC šifrování DES (1.3.14.3.2.7), AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), algoritmus 3DES (1.2.840.113549.3.7) nebo RC2 (1.2.840.113549.3.2) je snadno napadnutelný, stejně jako zprávy pomocí jakékoli jiné šifrovací algoritmy bloku v režimu CBC.</span><span class="sxs-lookup"><span data-stu-id="df57b-211">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="df57b-212">Když datový proud šifry nejsou náchylné k této konkrétní chyby, společnost Microsoft doporučuje, vždy ověřování data přes zkontrolujete ContentEncryptionAlgorithm hodnota.</span><span class="sxs-lookup"><span data-stu-id="df57b-212">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="df57b-213">Pro spravované aplikace, CMS EnvelopedData, blob může být zjištěna jako jakoukoli hodnotu, která je předána <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="df57b-213">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="df57b-214">Pro nativní aplikace, bude možné zjišťovat objekt blob CMS EnvelopedData jako libovolná hodnota zadaná pro popisovač CMS prostřednictvím [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) jejichž výsledná [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) je `CMSG_ENVELOPED` nebo je popisovač CMS později odeslané `CMSG_CTRL_DECRYPT` instrukce prostřednictvím [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).</span><span class="sxs-lookup"><span data-stu-id="df57b-214">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx) whose resulting [CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="df57b-215">Příklad citlivé kódu - spravované</span><span class="sxs-lookup"><span data-stu-id="df57b-215">Vulnerable code example - managed</span></span>

<span data-ttu-id="df57b-216">Tato metoda přečte soubor cookie a dešifruje ji a žádné kontrolu integrity dat je viditelná.</span><span class="sxs-lookup"><span data-stu-id="df57b-216">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="df57b-217">Obsah souboru cookie, který je pro čtení, tato metoda může být proto napadení uživatel, který ji obdržela, nebo jakékoli útočník, který má získat hodnotu šifrovaného souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="df57b-217">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="df57b-218">Následující příklad kódu doporučené postupy - spravované</span><span class="sxs-lookup"><span data-stu-id="df57b-218">Example code following recommended practices - managed</span></span>

<span data-ttu-id="df57b-219">Následující vzorový kód používá formát nestandardní zprávy z</span><span class="sxs-lookup"><span data-stu-id="df57b-219">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="df57b-220">kde `cipher_algorithm_id` a `hmac_algorithm_id` místní aplikace (nestandardní) reprezentace tyto algoritmy jsou algoritmus identifikátory.</span><span class="sxs-lookup"><span data-stu-id="df57b-220">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="df57b-221">Tyto identifikátory může mít smysl v dalších částí vaší existující zasílání zpráv protokolu místo jako úplné zřetězených bytestream.</span><span class="sxs-lookup"><span data-stu-id="df57b-221">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="df57b-222">Tento příklad také používá jeden hlavní klíč odvození šifrovací klíč a klíčem HMAC s klíčem.</span><span class="sxs-lookup"><span data-stu-id="df57b-222">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="df57b-223">To se i pro potřeby poskytuje pro vypnutí samostatně keyed aplikace do aplikace s klíči duální a podporovat zachování dva klíče jako různé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="df57b-223">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="df57b-224">Další zaručuje, že mimo synchronizace nelze získat HMAC klíč a šifrovací klíč.</span><span class="sxs-lookup"><span data-stu-id="df57b-224">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="df57b-225">Tato ukázka nepřijímá <xref:System.IO.Stream> pro šifrování nebo dešifrování.</span><span class="sxs-lookup"><span data-stu-id="df57b-225">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="df57b-226">Aktuální díky formátu dat jeden průchodu šifrování obtížné protože `hmac_tag` hodnotu předchází šifrovaný text.</span><span class="sxs-lookup"><span data-stu-id="df57b-226">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="df57b-227">Tento formát však jste vybrali, protože všechny prvky pevné velikosti udržuje na začátku zachovat analyzátor jednodušší.</span><span class="sxs-lookup"><span data-stu-id="df57b-227">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="df57b-228">Díky tento formát dat je možné, jeden průchodu dešifrování, i když je implementátor cautioned volání GetHashAndReset a ověřit před voláním TransformFinalBlock výsledek.</span><span class="sxs-lookup"><span data-stu-id="df57b-228">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="df57b-229">Pokud streamování šifrování je důležité, může se vyžadovat jiný režim AE.</span><span class="sxs-lookup"><span data-stu-id="df57b-229">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
