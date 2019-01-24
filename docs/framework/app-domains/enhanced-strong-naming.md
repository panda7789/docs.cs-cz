---
title: Vylepšené silné názvy
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b63e27a3eceb80d42d43eea321b0dc757ad69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688859"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="1107e-102">Vylepšené silné názvy</span><span class="sxs-lookup"><span data-stu-id="1107e-102">Enhanced Strong Naming</span></span>
<span data-ttu-id="1107e-103">Podpis silného názvu je mechanismus identity v rozhraní .NET Framework pro identifikaci sestavení.</span><span class="sxs-lookup"><span data-stu-id="1107e-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="1107e-104">Je digitální podpis veřejného klíče, který se obvykle používá k ověření integrity dat předávaných od příkazce (podepisující) příjemci (ověřovatel).</span><span class="sxs-lookup"><span data-stu-id="1107e-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="1107e-105">Tento podpis slouží jako jedinečná identita pro sestavení a zajistí, že odkazy na sestavení nejsou nejednoznačné.</span><span class="sxs-lookup"><span data-stu-id="1107e-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="1107e-106">Sestavení je podepsáno jako součást procesu sestavení a poté ověřeno, pokud je načten.</span><span class="sxs-lookup"><span data-stu-id="1107e-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="1107e-107">Podpisy se silným názvem pomáhají zabránit zlými úmysly v manipulaci se sestavením a opětovné podepsat sestavení s klíčem původního podepisujícího.</span><span class="sxs-lookup"><span data-stu-id="1107e-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="1107e-108">Však klíče se silným názvem neobsahují žádné spolehlivé informace o vydavateli, ani neobsahují hierarchii certifikátů.</span><span class="sxs-lookup"><span data-stu-id="1107e-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="1107e-109">Podpis silného názvu nezaručuje důvěryhodnost osoby, která podepsala sestavení nebo určit, zda tato osoba byla legitimním vlastníkem tohoto klíče; znamená to pouze, že vlastník tohoto klíče sestavení podepsal.</span><span class="sxs-lookup"><span data-stu-id="1107e-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="1107e-110">Proto nedoporučujeme použití podpisu silného názvu jako validátoru zabezpečení pro důvěřující kód třetí strany.</span><span class="sxs-lookup"><span data-stu-id="1107e-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="1107e-111">Microsoft Authenticode je doporučeným způsobem, jak ověřit kód.</span><span class="sxs-lookup"><span data-stu-id="1107e-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="1107e-112">Omezení konvenčních silných názvů.</span><span class="sxs-lookup"><span data-stu-id="1107e-112">Limitations of Conventional Strong Names</span></span>  
 <span data-ttu-id="1107e-113">Technologie silného pojmenování používaná ve verzích před [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] má následující nedostatky:</span><span class="sxs-lookup"><span data-stu-id="1107e-113">The strong naming technology used in versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has the following shortcomings:</span></span>  
  
-   <span data-ttu-id="1107e-114">Klíče jsou neustále pod útokem a dokonalejší metody a hardware usnadňují odvození soukromého klíče z veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="1107e-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="1107e-115">Pro ochranu proti útokům jsou nezbytné větší klíče.</span><span class="sxs-lookup"><span data-stu-id="1107e-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="1107e-116">Verze rozhraní .NET framework před [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] poskytují možnost přihlásit se pomocí klíče libovolné velikosti (výchozí velikost je 1024 bitů), ale podepsání sestavy s novým klíčem zalomí všechny binární soubory, které odkazují na starší identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="1107e-116">.NET Framework versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="1107e-117">Proto je velmi obtížné upgradovat velikost podpisového klíče, pokud chcete zachovat kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="1107e-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
-   <span data-ttu-id="1107e-118">Podepisování se silným názvem podporuje pouze algoritmus SHA-1.</span><span class="sxs-lookup"><span data-stu-id="1107e-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="1107e-119">SHA-1 bylo nedávno zjištěno jako nedostatečné pro zatřiďování zabezpečených aplikací.</span><span class="sxs-lookup"><span data-stu-id="1107e-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="1107e-120">Proto silnější algoritmus (SHA-256 nebo vyšší), je nezbytné.</span><span class="sxs-lookup"><span data-stu-id="1107e-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="1107e-121">Je možné, že algoritmus SHA-1, dojde ke ztrátě jeho postavení kompatibilní se standardem FIPS, což by problémy pro ty, kteří se rozhodli použít pouze kompatibilní se standardem FIPS software a algoritmy.</span><span class="sxs-lookup"><span data-stu-id="1107e-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="1107e-122">Výhody rozšířených silných názvů</span><span class="sxs-lookup"><span data-stu-id="1107e-122">Advantages of Enhanced Strong Names</span></span>  
 <span data-ttu-id="1107e-123">Hlavní výhody rozšířených silných názvů jsou kompatibilita se stávajícími silnými názvy a schopnost rozhodovat, že se jedna identita odpovídá jiné:</span><span class="sxs-lookup"><span data-stu-id="1107e-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
-   <span data-ttu-id="1107e-124">Vývojáři, kteří mají existující podepsaná sestavení mohou přenést svoji identitu na algoritmy SHA-2 při zachování kompatibility se sestaveními, která odkazují na staré identity.</span><span class="sxs-lookup"><span data-stu-id="1107e-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
-   <span data-ttu-id="1107e-125">Vývojáři, kteří vytvářejí nová sestavení a nejsou obeznámeni s již existujícími podpisy silného názvu můžete používat bezpečnější algoritmus SHA-2 a podepsat sestavení, tak jako vždy.</span><span class="sxs-lookup"><span data-stu-id="1107e-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="using-enhanced-strong-names"></a><span data-ttu-id="1107e-126">Použití vylepšených silných názvů</span><span class="sxs-lookup"><span data-stu-id="1107e-126">Using Enhanced Strong Names</span></span>  
 <span data-ttu-id="1107e-127">Klíče se silným názvem jsou tvořeny podpisovými klíči a klíč identity.</span><span class="sxs-lookup"><span data-stu-id="1107e-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="1107e-128">Sestavení je podepsáno pomocí klíče podpisu a je určeno klíčem identity.</span><span class="sxs-lookup"><span data-stu-id="1107e-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="1107e-129">Před verzí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], byly tyto dva klíče identické.</span><span class="sxs-lookup"><span data-stu-id="1107e-129">Prior to the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], these two keys were identical.</span></span> <span data-ttu-id="1107e-130">Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zůstává klíč identity stejný jako v předchozích verzích rozhraní .NET Framework, ale podpis klíče jsou rozšířeny silnější hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="1107e-130">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="1107e-131">Kromě toho podpisový klíč je podepsán klíčem identity pro tvorbu protipodpisu.</span><span class="sxs-lookup"><span data-stu-id="1107e-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="1107e-132"><xref:System.Reflection.AssemblySignatureKeyAttribute> Atribut umožňuje metadatům sestavení použít již existující veřejný klíč pro identitu sestavení, což umožňuje starším odkazům sestavení pokračovat v práci.</span><span class="sxs-lookup"><span data-stu-id="1107e-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="1107e-133"><xref:System.Reflection.AssemblySignatureKeyAttribute> Atribut používá protipodpis zajišťující, že vlastník nového klíče podpisu je také vlastníkem starého klíče identity.</span><span class="sxs-lookup"><span data-stu-id="1107e-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="signing-with-sha-2-without-key-migration"></a><span data-ttu-id="1107e-134">Přihlášení pomocí SHA-2 bez migrace klíče</span><span class="sxs-lookup"><span data-stu-id="1107e-134">Signing with SHA-2, Without Key Migration</span></span>  
 <span data-ttu-id="1107e-135">Spusťte následující příkazy z okna příkazového řádku a podepište tak sestavení bez přenášeného podpisu se silným názvem:</span><span class="sxs-lookup"><span data-stu-id="1107e-135">Run the following commands from a Command Prompt window to sign an assembly without migrating a strong name signature:</span></span>  
  
1.  <span data-ttu-id="1107e-136">Generovat nový klíč identity (v případě potřeby).</span><span class="sxs-lookup"><span data-stu-id="1107e-136">Generate the new identity key (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  <span data-ttu-id="1107e-137">Extrahujte veřejný klíč identity a určí, že algoritmus SHA-2 má být použit při přihlašování k tomuto klíči.</span><span class="sxs-lookup"><span data-stu-id="1107e-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="1107e-138">Vytvoří zpožděný podpis sestavení se souborem identity veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="1107e-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  <span data-ttu-id="1107e-139">Znovu podepište sestavení pomocí dvojice klíčů plnou identitou.</span><span class="sxs-lookup"><span data-stu-id="1107e-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a><span data-ttu-id="1107e-140">Přihlášení pomocí SHA-2 s migrací klíče</span><span class="sxs-lookup"><span data-stu-id="1107e-140">Signing with SHA-2, with Key Migration</span></span>  
 <span data-ttu-id="1107e-141">Spusťte následující příkazy z okna příkazového řádku a podepište tak sestavení s podpisem migrované silného názvu.</span><span class="sxs-lookup"><span data-stu-id="1107e-141">Run the following commands from a Command Prompt window to sign an assembly with a migrated strong name signature.</span></span>  
  
1.  <span data-ttu-id="1107e-142">Generování identitu a dvojici podpisových klíčů (v případě potřeby).</span><span class="sxs-lookup"><span data-stu-id="1107e-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  <span data-ttu-id="1107e-143">Extrahujte veřejný podpisový klíč a určí, že algoritmus SHA-2 má být použit při přihlašování k tomuto klíči.</span><span class="sxs-lookup"><span data-stu-id="1107e-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="1107e-144">Extrahujte veřejný klíč identity, která určuje algoritmus hash, který generuje podpis čítače.</span><span class="sxs-lookup"><span data-stu-id="1107e-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  <span data-ttu-id="1107e-145">Parametry pro generování <xref:System.Reflection.AssemblySignatureKeyAttribute> atributu a připojení atributu k sestavení.</span><span class="sxs-lookup"><span data-stu-id="1107e-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="1107e-146">To vytváří výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="1107e-146">This produces output similar to the following.</span></span>

    ```
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

    <span data-ttu-id="1107e-147">Tento výstup, pak je možné transformovat do atributu assemblysignaturekeyattribute je uveden.</span><span class="sxs-lookup"><span data-stu-id="1107e-147">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5.  <span data-ttu-id="1107e-148">Vytvoří zpožděný podpis sestavení s veřejným klíčem identity.</span><span class="sxs-lookup"><span data-stu-id="1107e-148">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  <span data-ttu-id="1107e-149">Plně podepište sestavení pomocí dvojice podpisových klíčů.</span><span class="sxs-lookup"><span data-stu-id="1107e-149">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1107e-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1107e-150">See also</span></span>
- [<span data-ttu-id="1107e-151">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="1107e-151">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
