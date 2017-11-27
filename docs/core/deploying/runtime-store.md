---
title: "Úložiště balíčku modulu runtime"
description: "Toto téma vysvětluje runtime balíček úložiště a cílový manifesty používané .NET Core."
keywords: "Rozhraní .NET, .NET core dotnet úložiště, úložiště balíček modulu runtime"
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 9521d8b4-25fc-412b-a65b-4c975ebf6bfd
ms.openlocfilehash: 607f8259fa6d8488a7fccf3c7d90b6cf40d5f237
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-package-store"></a>Úložiště balíčku modulu runtime

Od verze rozhraní .NET Core 2.0, je možné balíček a nasazení aplikací proti se známou sadou balíčky, které existují v cílovém prostředí. Výhody jsou rychlejší nasazení, nižší využití místa na disku a spuštění lepší výkon v některých případech.

Tato funkce je implementovaná jako *úložiště balíčku runtime*, tedy adresáře na disku, kde jsou uloženy balíčky (obvykle na */usr/local/share/dotnet/store* v systému macOS/Linux a *C: / Program soubory nebo dotnet/úložiště* v systému Windows). V tomto adresáři neexistují podadresáře pro architektury a [cílové rozhraní](../../standard/frameworks.md). Rozložení souboru je podobným způsobem, který [NuGet prostředky jsou nastíněny na disku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):

\dotnet   
&nbsp;&nbsp;\store   
&nbsp;&nbsp;&nbsp;&nbsp;\x64   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   
&nbsp;&nbsp;&nbsp;&nbsp;\x86   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   

A *cíl manifest* soubor obsahuje seznam balíčků v úložišti balíček modulu runtime. Vývojáři mohou být určeny tento manifest při publikování své aplikace. Cíl manifest se většinou poskytuje vlastníkem cílové produkčního prostředí.

## <a name="preparing-a-runtime-environment"></a>Příprava prostředí runtime

Správce běhového prostředí můžete optimalizovat aplikace pro rychlejší nasazení a nižší využití místa na disku podle budovy úložiště balíčku runtime a odpovídající manifest cíl.

Prvním krokem je vytvoření *manifestu balíčku úložiště* , obsahuje seznam balíčků, které tvoří úložišti balíček modulu runtime. Tento formát souboru není kompatibilní s formátem souboru projektu (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Příklad**

Následující příklad manifest balíčku úložiště (*packages.csproj*) se používá k přidání [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) a [ `Moq` ](https://www.nuget.org/packages/moq/) k úložišti balíček modulu runtime:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Zřízení úložiště balíčku runtime spuštěním `dotnet store` s manifestu balíčku úložiště, modulu runtime a framework:

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Příklad**

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Můžete předat více cest manifestu cílové úložiště balíčku do jednoho [ `dotnet store` ](../tools/dotnet-store.md) příkaz opakováním možnost a cestu v příkazu.

Ve výchozím nastavení, je výstup příkazu balíček úložiště v nabídce *.dotnet/úložiště* podadresáři profilu uživatele. Můžete zadat jiné umístění pomocí `--output <OUTPUT_DIRECTORY>` možnost. Kořenový adresář úložiště obsahuje cílový manifestu *artifact.xml* souboru. Tento soubor může být k dispozici ke stažení a použije autory aplikace, které chcete cílit toto úložiště při publikování.

**Příklad**

Následující *artifact.xml* soubor je vytvořen po spuštění předchozí příklad. Všimněte si, že [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) je závislost `Moq`, takže se má automaticky zahrnuty a zobrazí se v *artifacts.xml* souboru manifestu.

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publikování aplikace proti cílové manifestu

Pokud máte soubor manifestu cíl na disku, musíte zadat cestu k souboru, při publikování aplikace pomocí [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz:

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Příklad**

```console
dotnet publish --manifest manifest.xml
```

Výsledný publikované aplikace můžete nasadit pro prostředí, které má balíčky, které jsou popsané v manifestu cíl. Tak neučiníte způsobuje selhání spuštění aplikace.

Zadejte více manifesty cíl při publikování aplikace opakováním možnost a cestu (například `--manifest manifest1.xml --manifest manifest2.xml`). Pokud tak učiníte, aplikace je oříznut pro sjednocení balíčky zadané v manifestu soubory cíl zadaný pro příkaz.

## <a name="specifying-target-manifests-in-the-project-file"></a>Zadání manifesty cíl v souboru projektu

Alternativu k určení cílového manifesty s [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz je zadávat v souboru projektu jako středníky oddělený seznam cest v rámci  **\<TargetManifestFiles >** značky.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Zadejte cíl manifesty v souboru projektu pouze v případě, že cílové prostředí pro aplikaci je dobře známé, například pro projekty .NET Core. Tato akce není případ projekty open source. Uživatelé open-source projekt je obvykle nasadit do různých produkčního prostředí. Tyto provozní prostředí obvykle mají různé sady balíčky předem nainstalované. Nelze provádět předpoklady o manifest cíl v těchto prostředích, měli byste použít `--manifest` možnost [ `dotnet publish` ](../tools/dotnet-publish.md).

## <a name="aspnet-core-implicit-store"></a>Implicitní úložiště ASP.NET Core

Funkce úložiště balíčku runtime používají implicitně aplikace ASP.NET Core při nasazení aplikace jako [nasazení závislé na framework (disketové jednotky)](index.md#framework-dependent-deployments-fdd) aplikace. Cíle v [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) zahrnují manifesty odkazující na úložišti implicitní balíček v cílovém systému. Kromě toho jakékoli aplikaci disketové jednotky, která závisí na `Microsoft.AspNetCore.All` výsledky v publikované aplikaci, která obsahuje jenom aplikace a její prostředky a není balíčky uvedené v balíčku `Microsoft.AspNetCore.All` metapackage. Předpokládá se, zda tyto balíčky jsou k dispozici v cílovém systému.

Úložiště balíčku runtime je nainstalován na hostiteli, při instalaci .NET Core SDK. Další instalační programy může poskytnout úložišti balíček modulu runtime, včetně Zip nebo tarball instalace rozhraní .NET Core SDK, `apt-get`, Red Hat Yum, sady hostování v rozhraní .NET Core systému Windows Server a instalací balíčku úložiště ruční runtime.

Při nasazování [nasazení závislé na framework (disketové jednotky)](index.md#framework-dependent-deployments-fdd) aplikace, ujistěte se, že cílové prostředí má .NET Core SDK nainstalovat. Pokud je aplikace nasazená na prostředí, které neobsahuje ASP.NET Core, můžete zamítnutí úložišti implicitní zadáním  **\<PublishWithAspNetCoreTargetManifest >** nastavena na `false` v souboru projektu jako v v následujícím příkladu:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE] 
> Pro [samostatná nasazení (SCD)](index.md#self-contained-deployments-scd) aplikace, se předpokládá, že cílový systém neobsahuje nutně požadované balíčky manifestu. Proto  **\<PublishWithAspNetCoreTargetManifest >** nelze nastavit na `true` SCD aplikace.

Pokud nasazujete aplikaci s manifestu závislost, která je k dispozici v nasazení (sestavení se nachází ve *bin* složky), úložiště balíčku runtime *nepoužívá* na hostiteli pro toto sestavení. *Bin* sestavení složky se používá bez ohledu na jeho přítomnosti v úložišti runtime balíčku na hostiteli.

Verze závislosti uvedené v manifestu musí shodovat s verzí závislosti v úložišti balíček modulu runtime. Pokud máte Neshoda verzí mezi závislostí v manifestu cíl a verzi, která existuje v úložišti balíček modulu runtime a aplikaci neobsahuje požadovaná verze balíčku v jeho nasazení, aplikace se nespustí. Výjimka obsahuje název cílové manifestu, který volá úložiště balíčku sestavení modulu runtime, který vám pomůže vyřešit neshody.

Po nasazení *oříznut* při publikování, jsou pouze konkrétní verze manifestu balíčky, které jste uvedli vyřazeno z publikovaných výstup. Balíčky na uvedené verze musí být přítomen na hostiteli aplikace spustit.

## <a name="see-also"></a>Viz také
 [DotNet-publikování](../tools/dotnet-publish.md)  
 [úložiště DotNet.](../tools/dotnet-store.md)  
