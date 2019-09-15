---
title: Nastavit atributy sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d0809ec3da5a12abe950e63f9665037323a0ab39
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991670"
---
# <a name="set-assembly-attributes"></a>Nastavit atributy sestavení

Atributy sestavení jsou hodnoty, které poskytují informace o sestavení. Atributy jsou rozděleny do následujících sad informací:

- Atributy identity sestavení

- Informativní atributy

- Atributy manifestu sestavení

- Atributy silného názvu

## <a name="assembly-identity-attributes"></a>Atributy identity sestavení

Tři atributy spolu se silným názvem (Pokud je k dispozici) určují identitu sestavení: název, verzi a jazykovou verzi. Tyto atributy tvoří úplný název sestavení a jsou požadovány při odkazování sestavení v kódu. Atributy lze použít k nastavení verze a jazykové verze sestavení. Kompilátor nebo [linker sestavení (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) nastaví hodnotu názvu při vytvoření sestavení na základě souboru obsahujícího manifest sestavení.

Následující tabulka popisuje atributy Version a culture.

|Atribut identity sestavení|Popis|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|Výčtové pole označující jazykovou verzi, kterou sestavení podporuje. Sestavení může také určovat nezávislost jazykové verze, což značí, že obsahuje prostředky pro výchozí jazykovou verzi. **Poznámka:**  Modul runtime zpracovává všechna sestavení, která nemají atribut Culture nastaven na hodnotu null jako satelitní sestavení. Taková sestavení se vztahují na pravidla vazeb satelitního sestavení. Další informace najdete v tématu [jak modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Hodnota, která nastavuje atributy sestavení, například zda lze sestavení spustit vedle sebe.|
|<xref:System.Reflection.AssemblyVersionAttribute>|Číselná hodnota ve formátu *Hlavní*. *vedlejší*. *sestavení*. *Revize* (například 2.4.0.0). Modul CLR (Common Language Runtime) používá tuto hodnotu k provádění operací vazby v sestaveních se silným názvem. **Poznámka:**  <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> <xref:System.Reflection.AssemblyVersionAttribute> Pokud atribut není aplikován na sestavení, číslo verze určené atributem je používáno vlastnostmi, a. <xref:System.Reflection.AssemblyInformationalVersionAttribute>|

Následující příklad kódu ukazuje, jak použít atributy Version a Culture na sestavení.

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

## <a name="informational-attributes"></a>Informativní atributy

Pomocí informativních atributů lze poskytnout další informace o společnosti nebo produktu pro sestavení. Následující tabulka popisuje informační atributy, které lze použít pro sestavení.

|Informační atribut|Popis|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Řetězcová hodnota, která určuje název společnosti.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Hodnota řetězce, která určuje informace o autorských právech.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Řetězcová hodnota, která určuje číslo verze souboru Win32. To je obvykle výchozí verze sestavení.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Řetězcová hodnota, která určuje informace o verzi používané modulem CLR (Common Language Runtime), jako je například úplné číslo verze produktu. **Poznámka:**  Pokud je tento atribut použit pro sestavení, řetězec, který určuje, lze získat za běhu pomocí <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> vlastnosti. Řetězec se používá také v cestě a klíči registru, které <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> poskytuje vlastnosti a. <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType>|
|<xref:System.Reflection.AssemblyProductAttribute>|Řetězcová hodnota, která určuje informace o produktu.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Řetězcová hodnota určující informace o ochranných známkách.|

Tyto atributy se mohou zobrazit na stránce vlastností systému Windows v sestavení nebo mohou být přepsány pomocí možnosti kompilátoru **parametr/win32res** k určení vlastního souboru prostředků Win32.

## <a name="assembly-manifest-attributes"></a>Atributy manifestu sestavení

Atributy manifestu sestavení lze použít k poskytnutí informací v manifestu sestavení, včetně názvu, popisu, výchozího aliasu a konfigurace. Následující tabulka popisuje atributy manifestu sestavení.

|Atribut manifestu sestavení|Popis|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Řetězcová hodnota označující konfiguraci sestavení, jako je například maloobchod nebo ladění. Modul runtime tuto hodnotu nepoužívá.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Řetězcová hodnota určující výchozí alias, který má být použit odkazem na sestavení. Tato hodnota poskytuje popisný název, pokud samotný název sestavení není popisný (například hodnota GUID). Tuto hodnotu lze také použít jako krátký tvar úplného názvu sestavení.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Řetězcová hodnota určující krátký popis, který shrnuje povahu a účel sestavení.|
|<xref:System.Reflection.AssemblyTitleAttribute>|Řetězcová hodnota, která určuje popisný název pro sestavení. Například sestavení s názvem *comdlg* může mít název Microsoft Common Dialog Control.|

## <a name="strong-name-attributes"></a>Atributy silného názvu

Atributy silného názvu lze použít k nastavení silného názvu pro sestavení. Následující tabulka popisuje atributy silného názvu.

|Atribut silného názvu|Popis|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Logická hodnota označující, že se používá zpožděné podepisování.|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Řetězcová hodnota označující název souboru, který obsahuje buď veřejný klíč (Pokud používáte zpožděné podepisování), nebo veřejný i privátní klíč předaný jako parametr konstruktoru tohoto atributu. Všimněte si, že název souboru je relativní vzhledem k cestě výstupního souboru ( *. exe* nebo *. dll*), nikoli ke zdrojové cestě k souboru.|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Určuje kontejner klíčů, který obsahuje pár klíčů předaný jako parametr konstruktoru tohoto atributu.|

Následující příklad kódu ukazuje atributy, které mají být použity při použití opožděného podepisování k vytvoření sestavení se silným názvem se souborem veřejného klíče s názvem *myKey. snk*.

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

## <a name="see-also"></a>Viz také:

- [Vytváření sestavení](create.md)
- [Program se sestaveními](program.md)
