---
title: Vylepšené silné názvy
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: 1d582513b10de88e4e5b9b9ef8c338599d6980f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141171"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="af989-102">Vylepšené silné názvy</span><span class="sxs-lookup"><span data-stu-id="af989-102">Enhanced strong naming</span></span>
<span data-ttu-id="af989-103">Podpis silného názvu je mechanismus identity v rozhraní .NET Framework pro identifikaci sestavení.</span><span class="sxs-lookup"><span data-stu-id="af989-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="af989-104">Jedná se o digitální podpis veřejného klíče, který se obvykle používá k ověření integrity dat předávaných od původce (autora podpisu) příjemci (ověřovateli).</span><span class="sxs-lookup"><span data-stu-id="af989-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="af989-105">Tento podpis se používá jako jedinečná identita pro sestavení a zajišťuje, že odkazy na sestavení nejsou nejednoznačné.</span><span class="sxs-lookup"><span data-stu-id="af989-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="af989-106">Sestavení je podepsáno jako součást procesu sestavení a poté ověřeno při jeho načtení.</span><span class="sxs-lookup"><span data-stu-id="af989-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="af989-107">Podpisy silného názvu pomáhají zabránit škodlivým stranám v manipulaci se sestavením a poté znovu podepsat sestavení pomocí klíče původního podepisujícího.</span><span class="sxs-lookup"><span data-stu-id="af989-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="af989-108">Klíče silných názvů však neobsahují žádné spolehlivé informace o vydavateli ani neobsahují hierarchii certifikátů.</span><span class="sxs-lookup"><span data-stu-id="af989-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="af989-109">Podpis silného jména nezaručuje důvěryhodnost osoby, která shromáždění podepsala, ani neoznačuje, zda byla tato osoba legitimním vlastníkem klíče; označuje pouze to, že vlastník klíče podepsal sestavení.</span><span class="sxs-lookup"><span data-stu-id="af989-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="af989-110">Proto nedoporučujeme používat podpis silného názvu jako validátor zabezpečení pro důvěřování kódu jiného výrobce.</span><span class="sxs-lookup"><span data-stu-id="af989-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="af989-111">Microsoft Authenticode je doporučený způsob ověření kódu.</span><span class="sxs-lookup"><span data-stu-id="af989-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="af989-112">Omezení konvenčních silných názvů</span><span class="sxs-lookup"><span data-stu-id="af989-112">Limitations of conventional strong names</span></span>  
 <span data-ttu-id="af989-113">Technologie silného pojmenování používaná ve verzích před rozhraním .NET Framework 4.5 má následující nedostatky:</span><span class="sxs-lookup"><span data-stu-id="af989-113">The strong naming technology used in versions before the .NET Framework 4.5 has the following shortcomings:</span></span>  
  
- <span data-ttu-id="af989-114">Klíče jsou neustále pod útokem a vylepšené techniky a hardware usnadňují odvodit soukromý klíč z veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="af989-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="af989-115">Pro ochranu před útoky jsou nezbytné větší klíče.</span><span class="sxs-lookup"><span data-stu-id="af989-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="af989-116">Verze rozhraní .NET Framework před rozhraním .NET Framework 4.5 poskytují možnost podepisovat klíč libovolné velikosti (výchozí velikost je 1024 bitů), ale podepisování sestavení s novým klíčem přeruší všechny binární soubory, které odkazují na starší identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="af989-116">.NET Framework versions before the .NET Framework 4.5 provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="af989-117">Proto je velmi obtížné upgradovat velikost podpisového klíče, pokud chcete zachovat kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="af989-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
- <span data-ttu-id="af989-118">Podepisování silných názvů podporuje pouze algoritmus SHA-1.</span><span class="sxs-lookup"><span data-stu-id="af989-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="af989-119">Sha-1 bylo nedávno zjištěno, že je nedostatečná pro bezpečné hašování aplikací.</span><span class="sxs-lookup"><span data-stu-id="af989-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="af989-120">Proto silnější algoritmus (SHA-256 nebo vyšší) je nezbytné.</span><span class="sxs-lookup"><span data-stu-id="af989-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="af989-121">Je možné, že SHA-1 ztratí své postavení kompatibilní s FIPS, což by představovalo problémy pro ty, kteří se rozhodnou používat pouze software a algoritmy kompatibilní s FIPS.</span><span class="sxs-lookup"><span data-stu-id="af989-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="af989-122">Výhody rozšířených silných názvů</span><span class="sxs-lookup"><span data-stu-id="af989-122">Advantages of enhanced strong names</span></span>  
 <span data-ttu-id="af989-123">Hlavními výhodami rozšířených silných názvů jsou kompatibilita s již existujícími silnými názvy a možnost tvrdit, že jedna identita je rovnocenná jiné:</span><span class="sxs-lookup"><span data-stu-id="af989-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
- <span data-ttu-id="af989-124">Vývojáři, kteří mají již existující podepsaná sestavení, mohou migrovat své identity do algoritmů SHA-2 při zachování kompatibility se sestaveními, která odkazují na staré identity.</span><span class="sxs-lookup"><span data-stu-id="af989-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
- <span data-ttu-id="af989-125">Vývojáři, kteří vytvářejí nová sestavení a nezabývají se již existujícími podpisy silných názvů, mohou používat bezpečnější algoritmy SHA-2 a podepisovat sestavení jako vždy.</span><span class="sxs-lookup"><span data-stu-id="af989-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="use-enhanced-strong-names"></a><span data-ttu-id="af989-126">Použití rozšířených silných názvů</span><span class="sxs-lookup"><span data-stu-id="af989-126">Use enhanced strong names</span></span>  
 <span data-ttu-id="af989-127">Klíče se silným názvem se skládají z klíče podpisu a klíče identity.</span><span class="sxs-lookup"><span data-stu-id="af989-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="af989-128">Sestavení je podepsáno podpisovým klíčem a je identifikováno klíčem identity.</span><span class="sxs-lookup"><span data-stu-id="af989-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="af989-129">Před rozhraním .NET Framework 4.5 byly tyto dva klíče identické.</span><span class="sxs-lookup"><span data-stu-id="af989-129">Prior to the .NET Framework 4.5, these two keys were identical.</span></span> <span data-ttu-id="af989-130">Počínaje rozhraním .NET Framework 4.5 zůstává klíč identity stejný jako v předchozích verzích rozhraní .NET Framework, ale klíč podpisu je vylepšen silnějším algoritmem hash.</span><span class="sxs-lookup"><span data-stu-id="af989-130">Starting with the .NET Framework 4.5, the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="af989-131">Kromě toho je podpisový klíč podepsán pomocí klíče identity k vytvoření protipodpisu.</span><span class="sxs-lookup"><span data-stu-id="af989-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="af989-132">Atribut <xref:System.Reflection.AssemblySignatureKeyAttribute> umožňuje metadatům sestavení použít již existující veřejný klíč pro identitu sestavení, což umožňuje, aby staré odkazy na sestavení pokračovaly v práci.</span><span class="sxs-lookup"><span data-stu-id="af989-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="af989-133">Atribut <xref:System.Reflection.AssemblySignatureKeyAttribute> používá protipodpis k zajištění, že vlastník nového klíče podpisu je také vlastníkem starého klíče identity.</span><span class="sxs-lookup"><span data-stu-id="af989-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="sign-with-sha-2-without-key-migration"></a><span data-ttu-id="af989-134">Podepisovat pomocí SHA-2 bez migrace klíčů</span><span class="sxs-lookup"><span data-stu-id="af989-134">Sign with SHA-2, without key migration</span></span>  
 <span data-ttu-id="af989-135">Spusťte následující příkazy z příkazového řádku a podepište sestavení bez migrace podpisu silného názvu:</span><span class="sxs-lookup"><span data-stu-id="af989-135">Run the following commands from a command prompt to sign an assembly without migrating a strong name signature:</span></span>  
  
1. <span data-ttu-id="af989-136">Vygenerujte nový klíč identity (v případě potřeby).</span><span class="sxs-lookup"><span data-stu-id="af989-136">Generate the new identity key (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. <span data-ttu-id="af989-137">Extrahujte veřejný klíč identity a určete, že algoritmus SHA-2 by měl být použit při podepisování pomocí tohoto klíče.</span><span class="sxs-lookup"><span data-stu-id="af989-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="af989-138">Zpoždění podepsat sestavení se souborem veřejného klíče identity.</span><span class="sxs-lookup"><span data-stu-id="af989-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. <span data-ttu-id="af989-139">Znovu podepište sestavení pomocí dvojice klíčů úplné identity.</span><span class="sxs-lookup"><span data-stu-id="af989-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a><span data-ttu-id="af989-140">Podepisování pomocí SHA-2 s migrací klíčů</span><span class="sxs-lookup"><span data-stu-id="af989-140">Sign with SHA-2, with key migration</span></span>  
 <span data-ttu-id="af989-141">Spusťte následující příkazy z příkazového řádku a podepište sestavení s emigrovaným podpisem silného názvu.</span><span class="sxs-lookup"><span data-stu-id="af989-141">Run the following commands from a command prompt to sign an assembly with a migrated strong name signature.</span></span>  
  
1. <span data-ttu-id="af989-142">Vygenerujte dvojici identity a podpisového klíče (v případě potřeby).</span><span class="sxs-lookup"><span data-stu-id="af989-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. <span data-ttu-id="af989-143">Extrahujte veřejný klíč podpisu a určete, že algoritmus SHA-2 by měl být použit při podepisování pomocí tohoto klíče.</span><span class="sxs-lookup"><span data-stu-id="af989-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="af989-144">Extrahovat veřejný klíč identity, který určuje algoritmus hash, který generuje protipodpis.</span><span class="sxs-lookup"><span data-stu-id="af989-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. <span data-ttu-id="af989-145">Vygenerujte <xref:System.Reflection.AssemblySignatureKeyAttribute> parametry atributu a připojte atribut k sestavení.</span><span class="sxs-lookup"><span data-stu-id="af989-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="af989-146">To vytváří výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="af989-146">This produces output similar to the following.</span></span>

    ```output
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    <span data-ttu-id="af989-147">Tento výstup pak lze transformovat do AssemblySignatureKeyAttribute.</span><span class="sxs-lookup"><span data-stu-id="af989-147">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. <span data-ttu-id="af989-148">Zpoždění podepsat sestavení s veřejným klíčem identity.</span><span class="sxs-lookup"><span data-stu-id="af989-148">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. <span data-ttu-id="af989-149">Plně podepsat sestavení s dvojicí podpisového klíče.</span><span class="sxs-lookup"><span data-stu-id="af989-149">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="af989-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="af989-150">See also</span></span>

- [<span data-ttu-id="af989-151">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="af989-151">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
