---
title: Správa závislostí v nástrojích .NET Core
description: Vysvětluje, jak spravovat závislosti pomocí nástrojů .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: e14fa42534d807e2a0fcce1dabe747c18c5166b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733372"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>Správa závislostí pomocí .NET Core SDK 1,0

Když přesunete projekty .NET Core z Project. JSON na csproj a MSBuild, nastaly se významné investice také z důvodu sjednocení souboru projektu a prostředků, které umožňují sledování závislostí. Pro projekty .NET Core se jedná o podobný kód jako Project. JSON. Neexistuje žádný samostatný soubor JSON nebo XML, který sleduje závislosti NuGet. V této změně jsme také zavedli další typ *odkazu* do syntaxe csproj s názvem `<PackageReference>`. 

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

## <a name="adding-a-dependency-to-your-project"></a>Přidání závislosti do projektu
Přidání závislosti do projektu je jednoduché. Tady je příklad, jak přidat Json.NET verze `9.0.1` do projektu. Samozřejmě platí pro všechny ostatní závislosti NuGet. 

Po otevření souboru projektu se zobrazí dva nebo více `<ItemGroup>`ch uzlů. Všimněte si, že jeden z uzlů již obsahuje `<PackageReference>` prvky. Do tohoto uzlu můžete přidat novou závislost nebo vytvořit novou. je zcela na vás, protože výsledek bude stejný. 

V tomto příkladu použijeme výchozí šablonu, která je zahozena `dotnet new console`. Toto je jednoduchá Konzolová aplikace. Po otevření projektu jsme nejdřív našli `<ItemGroup>` už existující `<PackageReference>`. Následně do něj přidáte následující:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

Potom uložte projekt a spuštěním příkazu `dotnet restore` pro instalaci závislosti. 

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

## <a name="removing-a-dependency-from-the-project"></a>Odebrání závislosti z projektu
Odebrání závislosti ze souboru projektu zahrnuje pouhou odebrání `<PackageReference>` ze souboru projektu.
