---
title: Silné názvy (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140633"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="9b841-102">Silné názvy (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9b841-102">Strong Naming (Unmanaged API Reference)</span></span>
<span data-ttu-id="9b841-103">Rozhraní API pro silné pojmenování umožňuje klientovi spravovat podepisování silného názvu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b841-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="9b841-104">Podpis sestavení se silným názvem přidá šifrování pomocí veřejného klíče do souboru obsahujícího manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b841-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="9b841-105">Podepisování silného názvu pomáhá ověřit jedinečnost názvu, zabraňuje falšování názvu a poskytuje volajícím s jedinečnou identitou, když je odkaz vyřešen.</span><span class="sxs-lookup"><span data-stu-id="9b841-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="9b841-106">Nicméně není k dispozici žádná úroveň důvěryhodnosti se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9b841-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b841-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9b841-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b841-108">Všechny tyto funkce jsou zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="9b841-109">Navrhované alternativy najdete v rozhraní [ICLRStrongName](../hosting/iclrstrongname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9b841-109">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="9b841-110">GetHashFromAssemblyFile – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-110">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="9b841-111">Načte hodnotu hash zadaného souboru sestavení pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="9b841-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="9b841-112">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-113">GetHashFromAssemblyFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-113">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="9b841-114">Načte hodnotu hash souboru sestavení zadaného jako řetězec Unicode pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="9b841-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="9b841-115">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-116">GetHashFromBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-116">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="9b841-117">Načte hodnotu hash sestavení v zadané adrese paměti pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="9b841-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="9b841-118">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-119">GetHashFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-119">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="9b841-120">Vygeneruje hodnotu hash přes obsah zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="9b841-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="9b841-121">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-122">GetHashFromFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-122">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="9b841-123">Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.</span><span class="sxs-lookup"><span data-stu-id="9b841-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="9b841-124">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-125">GetHashFromHandle – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-125">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="9b841-126">Vygeneruje hodnotu hash přes obsah souboru se zadaným popisovačem souboru pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="9b841-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="9b841-127">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-128">StrongNameCompareAssemblies – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-128">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="9b841-129">Určuje, zda se dvě sestavení liší pouze signaturami silného názvu.</span><span class="sxs-lookup"><span data-stu-id="9b841-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="9b841-130">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-131">StrongNameErrorInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-131">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="9b841-132">Získá poslední kód chyby, který byl vyvolán jednou ze všech funkcí se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9b841-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="9b841-133">StrongNameFreeBuffer – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-133">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="9b841-134">Uvolní paměť, která byla přidělena předchozímu volání funkce silného názvu, jako je například [StrongNameGetPublicKey –](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey –](strongnametokenfrompublickey-function.md)nebo [StrongNameSignatureGeneration –](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="9b841-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="9b841-135">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-136">StrongNameGetBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-136">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="9b841-137">Vyplní zadanou vyrovnávací paměť binární reprezentací spustitelného souboru na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="9b841-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="9b841-138">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-139">StrongNameGetBlobFromImage – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-139">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="9b841-140">Načte binární reprezentaci image sestavení v zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="9b841-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="9b841-141">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-142">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-142">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="9b841-143">Získá veřejný klíč z páru privátních a veřejných klíčů.</span><span class="sxs-lookup"><span data-stu-id="9b841-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="9b841-144">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-145">StrongNameHashSize – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-145">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="9b841-146">Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="9b841-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="9b841-147">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-148">StrongNameKeyDelete – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-148">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="9b841-149">Odstraní zadaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="9b841-149">Deletes the specified key container.</span></span> <span data-ttu-id="9b841-150">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-151">StrongNameKeyGen – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-151">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="9b841-152">Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9b841-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="9b841-153">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-154">StrongNameKeyGenEx – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-154">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="9b841-155">Vygeneruje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9b841-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="9b841-156">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-157">StrongNameKeyInstall – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-157">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="9b841-158">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9b841-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="9b841-159">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-160">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-160">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="9b841-161">Vygeneruje podpis silného názvu pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b841-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="9b841-162">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-163">StrongNameSignatureGenerationEx – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-163">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="9b841-164">Vygeneruje podpis silného názvu pro zadané sestavení na základě zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="9b841-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="9b841-165">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-166">StrongNameSignatureSize – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-166">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="9b841-167">Vrátí velikost podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="9b841-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="9b841-168">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-169">StrongNameSignatureVerification – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-169">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="9b841-170">Získá hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu, který je ověřen podle zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="9b841-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="9b841-171">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-172">StrongNameSignatureVerificationEx – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-172">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="9b841-173">Načte hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="9b841-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="9b841-174">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-175">StrongNameSignatureVerificationFromImage – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-175">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="9b841-176">Ověřuje, že sestavení, které již bylo namapováno do paměti, je platné pro přidružený veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="9b841-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="9b841-177">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-178">StrongNameTokenFromAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-178">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="9b841-179">Vytvoří ze zadaného souboru sestavení token se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9b841-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="9b841-180">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-181">StrongNameTokenFromAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-181">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="9b841-182">Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="9b841-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="9b841-183">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-184">StrongNameTokenFromPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="9b841-184">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="9b841-185">Získá token představující veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="9b841-185">Gets a token representing a public key.</span></span> <span data-ttu-id="9b841-186">Zastaralé od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b841-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="9b841-187">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="9b841-187">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="9b841-188">Představuje veřejný klíč páru veřejného a privátního klíče v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="9b841-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b841-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b841-189">See also</span></span>

- [<span data-ttu-id="9b841-190">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b841-190">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="9b841-191">Referenční informace o nespravovaném rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9b841-191">Unmanaged API Reference</span></span>](../index.md)
