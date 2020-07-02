---
title: 'Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe'
description: Naučte se generovat primární spolupracující sestavení pomocí nástroje pro import knihovny typů (Tlbimp.exe), který je k dispozici v Windows SDK.
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
ms.openlocfilehash: 779b4863b6f1513f3566d4ab31660d88cda1039b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619127"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="8d1c4-103">Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="8d1c4-103">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>

<span data-ttu-id="8d1c4-104">Existují dva způsoby, jak vytvořit primární definiční sestavení:</span><span class="sxs-lookup"><span data-stu-id="8d1c4-104">There are two ways to generate a primary interop assembly:</span></span>

- <span data-ttu-id="8d1c4-105">Použití nástroje pro [Import knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) poskytované Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-105">Using the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) provided by the Windows SDK.</span></span>

  <span data-ttu-id="8d1c4-106">Nejjednodušší způsob, jak vypracovávat primární spolupracující sestavení, je použití [Tlbimp.exe (importér knihovny typů)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="8d1c4-106">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="8d1c4-107">Tlbimp.exe poskytuje následující záruky:</span><span class="sxs-lookup"><span data-stu-id="8d1c4-107">Tlbimp.exe provides the following safeguards:</span></span>

  - <span data-ttu-id="8d1c4-108">Kontroluje další registrovaná sestavení primární spolupráce před vytvořením nových definičních sestavení pro všechny vnořené odkazy knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-108">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>

  - <span data-ttu-id="8d1c4-109">Nepovedlo se vygenerovat primární definiční sestavení, pokud nezadáte buď kontejner, nebo název souboru, aby bylo primární sestavení vzájemné spolupráce silného názvu.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-109">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>

  - <span data-ttu-id="8d1c4-110">Při vynechání odkazů na závislá sestavení se nepovedlo vygenerovat primární definiční sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-110">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>

  - <span data-ttu-id="8d1c4-111">Pokud přidáte odkazy na závislá sestavení, která nejsou sestaveními primární spolupráce, nemusíte vygenerovat primární definiční sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-111">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>

- <span data-ttu-id="8d1c4-112">Ruční vytváření sestavení primární spolupráce ve zdrojovém kódu pomocí jazyka, který je kompatibilní se specifikací CLS (Common Language Specification), jako je C#.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-112">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="8d1c4-113">Tento přístup je užitečný v případě, že knihovna typů není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-113">This approach is useful when a type library is unavailable.</span></span>

<span data-ttu-id="8d1c4-114">Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-114">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="8d1c4-115">Podrobnosti najdete v tématu [Vytvoření páru klíčů](../../standard/assembly/create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="8d1c4-115">For details, see [Creating A Key Pair](../../standard/assembly/create-public-private-key-pair.md).</span></span>

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="8d1c4-116">Generování primárního definičního sestavení pomocí Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="8d1c4-116">To generate a primary interop assembly using Tlbimp.exe</span></span>

1. <span data-ttu-id="8d1c4-117">Na příkazovém řádku zadejte:</span><span class="sxs-lookup"><span data-stu-id="8d1c4-117">At the command prompt, type:</span></span>

    <span data-ttu-id="8d1c4-118">**Tlbimp** *tlbfile*  **/Primary/keyfile:** *filename* **/out:** *AssemblyName*</span><span class="sxs-lookup"><span data-stu-id="8d1c4-118">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>

    <span data-ttu-id="8d1c4-119">V tomto příkazu je *tlbfile* soubor obsahující knihovnu typů modelu COM, název *souboru* je název kontejneru nebo souboru, který obsahuje dvojici klíčů, a *AssemblyName* je název sestavení pro podepsání silným názvem.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-119">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>

<span data-ttu-id="8d1c4-120">Primární spolupracující sestavení můžou odkazovat jenom na jiná primární spolupracující sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-120">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="8d1c4-121">Pokud vaše sestavení odkazuje na typy z knihovny typů modelu COM třetí strany, je nutné získat primární definiční sestavení od vydavatele před tím, než bude možné vygenerovat vaše primární definiční sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-121">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="8d1c4-122">Pokud jste Vydavatel, je nutné před generováním odkazujícího primárního sestavení vzájemné spolupráce vygenerovat primární definiční sestavení pro závislou knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-122">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>

<span data-ttu-id="8d1c4-123">Závislé primární sestavení vzájemné spolupráce s číslem verze, které se liší od původní knihovny typů, není zjistitelné, když je nainstalován v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-123">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="8d1c4-124">Je nutné buď zaregistrovat závislé primární definiční sestavení v registru systému Windows, nebo můžete použít možnost **/reference** a ověřit, zda Tlbimp.exe najde závislou knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-124">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>

<span data-ttu-id="8d1c4-125">Můžete také zabalit více verzí knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-125">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="8d1c4-126">Pokyny najdete v tématu [Postup: zabalení více verzí knihoven typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8d1c4-126">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="8d1c4-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d1c4-127">Example</span></span>

<span data-ttu-id="8d1c4-128">Následující příklad importuje knihovnu typů modelu COM `LibUtil.tlb` a podepíše sestavení `LibUtil.dll` se silným názvem pomocí souboru klíče `CompanyA.snk` .</span><span class="sxs-lookup"><span data-stu-id="8d1c4-128">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="8d1c4-129">Vynecháte-li konkrétní název oboru názvů, tento příklad vytvoří výchozí obor názvů `LibUtil` .</span><span class="sxs-lookup"><span data-stu-id="8d1c4-129">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

<span data-ttu-id="8d1c4-130">Pro výstižnější název (pomocí *dodavatele*.\* Název knihovny\* – zásady pojmenování: v následujícím příkladu je popsán výchozí název souboru sestavení a název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-130">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

<span data-ttu-id="8d1c4-131">Následující příklad importuje `MyLib.tlb` , který odkazuje `CompanyA.LibUtil.dll` a podepíše sestavení `CompanyB.MyLib.dll` silným názvem pomocí souboru klíče `CompanyB.snk` .</span><span class="sxs-lookup"><span data-stu-id="8d1c4-131">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="8d1c4-132">Obor názvů `CompanyB.MyLib` přepíše výchozí název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8d1c4-132">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>

```console
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a><span data-ttu-id="8d1c4-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d1c4-133">See also</span></span>

- [<span data-ttu-id="8d1c4-134">Postupy: Registrace primárních sestavení spolupráce</span><span class="sxs-lookup"><span data-stu-id="8d1c4-134">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)
