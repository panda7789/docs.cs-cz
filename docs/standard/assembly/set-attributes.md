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
# <a name="set-assembly-attributes"></a>Nastavování atributů sestavení

Atributy sestavení jsou hodnoty, které poskytují informace o sestavení. Atributy jsou rozděleny do následujících sad informací:

- Atributy identity sestavení

- Informační atributy

- Atributy manifestu sestavení

- Atributy silného názvu

## <a name="assembly-identity-attributes"></a>Atributy identity sestavení

Tři atributy spolu se silným názvem (pokud je k dispozici) určují identitu sestavení: název, verze a jazyková verze. Tyto atributy tvoří úplný název sestavení a jsou vyžadovány při odkazování na sestavení v kódu. Atributy můžete použít k nastavení verze sestavení a jazykové verze. Kompilátor nebo [propojovač sestavení (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) nastaví hodnotu názvu při vytvoření sestavení na základě souboru obsahujícího manifest sestavení.

Následující tabulka popisuje atributy verze a jazykové verze.

|Atribut identity sestavení|Popis|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|Výčet pole označující jazykovou verzi, která podporuje sestavení. Sestavení můžete také určit nezávislost jazykové verze, označující, že obsahuje prostředky pro výchozí jazykovou verzi. **Poznámka:**  Za běhu zachází všechny sestavení, které nemá atribut jazykové verze nastavena na hodnotu null jako satelitní sestavení. Tato sestavení podléhají pravidlům pro závaznost satelitního sestavení. Další informace naleznete [v tématu How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Hodnota, která nastaví atributy sestavení, například zda lze sestavení spustit vedle sebe.|
|<xref:System.Reflection.AssemblyVersionAttribute>|Číselná hodnota ve formátu *major*. *nezletilá*. *stavět*. *(například* 2.4.0.0). Běžný jazyk runtime používá tuto hodnotu k provádění operací vazby v sestaveních se silným názvem. **Poznámka:**  Pokud <xref:System.Reflection.AssemblyInformationalVersionAttribute> atribut není použit pro sestavení, číslo verze <xref:System.Reflection.AssemblyVersionAttribute> určené atributem <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>je <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> použito vlastnostmi , a.|

Následující příklad kódu ukazuje, jak použít atributy verze a jazykové verze na sestavení.

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

## <a name="informational-attributes"></a>Informační atributy

Informační atributy můžete použít k poskytnutí dalších informací o společnosti nebo produktu pro sestavení. Následující tabulka popisuje informační atributy, které lze použít pro sestavení.

|Informační atribut|Popis|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Hodnota řetězce určující název společnosti.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Řetězcová hodnota určující informace o autorských právech.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Hodnota řetězce určující číslo verze souboru Win32. To obvykle výchozí verze sestavení.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Hodnota řetězce určující informace o verzi, které není používány běžným jazykem runtime, jako je například úplné číslo verze produktu. **Poznámka:**  Pokud je tento atribut použit na sestavení, řetězec, který určuje, <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> lze získat za běhu pomocí vlastnosti. Řetězec se také používá v cestě a klíč <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> registru poskytované vlastnosti a.|
|<xref:System.Reflection.AssemblyProductAttribute>|Řetězcová hodnota určující informace o produktu.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Hodnota řetězce určující informace o ochranné známce.|

Tyto atributy se mohou objevit na stránce Vlastnosti systému Windows sestavení nebo je lze přepsat pomocí možnosti kompilátoru **/win32res** a zadat vlastní soubor prostředků Win32.

## <a name="assembly-manifest-attributes"></a>Atributy manifestu sestavení

Atributy manifestu sestavení můžete použít k poskytnutí informací v manifestu sestavení, včetně názvu, popisu, výchozího aliasu a konfigurace. Následující tabulka popisuje atributy manifestu sestavení.

|Atribut manifestu sestavení|Popis|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Hodnota řetězce označující konfiguraci sestavení, například Maloobchod nebo Ladění. Za běhu nepoužívá tuto hodnotu.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Hodnota řetězce určující výchozí alias, který se má použít odkazováním na sestavení. Tato hodnota poskytuje popisný název, pokud název samotného sestavení není popisný (například hodnota GUID). Tuto hodnotu lze také použít jako krátký formulář úplného názvu sestavení.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Řetězcová hodnota určující krátký popis, který shrnuje povahu a účel sestavení.|
|<xref:System.Reflection.AssemblyTitleAttribute>|Hodnota řetězce určující popisný název sestavení. Například sestavení s názvem *comdlg* může mít název Microsoft Common Dialog Control.|

## <a name="strong-name-attributes"></a>Atributy silného názvu

Atributy silného názvu můžete použít k nastavení silného názvu sestavení. Následující tabulka popisuje atributy silného názvu.

|Atribut silného názvu|Popis|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Logická hodnota označující, že se používá podepisování zpoždění.|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Hodnota řetězce označující název souboru, který obsahuje buď veřejný klíč (pokud používáte podepisování zpoždění) nebo veřejný i soukromý klíč předaný jako parametr konstruktoru tohoto atributu. Všimněte si, že název souboru je relativní k cestě výstupního souboru *(exe* nebo *dll*), nikoli ke zdrojové cestě k souboru.|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Označuje kontejner klíčů, který obsahuje dvojici klíčů předanou jako parametr konstruktoru tohoto atributu.|

Následující příklad kódu ukazuje atributy, které mají být aplikovány při použití podepisování zpoždění k vytvoření sestavení se silným názvem se souborem veřejného klíče nazvaným *myKey.snk*.

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

## <a name="see-also"></a>Viz také

- [Vytváření sestavení](create.md)
