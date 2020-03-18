---
title: Port aplikace Windows Forms na jádro .NET Core
description: Naučí vás portovat aplikaci .NET Framework Windows Forms do .NET Core pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.openlocfilehash: dbd522851faa0a4fe435199914a034ee230d3455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116021"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>Jak portovat desktopovou aplikaci pro Windows Forms do jádra .NET Core

Tento článek popisuje, jak přenést desktopovou aplikaci založenou na formulářích Windows Forms z rozhraní .NET Framework na rozhraní .NET Core 3.0 nebo novější. Sada SDK .NET Core 3.0 obsahuje podporu aplikací windows forms. Windows Forms je stále pouze windows framework a běží pouze v systému Windows. Tento příklad používá rozhraní CLI sady .NET Core SDK k vytvoření a správě projektu.

V tomto článku se různé názvy používají k identifikaci typů souborů používaných pro migraci. Při migraci projektu budou soubory pojmenovány jinak, takže je mentálně přiřazuje k níže uvedeným:

| File | Popis |
| ---- | ----------- |
| **MyApps.sln** | Název souboru řešení. |
| **MyForms.csproj** | Název projektu .NET Framework Windows Forms na port. |
| **MyFormsCore.csproj** | Název nového projektu .NET Core, který vytvoříte. |
| **MyAppCore.exe** | Spustitelný soubor aplikace .NET Core Windows Forms. |

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro všechny návrháře práce, které chcete udělat.

  Nainstalujte následující úlohy sady Visual Studio:
  - Vývoj stolních počítačů .NET
  - Vývoj aplikací pro různé platformy pomocí rozhraní .NET Core

- Pracovní Windows Forms projektu v řešení, které se staví a běží bez problémů.
- Projekt kódovaný v c#.
- [.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 nebo novější.

> [!NOTE]
> **Visual Studio 2017** nepodporuje projekty .NET Core 3.0. **Visual Studio 2019** podporuje projekty .NET Core 3.0, ale ještě nepodporuje vizuální návrháře pro projekty .NET Core 3.0 Windows Forms. Chcete-li použít vizuální návrháře, musíte mít projekt .NET Windows Forms v řešení, které sdílí soubory formulářů s projektem .NET Core.

### <a name="consider"></a>Zvážit

Při přenosu aplikace .NET Framework Windows Forms je třeba zvážit několik věcí.

01. Zkontrolujte, zda je vaše aplikace dobrým kandidátem pro migraci.

    Pomocí [analyzátoru přenosové schopnosti rozhraní .NET určete,](../../standard/analyzers/portability-analyzer.md) zda bude projekt migrovat na rozhraní .NET Core 3.0. Pokud váš projekt má problémy s .NET Core 3.0, analyzátor vám pomůže identifikovat tyto problémy.

01. Používáte jinou verzi Windows Forms.

    Když byl vydán .NET Core 3.0 Preview 1, Windows Forms šel open source na GitHub. Kód pro .NET Core Windows Forms je rozpaky z codebase .NET Framework Windows Forms. Je možné, že existují určité rozdíly a vaše aplikace se nepřenese.

01. [Sada Kompatibilita systému Windows][compat-pack] vám může pomoci s migrací.

    Některá rozhraní API, která jsou k dispozici v rozhraní .NET Framework, nejsou k dispozici v rozhraní .NET Core 3.0. [Sada Windows Compatibility Pack][compat-pack] přidá mnoho z těchto rozhraní API a může pomoci vaší aplikaci Windows Forms stát se kompatibilní s .NET Core.

01. Aktualizujte balíčky NuGet používané vaším projektem.

    Je vždy vhodné použít nejnovější verze balíčků NuGet před jakoukoli migrací. Pokud vaše aplikace odkazuje na všechny balíčky NuGet, aktualizujte je na nejnovější verzi. Ujistěte se, že vaše aplikace úspěšně sestavení. Po upgradu, pokud existují nějaké chyby balíčku, downgrade balíček na nejnovější verzi, která nepřeruší váš kód.

01. Visual Studio 2019 ještě nepodporuje Návrhář e-uskutečně pro .NET Core 3.0

    V současné době je třeba zachovat existující soubor projektu .NET Framework Windows Forms, pokud chcete použít Návrhář e-aplikací Z aplikace Visual Studio.

## <a name="create-a-new-sdk-project"></a>Vytvoření nového projektu sady SDK

Nový projekt .NET Core 3.0, který vytvoříte, musí být v jiném adresáři než projekt rozhraní .NET Framework. Pokud jsou oba ve stejném adresáři, může dojít ke konfliktu se soubory, které jsou generovány v adresáři **obj.** V tomto příkladu vytvoříme adresář s názvem **MyFormsAppCore** v adresáři **SolutionFolder:**

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

Dále je třeba vytvořit projekt **MyFormsCore.csproj** v adresáři **MyFormsAppCore.** Tento soubor můžete vytvořit ručně pomocí textového editoru. Vložte do následujícího xml:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

Pokud nechcete vytvořit soubor projektu ručně, můžete ke generování projektu použít Visual Studio nebo .NET Core SDK. Je však nutné odstranit všechny ostatní soubory generované šablonou projektu s výjimkou souboru projektu. Chcete-li použít sadu SDK, spusťte z adresáře **SolutionFolder** následující příkaz:

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

Po vytvoření **souboru MyFormsCore.csproj**by měla adresářová struktura vypadat takto:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

Přidejte projekt **MyFormsCore.csproj** do **služby MyApps.sln** pomocí sady Visual Studio nebo rozhraní CLI jádra .NET z adresáře **SolutionFolder:**

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Oprava generování informací o sestavě

Projekty Windows Forms, které byly `AssemblyInfo.cs` vytvořeny pomocí rozhraní .NET Framework, obsahují soubor, který obsahuje atributy sestavení, jako je například verze sestavení, které má být generováno. Projekty ve stylu sady SDK automaticky generují tyto informace na základě souboru projektu sady SDK. S oběma typy "sestavení info" vytvoří konflikt. Vyřešte tento problém zakázáním automatického generování, `AssemblyInfo.cs` které vynutí, aby projekt používal existující soubor.

Existují tři nastavení, která `<PropertyGroup>` chcete přidat do hlavního uzlu.

- **Generovat informace o sestavení**\
Když nastavíte `false`tuto vlastnost , nebude generovat atributy sestavení. Tím se zabrání konfliktu `AssemblyInfo.cs` s existujícísoubor z projektu rozhraní .NET Framework.

- **Assemblyname**\
Hodnota této vlastnosti je výstupní binární vytvořené při kompilaci. Název nepotřebuje rozšíření, které k němu bylo přidáno. Například pomocí `MyCoreApp` produkuje `MyCoreApp.exe`.

- **Rootnamespace**\
Výchozí obor názvů používaný projektem. To by mělo odpovídat výchozí obor názvů projektu rozhraní .NET Framework.

Přidejte tyto tři `<PropertyGroup>` prvky `MyFormsCore.csproj` do uzlu v souboru:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>Přidání zdrojového kódu

Právě teď projekt **MyFormsCore.csproj** nekompiluje žádný kód. Ve výchozím nastavení projekty .NET Core automaticky zahrnují veškerý zdrojový kód v aktuálním adresáři a všechny podřízené adresáře. Projekt je nutné nakonfigurovat tak, aby zahrnoval kód z projektu rozhraní .NET Framework pomocí relativní cesty. Pokud váš projekt rozhraní .NET Framework používá soubory **.resx** pro ikony a prostředky pro formuláře, budete muset zahrnout i tyto.

Přidejte `<ItemGroup>` do projektu následující uzel. Každý příkaz obsahuje vzor glob souboru, který obsahuje podřízené adresáře.

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

Případně můžete vytvořit `<Compile>` položku `<EmbeddedResource>` nebo pro každý soubor v projektu rozhraní .NET Framework.

## <a name="add-nuget-packages"></a>Přidání balíčků NuGet

Přidejte každý balíček NuGet, na který odkazuje projekt rozhraní .NET Framework, do projektu .NET Core.

S největší pravděpodobností vaše aplikace .NET Framework Windows Forms má soubor **packages.config,** který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt. Můžete se podívat na tento seznam k určení, které balíčky NuGet přidat do projektu .NET Core. Například pokud projekt rozhraní .NET `MetroFramework`Framework `MetroFramework.Design`odkazuje `MetroFramework.Fonts` na balíčky , a NuGet, přidejte každý do projektu pomocí sady Visual Studio nebo rozhraní CLI jádra .NET z adresáře **SolutionFolder:**

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

Předchozí příkazy by přidat následující NuGet odkazy na projekt **MyFormsCore.csproj:**

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>Knihovny řízení portů

Pokud máte projekt knihovny Windows Forms Controls na port, pokyny jsou stejné jako portování projektu aplikace .NET Framework Windows Forms, s výjimkou několika nastavení. A místo kompilace do spustitelného souboru zkompilujete do knihovny. Rozdíl mezi spustitelný projekt a projekt knihovny, kromě cesty pro soubor globs, které obsahují zdrojový kód, je minimální.

Pomocí příkladu předchozího kroku umožňuje rozšířit projekty a soubory, se kterými pracujeme.

| File | Popis |
| ---- | ----------- |
| **MyApps.sln** | Název souboru řešení. |
| **MyControls.csproj** | Název projektu .NET Framework Windows Forms Controls na port. |
| **MyControlsCore.csproj** | Název nového projektu knihovny .NET Core, který vytvoříte. |
| **MyCoreControls.dll** | Knihovna .NET Core Windows Forms Controls. |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

Zvažte rozdíly mezi `MyControlsCore.csproj` projektem a `MyFormsCore.csproj` dříve vytvořeným projektem.

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyControlsCore</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

Zde je příklad toho, jak by vypadal soubor projektu knihovny .NET Core Windows Forms Controls:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>

    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>

</Project>
```

Jak můžete vidět, `<OutputType>` uzel byl odebrán, což výchozí kompilátor vytvořit knihovnu namísto spustitelný soubor. A `<AssemblyName>` `<RootNamespace>` byly změněny. Konkrétně `<RootNamespace>` by se měl shodovat s oborem názvů knihovny Ovládacíprvky systému Windows Forms, kterou portujete. A nakonec `<Compile>` byly `<EmbeddedResource>` uzly a byly upraveny tak, aby ukazovaly na složku knihovny ovládacích prvků windows forms, kterou portujete.

Dále v hlavním projektu .NET Core **MyFormsCore.csproj** přidejte odkaz na novou knihovnu .NET Core Windows Forms Control. Přidejte odkaz s visual studio nebo rozhraní cli jádra .NET z adresáře **SolutionFolder:**

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

Předchozí příkaz přidá do projektu **MyFormsCore.csproj** následující:

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a>Problémy s kompilací

Pokud máte problémy s kompilací projektů, je možné, že používáte některá rozhraní API pouze pro systém Windows, která jsou k dispozici v rozhraní .NET Framework, ale nejsou k dispozici v jádru .NET Core. Můžete zkusit přidat balíček [Windows Compatibility Pack][compat-pack] NuGet do projektu. Tento balíček běží pouze v systému Windows a přidá přibližně 20 000 rozhraní API systému Windows do projektů .NET Core a .NET Standard.

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

Předchozí příkaz přidá do projektu **MyFormsCore.csproj** následující:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Návrhář formulářů Windows

Jak je podrobně popsáno v tomto článku Visual Studio 2019 podporuje pouze Návrhář formulářů v projektech rozhraní .NET Framework. Vytvořením projektu .NET Core vedle sebe můžete projekt otestovat pomocí .NET Core při použití projektu rozhraní .NET Framework k navrhování formulářů. Soubor řešení obsahuje rozhraní .NET Framework i projekty .NET Core. Přidejte a navrhněte formuláře a ovládací prvky v projektu rozhraní .NET Framework a na základě vzorů glob souborů, které jsme přidali do projektů .NET Core, budou všechny nové nebo změněné soubory automaticky zahrnuty do projektů .NET Core.

Jakmile Visual Studio 2019 podporuje Návrhář e-Windows Forms, můžete zkopírovat a vložit obsah souboru projektu .NET Core do souboru projektu rozhraní .NET Framework. Pak odstraňte vzorky glob `<Source>` souboru přidané s položkami a. `<EmbeddedResource>` Opravte cesty k libovolnému odkazu na projekt, který vaše aplikace používá. To efektivně upgraduje projekt rozhraní .NET Framework na projekt .NET Core.

## <a name="next-steps"></a>Další kroky

- Informace o [rozdělení změn z rozhraní .NET Framework na .NET Core](../compatibility/fx-core.md).
- Přečtěte si další informace o [nástroji Windows Compatibility Pack][compat-pack].
- Podívejte se [na video o přenesení](https://www.youtube.com/watch?v=upVQEUc_KwU) projektu .NET Framework Windows Forms do .NET Core.

[compat-pack]: windows-compat-pack.md
