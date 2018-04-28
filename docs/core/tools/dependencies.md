---
title: Správa závislostí v nástrojů .NET Core
description: Vysvětluje, jak spravovat svoje závislosti pomocí nástrojů .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 5da4f5e4d837be874323ef700093b0d01c8ac98f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>Správa závislostí s .NET Core SDK 1.0

S přechodem .NET Core projektů ze souboru project.json csproj a MSBuild došlo také významné investice, jejichž výsledkem sjednocení soubor projektu a prostředky, které umožňují sledování závislostí. Pro projekty .NET Core se podobá se co project.json. Není k dispozici žádný samostatný soubor XML nebo JSON, který sleduje závislostí NuGet. Díky této změně jste zavedli jsme taky jiný typ *odkaz* do csproj syntaxe volat `<PackageReference>`. 

Tento dokument popisuje nové odkazového typu. Také ukazuje, jak můžete přidat závislost balíčku pomocí tento nový typ odkazu do projektu. 

## <a name="the-new-packagereference-element"></a>Nové \<PackageReference > elementu
`<PackageReference>` Má následující základní strukturu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Pokud jste obeznámeni s MSBuild, bude vypadat pro jiné odkazové typy, které již existují. Klíč je `Include` příkaz, který určuje id balíčku, který chcete přidat do projektu. `<Version>` Podřízený element určuje verzi, chcete-li získat. Verze jsou určené jako za [pravidla verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Pokud nejste obeznámeni s celkovým `csproj` syntaxe, najdete v článku [projektu MSBuild – reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) Další informace naleznete v dokumentaci.  

Přidání závislostí, která je k dispozici pouze v konkrétní cíl se provádí pomocí podmínky jako v následujícím příkladu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

Výše uvedené znamená, že závislost bude pouze platné, pokud je pro tento zadané cílové nedošlo k sestavení. `$(TargetFramework)` Ve stavu, je nastavený v projektu nástroje MSBuild vlastnost. Pro nejčastěji používané aplikace .NET Core nebudete muset provést. 

## <a name="adding-a-dependency-to-your-project"></a>Přidání závislostí do projektu
Přidání závislostí do projektu je jednoduchá. Tady je příklad toho, jak přidat Json.NET verze `9.0.1` do projektu. Samozřejmě se vztahuje na všechny ostatní závislostí NuGet. 

Když otevřete soubor projektu, se zobrazí dvě nebo více `<ItemGroup>` uzlů. Si všimnete, že jeden z uzlů již `<PackageReference>` elementy v ní. Můžete přidat nové závislosti pro tento uzel, nebo vytvořte novou; je zcela na vás jako výsledek budou stejné. 

V tomto příkladu použijeme výchozí šablonu, která je zrušených `dotnet new console`. Toto je jednoduché konzolové aplikace. Když jsme otevřete projekt, nám nejdřív najít `<ItemGroup>` s již existujícími `<PackageReference>` v ní. Potom jsme do něj přidejte následující:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
Potom jsme uložte projekt a spusťte `dotnet restore` příkaz pro instalaci závislost. 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Úplný projekt vypadá takto:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a>Odebrání závislost z projektu
Odebrání závislost ze souboru projektu vyžaduje jednoduše odebrání `<PackageReference>` ze souboru projektu.
