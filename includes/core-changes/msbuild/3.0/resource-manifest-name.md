---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968237"
---
### <a name="resource-manifest-file-names"></a>Názvy souborů manifestu prostředků

Počínaje rozhraním .NET Core 3.0 byl změněn název souboru manifestu generovaného prostředku.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="change-description"></a>Popis změny

Před rozhraním .NET Core 3.0, kdy byla metadata [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) nastavena pro soubor prostředku (*.resx)* v souboru projektu MSBuild, byl vygenerovaný název manifestu *Namespace.Classname.resources*. Pokud [dependentupon](/visualstudio/msbuild/common-msbuild-project-items#compile) nebyl nastaven, generovaný název manifestu byl *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.

Počínaje rozhraním .NET Core 3.0 je soubor *RESX* umístěn společně se stejným zdrojovým souborem, například v aplikacích windows forms, je název manifestu prostředků generován z úplného názvu prvního typu ve zdrojovém souboru. Pokud je například *Type.cs* společně umístěn s *Type.resx*, je vygenerovaný název manifestu *Namespace.Classname.resources*. Pokud však změníte některý z `EmbeddedResource` atributů vlastnosti souboru *Resx,* může se název generovaného souboru manifestu lišit:

- Pokud `LogicalName` je atribut `EmbeddedResource` vlastnosti nastaven, tato hodnota se používá jako název souboru manifestu prostředku.

  Příklady:

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Název souboru manifestu generovaného prostředku**: *SomeName.resources* (bez ohledu na název souboru *resx* nebo jazykovou verzi nebo jiná metadata).

- Pokud `LogicalName` není nastavena, `ManifestResourceName` ale `EmbeddedResource` atribut na vlastnost je nastavena, jeho hodnota, v kombinaci s příponou *.resources*, se používá jako název souboru manifestu prostředku.

  Příklady:

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Název souboru manifestu generovaného prostředku**: *SomeName.resources* nebo *SomeName.fr-FR.resources*.

- Pokud předchozí pravidla neplatí a `DependentUpon` atribut `EmbeddedResource` prvku je nastaven na zdrojový soubor, použije se v názvu souboru manifestu prostředku název typu první třídy ve zdrojovém souboru. Konkrétně je název generovaného souboru *\[Namespace.Classname . Jazyková verze].zdroje*.

  Příklady:

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Název souboru manifestu generovaného prostředku**: *Namespace.Classname.resources* nebo *Namespace.Classname.fr-FR.resources* (kde `Namespace.Classname` je název první třídy v *MyTypes.cs).*

- Pokud předchozí pravidla neplatí, `EmbeddedResourceUseDependentUponConvention` `true` je (výchozí pro .NET Core) a je zdrojový soubor spoluumístěný se souborem *.resx,* který má stejný název základního souboru, soubor *Resx* je závislý na odpovídajícím zdrojovém souboru a generovaný název je stejný jako v předchozím pravidle. Toto je pravidlo "výchozí nastavení" pro projekty .NET Core.
  
  Příklady:
  
  Soubory *MyTypes.cs* a *MyTypes.resx* nebo *MyTypes.fr-FR.resx* existují ve stejné složce.
  
  **Název souboru manifestu generovaného prostředku**: *Namespace.Classname.resources* nebo *Namespace.Classname.fr-FR.resources* (kde `Namespace.Classname` je název první třídy v *MyTypes.cs).*

- Pokud neplatí žádná z předchozích pravidel, je název souboru manifestu generovaného prostředku *RootNamespace.RelativePathWithDotsForSlashes.\[ Jazyková verze.] zdrojů*. Relativní cesta je hodnota `Link` atributu `EmbeddedResource` prvku, pokud je nastavena. V opačném případě relativní cesta `Identity` je hodnota `EmbeddedResource` atributu prvku. V sadě Visual Studio se jedná o cestu z kořenového adresáře projektu k souboru v Průzkumníku řešení.

#### <a name="recommended-action"></a>Doporučená akce

Pokud nejste spokojeni s generovanými názvy manifestů, můžete:

- Upravte metadata souboru prostředků podle jednoho z dříve popsaných pravidel pojmenování.

- Chcete-li `EmbeddedResourceUseDependentUponConvention` se zcela odhlásit z nové konvence, nastavte `false` v souboru projektu možnost odhlásit se z nové konvence:

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > Pokud `LogicalName` jsou `ManifestResourceName` k dispozici atributy nebo, jejich hodnoty budou stále použity pro název generovaného souboru.

#### <a name="category"></a>Kategorie

MSBuild

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Není dostupné.
