---
title: Silné názvy (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140633"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="d7761-102">Silné názvy (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="d7761-102">Strong Naming (Unmanaged API Reference)</span></span>
<span data-ttu-id="d7761-103">Silné rozhraní API pro pojmenování umožňuje klientovi spravovat podepisování silných názvů pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7761-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="d7761-104">Podepisování sestavení se silným názvem přidá šifrování veřejného klíče do souboru obsahujícího manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7761-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="d7761-105">Podpis silného názvu pomáhá ověřit jedinečnost názvu, zabraňuje falšování názvů a poskytuje volajícím jedinečnou identitu při překladu odkazu.</span><span class="sxs-lookup"><span data-stu-id="d7761-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="d7761-106">Žádná úroveň důvěryhodnosti však není spojena se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="d7761-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7761-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d7761-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7761-108">Všechny tyto funkce byly zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="d7761-109">Navrhované alternativy naleznete v rozhraní [ICLRStrongName.](../hosting/iclrstrongname-interface.md)</span><span class="sxs-lookup"><span data-stu-id="d7761-109">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="d7761-110">GetHashFromAssemblyFile – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-110">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="d7761-111">Získá hash zadaného souboru sestavení pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="d7761-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="d7761-112">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-113">GetHashFromAssemblyFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-113">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="d7761-114">Získá hash souboru sestavení zadané jako řetězec Unicode pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="d7761-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="d7761-115">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-116">GetHashFromBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-116">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="d7761-117">Získá hash sestavení na zadanou adresu paměti pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="d7761-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="d7761-118">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-119">GetHashFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-119">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="d7761-120">Generuje hash nad obsahem zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="d7761-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="d7761-121">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-122">GetHashFromFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-122">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="d7761-123">Generuje hash nad obsahem souboru určeného řetězcem Unicode.</span><span class="sxs-lookup"><span data-stu-id="d7761-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="d7761-124">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-125">GetHashFromHandle – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-125">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="d7761-126">Generuje hash nad obsahem souboru se zadaným popisovačem souboru pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="d7761-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="d7761-127">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-128">StrongNameCompareAssemblies – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-128">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="d7761-129">Určuje, zda se dvě sestavení liší pouze podpisy silného názvu.</span><span class="sxs-lookup"><span data-stu-id="d7761-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="d7761-130">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-131">StrongNameErrorInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-131">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="d7761-132">Získá poslední kód chyby, která byla vyvolána jedním z funkce silného názvu.</span><span class="sxs-lookup"><span data-stu-id="d7761-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="d7761-133">StrongNameFreeBuffer – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-133">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="d7761-134">Uvolní paměť, která byla přidělena s předchozím voláním funkce silného názvu, jako je [například StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)nebo [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="d7761-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="d7761-135">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-136">StrongNameGetBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-136">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="d7761-137">Vyplní zadanou vyrovnávací paměť binární reprezentací spustitelného souboru na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="d7761-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="d7761-138">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-139">StrongNameGetBlobFromImage – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-139">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="d7761-140">Získá binární reprezentaci obrazu sestavení na zadanou adresu paměti.</span><span class="sxs-lookup"><span data-stu-id="d7761-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="d7761-141">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-142">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-142">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="d7761-143">Získá veřejný klíč z dvojice soukromého a veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="d7761-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="d7761-144">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-145">StrongNameHashSize – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-145">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="d7761-146">Získá velikost vyrovnávací paměti požadovanou pro algoritmus hash pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="d7761-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="d7761-147">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-148">StrongNameKeyDelete – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-148">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="d7761-149">Odstraní zadaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="d7761-149">Deletes the specified key container.</span></span> <span data-ttu-id="d7761-150">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-151">StrongNameKeyGen – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-151">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="d7761-152">Vytvoří nový pár veřejného a soukromého klíče pro použití silného názvu.</span><span class="sxs-lookup"><span data-stu-id="d7761-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="d7761-153">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-154">StrongNameKeyGenEx – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-154">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="d7761-155">Generuje nový pár veřejného a soukromého klíče se zadanou velikostí klíče pro použití silného názvu.</span><span class="sxs-lookup"><span data-stu-id="d7761-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="d7761-156">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-157">StrongNameKeyInstall – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-157">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="d7761-158">Importuje pár veřejného a soukromého klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d7761-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="d7761-159">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-160">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-160">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="d7761-161">Generuje podpis silného názvu pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7761-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="d7761-162">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-163">StrongNameSignatureGenerationEx – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-163">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="d7761-164">Generuje podpis silného názvu pro zadané sestavení na základě zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="d7761-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="d7761-165">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-166">StrongNameSignatureSize – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-166">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="d7761-167">Vrátí velikost podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="d7761-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="d7761-168">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-169">StrongNameSignatureVerification – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-169">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="d7761-170">Získá hodnotu označující, zda manifest sestavení na zadané cestě obsahuje podpis silného názvu, který je ověřen podle zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="d7761-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="d7761-171">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-172">StrongNameSignatureVerificationEx – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-172">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="d7761-173">Získá hodnotu označující, zda manifest sestavení na zadané cestě obsahuje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="d7761-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="d7761-174">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-175">StrongNameSignatureVerificationFromImage – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-175">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="d7761-176">Ověří, zda je sestavení, které již bylo namapováno do paměti, platné pro přidružený veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="d7761-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="d7761-177">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-178">StrongNameTokenFromAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-178">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="d7761-179">Vytvoří token silného názvu ze zadaného souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7761-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="d7761-180">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-181">StrongNameTokenFromAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-181">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="d7761-182">Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="d7761-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="d7761-183">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-184">StrongNameTokenFromPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="d7761-184">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="d7761-185">Získá token představující veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="d7761-185">Gets a token representing a public key.</span></span> <span data-ttu-id="d7761-186">Zastaralé počínaje rozhraním .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7761-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d7761-187">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="d7761-187">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="d7761-188">Představuje veřejný klíč dvojice veřejného a soukromého klíče v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="d7761-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7761-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7761-189">See also</span></span>

- [<span data-ttu-id="d7761-190">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7761-190">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="d7761-191">Nespravované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d7761-191">Unmanaged API Reference</span></span>](../index.md)
