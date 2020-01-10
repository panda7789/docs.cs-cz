---
title: Kryptografický model rozhraní .NET framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: f0c00e4cc866c537fe26dd1ad466d6cde95bc608
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706224"
---
# <a name="net-framework-cryptography-model"></a><span data-ttu-id="38378-102">Kryptografický model rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="38378-102">.NET Framework Cryptography Model</span></span>

<span data-ttu-id="38378-103">.NET Framework poskytuje implementace mnoha standardních kryptografických algoritmů.</span><span class="sxs-lookup"><span data-stu-id="38378-103">The .NET Framework provides implementations of many standard cryptographic algorithms.</span></span> <span data-ttu-id="38378-104">Tyto algoritmy se snadno používají a mají nejbezpečnější možné výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="38378-104">These algorithms are easy to use and have the safest possible default properties.</span></span> <span data-ttu-id="38378-105">Kromě toho je model .NET Framework kryptografie dědičnosti objektů, návrh datového proudu a konfigurace velmi rozšiřitelný.</span><span class="sxs-lookup"><span data-stu-id="38378-105">In addition, the .NET Framework cryptography model of object inheritance, stream design, and configuration is extremely extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="38378-106">Dědičnost objektů</span><span class="sxs-lookup"><span data-stu-id="38378-106">Object Inheritance</span></span>

<span data-ttu-id="38378-107">Systém zabezpečení .NET Framework implementuje rozšiřitelný vzor dědičnosti odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="38378-107">The .NET Framework security system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="38378-108">Hierarchie je následující:</span><span class="sxs-lookup"><span data-stu-id="38378-108">The hierarchy is as follows:</span></span>

- <span data-ttu-id="38378-109">Třída typu algoritmu, například <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> nebo <xref:System.Security.Cryptography.HashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="38378-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="38378-110">Tato úroveň je abstraktní.</span><span class="sxs-lookup"><span data-stu-id="38378-110">This level is abstract.</span></span>

- <span data-ttu-id="38378-111">Třída algoritmu, která dědí z třídy typu algoritmu; například <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>nebo <xref:System.Security.Cryptography.ECDiffieHellman>.</span><span class="sxs-lookup"><span data-stu-id="38378-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="38378-112">Tato úroveň je abstraktní.</span><span class="sxs-lookup"><span data-stu-id="38378-112">This level is abstract.</span></span>

- <span data-ttu-id="38378-113">Implementace třídy algoritmu, která dědí z třídy algoritmu; například <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>nebo <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="38378-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="38378-114">Tato úroveň je plně implementovaná.</span><span class="sxs-lookup"><span data-stu-id="38378-114">This level is fully implemented.</span></span>

<span data-ttu-id="38378-115">Pomocí tohoto modelu odvozených tříd lze snadno přidat nový algoritmus nebo novou implementaci stávajícího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="38378-115">Using this pattern of derived classes, it is easy to add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="38378-116">Například pro vytvoření nového algoritmu veřejného klíče byste dědili z třídy <xref:System.Security.Cryptography.AsymmetricAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="38378-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="38378-117">Chcete-li vytvořit novou implementaci konkrétního algoritmu, je třeba vytvořit neabstraktní odvozenou třídu tohoto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="38378-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a><span data-ttu-id="38378-118">Jak jsou implementovány algoritmy v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38378-118">How Algorithms Are Implemented in the .NET Framework</span></span>

<span data-ttu-id="38378-119">Jako příklad různých implementací dostupných pro algoritmus zvažte symetrické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="38378-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="38378-120">Základem všech symetrických algoritmů je <xref:System.Security.Cryptography.SymmetricAlgorithm>, které jsou zděděny následujícími algoritmy:</span><span class="sxs-lookup"><span data-stu-id="38378-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by the following algorithms:</span></span>

1. <xref:System.Security.Cryptography.Aes>

2. <xref:System.Security.Cryptography.DES>

3. <xref:System.Security.Cryptography.RC2>

4. <xref:System.Security.Cryptography.Rijndael>

5. <xref:System.Security.Cryptography.TripleDES>

<span data-ttu-id="38378-121"><xref:System.Security.Cryptography.Aes> dědí dvě třídy: <xref:System.Security.Cryptography.AesCryptoServiceProvider> a <xref:System.Security.Cryptography.AesManaged>.</span><span class="sxs-lookup"><span data-stu-id="38378-121"><xref:System.Security.Cryptography.Aes> is inherited by two classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> and <xref:System.Security.Cryptography.AesManaged>.</span></span> <span data-ttu-id="38378-122">Třída <xref:System.Security.Cryptography.AesCryptoServiceProvider> je Obálka kolem implementace rozhraní Windows Cryptography API (CAPI) pro AES, zatímco třída <xref:System.Security.Cryptography.AesManaged> je zapsána výhradně ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="38378-122">The <xref:System.Security.Cryptography.AesCryptoServiceProvider> class is a wrapper around the Windows Cryptography API (CAPI) implementation of Aes, whereas the <xref:System.Security.Cryptography.AesManaged> class is written entirely in managed code.</span></span> <span data-ttu-id="38378-123">Kromě implementace spravovaného rozhraní CAPI existuje také třetí typ implementace, kryptografická generace (CNG).</span><span class="sxs-lookup"><span data-stu-id="38378-123">There is also a third type of implementation, Cryptography Next Generation (CNG), in addition to the managed and CAPI implementations.</span></span> <span data-ttu-id="38378-124">Příkladem algoritmu CNG je <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="38378-124">An example of a CNG algorithm is <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="38378-125">Algoritmy CNG jsou k dispozici v systému Windows Vista a novějších.</span><span class="sxs-lookup"><span data-stu-id="38378-125">CNG algorithms are available on Windows Vista and later.</span></span>

<span data-ttu-id="38378-126">Můžete zvolit, která implementace je pro vás nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="38378-126">You can choose which implementation is best for you.</span></span>  <span data-ttu-id="38378-127">Spravované implementace jsou k dispozici na všech platformách, které podporují .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38378-127">The managed implementations are available on all platforms that support the .NET Framework.</span></span>  <span data-ttu-id="38378-128">Implementace rozhraní CAPI jsou k dispozici ve starších operačních systémech a již nejsou vyvíjeny.</span><span class="sxs-lookup"><span data-stu-id="38378-128">The CAPI implementations are available on older operating systems, and are no longer being developed.</span></span> <span data-ttu-id="38378-129">CNG je nejnovější implementace, při které bude provedeno nové vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="38378-129">CNG is the very latest implementation where new development will take place.</span></span> <span data-ttu-id="38378-130">Spravované implementace však nejsou certifikovány standardy FIPS (Federal Information Processing Standards) a mohou být nižší než obálkové třídy.</span><span class="sxs-lookup"><span data-stu-id="38378-130">However, the managed implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the wrapper classes.</span></span>

## <a name="stream-design"></a><span data-ttu-id="38378-131">Návrh streamu</span><span class="sxs-lookup"><span data-stu-id="38378-131">Stream Design</span></span>

<span data-ttu-id="38378-132">Modul common language runtime používá pro implementaci symetrických algoritmů a algoritmů hash návrh orientovaný na proud.</span><span class="sxs-lookup"><span data-stu-id="38378-132">The common language runtime uses a stream-oriented design for implementing symmetric algorithms and hash algorithms.</span></span> <span data-ttu-id="38378-133">Základem tohoto návrhu je <xref:System.Security.Cryptography.CryptoStream> třída, která je odvozena od <xref:System.IO.Stream> třídy.</span><span class="sxs-lookup"><span data-stu-id="38378-133">The core of this design is the <xref:System.Security.Cryptography.CryptoStream> class, which derives from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="38378-134">Kryptografické objekty založené na datových proudech podporují jedno standardní rozhraní (`CryptoStream`) pro zpracování části přenosu dat objektu.</span><span class="sxs-lookup"><span data-stu-id="38378-134">Stream-based cryptographic objects support a single standard interface (`CryptoStream`) for handling the data transfer portion of the object.</span></span> <span data-ttu-id="38378-135">Vzhledem k tomu, že všechny objekty jsou postaveny na standardním rozhraní, můžete zřetězit více objektů (například objekt hash následovaný objektem šifrování) a můžete provádět více operací s daty, aniž byste pro ně potřebovali jakékoli zprostředkující úložiště.</span><span class="sxs-lookup"><span data-stu-id="38378-135">Because all the objects are built on a standard interface, you can chain together multiple objects (such as a hash object followed by an encryption object), and you can perform multiple operations on the data without needing any intermediate storage for it.</span></span> <span data-ttu-id="38378-136">Model streamování také umožňuje vytvářet objekty z menších objektů.</span><span class="sxs-lookup"><span data-stu-id="38378-136">The streaming model also enables you to build objects from smaller objects.</span></span> <span data-ttu-id="38378-137">Například kombinované šifrování a algoritmus hash lze zobrazit jako jeden objekt datového proudu, i když tento objekt může být sestaven ze sady objektů datového proudu.</span><span class="sxs-lookup"><span data-stu-id="38378-137">For example, a combined encryption and hash algorithm can be viewed as a single stream object, although this object might be built from a set of stream objects.</span></span>

## <a name="cryptographic-configuration"></a><span data-ttu-id="38378-138">Konfigurace kryptografie</span><span class="sxs-lookup"><span data-stu-id="38378-138">Cryptographic Configuration</span></span>

<span data-ttu-id="38378-139">Kryptografická konfigurace umožňuje vyřešit konkrétní implementaci algoritmu pro název algoritmu a umožňuje rozšiřitelnost .NET Frameworkch kryptografických tříd.</span><span class="sxs-lookup"><span data-stu-id="38378-139">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET Framework cryptography classes.</span></span> <span data-ttu-id="38378-140">Můžete přidat vlastní hardware nebo softwarovou implementaci algoritmu a namapovat implementaci na název algoritmu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="38378-140">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="38378-141">Pokud v konfiguračním souboru není zadaný algoritmus, použijí se výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="38378-141">If an algorithm is not specified in the configuration file, the default settings are used.</span></span> <span data-ttu-id="38378-142">Další informace o konfiguraci kryptografie naleznete v tématu [Configuring Cryptography Classes](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span><span class="sxs-lookup"><span data-stu-id="38378-142">For more information about cryptographic configuration, see [Configuring Cryptography Classes](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span></span>

## <a name="choosing-an-algorithm"></a><span data-ttu-id="38378-143">Výběr algoritmu</span><span class="sxs-lookup"><span data-stu-id="38378-143">Choosing an Algorithm</span></span>

<span data-ttu-id="38378-144">Můžete vybrat algoritmus z různých důvodů: například pro integritu dat, pro ochranu osobních údajů nebo pro vygenerování klíče.</span><span class="sxs-lookup"><span data-stu-id="38378-144">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="38378-145">Algoritmy symetrického a algoritmu hash jsou určené k ochraně dat z důvodů integrity (chráněných před změnou) nebo z důvodů ochrany osobních údajů (ochrana před zobrazením).</span><span class="sxs-lookup"><span data-stu-id="38378-145">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="38378-146">Algoritmy hash jsou primárně používány pro integritu dat.</span><span class="sxs-lookup"><span data-stu-id="38378-146">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="38378-147">Tady je seznam doporučených algoritmů podle aplikace:</span><span class="sxs-lookup"><span data-stu-id="38378-147">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="38378-148">Ochrana dat:</span><span class="sxs-lookup"><span data-stu-id="38378-148">Data privacy:</span></span>

  - <xref:System.Security.Cryptography.Aes>

- <span data-ttu-id="38378-149">Integrita dat:</span><span class="sxs-lookup"><span data-stu-id="38378-149">Data integrity:</span></span>

  - <xref:System.Security.Cryptography.HMACSHA256>

  - <xref:System.Security.Cryptography.HMACSHA512>

- <span data-ttu-id="38378-150">Digitální podpis:</span><span class="sxs-lookup"><span data-stu-id="38378-150">Digital signature:</span></span>

  - <xref:System.Security.Cryptography.ECDsa>

  - <xref:System.Security.Cryptography.RSA>

- <span data-ttu-id="38378-151">Výměna klíčů:</span><span class="sxs-lookup"><span data-stu-id="38378-151">Key exchange:</span></span>

  - <xref:System.Security.Cryptography.ECDiffieHellman>

  - <xref:System.Security.Cryptography.RSA>

- <span data-ttu-id="38378-152">Náhodné číslo generace:</span><span class="sxs-lookup"><span data-stu-id="38378-152">Random number generation:</span></span>

  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>

- <span data-ttu-id="38378-153">Generuje se klíč z hesla:</span><span class="sxs-lookup"><span data-stu-id="38378-153">Generating a key from a password:</span></span>

  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="38378-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38378-154">See also</span></span>

- [<span data-ttu-id="38378-155">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="38378-155">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
