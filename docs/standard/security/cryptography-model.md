---
title: "Kryptografický model rozhraní .NET framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9fb0a726a4bef5b6efa67d5f63c1899468f7e8ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="net-framework-cryptography-model"></a><span data-ttu-id="3721a-102">Kryptografický model rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="3721a-102">.NET Framework Cryptography Model</span></span>
<span data-ttu-id="3721a-103">Rozhraní .NET Framework poskytuje implementace mnoho standardní kryptografických algoritmů.</span><span class="sxs-lookup"><span data-stu-id="3721a-103">The .NET Framework provides implementations of many standard cryptographic algorithms.</span></span> <span data-ttu-id="3721a-104">Tyto algoritmy jsou snadno použitelné a mají nejbezpečnější možné výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3721a-104">These algorithms are easy to use and have the safest possible default properties.</span></span> <span data-ttu-id="3721a-105">Kromě toho je velmi extensible Kryptografický model rozhraní .NET Framework objekt dědičnosti, datový proud návrh a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3721a-105">In addition, the .NET Framework cryptography model of object inheritance, stream design, and configuration is extremely extensible.</span></span>  
  
## <a name="object-inheritance"></a><span data-ttu-id="3721a-106">Objekt dědičnosti</span><span class="sxs-lookup"><span data-stu-id="3721a-106">Object Inheritance</span></span>  
 <span data-ttu-id="3721a-107">Systém zabezpečení rozhraní .NET Framework implementuje rozšiřitelné vzory odvozené dědičnosti tříd.</span><span class="sxs-lookup"><span data-stu-id="3721a-107">The .NET Framework security system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="3721a-108">V hierarchii je následující:</span><span class="sxs-lookup"><span data-stu-id="3721a-108">The hierarchy is as follows:</span></span>  
  
-   <span data-ttu-id="3721a-109">Typ algoritmu třídy, jako například <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> nebo <xref:System.Security.Cryptography.HashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="3721a-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="3721a-110">Tato úroveň je abstraktní.</span><span class="sxs-lookup"><span data-stu-id="3721a-110">This level is abstract.</span></span>  
  
-   <span data-ttu-id="3721a-111">Třída algoritmu, který dědí z třídy typu algoritmus; například <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, nebo <xref:System.Security.Cryptography.ECDiffieHellman>.</span><span class="sxs-lookup"><span data-stu-id="3721a-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="3721a-112">Tato úroveň je abstraktní.</span><span class="sxs-lookup"><span data-stu-id="3721a-112">This level is abstract.</span></span>  
  
-   <span data-ttu-id="3721a-113">Implementace třídy algoritmu, který dědí z třídy algoritmus; například <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, nebo <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="3721a-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="3721a-114">Tato úroveň je plně implementováno.</span><span class="sxs-lookup"><span data-stu-id="3721a-114">This level is fully implemented.</span></span>  
  
 <span data-ttu-id="3721a-115">Pomocí tohoto vzoru odvozených tříd, je snadné přidání nového algoritmu nebo nové implementace existujícího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="3721a-115">Using this pattern of derived classes, it is easy to add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="3721a-116">Například pokud chcete vytvořit nový algoritmus veřejného klíče, by dědění ze <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy.</span><span class="sxs-lookup"><span data-stu-id="3721a-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="3721a-117">K vytvoření nové implementace konkrétní algoritmem, by vytvořit třídu odvozené neabstraktní tento algoritmus.</span><span class="sxs-lookup"><span data-stu-id="3721a-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a><span data-ttu-id="3721a-118">Jak jsou implementované algoritmy v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3721a-118">How Algorithms Are Implemented in the .NET Framework</span></span>  
 <span data-ttu-id="3721a-119">Jako příklad různé implementace, které jsou k dispozici pro algoritmus vezměte v úvahu symetrické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="3721a-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="3721a-120">Základ pro všechny symetrické algoritmy je <xref:System.Security.Cryptography.SymmetricAlgorithm>, který zdědí tyto algoritmy:</span><span class="sxs-lookup"><span data-stu-id="3721a-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by the following algorithms:</span></span>  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <span data-ttu-id="3721a-121"><xref:System.Security.Cryptography.Aes>zdědí dvě třídy: <xref:System.Security.Cryptography.AesCryptoServiceProvider> a <xref:System.Security.Cryptography.AesManaged>.</span><span class="sxs-lookup"><span data-stu-id="3721a-121"><xref:System.Security.Cryptography.Aes> is inherited by two classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> and <xref:System.Security.Cryptography.AesManaged>.</span></span> <span data-ttu-id="3721a-122"><xref:System.Security.Cryptography.AesCryptoServiceProvider> Třída je obálku kolem implementace rozhraní API kryptografie systému Windows (CAPI) Aes, zatímco <xref:System.Security.Cryptography.AesManaged> třída je zapsán zcela ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="3721a-122">The <xref:System.Security.Cryptography.AesCryptoServiceProvider> class is a wrapper around the Windows Cryptography API (CAPI) implementation of Aes, whereas the <xref:System.Security.Cryptography.AesManaged> class is written entirely in managed code.</span></span> <span data-ttu-id="3721a-123">Je také třetí typ implementace Cryptography Next Generation (CNG), v CAPI implementace a přidání do spravovaný.</span><span class="sxs-lookup"><span data-stu-id="3721a-123">There is also a third type of implementation, Cryptography Next Generation (CNG), in addition to the managed and CAPI implementations.</span></span> <span data-ttu-id="3721a-124">Je například algoritmus CNG <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="3721a-124">An example of a CNG algorithm is <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="3721a-125">CNG algoritmy jsou k dispozici v systému Windows Vista nebo novější.</span><span class="sxs-lookup"><span data-stu-id="3721a-125">CNG algorithms are available on Windows Vista and later.</span></span>  
  
 <span data-ttu-id="3721a-126">Můžete zvolit, které implementace je pro vás nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="3721a-126">You can choose which implementation is best for you.</span></span>  <span data-ttu-id="3721a-127">Spravované implementace jsou k dispozici na všech platformách, které podporují rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3721a-127">The managed implementations are available on all platforms that support the .NET Framework.</span></span>  <span data-ttu-id="3721a-128">Implementace CAPI jsou dostupné ve starších operačních systémech a jsou už vyvíjených.</span><span class="sxs-lookup"><span data-stu-id="3721a-128">The CAPI implementations are available on older operating systems, and are no longer being developed.</span></span> <span data-ttu-id="3721a-129">CNG je velmi nejnovější implementace, kde bude probíhat vývoj nových.</span><span class="sxs-lookup"><span data-stu-id="3721a-129">CNG is the very latest implementation where new development will take place.</span></span> <span data-ttu-id="3721a-130">Spravované implementace však nejsou certifikovány podle na zpracování standardů FIPS (Federal Information) a může být pomalejší než obálkové třídy.</span><span class="sxs-lookup"><span data-stu-id="3721a-130">However, the managed implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the wrapper classes.</span></span>  
  
## <a name="stream-design"></a><span data-ttu-id="3721a-131">Návrh datového proudu</span><span class="sxs-lookup"><span data-stu-id="3721a-131">Stream Design</span></span>  
 <span data-ttu-id="3721a-132">Modul common language runtime používá návrh orientované na datový proud pro implementaci symetrické algoritmy a algoritmů hash.</span><span class="sxs-lookup"><span data-stu-id="3721a-132">The common language runtime uses a stream-oriented design for implementing symmetric algorithms and hash algorithms.</span></span> <span data-ttu-id="3721a-133">Je základní tohoto návrhu <xref:System.Security.Cryptography.CryptoStream> třída, která je odvozena z <xref:System.IO.Stream> třídy.</span><span class="sxs-lookup"><span data-stu-id="3721a-133">The core of this design is the <xref:System.Security.Cryptography.CryptoStream> class, which derives from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="3721a-134">Na základě datového proudu kryptografické objekty podporují jediné standardní rozhraní (`CryptoStream`) pro zpracování datové části přenosu objektu.</span><span class="sxs-lookup"><span data-stu-id="3721a-134">Stream-based cryptographic objects support a single standard interface (`CryptoStream`) for handling the data transfer portion of the object.</span></span> <span data-ttu-id="3721a-135">Vzhledem k tomu, že všechny objekty jsou postaveny na standardní rozhraní, můžete společně zřetězit více objektů (například objekt algoritmu hash a potom objektem šifrování), a můžete provádět více operací na základě dat bez nutnosti jakékoli zprostředkující úložiště pro ni.</span><span class="sxs-lookup"><span data-stu-id="3721a-135">Because all the objects are built on a standard interface, you can chain together multiple objects (such as a hash object followed by an encryption object), and you can perform multiple operations on the data without needing any intermediate storage for it.</span></span> <span data-ttu-id="3721a-136">Streamování modelu také umožňuje vytvářet objekty z menších objektů.</span><span class="sxs-lookup"><span data-stu-id="3721a-136">The streaming model also enables you to build objects from smaller objects.</span></span> <span data-ttu-id="3721a-137">Například Kombinovaný algoritmus šifrování a hash lze zobrazit jako objekt jednoho datového proudu, i když tento objekt může být sestaven z sadu objektů datového proudu.</span><span class="sxs-lookup"><span data-stu-id="3721a-137">For example, a combined encryption and hash algorithm can be viewed as a single stream object, although this object might be built from a set of stream objects.</span></span>  
  
## <a name="cryptographic-configuration"></a><span data-ttu-id="3721a-138">Konfigurace kryptografie</span><span class="sxs-lookup"><span data-stu-id="3721a-138">Cryptographic Configuration</span></span>  
 <span data-ttu-id="3721a-139">Konfigurace kryptografie umožňuje vyřešit konkrétní implementaci algoritmu na název algoritmu, což rozšíření tříd šifrování .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3721a-139">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET Framework cryptography classes.</span></span> <span data-ttu-id="3721a-140">Můžete přidat vlastní hardware nebo software implementaci algoritmu a mapovat implementaci název algoritmu podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="3721a-140">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="3721a-141">Pokud není algoritmus zadané v konfiguračním souboru, použijí se výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="3721a-141">If an algorithm is not specified in the configuration file, the default settings are used.</span></span> <span data-ttu-id="3721a-142">Další informace o kryptografických konfiguraci najdete v tématu [konfigurace šifrovacích tříd](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span><span class="sxs-lookup"><span data-stu-id="3721a-142">For more information about cryptographic configuration, see [Configuring Cryptography Classes](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span></span>  
  
## <a name="choosing-an-algorithm"></a><span data-ttu-id="3721a-143">Výběr algoritmu</span><span class="sxs-lookup"><span data-stu-id="3721a-143">Choosing an Algorithm</span></span>  
 <span data-ttu-id="3721a-144">Můžete vybrat algoritmus různých důvodů: například pro integritu dat, ochrany osobních údajů, nebo informace o generování klíče.</span><span class="sxs-lookup"><span data-stu-id="3721a-144">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="3721a-145">Algoritmy Symmetric a hash jsou určeny k ochraně dat pro integritu důvodů (chránit před změn) nebo z důvodů ochrany osobních údajů (ochrana ze zobrazení).</span><span class="sxs-lookup"><span data-stu-id="3721a-145">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="3721a-146">Algoritmy hash se používají primárně pro integritu dat.</span><span class="sxs-lookup"><span data-stu-id="3721a-146">Hash algorithms are used primarily for data integrity.</span></span>  
  
 <span data-ttu-id="3721a-147">Tady je seznam doporučené algoritmy aplikací:</span><span class="sxs-lookup"><span data-stu-id="3721a-147">Here is a list of recommended algorithms by application:</span></span>  
  
-   <span data-ttu-id="3721a-148">Ochrana dat:</span><span class="sxs-lookup"><span data-stu-id="3721a-148">Data privacy:</span></span>  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   <span data-ttu-id="3721a-149">Integrita dat:</span><span class="sxs-lookup"><span data-stu-id="3721a-149">Data integrity:</span></span>  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   <span data-ttu-id="3721a-150">Digitální podpis:</span><span class="sxs-lookup"><span data-stu-id="3721a-150">Digital signature:</span></span>  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   <span data-ttu-id="3721a-151">Výměna klíčů:</span><span class="sxs-lookup"><span data-stu-id="3721a-151">Key exchange:</span></span>  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   <span data-ttu-id="3721a-152">Náhodné generování čísel:</span><span class="sxs-lookup"><span data-stu-id="3721a-152">Random number generation:</span></span>  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   <span data-ttu-id="3721a-153">Generování klíče z hesla:</span><span class="sxs-lookup"><span data-stu-id="3721a-153">Generating a key from a password:</span></span>  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a><span data-ttu-id="3721a-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="3721a-154">See Also</span></span>  
 [<span data-ttu-id="3721a-155">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="3721a-155">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 
