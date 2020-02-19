---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451880"
---
### <a name="resource-manifest-file-names"></a>Názvy souborů manifestu prostředků

Počínaje platformou .NET Core 3,0 se změnil název souboru manifestu generovaného manifestu.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="change-description"></a>Změnit popis

Před rozhraním .NET Core 3,0 se při nastavení metadat [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) pro soubor prostředků ( *. resx*) v souboru projektu MSBuild vygeneroval název manifestu *Namespace. ClassName. Resources*. Pokud [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) nebyl nastaven, vygenerovaný název manifestu byl *obor názvů. ClassName. FolderPathRelativeToRoot. Culture. Resources*.

Počínaje platformou .NET Core 3,0 platí, že pokud se soubor *. resx* nachází společně se zdrojovým souborem se stejným názvem, například v model Windows Forms aplikace, název manifestu prostředku je vygenerován z úplného názvu prvního typu ve zdrojovém souboru. Například pokud je *Type.cs* společně umístěn s *Type. resx*, vygenerovaný název manifestu je Namespace. *ClassName. Resources*. Nicméně pokud upravíte kterýkoli z atributů vlastnosti `EmbeddedResource` souboru *. resx* , název souboru manifestu se může lišit:

- Pokud je nastaven atribut `LogicalName` u vlastnosti `EmbeddedResource`, použije se tato hodnota jako název souboru manifestu prostředku.

  Příklady:

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Vygenerovaný název souboru manifestu prostředku**: *Příklady. Resources* (bez ohledu na název souboru *. resx* nebo jazykovou verzi nebo jiná metadata).

- Pokud `LogicalName` není nastavena, ale atribut `ManifestResourceName` vlastnosti `EmbeddedResource` je nastaven, jeho hodnota se v kombinaci s příponou souboru *. Resources*používá jako název souboru manifestu prostředku.

  Příklady:

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Vygenerovaný název souboru manifestu prostředku**: *Příklady. Resources* nebo *SomeName.fr-fr. Resources*.

- Pokud předchozí pravidla neplatí a atribut `DependentUpon` elementu `EmbeddedResource` je nastaven na zdrojový soubor, v názvu souboru manifestu prostředků se použije název typu první třídy ve zdrojovém souboru. Konkrétně název generovaného souboru je *Namespace. Classname\[. Culture]. Resources*.

  Příklady:

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Vygenerovaný název souboru manifestu prostředku**: *Namespace. ClassName. Resources* nebo *Namespace.ClassName.fr-fr. resources* (kde `Namespace.Classname` je název první třídy v *myTypes.cs*).

- Pokud se předchozí pravidla nevztahují, `EmbeddedResourceUseDependentUponConvention` je `true` (výchozí pro .NET Core) a existuje zdrojový soubor, který se nachází v souboru *. resx* , který má stejný základní název souboru, pak je soubor *. resx* závislý na odpovídajícím zdrojovém souboru a vygenerovaný název je stejný jako v předchozím pravidle. Toto je pravidlo "výchozí nastavení" pro projekty .NET Core.
  
  Příklady:
  
  Soubory *myTypes.cs* a *myTypes. resx* nebo *myTypes.fr-fr. resx* existují ve stejné složce.
  
  **Vygenerovaný název souboru manifestu prostředku**: *Namespace. ClassName. Resources* nebo *Namespace.ClassName.fr-fr. resources* (kde `Namespace.Classname` je název první třídy v *myTypes.cs*).
    
- Pokud žádné z předchozích pravidel neplatí, název souboru manifestu prostředku je *RootNamespace. RelativePathWithDotsForSlashes.\[culture.] prostředky*. Relativní cesta je hodnota atributu `Link` elementu `EmbeddedResource`, pokud je nastavena. V opačném případě je relativní cesta hodnotou atributu `Identity` `EmbeddedResource` elementu. V aplikaci Visual Studio se jedná o cestu z kořenového adresáře projektu k souboru v Průzkumník řešení.

#### <a name="recommended-action"></a>Doporučená akce

Pokud nejste spokojeni s generovanými názvy manifestů, můžete:

- Upravte metadata souboru prostředků podle některého z dříve popsaných pravidel pojmenování.

- Nastavte `EmbeddedResourceUseDependentUponConvention` pro `false` v souboru projektu tak, aby se odhlásila od zcela nové smlouvy:

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > Pokud jsou k dispozici atributy `LogicalName` nebo `ManifestResourceName`, budou jejich hodnoty nadále použity pro vygenerovaný název souboru.

#### <a name="category"></a>Kategorie

MSBuild

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Není k dispozici
