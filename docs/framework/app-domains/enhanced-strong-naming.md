---
title: "Vylepšené silné názvy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77eec473b95720e432c94b79778fa518f3ecf1c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="e6322-102">Vylepšené silné názvy</span><span class="sxs-lookup"><span data-stu-id="e6322-102">Enhanced Strong Naming</span></span>
<span data-ttu-id="e6322-103">Podpis silného názvu je mechanismus identity v rozhraní .NET Framework pro identifikaci sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6322-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="e6322-104">Je digitální podpis veřejného klíče, který se obvykle používá k ověření integrity dat, které jsou předávány z původce (podepisující osoba) k příjemce (ověřovatele).</span><span class="sxs-lookup"><span data-stu-id="e6322-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="e6322-105">Tento podpis slouží jako jedinečnou identitu pro sestavení a zajišťuje, aby odkazy na sestavení byla jednoznačná.</span><span class="sxs-lookup"><span data-stu-id="e6322-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="e6322-106">Sestavení je podepsaný jako součást procesu sestavení a potom ověřit, když je načten.</span><span class="sxs-lookup"><span data-stu-id="e6322-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="e6322-107">Silné jméno podpisy Zabraňte zlými úmysly manipulovat se sestavení a opětovné podepisování sestavení s klíčem původní podepisující osoba.</span><span class="sxs-lookup"><span data-stu-id="e6322-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="e6322-108">Ale klíče silný název nesmí obsahovat žádné spolehlivé informace o vydavateli, ani obsahují hierarchie certifikačních autorit.</span><span class="sxs-lookup"><span data-stu-id="e6322-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="e6322-109">Podpis silného názvu zaručit důvěryhodnost osoby, která podepsala sestavení nebo označuje, zda byla tato osoba legitimní vlastníka klíče; Označuje, pouze zda Vlastník klíče podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6322-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="e6322-110">Nedoporučujeme proto pomocí podpis silného názvu jako validátor zabezpečení pro důvěryhodné kód třetích stran.</span><span class="sxs-lookup"><span data-stu-id="e6322-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="e6322-111">Microsoft Authenticode je doporučený způsob ověření kódu.</span><span class="sxs-lookup"><span data-stu-id="e6322-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="e6322-112">Omezení konvenční silné názvy</span><span class="sxs-lookup"><span data-stu-id="e6322-112">Limitations of Conventional Strong Names</span></span>  
 <span data-ttu-id="e6322-113">Silné pojmenování technologie používané ve verzi před [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] má následující nedostatků:</span><span class="sxs-lookup"><span data-stu-id="e6322-113">The strong naming technology used in versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has the following shortcomings:</span></span>  
  
-   <span data-ttu-id="e6322-114">Klíče jsou neustále probíhá útok a vylepšené technik a hardwaru usnadňují odvodit privátní klíč z veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="e6322-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="e6322-115">Ochrana před útoky, větší klíče jsou nezbytné.</span><span class="sxs-lookup"><span data-stu-id="e6322-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="e6322-116">Verze rozhraní .NET framework před [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] poskytují možnost přihlášení pomocí jakékoli velikost klíče (výchozí velikost je 1 024 bitů), ale podepsání sestavení pomocí nového klíče dělí všechny binární soubory, které odkazují na starší identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6322-116">.NET Framework versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="e6322-117">Proto je velmi obtížné upgrade velikost podpisový klíč, pokud chcete, aby byla zachována kompatibilita.</span><span class="sxs-lookup"><span data-stu-id="e6322-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
-   <span data-ttu-id="e6322-118">Podpis silného názvu podporuje pouze algoritmus SHA-1.</span><span class="sxs-lookup"><span data-stu-id="e6322-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="e6322-119">Nedávno bylo zjištěno SHA-1, nedostatečné pro zabezpečené hash aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6322-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="e6322-120">Proto se silnějším algoritmem je nutné (SHA-256 nebo vyšší).</span><span class="sxs-lookup"><span data-stu-id="e6322-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="e6322-121">Je možné, že SHA-1, dojde ke ztrátě jejího kompatibilní se standardem FIPS umístění, která by měla představit problémy pro ty, kteří se rozhodnou používejte pouze kompatibilní se standardem FIPS softwaru a algoritmy.</span><span class="sxs-lookup"><span data-stu-id="e6322-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="e6322-122">Výhody vylepšené silné názvy</span><span class="sxs-lookup"><span data-stu-id="e6322-122">Advantages of Enhanced Strong Names</span></span>  
 <span data-ttu-id="e6322-123">Hlavní výhody vylepšené silné názvy jsou kompatibilitu s existující silné názvy a schopnost deklarace identity na jiný odpovídá jedné identity:</span><span class="sxs-lookup"><span data-stu-id="e6322-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
-   <span data-ttu-id="e6322-124">Vývojáři, kteří mají existující podepsaná sestavení můžete migrovat své identity algoritmy SHA-2 při zachování kompatibility s sestavení, které odkazují na staré identity.</span><span class="sxs-lookup"><span data-stu-id="e6322-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
-   <span data-ttu-id="e6322-125">Vývojáři, kteří vytvářejí nové sestavení a nevadí existující podpisy silným názvem můžete používat bezpečnější algoritmus SHA-2 a podepsání sestavení mají vždy.</span><span class="sxs-lookup"><span data-stu-id="e6322-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="using-enhanced-strong-names"></a><span data-ttu-id="e6322-126">Pomocí vylepšené silné názvy</span><span class="sxs-lookup"><span data-stu-id="e6322-126">Using Enhanced Strong Names</span></span>  
 <span data-ttu-id="e6322-127">Silné jméno klíče obsahovat klíč podpisu a klíč identity.</span><span class="sxs-lookup"><span data-stu-id="e6322-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="e6322-128">Sestavení je podepsán klíč podpisu a je určeno klíčem identity.</span><span class="sxs-lookup"><span data-stu-id="e6322-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="e6322-129">Před verzí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], tyto dva klíče byly identické.</span><span class="sxs-lookup"><span data-stu-id="e6322-129">Prior to the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], these two keys were identical.</span></span> <span data-ttu-id="e6322-130">Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], klíč identity zůstává stejná jako v předchozích verzích rozhraní .NET Framework, ale klíč podpisu je rozšířené silnější algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="e6322-130">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="e6322-131">Kromě toho klíč podpisu je podepsán klíč identity vytvoří kontrolní podpis.</span><span class="sxs-lookup"><span data-stu-id="e6322-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="e6322-132"><xref:System.Reflection.AssemblySignatureKeyAttribute> Atribut umožňuje metadata sestavení používat existující veřejný klíč pro identitu, sestavení, která umožňuje staré odkazy na sestavení, chcete-li pokračovat v práci.</span><span class="sxs-lookup"><span data-stu-id="e6322-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="e6322-133"><xref:System.Reflection.AssemblySignatureKeyAttribute> Atribut používá kontrolní podpis, aby vlastník nového klíče podpisu je také vlastníkem starý klíč identity.</span><span class="sxs-lookup"><span data-stu-id="e6322-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="signing-with-sha-2-without-key-migration"></a><span data-ttu-id="e6322-134">Podepsání pomocí algoritmu SHA-2, bez migrace klíče</span><span class="sxs-lookup"><span data-stu-id="e6322-134">Signing with SHA-2, Without Key Migration</span></span>  
 <span data-ttu-id="e6322-135">Spusťte následující příkazy z okna příkazového řádku pro podepsání sestavení bez migrace podpis silného názvu:</span><span class="sxs-lookup"><span data-stu-id="e6322-135">Run the following commands from a Command Prompt window to sign an assembly without migrating a strong name signature:</span></span>  
  
1.  <span data-ttu-id="e6322-136">Vygenerujte nový klíč identity (v případě potřeby).</span><span class="sxs-lookup"><span data-stu-id="e6322-136">Generate the new identity key (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  <span data-ttu-id="e6322-137">Extrahujte identity veřejný klíč a zadat, že algoritmus SHA-2 má být použita při přihlašování pomocí tohoto klíče.</span><span class="sxs-lookup"><span data-stu-id="e6322-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="e6322-138">Zpoždění podepsání sestavení s identity soubor veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="e6322-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  <span data-ttu-id="e6322-139">Nové podepsání sestavení s páru klíčů úplné identity.</span><span class="sxs-lookup"><span data-stu-id="e6322-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a><span data-ttu-id="e6322-140">Podepsání pomocí algoritmu SHA-2, přičemž migrace klíče</span><span class="sxs-lookup"><span data-stu-id="e6322-140">Signing with SHA-2, with Key Migration</span></span>  
 <span data-ttu-id="e6322-141">Spusťte následující příkazy z okna příkazového řádku pro podepsání sestavení podpisem migrované silným názvem.</span><span class="sxs-lookup"><span data-stu-id="e6322-141">Run the following commands from a Command Prompt window to sign an assembly with a migrated strong name signature.</span></span>  
  
1.  <span data-ttu-id="e6322-142">Generovat identity a podpis pár klíčů (v případě potřeby).</span><span class="sxs-lookup"><span data-stu-id="e6322-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  <span data-ttu-id="e6322-143">Extrahujte podpis veřejný klíč a zadat, že algoritmus SHA-2 má být použita při přihlašování pomocí tohoto klíče.</span><span class="sxs-lookup"><span data-stu-id="e6322-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="e6322-144">Extrahujte veřejný klíč identity, který určuje algoritmus hash, který generuje kontrolní podpis.</span><span class="sxs-lookup"><span data-stu-id="e6322-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  <span data-ttu-id="e6322-145">Generovat parametry <xref:System.Reflection.AssemblySignatureKeyAttribute> atribut a atribut přiřadit sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6322-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  <span data-ttu-id="e6322-146">Zpoždění podepsání sestavení s veřejným klíčem identity.</span><span class="sxs-lookup"><span data-stu-id="e6322-146">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  <span data-ttu-id="e6322-147">Plně podepište sestavení tohoto páru klíčů pro podpis.</span><span class="sxs-lookup"><span data-stu-id="e6322-147">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e6322-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6322-148">See Also</span></span>  
 [<span data-ttu-id="e6322-149">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="e6322-149">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
