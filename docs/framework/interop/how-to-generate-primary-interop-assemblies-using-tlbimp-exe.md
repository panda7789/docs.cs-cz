---
title: 'Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1136dd3220b189d60b4972410ce0ce6657d07cd
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218980"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="2e9b9-102">Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="2e9b9-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>
<span data-ttu-id="2e9b9-103">Existují dva způsoby, jak vygenerovat primární spolupracující sestavení:</span><span class="sxs-lookup"><span data-stu-id="2e9b9-103">There are two ways to generate a primary interop assembly:</span></span>  
  
-   <span data-ttu-id="2e9b9-104">Použití [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) poskytované [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e9b9-104">Using the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
     <span data-ttu-id="2e9b9-105">Nejjednodušší způsob, jak vytvořit primárních sestavení vzájemné spolupráce je použít [Tlbimp.exe (Importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="2e9b9-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="2e9b9-106">Tlbimp.exe obsahuje následující bezpečnostní opatření:</span><span class="sxs-lookup"><span data-stu-id="2e9b9-106">Tlbimp.exe provides the following safeguards:</span></span>  
  
    -   <span data-ttu-id="2e9b9-107">Vyhledá další registrovaných primárních spolupracujících sestavení před vytvořením nového sestavení vzájemné spolupráce pro všechny odkazy na knihovnu vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>  
  
    -   <span data-ttu-id="2e9b9-108">Pokud nezadáte, kontejneru nebo souboru název primárního spolupracujícího sestavení silným názvem generování primárních sestavení vzájemné spolupráce se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>  
  
    -   <span data-ttu-id="2e9b9-109">Generování primárních sestavení vzájemné spolupráce vynecháte odkazy na závislé sestavení se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>  
  
    -   <span data-ttu-id="2e9b9-110">Generování primárního spolupracujícího sestavení, pokud přidáte odkazy na závislé sestavení, které nejsou primární spolupracující sestavení se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>  
  
-   <span data-ttu-id="2e9b9-111">Ruční vytváření primárních sestavení vzájemné spolupráce ve zdrojovém kódu pomocí jazyka, který je kompatibilní s specifikace CLS (Common Language), jako například C#.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="2e9b9-112">Tento přístup je užitečný, pokud knihovna typů není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-112">This approach is useful when a type library is unavailable.</span></span>  
  
 <span data-ttu-id="2e9b9-113">Musíte mít pár kryptografických klíčů k podepsání sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="2e9b9-114">Podrobnosti najdete v tématu [vytváření dvojice klíč A](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="2e9b9-114">For details, see [Creating A Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="2e9b9-115">Chcete-li vygenerovat primární sestavení vzájemné spolupráce pomocí Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="2e9b9-115">To generate a primary interop assembly using Tlbimp.exe</span></span>  
  
1.  <span data-ttu-id="2e9b9-116">V příkazovém řádku zadejte příkaz:</span><span class="sxs-lookup"><span data-stu-id="2e9b9-116">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="2e9b9-117">**Tlbimp** *tlbfile\*\*\*/primary/keyfile:*\* *filename* **/out:** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="2e9b9-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>  
  
     <span data-ttu-id="2e9b9-118">V tomto příkazu *tlbfile* je soubor, který obsahuje knihovnu typů modelu COM *filename* je název kontejneru nebo souboru, který obsahuje pár klíčů a *assemblyname* je název sestavení podepsáno pomocí silného názvu.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>  
  
 <span data-ttu-id="2e9b9-119">Primární spolupracující sestavení může odkazovat jenom jiných primárních sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="2e9b9-120">Pokud vaše sestavení používá odkazy na typy v knihovně typů modelu COM třetích stran, musíte získat primární spolupracující sestavení od vydavatele předtím, než můžete vygenerovat primární definiční sestavení.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="2e9b9-121">Pokud jste vydavatel, budete muset vygenerovat primární spolupracující sestavení pro závislou typovou knihovnu před generováním odkazující sestavení primární spolupráce.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>  
  
 <span data-ttu-id="2e9b9-122">Závislé primárního spolupracujícího sestavení s číslem verze, která se liší od původní knihovna typů není zjistitelné při instalaci v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="2e9b9-123">Musíte zaregistrovat závislé sestavení primární spolupráce v registru Windows nebo použít **/reference** možnost, abyste měli jistotu, že Tlbimp.exe najde závislá knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>  
  
 <span data-ttu-id="2e9b9-124">Můžete také zabalit několik verzí knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="2e9b9-125">Pokyny najdete v tématu [jak: Sbalení více verzí knihoven typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2e9b9-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e9b9-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e9b9-126">Example</span></span>  
 <span data-ttu-id="2e9b9-127">Následující příklad importuje knihovna typů COM `LibUtil.tlb` a podepíše sestavení `LibUtil.dll` se silným názvem pomocí souboru s klíči `CompanyA.snk`.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="2e9b9-128">Vynecháním názvu konkrétní obor názvů, tento příklad vytvoří výchozí obor názvů `LibUtil`.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 <span data-ttu-id="2e9b9-129">Pro více popisný název (pomocí *podporovány*. *NázevKnihovny* pojmenování obecných zásad), tento příklad přepíše výchozí název souboru sestavení a název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 <span data-ttu-id="2e9b9-130">Následující příklad importuje `MyLib.tlb`, který se odkazuje na `CompanyA.LibUtil.dll`, a podepíše sestavení `CompanyB.MyLib.dll` se silným názvem pomocí souboru s klíči `CompanyB.snk`.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="2e9b9-131">Obor názvů, `CompanyB.MyLib`, přepíše výchozí název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2e9b9-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e9b9-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e9b9-132">See also</span></span>
- [<span data-ttu-id="2e9b9-133">Postupy: Registrace primárních sestavení spolupráce</span><span class="sxs-lookup"><span data-stu-id="2e9b9-133">How to: Register Primary Interop Assemblies</span></span>](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
