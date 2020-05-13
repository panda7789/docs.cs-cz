---
title: Jak nástroj MSBuild generuje názvy souborů manifestu
description: Popisuje faktory, které ovlivňují název názvu souboru manifestu prostředku, který je generován nástrojem MSBuild v době kompilace.
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 383bf6a077b0631e70ddaa4721b20e992127a73c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83232324"
---
# <a name="how-resource-manifest-files-are-named"></a>Jak se nazývají soubory manifestu prostředků

Když nástroj MSBuild zkompiluje projekt .NET Core, soubory prostředků XML, které mají příponu souboru *. resx* , jsou převedeny do binárních souborů *. Resources* . Binární soubory jsou vloženy do výstupu kompilátoru a lze je číst pomocí <xref:System.Resources.ResourceManager> . Tento článek popisuje, jak nástroj MSBuild zvolí název pro každý soubor *. Resources* .

> [!TIP]
> Pokud explicitně přidáte položku prostředku do souboru projektu a je také [zahrnutá ve výchozím nastavení include globy pro .NET Core](../project-sdk/overview.md#default-compilation-includes), zobrazí se chyba buildu. Chcete-li soubory prostředků zahrnout jako `EmbeddedResource` položky ručně, nastavte `EnableDefaultEmbeddedResourceItems` vlastnost na hodnotu false.

## <a name="default-name"></a>Výchozí název

V rozhraní .NET Core 3,0 a novějším je výchozí název pro manifest prostředku použit, pokud jsou splněny obě následující podmínky:

- Soubor prostředků není explicitně obsažen v souboru projektu jako `EmbeddedResource` položka s `LogicalName` `ManifestResourceName` `DependentUpon` metadaty, nebo.
- `EmbeddedResourceUseDependentUponConvention`Vlastnost není nastavena na hodnotu `false` v souboru projektu. Ve výchozím nastavení je tato vlastnost nastavena na hodnotu `true` . Další informace najdete v tématu [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).

Pokud se soubor prostředků nachází společně se zdrojovým souborem (*. cs* nebo *. vb*) se stejným kořenovým názvem souboru, bude pro název souboru manifestu použit úplný název prvního typu, který je definován ve zdrojovém souboru. Například pokud `MyNamespace.Form1` je první typ definovaný v *Form1.cs*a *Form1.cs* se nachází v souboru *Form1. resx*, vygenerovaný název manifestu pro tento soubor prostředků je *MyNamespace. Form1. Resources*.

## <a name="logicalname-metadata"></a>Logická metadata

Pokud je soubor prostředků explicitně obsažen v souboru projektu jako `EmbeddedResource` položka s `LogicalName` metadaty, `LogicalName` použije se jako název manifestu hodnota. `LogicalName`má přednost před všemi ostatními metadaty nebo nastavením.

Například název manifestu pro soubor prostředků, který je definován v následujícím fragmentu souboru projektu, je příkladem *. Resources*.

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

-nebo-

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a>Metadata ManifestResourceName

Pokud je soubor prostředků explicitně zahrnutý v souboru projektu jako `EmbeddedResource` položka s `ManifestResourceName` metadaty (a chybí `LogicalName` ), `ManifestResourceName` použije se jako název souboru manifestu hodnota v kombinaci s příponou *. Resources.*

Například název manifestu pro soubor prostředků, který je definován v následujícím fragmentu souboru projektu, je příkladem *. Resources*.

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

Název manifestu pro soubor prostředků, který je definován v následujícím fragmentu souboru projektu, je *SomeName.fr-fr. Resources*.

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a>Metadata DependentUpon

Pokud je soubor prostředků explicitně obsažen v souboru projektu jako `EmbeddedResource` položka s `DependentUpon` metadaty (a `LogicalName` `ManifestResourceName` chybí), informace ze zdrojového souboru definovaného pomocí `DependentUpon` se používají pro název souboru manifestu prostředku. Konkrétně název prvního typu, který je definován ve zdrojovém souboru, se používá v názvu manifestu následujícím způsobem: *Namespace. ClassName \[ . Culture]. Resources*.

Například název manifestu pro soubor prostředků, který je definován v následujícím fragmentu souboru projektu, je Namespace. *ClassName. Resources* (kde `Namespace.Classname` je první třída definovaná v *myTypes.cs*).

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

Název manifestu pro soubor prostředků, který je definován v následujícím fragmentu souboru projektu, je *Namespace.ClassName.fr-fr. Resources* (kde `Namespace.Classname` je první třída definovaná v *myTypes.cs*).

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a>Vlastnost EmbeddedResourceUseDependentUponConvention

Pokud `EmbeddedResourceUseDependentUponConvention` je nastaven na hodnotu `false` v souboru projektu, každý název souboru manifestu prostředku je založen na kořenovém oboru názvů pro projekt a relativní cestu z kořene projektu k souboru *. resx* . Přesněji řečeno, vygenerovaný název souboru manifestu prostředku je *RootNamespace. RelativePathWithDotsForSlashes. \[ Culture.] prostředky*. To je také logika sloužící ke generování názvů manifestu ve verzích .NET Core starších než 3,0.

> [!NOTE]
>
> - Pokud `RootNamespace` není definován, použije se výchozí název projektu.
> - Pokud `LogicalName` `ManifestResourceName` `DependentUpon` jsou zadána metadata pro položku v souboru projektu, nebo jsou uvedena metadata `EmbeddedResource` , toto pravidlo pro pojmenovávání neplatí pro tento soubor prostředků.

## <a name="see-also"></a>Viz také

- [Jak funguje vytváření názvů prostředků manifestu](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [Vlastnosti nástroje MSBuild pro projekty .NET Core SDK](../project-sdk/msbuild-props.md)
- [Nejnovější změny nástroje MSBuild](../compatibility/msbuild.md)
