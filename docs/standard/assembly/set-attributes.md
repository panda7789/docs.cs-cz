---
title: Nastavování atributů sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 0e4e2e595ed4f95511bd23ab0ed00139f71b2c8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740469"
---
# <a name="set-assembly-attributes"></a><span data-ttu-id="f0653-102">Nastavování atributů sestavení</span><span class="sxs-lookup"><span data-stu-id="f0653-102">Set assembly attributes</span></span>

<span data-ttu-id="f0653-103">Atributy sestavení jsou hodnoty, které poskytují informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-103">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="f0653-104">Atributy jsou rozděleny do následujících sad informací:</span><span class="sxs-lookup"><span data-stu-id="f0653-104">The attributes are divided into the following sets of information:</span></span>

- <span data-ttu-id="f0653-105">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="f0653-105">Assembly identity attributes</span></span>

- <span data-ttu-id="f0653-106">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="f0653-106">Informational attributes</span></span>

- <span data-ttu-id="f0653-107">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="f0653-107">Assembly manifest attributes</span></span>

- <span data-ttu-id="f0653-108">Atributy silného názvu</span><span class="sxs-lookup"><span data-stu-id="f0653-108">Strong name attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="f0653-109">Atributy identity sestavení</span><span class="sxs-lookup"><span data-stu-id="f0653-109">Assembly identity attributes</span></span>

<span data-ttu-id="f0653-110">Tři atributy spolu se silným názvem (pokud je k dispozici) určují identitu sestavení: název, verze a jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="f0653-110">Three attributes, together with a strong name (if applicable), determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="f0653-111">Tyto atributy tvoří úplný název sestavení a jsou vyžadovány při odkazování na sestavení v kódu.</span><span class="sxs-lookup"><span data-stu-id="f0653-111">These attributes form the full name of the assembly and are required when referencing the assembly in code.</span></span> <span data-ttu-id="f0653-112">Atributy můžete použít k nastavení verze sestavení a jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="f0653-112">You can use attributes to set an assembly's version and culture.</span></span> <span data-ttu-id="f0653-113">Kompilátor nebo [propojovač sestavení (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) nastaví hodnotu názvu při vytvoření sestavení na základě souboru obsahujícího manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-113">The compiler or the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) sets the name value when the assembly is created, based on the file containing the assembly manifest.</span></span>

<span data-ttu-id="f0653-114">Následující tabulka popisuje atributy verze a jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="f0653-114">The following table describes the version and culture attributes.</span></span>

|<span data-ttu-id="f0653-115">Atribut identity sestavení</span><span class="sxs-lookup"><span data-stu-id="f0653-115">Assembly identity attribute</span></span>|<span data-ttu-id="f0653-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f0653-116">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="f0653-117">Výčet pole označující jazykovou verzi, která podporuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-117">Enumerated field indicating the culture that the assembly supports.</span></span> <span data-ttu-id="f0653-118">Sestavení můžete také určit nezávislost jazykové verze, označující, že obsahuje prostředky pro výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="f0653-118">An assembly can also specify culture independence, indicating that it contains the resources for the default culture.</span></span> <span data-ttu-id="f0653-119">**Poznámka:**  Za běhu zachází všechny sestavení, které nemá atribut jazykové verze nastavena na hodnotu null jako satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-119">**Note:**  The runtime treats any assembly that does not have the culture attribute set to null as a satellite assembly.</span></span> <span data-ttu-id="f0653-120">Tato sestavení podléhají pravidlům pro závaznost satelitního sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-120">Such assemblies are subject to satellite assembly binding rules.</span></span> <span data-ttu-id="f0653-121">Další informace naleznete [v tématu How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="f0653-121">For more information, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="f0653-122">Hodnota, která nastaví atributy sestavení, například zda lze sestavení spustit vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="f0653-122">Value that sets assembly attributes, such as whether the assembly can be run side by side.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="f0653-123">Číselná hodnota ve formátu *major*. *nezletilá*. *stavět*. *(například* 2.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="f0653-123">Numeric value in the format *major*.*minor*.*build*.*revision* (for example, 2.4.0.0).</span></span> <span data-ttu-id="f0653-124">Běžný jazyk runtime používá tuto hodnotu k provádění operací vazby v sestaveních se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="f0653-124">The common language runtime uses this value to perform binding operations in strong-named assemblies.</span></span> <span data-ttu-id="f0653-125">**Poznámka:**  Pokud <xref:System.Reflection.AssemblyInformationalVersionAttribute> atribut není použit pro sestavení, číslo verze <xref:System.Reflection.AssemblyVersionAttribute> určené atributem <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>je <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> použito vlastnostmi , a.</span><span class="sxs-lookup"><span data-stu-id="f0653-125">**Note:**  If the <xref:System.Reflection.AssemblyInformationalVersionAttribute> attribute is not applied to an assembly, the version number specified by the <xref:System.Reflection.AssemblyVersionAttribute> attribute is used by the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|

<span data-ttu-id="f0653-126">Následující příklad kódu ukazuje, jak použít atributy verze a jazykové verze na sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-126">The following code example shows how to apply the version and culture attributes to an assembly.</span></span>

```cpp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")];
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")];
```

```csharp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")]
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")]
```

```vb
' Set version number for the assembly.
<Assembly:AssemblyVersionAttribute("4.3.2.1")>
' Set culture as German.
<Assembly:AssemblyCultureAttribute("de")>
```

## <a name="informational-attributes"></a><span data-ttu-id="f0653-127">Informační atributy</span><span class="sxs-lookup"><span data-stu-id="f0653-127">Informational attributes</span></span>

<span data-ttu-id="f0653-128">Informační atributy můžete použít k poskytnutí dalších informací o společnosti nebo produktu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-128">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="f0653-129">Následující tabulka popisuje informační atributy, které lze použít pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-129">The following table describes the informational attributes you can apply to an assembly.</span></span>

|<span data-ttu-id="f0653-130">Informační atribut</span><span class="sxs-lookup"><span data-stu-id="f0653-130">Informational attribute</span></span>|<span data-ttu-id="f0653-131">Popis</span><span class="sxs-lookup"><span data-stu-id="f0653-131">Description</span></span>|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="f0653-132">Hodnota řetězce určující název společnosti.</span><span class="sxs-lookup"><span data-stu-id="f0653-132">String value specifying a company name.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="f0653-133">Řetězcová hodnota určující informace o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="f0653-133">String value specifying copyright information.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="f0653-134">Hodnota řetězce určující číslo verze souboru Win32.</span><span class="sxs-lookup"><span data-stu-id="f0653-134">String value specifying the Win32 file version number.</span></span> <span data-ttu-id="f0653-135">To obvykle výchozí verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-135">This normally defaults to the assembly version.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="f0653-136">Hodnota řetězce určující informace o verzi, které není používány běžným jazykem runtime, jako je například úplné číslo verze produktu.</span><span class="sxs-lookup"><span data-stu-id="f0653-136">String value specifying version information that is not used by the common language runtime, such as a full product version number.</span></span> <span data-ttu-id="f0653-137">**Poznámka:**  Pokud je tento atribut použit na sestavení, řetězec, který určuje, <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> lze získat za běhu pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f0653-137">**Note:**  If this attribute is applied to an assembly, the string it specifies can be obtained at run time by using the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f0653-138">Řetězec se také používá v cestě a klíč <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> registru poskytované vlastnosti a.</span><span class="sxs-lookup"><span data-stu-id="f0653-138">The string is also used in the path and registry key provided by the <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="f0653-139">Řetězcová hodnota určující informace o produktu.</span><span class="sxs-lookup"><span data-stu-id="f0653-139">String value specifying product information.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="f0653-140">Hodnota řetězce určující informace o ochranné známce.</span><span class="sxs-lookup"><span data-stu-id="f0653-140">String value specifying trademark information.</span></span>|

<span data-ttu-id="f0653-141">Tyto atributy se mohou objevit na stránce Vlastnosti systému Windows sestavení nebo je lze přepsat pomocí možnosti kompilátoru **/win32res** a zadat vlastní soubor prostředků Win32.</span><span class="sxs-lookup"><span data-stu-id="f0653-141">These attributes can appear on the Windows Properties page of the assembly, or they can be overridden using the **/win32res** compiler option to specify your own Win32 resource file.</span></span>

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="f0653-142">Atributy manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="f0653-142">Assembly manifest attributes</span></span>

<span data-ttu-id="f0653-143">Atributy manifestu sestavení můžete použít k poskytnutí informací v manifestu sestavení, včetně názvu, popisu, výchozího aliasu a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f0653-143">You can use assembly manifest attributes to provide information in the assembly manifest, including title, description, the default alias, and configuration.</span></span> <span data-ttu-id="f0653-144">Následující tabulka popisuje atributy manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-144">The following table describes the assembly manifest attributes.</span></span>

|<span data-ttu-id="f0653-145">Atribut manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="f0653-145">Assembly manifest attribute</span></span>|<span data-ttu-id="f0653-146">Popis</span><span class="sxs-lookup"><span data-stu-id="f0653-146">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="f0653-147">Hodnota řetězce označující konfiguraci sestavení, například Maloobchod nebo Ladění.</span><span class="sxs-lookup"><span data-stu-id="f0653-147">String value indicating the configuration of the assembly, such as Retail or Debug.</span></span> <span data-ttu-id="f0653-148">Za běhu nepoužívá tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f0653-148">The runtime does not use this value.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="f0653-149">Hodnota řetězce určující výchozí alias, který se má použít odkazováním na sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-149">String value specifying a default alias to be used by referencing assemblies.</span></span> <span data-ttu-id="f0653-150">Tato hodnota poskytuje popisný název, pokud název samotného sestavení není popisný (například hodnota GUID).</span><span class="sxs-lookup"><span data-stu-id="f0653-150">This value provides a friendly name when the name of the assembly itself is not friendly (such as a GUID value).</span></span> <span data-ttu-id="f0653-151">Tuto hodnotu lze také použít jako krátký formulář úplného názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-151">This value can also be used as a short form of the full assembly name.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="f0653-152">Řetězcová hodnota určující krátký popis, který shrnuje povahu a účel sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-152">String value specifying a short description that summarizes the nature and purpose of the assembly.</span></span>|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="f0653-153">Hodnota řetězce určující popisný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-153">String value specifying a friendly name for the assembly.</span></span> <span data-ttu-id="f0653-154">Například sestavení s názvem *comdlg* může mít název Microsoft Common Dialog Control.</span><span class="sxs-lookup"><span data-stu-id="f0653-154">For example, an assembly named *comdlg* might have the title Microsoft Common Dialog Control.</span></span>|

## <a name="strong-name-attributes"></a><span data-ttu-id="f0653-155">Atributy silného názvu</span><span class="sxs-lookup"><span data-stu-id="f0653-155">Strong name attributes</span></span>

<span data-ttu-id="f0653-156">Atributy silného názvu můžete použít k nastavení silného názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0653-156">You can use strong name attributes to set a strong name for an assembly.</span></span> <span data-ttu-id="f0653-157">Následující tabulka popisuje atributy silného názvu.</span><span class="sxs-lookup"><span data-stu-id="f0653-157">The following table describes the strong name attributes.</span></span>

|<span data-ttu-id="f0653-158">Atribut silného názvu</span><span class="sxs-lookup"><span data-stu-id="f0653-158">Strong name attribute</span></span>|<span data-ttu-id="f0653-159">Popis</span><span class="sxs-lookup"><span data-stu-id="f0653-159">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|<span data-ttu-id="f0653-160">Logická hodnota označující, že se používá podepisování zpoždění.</span><span class="sxs-lookup"><span data-stu-id="f0653-160">Boolean value indicating that delay signing is being used.</span></span>|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|<span data-ttu-id="f0653-161">Hodnota řetězce označující název souboru, který obsahuje buď veřejný klíč (pokud používáte podepisování zpoždění) nebo veřejný i soukromý klíč předaný jako parametr konstruktoru tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="f0653-161">String value indicating the name of the file that contains either the public key (if using delay signing) or both the public and private keys passed as a parameter to the constructor of this attribute.</span></span> <span data-ttu-id="f0653-162">Všimněte si, že název souboru je relativní k cestě výstupního souboru *(exe* nebo *dll*), nikoli ke zdrojové cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="f0653-162">Note that the file name is relative to the output file path (the *.exe* or *.dll*), not the source file path.</span></span>|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|<span data-ttu-id="f0653-163">Označuje kontejner klíčů, který obsahuje dvojici klíčů předanou jako parametr konstruktoru tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="f0653-163">Indicates the key container that contains the key pair passed as a parameter to the constructor of this attribute.</span></span>|

<span data-ttu-id="f0653-164">Následující příklad kódu ukazuje atributy, které mají být aplikovány při použití podepisování zpoždění k vytvoření sestavení se silným názvem se souborem veřejného klíče nazvaným *myKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="f0653-164">The following code example shows the attributes to apply when using delay signing to create a strong-named assembly with a public key file called *myKey.snk*.</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("myKey.snk")];
[assembly:AssemblyDelaySignAttribute(true)];
```

```csharp
[assembly:AssemblyKeyFileAttribute("myKey.snk")]
[assembly:AssemblyDelaySignAttribute(true)]
```

```vb
<Assembly:AssemblyKeyFileAttribute("myKey.snk")>
<Assembly:AssemblyDelaySignAttribute(True)>
```

## <a name="see-also"></a><span data-ttu-id="f0653-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0653-165">See also</span></span>

- [<span data-ttu-id="f0653-166">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="f0653-166">Create assemblies</span></span>](create.md)
