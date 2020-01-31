---
title: Správa závislostí v nástrojích .NET Core
description: Vysvětluje, jak spravovat závislosti pomocí nástrojů .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: 28280dc05e746cdef4e90870cd4cb528382c45bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787865"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a>Správa závislostí pomocí .NET Core SDK 1,0

Když přesunete projekty .NET Core z Project. JSON na csproj a MSBuild, nastaly se významné investice také z důvodu sjednocení souboru projektu a prostředků, které umožňují sledování závislostí. U projektů .NET Core se jedná o podobnou funkci Project. JSON. Neexistuje žádný samostatný soubor JSON nebo XML, který sleduje závislosti NuGet. V této změně jsme také zavedli další typ *odkazu* do syntaxe csproj s názvem `<PackageReference>`.

Tento dokument popisuje nový typ odkazu. Také ukazuje, jak přidat závislost balíčku pomocí tohoto nového typu odkazu na váš projekt.

## <a name="the-new-packagereference-element"></a>Nový \<prvek > PackageReference

`<PackageReference>` má následující základní strukturu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Pokud jste obeznámeni s nástrojem MSBuild, bude se seznámit s dalšími typy odkazů, které již existují. Klíč je příkaz `Include`, který určuje ID balíčku, který chcete přidat do projektu. Podřízený prvek `<Version>` určuje verzi, která má být získána. Verze jsou zadány na základě [pravidel verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Pokud nejste obeznámeni s celkovou syntaxí `csproj`, další informace naleznete v referenční dokumentaci k [projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) .

Přidání závislosti, která je k dispozici pouze v určitém cíli, se provádí pomocí podmínek, jako v následujícím příkladu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Výše uvedené znamená, že závislost bude platná pouze v případě, že se pro daný cíl děje sestavení. `$(TargetFramework)` v podmínce je vlastnost MSBuild, která je nastavena v projektu. Pro většinu běžných aplikací .NET Core to nebudete potřebovat.

## <a name="add-a-dependency-to-the-project"></a>Přidat závislost do projektu

Přidání závislosti do projektu je jednoduché. Tady je příklad, jak přidat Json.NET verze `9.0.1` do projektu. Samozřejmě platí pro všechny ostatní závislosti NuGet.

Po otevření souboru projektu se zobrazí dva nebo více `<ItemGroup>`ch uzlů. Všimněte si, že jeden z uzlů již obsahuje `<PackageReference>` prvky. Do tohoto uzlu můžete přidat novou závislost nebo vytvořit novou. je to na vás, protože výsledek bude stejný.

Následující příklad používá výchozí šablonu, která je zahozena `dotnet new console`. Toto je jednoduchá Konzolová aplikace. Když otevřete projekt, najdete `<ItemGroup>` s již existujícím `<PackageReference>`em. Přidejte do něj následující:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

Potom uložte projekt a spusťte příkaz `dotnet restore` pro instalaci závislosti.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Úplný projekt vypadá takto:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="remove-a-dependency-from-the-project"></a>Odebrat závislost z projektu

Odebrání závislosti ze souboru projektu zahrnuje pouhou odebrání `<PackageReference>` ze souboru projektu.
