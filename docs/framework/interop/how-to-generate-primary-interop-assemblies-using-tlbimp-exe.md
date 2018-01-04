---
title: "Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d459ac318f2c4a3911830d08e26b31ae5366e896
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="18a8b-102">Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="18a8b-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>
<span data-ttu-id="18a8b-103">Existují dva způsoby, jak vygenerovat primární spolupracující sestavení:</span><span class="sxs-lookup"><span data-stu-id="18a8b-103">There are two ways to generate a primary interop assembly:</span></span>  
  
-   <span data-ttu-id="18a8b-104">Pomocí [zadejte Importér knihovny (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) poskytované [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="18a8b-104">Using the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
     <span data-ttu-id="18a8b-105">Nejjednodušší způsob, jak můžete vytvořit primární spolupracující sestavení se má používat [Tlbimp.exe (Importér knihovny)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="18a8b-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="18a8b-106">Tlbimp.exe poskytuje následující bezpečnostní opatření:</span><span class="sxs-lookup"><span data-stu-id="18a8b-106">Tlbimp.exe provides the following safeguards:</span></span>  
  
    -   <span data-ttu-id="18a8b-107">Zkontroluje ostatní registrované primární spolupracující sestavení před vytvořením nového sestavení vzájemné spolupráce pro všechny vnořené typy knihovny odkazy.</span><span class="sxs-lookup"><span data-stu-id="18a8b-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>  
  
    -   <span data-ttu-id="18a8b-108">Pokud nezadáte buď kontejner, nebo název souboru umožnit primární spolupracující sestavení silným názvem generování primárních sestavení vzájemné spolupráce se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="18a8b-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>  
  
    -   <span data-ttu-id="18a8b-109">Emitování primárních sestavení vzájemné spolupráce, pokud vynecháte odkazy na závislé sestavení se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="18a8b-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>  
  
    -   <span data-ttu-id="18a8b-110">Emitování primárních sestavení vzájemné spolupráce, pokud přidáte odkazy na závislé sestavení, které nejsou primární spolupracující sestavení se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="18a8b-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>  
  
-   <span data-ttu-id="18a8b-111">Primární spolupracující sestavení ruční vytváření ve zdrojovém kódu pomocí jazyka, který je kompatibilní s specifikace CLS (Common Language), například C#.</span><span class="sxs-lookup"><span data-stu-id="18a8b-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="18a8b-112">Tento přístup je užitečné, když není k dispozici knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="18a8b-112">This approach is useful when a type library is unavailable.</span></span>  
  
 <span data-ttu-id="18a8b-113">Musíte mít páru kryptografických klíčů k podepsání sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="18a8b-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="18a8b-114">Podrobnosti najdete v tématu [vytvoření páru klíč A](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="18a8b-114">For details, see [Creating A Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="18a8b-115">Ke generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="18a8b-115">To generate a primary interop assembly using Tlbimp.exe</span></span>  
  
1.  <span data-ttu-id="18a8b-116">V příkazovém řádku zadejte příkaz:</span><span class="sxs-lookup"><span data-stu-id="18a8b-116">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="18a8b-117">**Tlbimp** *tlbfile***/primární/keyfile:** *filename* **/out:** *assemblyname* </span><span class="sxs-lookup"><span data-stu-id="18a8b-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>  
  
     <span data-ttu-id="18a8b-118">V tomto příkazu *tlbfile* je soubor obsahuje knihovnu typů COM *filename* je název kontejneru nebo soubor, který obsahuje pár klíčů a *assemblyname* je název sestavení se silným názvem přihlásit.</span><span class="sxs-lookup"><span data-stu-id="18a8b-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>  
  
 <span data-ttu-id="18a8b-119">Primární spolupracující sestavení může odkazovat jenom jiné primární spolupracující sestavení.</span><span class="sxs-lookup"><span data-stu-id="18a8b-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="18a8b-120">Pokud vaše sestavení odkazuje typy z knihovny typů COM třetích stran, musíte získat primární spolupracující sestavení od vydavatele, než může generovat vaší primární spolupracující sestavení.</span><span class="sxs-lookup"><span data-stu-id="18a8b-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="18a8b-121">Pokud jste vydavatele, musíte vygenerovat primární spolupracující sestavení pro knihovnu závislého typu před vygenerováním odkazující sestavení primární spolupráce.</span><span class="sxs-lookup"><span data-stu-id="18a8b-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>  
  
 <span data-ttu-id="18a8b-122">Závislé sestavení primární spolupráce s číslem verze, která se liší od původního knihovny typů není zjistitelný při instalaci v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="18a8b-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="18a8b-123">Musíte zaregistrovat závislé sestavení primární spolupráce v registru systému Windows nebo pomocí **/reference** možnost Ujistěte se, že vyhledá Tlbimp.exe závislé knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="18a8b-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>  
  
 <span data-ttu-id="18a8b-124">Můžete také zabalit několik verzí knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="18a8b-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="18a8b-125">Pokyny najdete v tématu [postupy: zabalení více verzí z knihovny typů](http://msdn.microsoft.com/en-us/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f).</span><span class="sxs-lookup"><span data-stu-id="18a8b-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](http://msdn.microsoft.com/en-us/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18a8b-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="18a8b-126">Example</span></span>  
 <span data-ttu-id="18a8b-127">Následující příklad importuje knihovny typů COM `LibUtil.tlb` a podepisuje sestavení `LibUtil.dll` se silným názvem pomocí souboru klíče `CompanyA.snk`.</span><span class="sxs-lookup"><span data-stu-id="18a8b-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="18a8b-128">Díky vynechání název konkrétní oboru názvů, tento příklad vytvoří výchozí obor názvů `LibUtil`.</span><span class="sxs-lookup"><span data-stu-id="18a8b-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 <span data-ttu-id="18a8b-129">Pro více popisný název (pomocí *poznámky:*. *NázevKnihovny* pojmenování platí), tento příklad přepíše výchozí název souboru sestavení a název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="18a8b-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 <span data-ttu-id="18a8b-130">Následující příklad importuje `MyLib.tlb`, jehož odkazy `CompanyA.LibUtil.dll`, a podepisuje sestavení `CompanyB.MyLib.dll` se silným názvem pomocí souboru klíče `CompanyB.snk`.</span><span class="sxs-lookup"><span data-stu-id="18a8b-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="18a8b-131">Obor názvů, `CompanyB.MyLib`, přepíše výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="18a8b-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="18a8b-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="18a8b-132">See Also</span></span>  
 [<span data-ttu-id="18a8b-133">Postupy: Registrace primárních sestavení spolupráce</span><span class="sxs-lookup"><span data-stu-id="18a8b-133">How to: Register Primary Interop Assemblies</span></span>](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
