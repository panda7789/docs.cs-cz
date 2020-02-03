---
title: Úložiště balíčků modulu runtime
description: Naučte se používat úložiště balíčků modulu runtime pro cílení na manifesty používané .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: 8c58ccdb90e5ae9830313f52c19f58629ea5b0a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737784"
---
# <a name="runtime-package-store"></a>Úložiště balíčků modulu runtime

Počínaje .NET Core 2,0 je možné zabalit a nasazovat aplikace na známou sadu balíčků, které existují v cílovém prostředí. Výhody jsou rychlejší nasazení, nižší využití místa na disku a Vylepšený výkon při spuštění v některých případech.

Tato funkce je implementována jako *běhové úložiště balíčků*, což je adresář na disku, kde jsou uloženy balíčky (obvykle na */usr/local/share/dotnet/Store* v MacOS/Linux a *C:/Program Files/dotnet/Store* ve Windows). V tomto adresáři jsou podadresáře pro architektury a [cílové](../../standard/frameworks.md)architektury. Rozložení souboru je podobné způsobu, jakým [jsou prostředky NuGet na disku rozloženy](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):

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

*Cílový soubor manifestu* uvádí balíčky v úložišti balíčků modulu runtime. Vývojáři můžou tento manifest cílit při publikování aplikace. Cílový manifest je obvykle poskytován vlastníkem cílového produkčního prostředí.

## <a name="preparing-a-runtime-environment"></a>Příprava běhového prostředí

Správce běhového prostředí může optimalizovat aplikace pro rychlejší nasazení a snížit využití místa na disku vytvořením běhového balíčku za běhu a odpovídajícího cílového manifestu.

Prvním krokem je vytvoření *manifestu balíčku pro úložiště* , který obsahuje seznam balíčků, které tvoří úložiště balíčků modulu runtime. Tento formát souboru je kompatibilní s formátem souboru projektu (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Příklad**

Následující ukázkový manifest úložiště balíčků (*Packages. csproj*) se používá k přidání [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) a [`Moq`](https://www.nuget.org/packages/moq/) do úložiště balíčků modulu runtime:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Zajistěte, aby se úložiště balíčků modulu runtime spustilo `dotnet store` s manifestem úložiště balíčků, modulem runtime a architekturou:

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Příklad**

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Pomocí možnosti a cesty v příkazu můžete předat několik cest k manifestu cílového úložiště balíčků do jednoho [`dotnet store`](../tools/dotnet-store.md) příkazu.

Ve výchozím nastavení je výstupem příkazu úložiště balíčků v podadresáři *. dotnet/Store* profilu uživatele. Pomocí možnosti `--output <OUTPUT_DIRECTORY>` můžete zadat jiné umístění. Kořenový adresář úložiště obsahuje cílový soubor *. XML artefaktu* manifestu. Tento soubor může být zpřístupněn ke stažení a musí ho používat autoři aplikací, kteří chtějí toto úložiště cílit při publikování.

**Příklad**

Následující soubor *artefakt. XML* se vytvoří po spuštění předchozího příkladu. Všimněte si, že [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) je závislost `Moq`, takže je automaticky zahrnutá a zobrazí se v souboru manifestu *artefakts. XML* .

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publikování aplikace proti cílovému manifestu

Pokud máte cílový soubor manifestu na disku, zadejte cestu k souboru při publikování aplikace pomocí příkazu [`dotnet publish`](../tools/dotnet-publish.md) :

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Příklad**

```dotnetcli
dotnet publish --manifest manifest.xml
```

Výslednou publikovanou aplikaci nasadíte do prostředí, které obsahuje balíčky popsané v cílovém manifestu. V důsledku neúspěšného spuštění aplikace dojde k selhání.

Zadejte více cílových manifestů při publikování aplikace opakováním možnosti a cesty (například `--manifest manifest1.xml --manifest manifest2.xml`). V takovém případě se aplikace ořízne pro sjednocení balíčků zadaných v cílových souborech manifestu, které jsou k dispozici v příkazu.

## <a name="specifying-target-manifests-in-the-project-file"></a>Určení cílových manifestů v souboru projektu

Alternativou k určení cílových manifestů pomocí příkazu [`dotnet publish`](../tools/dotnet-publish.md) je zadat je do souboru projektu jako seznam cest oddělených středníkem v **\<TargetManifestFiles >** značku.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Zadejte cílové manifesty v souboru projektu pouze v případě, že cílové prostředí pro aplikaci je dobře známé, například u projektů .NET Core. Nejedná se o případ open source projektů. Uživatelé open source projektu ji obvykle nasadí do různých produkčních prostředí. Tato produkční prostředí mají většinou nainstalované různé sady balíčků. V takových prostředích nemůžete vytvářet předpoklady pro cílový manifest, proto byste měli použít možnost `--manifest` [`dotnet publish`](../tools/dotnet-publish.md).

## <a name="aspnet-core-implicit-store"></a>ASP.NET Core implicitního úložiště

ASP.NET Core implicitní úložiště platí pouze pro ASP.NET Core 2,0. Důrazně doporučujeme, aby aplikace používaly ASP.NET Core 2,1 a novější, které **nepoužívají implicitní** úložiště. ASP.NET Core 2,1 a novější používají sdílené rozhraní.

Funkce úložiště balíčků za běhu se implicitně používá v aplikaci ASP.NET Core, když se aplikace nasadí jako aplikace [nasazení závislá na rozhraní (FDD)](index.md#framework-dependent-deployments-fdd) . Cíle v [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) zahrnují manifesty odkazující na implicitní úložiště balíčků v cílovém systému. Kromě toho jakákoli aplikace FDD, která závisí na balíčku `Microsoft.AspNetCore.All`, má za následek publikovanou aplikaci, která obsahuje jenom aplikaci a její prostředky, a ne balíčky uvedené v `Microsoft.AspNetCore.All` Metapackage. Předpokládá se, že tyto balíčky jsou k dispozici v cílovém systému.

V případě, že je nainstalováno .NET Core SDK, je úložiště balíčků modulu runtime nainstalováno na hostiteli. Další instalační programy můžou poskytnout běhové úložiště balíčků, včetně instalace zip/tarballu .NET Core SDK, `apt-get`, Red Hat Yumu, hostitelského sady Windows serveru .NET Core a ručních instalací balíčků běhového prostředí.

Při nasazování aplikace [pro nasazení závislé na rozhraní (FDD)](index.md#framework-dependent-deployments-fdd) se ujistěte, že je v cílovém prostředí nainstalovaný .NET Core SDK. Pokud je aplikace nasazená do prostředí, které neobsahuje ASP.NET Core, můžete implicitní úložiště odhlásit zadáním **\<PublishWithAspNetCoreTargetManifest >** nastaveno na `false` v souboru projektu, jako v následujícím příkladu:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> Pro aplikace [s podporou nasazení (SCD)](index.md#self-contained-deployments-scd) se předpokládá, že cílový systém nutně neobsahuje požadované balíčky manifestu. Proto **\<PublishWithAspNetCoreTargetManifest >** pro aplikaci SCD nelze nastavit na `true`.

Pokud nasadíte aplikaci se závislostí manifestu, která je přítomna v nasazení (sestavení je k dispozici ve složce *bin* ), není úložiště balíčků modulu runtime *použito* na hostiteli pro toto sestavení. Sestavení složky *bin* se používá bez ohledu na jeho přítomnost v úložišti balíčků modulu runtime na hostiteli.

Verze závislosti uvedená v manifestu se musí shodovat s verzí závislosti v úložišti balíčků modulu runtime. Pokud se neshoduje s verzí mezi závislostí v cílovém manifestu a verzí, která existuje v úložišti balíčků modulu runtime a aplikace neobsahuje požadovanou verzi balíčku ve svém nasazení, aplikace se nepodaří spustit. Výjimkou je název cílového manifestu, který byl volán pro sestavení úložiště balíčků modulu runtime, což vám pomůže vyřešit neshodu.

Pokud je při publikování *oříznuto* nasazení, jsou z publikovaného výstupu zadrženy pouze konkrétní verze balíčků manifestů, které označíte. Aby bylo možné aplikaci spustit, musí být balíčky na zmíněných verzích přítomny na hostiteli.

## <a name="see-also"></a>Viz také

- [dotnet – publikování](../tools/dotnet-publish.md)
- [dotnet – úložiště](../tools/dotnet-store.md)
