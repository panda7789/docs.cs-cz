---
title: Kryptografický model rozhraní .NET framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d74ce08197ac76a601202da8e35ca6f619207076
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43885744"
---
# <a name="net-framework-cryptography-model"></a><span data-ttu-id="7c737-102">Kryptografický model rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="7c737-102">.NET Framework Cryptography Model</span></span>
<span data-ttu-id="7c737-103">Rozhraní .NET Framework poskytuje mnoho standardních kryptografických algoritmů implementace.</span><span class="sxs-lookup"><span data-stu-id="7c737-103">The .NET Framework provides implementations of many standard cryptographic algorithms.</span></span> <span data-ttu-id="7c737-104">Tyto algoritmy jsou snadné použití a nejbezpečnější možné výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7c737-104">These algorithms are easy to use and have the safest possible default properties.</span></span> <span data-ttu-id="7c737-105">Kryptografický model rozhraní .NET Framework dědičnost objektů, stream návrhu a konfigurace je také velmi rozšiřitelné.</span><span class="sxs-lookup"><span data-stu-id="7c737-105">In addition, the .NET Framework cryptography model of object inheritance, stream design, and configuration is extremely extensible.</span></span>  
  
## <a name="object-inheritance"></a><span data-ttu-id="7c737-106">Dědičnost objektů</span><span class="sxs-lookup"><span data-stu-id="7c737-106">Object Inheritance</span></span>  
 <span data-ttu-id="7c737-107">Systém zabezpečení rozhraní .NET Framework implementuje extensible vzor odvozené dědičnosti tříd.</span><span class="sxs-lookup"><span data-stu-id="7c737-107">The .NET Framework security system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="7c737-108">Hierarchie vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="7c737-108">The hierarchy is as follows:</span></span>  
  
-   <span data-ttu-id="7c737-109">Třídy typu algoritmu, jako například <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> nebo <xref:System.Security.Cryptography.HashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="7c737-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="7c737-110">Tato úroveň je abstraktní.</span><span class="sxs-lookup"><span data-stu-id="7c737-110">This level is abstract.</span></span>  
  
-   <span data-ttu-id="7c737-111">Třída algoritmu, který dědí z třídy typu algoritmu; například <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, nebo <xref:System.Security.Cryptography.ECDiffieHellman>.</span><span class="sxs-lookup"><span data-stu-id="7c737-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="7c737-112">Tato úroveň je abstraktní.</span><span class="sxs-lookup"><span data-stu-id="7c737-112">This level is abstract.</span></span>  
  
-   <span data-ttu-id="7c737-113">Implementace třídy algoritmus, který dědí z třídy algoritmus; například <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, nebo <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="7c737-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="7c737-114">Tato úroveň je plně implementovány.</span><span class="sxs-lookup"><span data-stu-id="7c737-114">This level is fully implemented.</span></span>  
  
 <span data-ttu-id="7c737-115">Použití tohoto modelu odvozené třídy, je snadné přidat nový algoritmus nebo nové implementace algoritmu existující.</span><span class="sxs-lookup"><span data-stu-id="7c737-115">Using this pattern of derived classes, it is easy to add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="7c737-116">Například pokud chcete vytvořit nový algoritmus veřejného klíče, by dědění z <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy.</span><span class="sxs-lookup"><span data-stu-id="7c737-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="7c737-117">Chcete-li vytvořit nové implementace algoritmu konkrétní, vytvořili byste Odvozené neabstraktní třídy tohoto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="7c737-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a><span data-ttu-id="7c737-118">Jak se implementují algoritmy v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7c737-118">How Algorithms Are Implemented in the .NET Framework</span></span>  
 <span data-ttu-id="7c737-119">Jako příklad různé implementace, které jsou k dispozici pro algoritmus vezměte v úvahu symetrické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="7c737-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="7c737-120">Základ pro všechny symetrické algoritmy je <xref:System.Security.Cryptography.SymmetricAlgorithm>, která dědí tyto algoritmy:</span><span class="sxs-lookup"><span data-stu-id="7c737-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by the following algorithms:</span></span>  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <span data-ttu-id="7c737-121"><xref:System.Security.Cryptography.Aes> zdědí dvou tříd: <xref:System.Security.Cryptography.AesCryptoServiceProvider> a <xref:System.Security.Cryptography.AesManaged>.</span><span class="sxs-lookup"><span data-stu-id="7c737-121"><xref:System.Security.Cryptography.Aes> is inherited by two classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> and <xref:System.Security.Cryptography.AesManaged>.</span></span> <span data-ttu-id="7c737-122"><xref:System.Security.Cryptography.AesCryptoServiceProvider> Třída představuje obálku kolem Windows Cryptography API (CAPI) provádění Aes, zatímco <xref:System.Security.Cryptography.AesManaged> třídy je vytvořené zcela v spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="7c737-122">The <xref:System.Security.Cryptography.AesCryptoServiceProvider> class is a wrapper around the Windows Cryptography API (CAPI) implementation of Aes, whereas the <xref:System.Security.Cryptography.AesManaged> class is written entirely in managed code.</span></span> <span data-ttu-id="7c737-123">Existuje také třetí typ implementace, Cryptography Next Generation (CNG), také na spravovanou a CAPI implementace.</span><span class="sxs-lookup"><span data-stu-id="7c737-123">There is also a third type of implementation, Cryptography Next Generation (CNG), in addition to the managed and CAPI implementations.</span></span> <span data-ttu-id="7c737-124">Je například algoritmus CNG <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="7c737-124">An example of a CNG algorithm is <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="7c737-125">Algoritmy CNG jsou k dispozici v systému Windows Vista nebo novější.</span><span class="sxs-lookup"><span data-stu-id="7c737-125">CNG algorithms are available on Windows Vista and later.</span></span>  
  
 <span data-ttu-id="7c737-126">Můžete zvolit, která implementace je pro vás nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="7c737-126">You can choose which implementation is best for you.</span></span>  <span data-ttu-id="7c737-127">Spravované implementace jsou k dispozici na všech platformách, které podporují rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c737-127">The managed implementations are available on all platforms that support the .NET Framework.</span></span>  <span data-ttu-id="7c737-128">Implementace CAPI jsou k dispozici ve starších operačních systémech a jsou už nevyvíjí.</span><span class="sxs-lookup"><span data-stu-id="7c737-128">The CAPI implementations are available on older operating systems, and are no longer being developed.</span></span> <span data-ttu-id="7c737-129">CNG je velmi nejnovější implementace, ve kterém bude probíhat vývoj nových projektů.</span><span class="sxs-lookup"><span data-stu-id="7c737-129">CNG is the very latest implementation where new development will take place.</span></span> <span data-ttu-id="7c737-130">Spravované implementace však nejsou certifikovány podle informace o zpracování normy FIPS (Federal) a může být pomalejší než obálkové třídy.</span><span class="sxs-lookup"><span data-stu-id="7c737-130">However, the managed implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the wrapper classes.</span></span>  
  
## <a name="stream-design"></a><span data-ttu-id="7c737-131">Stream návrhu</span><span class="sxs-lookup"><span data-stu-id="7c737-131">Stream Design</span></span>  
 <span data-ttu-id="7c737-132">Modul common language runtime používá orientovaný na stream návrhu pro implementaci symetrické algoritmy a hashovacích algoritmů.</span><span class="sxs-lookup"><span data-stu-id="7c737-132">The common language runtime uses a stream-oriented design for implementing symmetric algorithms and hash algorithms.</span></span> <span data-ttu-id="7c737-133">Je základní tento návrh <xref:System.Security.Cryptography.CryptoStream> třída, která je odvozena z <xref:System.IO.Stream> třídy.</span><span class="sxs-lookup"><span data-stu-id="7c737-133">The core of this design is the <xref:System.Security.Cryptography.CryptoStream> class, which derives from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="7c737-134">Na základě Stream kryptografických objekty podporují rozhraní jediným standardním (`CryptoStream`) pro zpracování části přenosu dat objektu.</span><span class="sxs-lookup"><span data-stu-id="7c737-134">Stream-based cryptographic objects support a single standard interface (`CryptoStream`) for handling the data transfer portion of the object.</span></span> <span data-ttu-id="7c737-135">Vzhledem k tomu, že všechny objekty jsou postavené na standardní rozhraní, můžete zřetězit dohromady víc objektů (například objekt algoritmu hash, za nímž následuje objekt šifrování) a můžete provádět více operací s daty bez nutnosti jakékoli sloužící jako přechodné úložiště pro něj.</span><span class="sxs-lookup"><span data-stu-id="7c737-135">Because all the objects are built on a standard interface, you can chain together multiple objects (such as a hash object followed by an encryption object), and you can perform multiple operations on the data without needing any intermediate storage for it.</span></span> <span data-ttu-id="7c737-136">Streamování modelu také umožňuje vytvářet objekty z menších objektů.</span><span class="sxs-lookup"><span data-stu-id="7c737-136">The streaming model also enables you to build objects from smaller objects.</span></span> <span data-ttu-id="7c737-137">Kombinované šifrování a hashovací algoritmus může například zobrazit jako objekt jeden datový proud, i když tento objekt může být sestavena na základě sady objektů datového proudu.</span><span class="sxs-lookup"><span data-stu-id="7c737-137">For example, a combined encryption and hash algorithm can be viewed as a single stream object, although this object might be built from a set of stream objects.</span></span>  
  
## <a name="cryptographic-configuration"></a><span data-ttu-id="7c737-138">Kryptografická konfigurace</span><span class="sxs-lookup"><span data-stu-id="7c737-138">Cryptographic Configuration</span></span>  
 <span data-ttu-id="7c737-139">Kryptografická konfigurace umožňuje vyřešit konkrétní implementaci algoritmus název algoritmu, což rozšíření tříd šifrování .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c737-139">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET Framework cryptography classes.</span></span> <span data-ttu-id="7c737-140">Můžete přidat vlastní hardware ani software provádění algoritmu a implementaci namapovat název algoritmu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="7c737-140">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="7c737-141">Pokud algoritmus není zadané v konfiguračním souboru, použijí se výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="7c737-141">If an algorithm is not specified in the configuration file, the default settings are used.</span></span> <span data-ttu-id="7c737-142">Další informace o kryptografická konfigurace najdete v tématu [konfigurace šifrovacích tříd](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7c737-142">For more information about cryptographic configuration, see [Configuring Cryptography Classes](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span></span>  
  
## <a name="choosing-an-algorithm"></a><span data-ttu-id="7c737-143">Výběr algoritmu</span><span class="sxs-lookup"><span data-stu-id="7c737-143">Choosing an Algorithm</span></span>  
 <span data-ttu-id="7c737-144">Algoritmus můžete vybrat z různých důvodů: třeba pro integritu dat, ochrany osobních údajů nebo ke generování klíče.</span><span class="sxs-lookup"><span data-stu-id="7c737-144">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="7c737-145">Symmetric a hashovací algoritmy jsou určené pro ochranu dat z důvodu zachování integrity (Ochrana před změnami) nebo z důvodů ochrany osobních údajů (ochrana ze zobrazení).</span><span class="sxs-lookup"><span data-stu-id="7c737-145">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="7c737-146">Algoritmy hash se používají především pro integritu dat.</span><span class="sxs-lookup"><span data-stu-id="7c737-146">Hash algorithms are used primarily for data integrity.</span></span>  
  
 <span data-ttu-id="7c737-147">Tady je seznam doporučených algoritmy aplikací:</span><span class="sxs-lookup"><span data-stu-id="7c737-147">Here is a list of recommended algorithms by application:</span></span>  
  
-   <span data-ttu-id="7c737-148">Data o ochraně osobních údajů:</span><span class="sxs-lookup"><span data-stu-id="7c737-148">Data privacy:</span></span>  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   <span data-ttu-id="7c737-149">Integrita dat:</span><span class="sxs-lookup"><span data-stu-id="7c737-149">Data integrity:</span></span>  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   <span data-ttu-id="7c737-150">Digitální podpis:</span><span class="sxs-lookup"><span data-stu-id="7c737-150">Digital signature:</span></span>  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   <span data-ttu-id="7c737-151">Výměna klíčů:</span><span class="sxs-lookup"><span data-stu-id="7c737-151">Key exchange:</span></span>  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   <span data-ttu-id="7c737-152">Náhodné generování čísel:</span><span class="sxs-lookup"><span data-stu-id="7c737-152">Random number generation:</span></span>  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   <span data-ttu-id="7c737-153">Generuje se klíč z hesla:</span><span class="sxs-lookup"><span data-stu-id="7c737-153">Generating a key from a password:</span></span>  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a><span data-ttu-id="7c737-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c737-154">See also</span></span>

- [<span data-ttu-id="7c737-155">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="7c737-155">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
