---
title: Úložiště balíčků modulu runtime
description: Další informace o použití úložiště balíčků modulu runtime pro cílové manifestů, které používá .NET Core.
author: bleroy
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: a190e148715547fde29d3a852183ea4d75065e79
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170350"
---
# <a name="runtime-package-store"></a>Úložiště balíčků modulu runtime

Počínaje .NET Core 2.0, je možné k zabalení a nasazení aplikace před známými sadu balíčků, které existují v cílovém prostředí. Výhody jsou rychlejší nasazení, nižší využití místa na disku a vylepšené spouštění výkonu v některých případech.

Tato funkce je implementovaná jako *úložiště balíčků modulu runtime*, což je adresář na disku, kde jsou uloženy balíčky (obvykle v */usr/local/share/dotnet/store* v systému macOS nebo Linuxu a *C: / Program soubory/dotnet/store* na Windows). V tomto adresáři neexistují podadresáře pro architektury a [platforem](../../standard/frameworks.md). Soubor rozložení je podobným způsobem, který [NuGet prostředky jsou rozloženy na disku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):

```
\dotnet
    \store
        \x64
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
        \x86
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
```

A *cíl manifestu* soubor obsahuje seznam balíčků v úložiště balíčků modulu runtime. Vývojáři mohou cílit manifestu, při publikování své aplikace. Cíl manifestu se většinou poskytuje vlastník cílové produkčního prostředí.

## <a name="preparing-a-runtime-environment"></a>Příprava prostředí runtime

Správce prostředí modulu runtime může optimalizovat aplikace pro rychlejší nasazení a nižší využití místa na disku vytvořením úložiště balíčků modulu runtime a odpovídající cíl manifestu.

Prvním krokem je vytvoření *manifest balíčku úložiště* , který obsahuje seznam balíčků, které tvoří úložiště balíčků modulu runtime. Tento formát souboru je kompatibilní s formátem souboru projektu (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Příklad**

Následující příklad manifestu úložiště balíčků (*packages.csproj*) se používá k přidání [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) a [ `Moq` ](https://www.nuget.org/packages/moq/) do úložiště balíčků modulu runtime:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Zřídit úložiště balíčků modulu runtime pomocí provádí `dotnet store` manifest balíčku úložiště, modul runtime a framework:

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Příklad**

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Můžete předat více cílové úložiště balíčků cesty k manifestu do jediné [ `dotnet store` ](../tools/dotnet-store.md) příkaz opakováním možnost a cestu v příkazu.

Výchozí výstup příkazu je balíček úložiště v nabídce *.dotnet/store* podadresář tím profil daného uživatele. Můžete zadat jiné umístění pomocí `--output <OUTPUT_DIRECTORY>` možnost. Kořenový adresář úložiště obsahuje cíl manifestu *artifact.xml* souboru. Tento soubor může být k dispozici ke stažení a používá aplikace autory, kteří chtějí cílí toto úložiště při publikování.

**Příklad**

Následující *artifact.xml* po spuštění předchozího příkladu je vytvořen soubor. Všimněte si, že [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) je závislost `Moq`, takže ji vložila automaticky a zobrazí se v *artifacts.xml* soubor manifestu.

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publikování aplikace proti cílové manifestu

Pokud máte soubor manifestu cíl na disku, je při publikování aplikace s využitím zadat cestu k souboru [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz:

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Příklad**

```console
dotnet publish --manifest manifest.xml
```

Nasazení výsledné publikované aplikace do prostředí, který má balíčky, které je popsáno v manifestu cíl. Pokud tak neučiníte za následek selhání spuštění aplikace.

Určení více manifestů cílové při publikování aplikace opakováním možnost a cestu (například `--manifest manifest1.xml --manifest manifest2.xml`). Pokud tak učiníte, aplikace je oříznut pro sjednocení balíčky zadané v cílové soubory manifestu k příkazu k dispozici.

## <a name="specifying-target-manifests-in-the-project-file"></a>Zadání cílové manifesty v souboru projektu

Alternativa k určení cílového manifesty s [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz je se zadávají v souboru projektu jako středníkem oddělený seznam cest v rámci  **\<TargetManifestFiles >** značky.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Určení manifestů cíl v souboru projektu, pouze v případě cílového prostředí pro aplikaci je dobře známé, například pro projekty .NET Core. To není případ open-source projektů. Uživatelé open source projektu je obvykle nasazení do různých produkční prostředí. Tyto produkční prostředí obvykle mají různé sady předem nainstalované balíčky. Předpoklady o cíl manifestu nemůže provádět v těchto prostředích, proto byste měli použít `--manifest` možnost [ `dotnet publish` ](../tools/dotnet-publish.md).

## <a name="aspnet-core-implicit-store"></a>Implicitní úložiště ASP.NET Core

ASP.NET Core implicitní úložiště platí jenom pro ASP.NET Core 2.0. Důrazně doporučujeme aplikace pomocí ASP.NET Core 2.1 nebo novější, která zajišťuje **není** použít implicitní úložiště. ASP.NET Core 2.1 a pozdější použití sdílené architektuře.

Funkce úložiště balíčků modulu runtime používá implicitně aplikace ASP.NET Core při nasazení aplikace jako [nasazení závisí na architektuře (chyba)](index.md#framework-dependent-deployments-fdd) aplikace. Cíle v [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) zahrnují manifesty odkazující na implicitní úložiště balíček v cílovém systému. Kromě toho libovolnou aplikaci disketové jednotky, na kterém závisí `Microsoft.AspNetCore.All` balíček výsledky v publikované aplikaci, která obsahuje jenom aplikace a její prostředky a není balíčky uvedené v `Microsoft.AspNetCore.All` Microsoft.aspnetcore.all. Předpokládá se, že tyto balíčky jsou k dispozici v cílovém systému.

Úložiště balíčků modulu runtime je nainstalován na hostiteli, když je nainstalovaná sada .NET Core SDK. Další instalační programy může poskytovat úložiště balíčků modulu runtime, včetně Zip/tarballu instalace sady .NET Core SDK `apt-get`, Red Hat Yumu, sady .NET Core Windows serveru, který hostuje a ruční runtime úložiště balíčků zařízení.

Při nasazování [nasazení závisí na architektuře (chyba)](index.md#framework-dependent-deployments-fdd) aplikace, ujistěte se, že cílové prostředí má nainstalovaná sada .NET Core SDK. Pokud je aplikace nasazena do prostředí, který neobsahuje ASP.NET Core, můžete zrušit implicitní úložiště tak, že zadáte  **\<PublishWithAspNetCoreTargetManifest >** nastavena na `false` v souboru projektu jako v v následujícím příkladu:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> Pro [samostatná nasazení (SCD)](index.md#self-contained-deployments-scd) aplikací, se předpokládá, že cílový systém nutně neobsahuje požadované balíčky manifestu. Proto  **\<PublishWithAspNetCoreTargetManifest >** nelze nastavit na `true` SCD aplikace.

Pokud nasazujete aplikaci se závislostí manifestu, který je k dispozici v nasazení (je k dispozici v sestavení *bin* složky), úložiště balíčků modulu runtime *nepoužívá* na hostiteli pro toto sestavení. *Bin* sestavení složky se používá bez ohledu na jejich přítomnosti v úložiště balíčků modulu runtime na hostiteli.

Verze závislosti uvedené v manifestu musí odpovídat verzi závislosti v úložiště balíčků modulu runtime. Pokud máte Neshoda verzí mezi závislosti v manifestu cíl a verze, která existuje v úložiště balíčků modulu runtime a aplikace neobsahuje požadovanou verzi balíčku v jeho nasazení, aplikace se nespustí. Výjimka obsahuje název cílového manifestu, který volá se pro sestavení úložiště balíčků modulu runtime, které vám pomohou s řešením neshoda.

Pokud je nasazení *oříznut* při publikování, jsou pouze konkrétní verze manifestu balíčky určujete sražených z publikovaných výstupu. Balíčky na uvedené verze musí být k dispozici na na spuštění hostitele pro aplikaci.

## <a name="see-also"></a>Viz také:

* [DotNet – publikování](../tools/dotnet-publish.md)  
* [DotNet Restore](../tools/dotnet-store.md)  
