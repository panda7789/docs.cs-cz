---
ms.openlocfilehash: d75dc2caa3a002b9d34ac74f2c5c5e192281c0df
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281293"
---
### <a name="default-activityidformat-is-w3c"></a>Výchozí ActivityIdFormat je W3C.

Výchozí formát identifikátoru pro aktivitu ( <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> ) je nyní <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .

#### <a name="change-description"></a>Popis změny

Formát ID aktivity W3C byl představen v .NET Core 3,0 jako alternativa k formátu hierarchického ID. Pro zachování kompatibility ale formát W3C není výchozí, dokud neproběhne .NET 5,0. Ve výchozím nastavení byla v rozhraní .NET 5,0 změněna, protože [formát W3C byl ratifikován](https://www.w3.org/TR/trace-context/) a byl získán v rámci více implementací jazyka.

Pokud se vaše aplikace zaměřuje na jinou platformu než .NET 5,0 nebo novější, bude se jednat o staré chování, kde <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> je výchozí formát. Tato výchozí hodnota se vztahuje na platformy Net45 +, netstandard 1.1 + a netcoreapp (1. x, 2. x a 3. x). V rozhraní .NET 5,0 a novějším <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> je nastaveno na <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 7

#### <a name="recommended-action"></a>Doporučená akce

Pokud je vaše aplikace nezávislá na identifikátor, který se používá pro distribuované trasování, není nutné provádět žádnou akci. Knihovny jako ASP.NET Core a <xref:System.Net.Http.HttpClient> mohou využívat nebo rozšiřovat obě verze rozhraní <xref:System.Diagnostics.ActivityIdFormat> .

Pokud potřebujete interoperabilitu se stávajícími systémy nebo aktuální systémy spoléhají na formát identifikátoru, můžete zachovat staré chování nastavením <xref:System.Diagnostics.Activity.DefaultIdFormat> na <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> . Alternativně můžete nastavit přepínač AppContext jedním ze tří způsobů:

- V souboru projektu.

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- V *runtimeconfig.jsv* souboru.

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- Prostřednictvím proměnné prostředí.

  Nastavte `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` na `true` nebo 1.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
