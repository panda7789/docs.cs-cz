---
title: Kryptografický model .NET
description: Projděte si implementace obvyklých kryptografických algoritmů v .NET. Seznamte se s rozšiřitelným kryptografickým modelem dědičnosti objektů, návrhem datového proudu a konfigurací &.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], model
- encryption [.NET], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: 0b3e07238bf0932572c222f7b947cfa7ae0221a9
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556992"
---
# <a name="net-cryptography-model"></a><span data-ttu-id="fb6f9-104">Kryptografický model .NET</span><span class="sxs-lookup"><span data-stu-id="fb6f9-104">.NET Cryptography Model</span></span>

<span data-ttu-id="fb6f9-105">Rozhraní .NET poskytuje implementace mnoha standardních kryptografických algoritmů a model kryptografie .NET je rozšiřitelný.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-105">.NET provides implementations of many standard cryptographic algorithms, and the .NET cryptography model is extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="fb6f9-106">Dědičnost objektů</span><span class="sxs-lookup"><span data-stu-id="fb6f9-106">Object Inheritance</span></span>

<span data-ttu-id="fb6f9-107">Systém kryptografie rozhraní .NET implementuje rozšiřitelný vzor dědičnosti odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-107">The .NET cryptography system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="fb6f9-108">Hierarchie je následující:</span><span class="sxs-lookup"><span data-stu-id="fb6f9-108">The hierarchy is as follows:</span></span>

- <span data-ttu-id="fb6f9-109">Třída typu algoritmu, například <xref:System.Security.Cryptography.SymmetricAlgorithm> , <xref:System.Security.Cryptography.AsymmetricAlgorithm> nebo <xref:System.Security.Cryptography.HashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="fb6f9-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm>, or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="fb6f9-110">Tato úroveň je abstraktní.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-110">This level is abstract.</span></span>

- <span data-ttu-id="fb6f9-111">Třída algoritmu, která dědí z třídy typu algoritmu; Například,, <xref:System.Security.Cryptography.Aes> <xref:System.Security.Cryptography.RSA> nebo <xref:System.Security.Cryptography.ECDiffieHellman> .</span><span class="sxs-lookup"><span data-stu-id="fb6f9-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RSA>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="fb6f9-112">Tato úroveň je abstraktní.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-112">This level is abstract.</span></span>

- <span data-ttu-id="fb6f9-113">Implementace třídy algoritmu, která dědí z třídy algoritmu; Například,, <xref:System.Security.Cryptography.AesManaged> <xref:System.Security.Cryptography.RC2CryptoServiceProvider> nebo <xref:System.Security.Cryptography.ECDiffieHellmanCng> .</span><span class="sxs-lookup"><span data-stu-id="fb6f9-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="fb6f9-114">Tato úroveň je plně implementovaná.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-114">This level is fully implemented.</span></span>

<span data-ttu-id="fb6f9-115">Tento vzor odvozených tříd umožňuje přidat nový algoritmus nebo novou implementaci existujícího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-115">This pattern of derived classes lets you add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="fb6f9-116">Například pro vytvoření nového algoritmu veřejného klíče byste měli dědit z <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="fb6f9-117">Chcete-li vytvořit novou implementaci konkrétního algoritmu, je třeba vytvořit neabstraktní odvozenou třídu tohoto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-net"></a><span data-ttu-id="fb6f9-118">Způsob implementace algoritmů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="fb6f9-118">How Algorithms Are Implemented in .NET</span></span>

<span data-ttu-id="fb6f9-119">Jako příklad různých implementací dostupných pro algoritmus zvažte symetrické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="fb6f9-120">Základem všech symetrických algoritmů je <xref:System.Security.Cryptography.SymmetricAlgorithm> , který je zděděn pomocí <xref:System.Security.Cryptography.Aes> , <xref:System.Security.Cryptography.TripleDES> a dalších, které již nejsou doporučovány.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.TripleDES>, and others that are no longer recommended.</span></span>

<span data-ttu-id="fb6f9-121"><xref:System.Security.Cryptography.Aes>dědí <xref:System.Security.Cryptography.AesCryptoServiceProvider> aplikace, <xref:System.Security.Cryptography.AesCng> a <xref:System.Security.Cryptography.AesManaged> .</span><span class="sxs-lookup"><span data-stu-id="fb6f9-121"><xref:System.Security.Cryptography.Aes> is inherited by <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.AesCng>, and <xref:System.Security.Cryptography.AesManaged>.</span></span>

<span data-ttu-id="fb6f9-122">V .NET Framework ve Windows:</span><span class="sxs-lookup"><span data-stu-id="fb6f9-122">In .NET Framework on Windows:</span></span>

* <span data-ttu-id="fb6f9-123">`*CryptoServiceProvider`třídy algoritmů, například <xref:System.Security.Cryptography.AesCryptoServiceProvider> , jsou obálkou v rámci implementace algoritmu rozhraní API kryptografických služeb systému Windows (CAPI).</span><span class="sxs-lookup"><span data-stu-id="fb6f9-123">`*CryptoServiceProvider` algorithm classes, such as <xref:System.Security.Cryptography.AesCryptoServiceProvider>, are wrappers around the Windows Cryptography API (CAPI) implementation of an algorithm.</span></span>
* <span data-ttu-id="fb6f9-124">`*Cng`třídy algoritmů, jako <xref:System.Security.Cryptography.ECDiffieHellmanCng> jsou obálky, představují implementaci Kryptografické služby Windows Cryptography Next Generation (CNG).</span><span class="sxs-lookup"><span data-stu-id="fb6f9-124">`*Cng` algorithm classes, such as <xref:System.Security.Cryptography.ECDiffieHellmanCng> are wrappers around the Windows Cryptography Next Generation (CNG) implementation.</span></span>
* <span data-ttu-id="fb6f9-125">`*Managed`třídy, jako <xref:System.Security.Cryptography.AesManaged> jsou, jsou zapsány výhradně ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-125">`*Managed` classes, such as <xref:System.Security.Cryptography.AesManaged>, are written entirely in managed code.</span></span> <span data-ttu-id="fb6f9-126">`*Managed`implementace nejsou certifikovány standardy FIPS (Federal Information Processing Standards) a mohou být nižší než `*CryptoServiceProvider` `*Cng` obálkové třídy a.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-126">`*Managed` implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the `*CryptoServiceProvider` and `*Cng` wrapper classes.</span></span>

<span data-ttu-id="fb6f9-127">V rozhraní .NET Core a .NET 5 a novějších verzích jsou všechny implementační třídy ( `*CryptoServiceProvider` , `*Managed` a `*Cng` ) obálky pro algoritmy operačního systému (OS).</span><span class="sxs-lookup"><span data-stu-id="fb6f9-127">In .NET Core and .NET 5 and later versions, all implementation classes (`*CryptoServiceProvider`, `*Managed`, and `*Cng`) are wrappers for the operating system (OS) algorithms.</span></span> <span data-ttu-id="fb6f9-128">Pokud jsou algoritmy operačního systému certifikované pro Standard FIPS, používá .NET algoritmy s certifikací FIPS.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-128">If the OS algorithms are FIPS-certified, then .NET uses FIPS-certified algorithms.</span></span> <span data-ttu-id="fb6f9-129">Další informace najdete v tématu [kryptografie mezi platformami](cross-platform-cryptography.md).</span><span class="sxs-lookup"><span data-stu-id="fb6f9-129">For more information, see [Cross-Platform Cryptography](cross-platform-cryptography.md).</span></span>

<span data-ttu-id="fb6f9-130">Ve většině případů nemusíte přímo odkazovat na třídu implementace algoritmu, jako je například `AesCryptoServiceProvider` .</span><span class="sxs-lookup"><span data-stu-id="fb6f9-130">In most cases, you don't need to directly reference an algorithm implementation class, such as `AesCryptoServiceProvider`.</span></span> <span data-ttu-id="fb6f9-131">Metody a vlastnosti, které obvykle potřebujete, jsou v základní třídě algoritmu, například `Aes` .</span><span class="sxs-lookup"><span data-stu-id="fb6f9-131">The methods and properties you typically need are on the base algorithm class, such as `Aes`.</span></span> <span data-ttu-id="fb6f9-132">Vytvořte instanci výchozí třídy implementace pomocí metody Factory v základní třídě algoritmu a přečtěte si základní třídu algoritmu.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-132">Create an instance of a default implementation class by using a factory method on the base algorithm class, and refer to the base algorithm class.</span></span> <span data-ttu-id="fb6f9-133">Podívejte se například na zvýrazněný řádek kódu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="fb6f9-133">For example, see the highlighted line of code in the following example:</span></span>

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="16":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="12":::

## <a name="cryptographic-configuration"></a><span data-ttu-id="fb6f9-134">Konfigurace kryptografie</span><span class="sxs-lookup"><span data-stu-id="fb6f9-134">Cryptographic Configuration</span></span>

<span data-ttu-id="fb6f9-135">Kryptografická konfigurace umožňuje vyřešit konkrétní implementaci algoritmu pro název algoritmu, což umožňuje rozšiřitelnost tříd kryptografie .NET.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-135">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET cryptography classes.</span></span> <span data-ttu-id="fb6f9-136">Můžete přidat vlastní hardware nebo softwarovou implementaci algoritmu a namapovat implementaci na název algoritmu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-136">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="fb6f9-137">Pokud v konfiguračním souboru není zadaný algoritmus, použijí se výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-137">If an algorithm is not specified in the configuration file, the default settings are used.</span></span>

## <a name="choosing-an-algorithm"></a><span data-ttu-id="fb6f9-138">Výběr algoritmu</span><span class="sxs-lookup"><span data-stu-id="fb6f9-138">Choosing an Algorithm</span></span>

<span data-ttu-id="fb6f9-139">Můžete vybrat algoritmus z různých důvodů: například pro integritu dat, pro ochranu osobních údajů nebo pro vygenerování klíče.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-139">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="fb6f9-140">Algoritmy symetrického a algoritmu hash jsou určené k ochraně dat z důvodů integrity (chráněných před změnou) nebo z důvodů ochrany osobních údajů (ochrana před zobrazením).</span><span class="sxs-lookup"><span data-stu-id="fb6f9-140">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="fb6f9-141">Algoritmy hash jsou primárně používány pro integritu dat.</span><span class="sxs-lookup"><span data-stu-id="fb6f9-141">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="fb6f9-142">Tady je seznam doporučených algoritmů podle aplikace:</span><span class="sxs-lookup"><span data-stu-id="fb6f9-142">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="fb6f9-143">Ochrana dat:</span><span class="sxs-lookup"><span data-stu-id="fb6f9-143">Data privacy:</span></span>
  - <xref:System.Security.Cryptography.Aes>
- <span data-ttu-id="fb6f9-144">Integrita dat:</span><span class="sxs-lookup"><span data-stu-id="fb6f9-144">Data integrity:</span></span>
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- <span data-ttu-id="fb6f9-145">Digitální podpis:</span><span class="sxs-lookup"><span data-stu-id="fb6f9-145">Digital signature:</span></span>
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="fb6f9-146">Výměna klíčů:</span><span class="sxs-lookup"><span data-stu-id="fb6f9-146">Key exchange:</span></span>
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="fb6f9-147">Náhodné číslo generace:</span><span class="sxs-lookup"><span data-stu-id="fb6f9-147">Random number generation:</span></span>
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- <span data-ttu-id="fb6f9-148">Generuje se klíč z hesla:</span><span class="sxs-lookup"><span data-stu-id="fb6f9-148">Generating a key from a password:</span></span>
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="fb6f9-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb6f9-149">See also</span></span>

- [<span data-ttu-id="fb6f9-150">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="fb6f9-150">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="fb6f9-151">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="fb6f9-151">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="fb6f9-152">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fb6f9-152">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
