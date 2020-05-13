---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206205"
---
### <a name="resource-manifest-file-name-change"></a>Název souboru manifestu prostředku – změna

Počínaje platformou .NET Core 3,0 ve výchozím případě nástroj MSBuild generuje pro soubory prostředků jiný název souboru manifestu.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="change-description"></a>Popis změny

Před rozhraním .NET Core 3,0, pokud `LogicalName` `ManifestResourceName` nebyla zadána žádná, nebo `DependentUpon` metadata pro `EmbeddedResource` položku v souboru projektu, nástroj MSBuild vygeneroval ve vzoru název souboru manifestu `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` . Pokud `RootNamespace` není v souboru projektu definován, je výchozím názvem projektu. Například vygenerovaný název manifestu pro soubor prostředků s názvem *Form1. resx* v kořenovém adresáři projektu byl *MyProject. Form1. Resources*.

Počínaje platformou .NET Core 3,0 platí, že pokud se soubor prostředků nachází společně se zdrojovým souborem se stejným názvem (například *Form1. resx* a *Form1.cs*), nástroj MSBuild používá informace o typu ze zdrojového souboru pro vygenerování názvu souboru manifestu ve vzoru `<Namespace>.<ClassName>.resources` . Obor názvů a název třídy jsou extrahovány z prvního typu v společně umístěném zdrojovém souboru. Například vygenerovaný název manifestu pro soubor prostředků s názvem *Form1. resx* , který je společně umístěn pomocí zdrojového souboru s názvem *Form1.cs* , je *MyNamespace. Form1. Resources*. Klíčovým poznámku je, že první část názvu souboru se liší od předchozích verzí .NET Core (*MyNamespace* místo *MyProject*).

> [!NOTE]
> Pokud máte `LogicalName` metadata, `ManifestResourceName` nebo `DependentUpon` zadaná pro `EmbeddedResource` položku v souboru projektu, pak tato změna nemá vliv na daný soubor prostředků.

Tato Průlomová změna byla představena s přidáním `EmbeddedResourceUseDependentUponConvention` vlastnosti do projektů .NET Core. Ve výchozím nastavení nejsou soubory prostředků explicitně uvedeny v souboru projektu .NET Core, takže nemají žádná `DependentUpon` metadata pro určení způsobu pojmenování vygenerovaného souboru *. Resources* . Pokud `EmbeddedResourceUseDependentUponConvention` je nastaven na `true` , což je výchozí, MSBuild hledá umístěný zdrojový soubor a z něj extrahuje obor názvů a název třídy. Pokud nastavíte `EmbeddedResourceUseDependentUponConvention` na `false` , nástroj MSBuild vygeneruje název manifestu podle předchozího chování, které kombinuje `RootNamespace` a relativní cestu k souboru.

#### <a name="recommended-action"></a>Doporučená akce

Ve většině případů není nutná žádná akce v rámci vývojáře a vaše aplikace by měla fungovat i nadále. Pokud však tato změna poškodí vaši aplikaci, můžete:

- Změňte kód tak, aby očekával nový název manifestu.

- Odsouhlasit nové zásady vytváření názvů nastavením `EmbeddedResourceUseDependentUponConvention` na `false` v souboru projektu

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a>Kategorie

MSBuild

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

–
