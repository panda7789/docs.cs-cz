---
title: Správa závislostí v nástroje pro .NET Core
description: Vysvětluje, jak spravovat závislosti s nástroji .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.openlocfilehash: cbeb9ad17932f6abaf14333a71fab2b4b8fd099c
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46005330"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a>Správa závislostí s .NET Core SDK 1.0

S přechodem na projektů .NET Core ze souboru project.json na csproj a MSBuild došlo také významnou investici, jejímž výsledkem sjednocení soubor projektu a prostředky, které umožňují sledování závislostí. Pro projekty .NET Core je podobná nebyla jaké project.json. Neexistuje žádný samostatný soubor JSON nebo XML, který sleduje závislostí NuGet. S touto změnou jsme zavedli jiný typ *odkaz* do souboru csproj syntaxe volána `<PackageReference>`. 

Tento dokument popisuje nový typ odkazu. Také ukazuje, jak přidat závislost balíčku pomocí tento nový typ odkazu do projektu. 

## <a name="the-new-packagereference-element"></a>Nové \<PackageReference > – element
`<PackageReference>` Má následující základní strukturu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Pokud jste se seznámili s nástrojem MSBuild, bude vypadat povědomě na jiné typy odkazů, které již existují. Klíč je `Include` příkazu, který určuje id balíčku, který chcete přidat do projektu. `<Version>` Podřízený prvek určuje verzi zobrazíte. Verze jsou určeny podle [pravidla verze NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Pokud nejste obeznámeni s celkovým `csproj` syntaxe, naleznete v tématu [odkaz na projekt MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) Další informace naleznete v dokumentaci.  

Přidání závislostí, který je k dispozici pouze v konkrétní cíle se provádí pomocí podmínek stejně jako v následujícím příkladu:

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

Výše uvedené znamená, že závislost budou pouze platná, pokud sestavení se děje to uvedeny cíle. `$(TargetFramework)` v podmínce je vlastnost MSBuild, která je nastavena v projektu. Pro nejčastěji používané aplikace .NET Core nemusíte to provést. 

## <a name="adding-a-dependency-to-your-project"></a>Přidání závislostí do projektu
Přidání závislostí pro váš projekt je jednoduché. Tady je příklad toho, jak přidat verzi Json.NET `9.0.1` do projektu. Samozřejmě se vztahuje na všechny další závislosti NuGet. 

Při otevření souboru projektu se zobrazí dvě nebo více `<ItemGroup>` uzly. Všimnete si, že jeden z uzlů již `<PackageReference>` prvky v ní. Můžete přidat nové závislosti pro tento uzel nebo vytvořte novou; To je zcela na vás jako výsledek bude stejný. 

V tomto příkladu použijeme výchozí šablonu, která na základě `dotnet new console`. Toto je jednoduchou konzolovou aplikaci. Když nám otevřít projekt, jsme nejprve vyhledat `<ItemGroup>` s již existujícím `<PackageReference>` v ní. Potom jsme do něj přidejte následující:

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
Potom jsme uložte projekt a spusťte `dotnet restore` příkaz a nainstalujte závislosti. 

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

## <a name="removing-a-dependency-from-the-project"></a>Odebrání závislostí projektu
Odebrání závislosti ze souboru projektu vyžaduje jednoduše odebrání `<PackageReference>` ze souboru projektu.
