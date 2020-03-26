---
title: Úložiště balíčků modulu runtime
description: Zjistěte, jak pomocí úložiště balíčků runtime cílit manifesty používané jádrem .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: ba3182b682e8a47397ac09ed46afe25190d34e5f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134265"
---
# <a name="runtime-package-store"></a>Úložiště balíčků modulu runtime

Počínaje rozhraním .NET Core 2.0 je možné balit a nasazovat aplikace proti známé sadě balíčků, které existují v cílovém prostředí. Výhodou jsou rychlejší nasazení, nižší využití místa na disku a v některých případech lepší výkon při spuštění.

Tato funkce je implementována jako *runtime package store*, což je adresář na disku, kde jsou uloženy balíčky (obvykle na */usr/local/share/dotnet/store* na macOS/Linux a *C:/Program Files/dotnet/store* v systému Windows). Pod tímto adresářem jsou podadresáře pro architektury a [cílové architektury](../../standard/frameworks.md). Rozložení souboru je podobné způsobu, jakým [jsou prostředky NuGet rozloženy na disku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):

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

*Cílový soubor manifestu* uvádí balíčky v úložišti balíčků runtime. Vývojáři mohou cílit na tento manifest při publikování své aplikace. Cílový manifest je obvykle poskytován vlastníkem cílového produkčního prostředí.

## <a name="preparing-a-runtime-environment"></a>Příprava runtime prostředí

Správce prostředí runtime můžete optimalizovat aplikace pro rychlejší nasazení a nižší využití místa na disku vytvořením úložiště balíčků runtime a odpovídající cílový manifest.

Prvním krokem je vytvoření *manifestu úložiště balíčků,* který obsahuje seznam balíčků, které tvoří úložiště balíčků runtime. Tento formát souboru je kompatibilní s formátem souboru projektu (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Příklad**

Následující ukázkový manifest úložiště balíčků *(packages.csproj*) se používá k přidání [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) a [`Moq`](https://www.nuget.org/packages/moq/) do runtime úložiště balíčků:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Zřízení úložiště balíčků runtime `dotnet store` spuštěním s manifestem úložiště balíčků, runtime a framework:

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Příklad**

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Můžete předat více cest manifestu úložiště [`dotnet store`](../tools/dotnet-store.md) cílového balíčku k jednomu příkazu opakováním možnosti a cesty v příkazu.

Ve výchozím nastavení je výstupem příkazu úložiště balíčků pod podadresářem *.dotnet/store* profilu uživatele. Pomocí možnosti `--output <OUTPUT_DIRECTORY>` můžete určit jiné umístění. Kořenový adresář úložiště obsahuje cílový soubor *manifestu artefakt.xml.* Tento soubor může být k dispozici ke stažení a může být použit autory aplikací, kteří chtějí cílit na tento obchod při publikování.

**Příklad**

Následující soubor *artifact.xml* je vytvořen po spuštění předchozího příkladu. Všimněte [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) si, že `Moq`je závislost , takže je součástí automaticky a zobrazí se v souboru manifestu *artifacts.xml.*

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publikování aplikace proti cílovému manifestu

Pokud máte na disku cílový soubor manifestu, zadejte cestu k [`dotnet publish`](../tools/dotnet-publish.md) souboru při publikování aplikace pomocí příkazu:

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Příklad**

```dotnetcli
dotnet publish --manifest manifest.xml
```

Nasadíte výsledné publikované aplikace do prostředí, které má balíčky popsané v cílovémanifestu. Pokud tak neučiníte, nepodaří se spuštění aplikace.

Při publikování aplikace zadejte více cílových manifestů opakováním `--manifest manifest1.xml --manifest manifest2.xml`možnosti a cesty (například ). Pokud tak učiníte, aplikace je oříznuta pro sjednocení balíčků zadaných v cílových souborech manifestu, které jsou k dispozici příkazu.

## <a name="specifying-target-manifests-in-the-project-file"></a>Určení cílových manifestů v souboru projektu

Alternativou k určení cílových [`dotnet publish`](../tools/dotnet-publish.md) manifestů pomocí příkazu je zadat je v souboru projektu jako seznam cest oddělených středníkem pod značkou ** \<TargetManifestFiles>.**

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Zadejte cílové manifesty v souboru projektu pouze v případě, že cílové prostředí pro aplikaci je dobře známé, například pro projekty .NET Core. To není případ open-source projektů. Uživatelé projektu s otevřeným zdrojovým kódem obvykle nasazují do různých produkčních prostředí. Tato produkční prostředí mají obvykle různé sady balíčků předinstalovaných. V takových prostředích nelze provádět předpoklady o cílovém manifestu, takže byste měli použít `--manifest` možnost [`dotnet publish`](../tools/dotnet-publish.md).

## <a name="aspnet-core-implicit-store"></a>ASP.NET implicitní úložiště Core

Implicitní úložiště ASP.NET Core se vztahuje pouze na ASP.NET Core 2.0. Důrazně doporučujeme, aby aplikace používaly ASP.NET Core 2.1 a novějším, který **nepoužívá** implicitní úložiště. ASP.NET Core 2.1 a později používat sdílený rámec.

Funkce runtime package store se implicitně používá aplikace ASP.NET Core, když je aplikace nasazená jako aplikace [pro nasazení (FDD) závislá na rámci.](index.md#publish-runtime-dependent) Cíle v [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) zahrnují manifesty odkazující na implicitní úložiště balíčků v cílovém systému. Kromě toho všechny FDD aplikace, `Microsoft.AspNetCore.All` která závisí na balíčku výsledky v publikované aplikaci, která `Microsoft.AspNetCore.All` obsahuje pouze aplikaci a její prostředky a ne balíčky uvedené v metabalíčku. Předpokládá se, že tyto balíčky jsou přítomny v cílovém systému.

Úložiště runtime balíčků je nainstalováno na hostiteli při instalaci sady .NET Core SDK. Ostatní instalační programy mohou poskytovat runtime package store, včetně zip/tarball ových `apt-get`instalací sady .NET Core SDK, , Red Hat Yum, balíčku .NET Core Windows Server Hosting a ručních instalací úložiště runtime balíčků.

Při nasazování aplikace [pro nasazení v rámci (FDD)](index.md#publish-runtime-dependent) se ujistěte, že cílové prostředí má nainstalovanou sadu .NET Core SDK. Pokud je aplikace nasazená do prostředí, které neobsahuje ASP.NET Core, můžete se odhlásit z implicitního úložiště `false` zadáním ** \<>PublishWithAspNetCoreTargetManifest** nastavena v souboru projektu jako v následujícím příkladu:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> Pro [samostatné nasazení (SCD)](index.md#publish-self-contained) aplikace se předpokládá, že cílový systém nemusí nutně obsahovat požadované balíčky manifestu. Proto ** \<PublishWithAspNetCoreTargetManifest>** nelze `true` nastavit pro aplikaci SCD.

Pokud nasadíte aplikaci se závislostí na manifestu, která je přítomna v nasazení (sestavení je k dispozici ve složce *přihrádky),* úložiště balíčků runtime *se nepoužívá* na hostiteli pro toto sestavení. Sestavení složky *přihrádky* se používá bez ohledu na jeho přítomnost v úložišti balíčků runtime na hostiteli.

Verze závislosti uvedená v manifestu musí odpovídat verzi závislosti v runtime package store. Pokud máte neshodu verzí mezi závislostí v cílovém manifestu a verzí, která existuje v obchodě s balíčky runtime a aplikace neobsahuje požadovanou verzi balíčku v jeho nasazení, aplikace se nepodaří spustit. Výjimka zahrnuje název cílového manifestu, který volal pro sestavení úložiště balíčků runtime, který vám pomůže vyřešit neshodu.

Při *oříznutí* nasazení při publikování jsou z publikovaného výstupu odepřeny pouze konkrétní verze balíčků manifestu, které označujete. Balíčky v uvedených verzích musí být k dispozici na hostiteli, aby aplikace začala.

## <a name="see-also"></a>Viz také

- [dotnet-publikovat](../tools/dotnet-publish.md)
- [dotnet-store](../tools/dotnet-store.md)
