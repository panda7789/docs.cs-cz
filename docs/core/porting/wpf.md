---
title: Port aplikace WPF až po .NET Core 3.0
description: Vás naučí, jak přenést aplikaci rozhraní .NET Framework Windows Presentation Foundation pro .NET Core 3.0 pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 5c7e3aca0a473abb831693244d1b194985f2ef7f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342203"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>Postupy: Port desktopovou aplikaci WPF až po .NET Core

Tento článek popisuje, jak přenést na základě Windows Presentation Foundation (WPF) aplikaci klasické pracovní plochy z rozhraní .NET Framework do .NET Core 3.0. .NET Core 3.0 SDK obsahuje podporu pro aplikace WPF. WPF je stále rozhraní jen pro Windows a pouze běží na Windows. Tento příklad používá rozhraní příkazového řádku .NET Core SDK k vytváření a správě vašeho projektu.

V tomto článku najdete různé názvy umožňují určit typy souborů se používá pro migraci. Při migraci vašeho projektu, soubory budou pojmenované jinak, takže duševně je přizpůsobit uvedené níže:

| Soubor | Popis |
| ---- | ----------- |
| **MyApps.sln** | Název souboru řešení. |
| **MyWPF.csproj** | Název projektu WPF rozhraní .NET Framework na port. |
| **MyWPFCore.csproj** | Název nového projektu .NET Core, který vytvoříte. |
| **MyAppCore.exe** | Spustitelný soubor aplikace .NET Core WPF. |

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro jakékoli návrháře práce, které chcete provést.

  Instalace následujících úlohách sady Visual Studio:
  - Vývoj desktopových aplikací .NET
  - Vývoj pro různé platformy .NET

- Projekt WPF práci v řešení, které vytvoří a spustí bez problému.
- Váš projekt musí být zakódované v C#. 
- Nainstalujte nejnovější [.NET Core 3.0](https://aka.ms/netcore3download) ve verzi preview.

>[!NOTE]
>**Visual Studio 2017** nepodporuje projekty .NET Core 3.0. **Visual Studio 2019** podporuje projekty .NET Core 3.0, ale zatím nepodporuje vizuálního návrháře pro projekty .NET Core 3.0 WPF. Do vizuálního návrháře použít, musí mít projekt .NET WPF ve vašem řešení, která sdílí soubory s projektem .NET Core.

### <a name="consider"></a>Vezměte v úvahu

Při přenesení aplikace rozhraní .NET Framework WPF, existuje několik věcí, které musíte zvážit.

01. Zkontrolujte, že vaše aplikace je vhodným kandidátem pro migraci.

    Použití [.NET Portability Analyzeru](../../standard/analyzers/portability-analyzer.md) chcete ověřit, jestli váš projekt bude migrovat na rozhraní .NET Core 3.0. Pokud váš projekt obsahuje problémy s .NET Core 3.0, analyzátor vám pomůže určit tyto problémy.

01. Používáte jinou verzi WPF.

    Pokud byla vydána .NET Core 3.0 ve verzi Preview 1, WPF se nepovedlo open source na Githubu. Kód pro .NET Core WPF je základ kódu rozhraní .NET Framework WPF. Je možné, existují určité rozdíly a vaše aplikace nebude portu.

01. [Windows Compatibility Pack] [ compat-pack] můžete migrovat.

    Některá rozhraní API, které jsou k dispozici v rozhraní .NET Framework nejsou k dispozici v rozhraní .NET Core 3.0. [Windows Compatibility Pack] [ compat-pack] přidá mnohé z těchto rozhraní API a může pomoct vaší aplikace WPF, budou kompatibilní s .NET Core.

01. Aktualizujte balíčky NuGet používané vaším projektem.

    Je vždy vhodné použít nejnovější verzi balíčků NuGet před nějaká migrace. Pokud aplikace odkazuje na všechny balíčky NuGet, můžete je aktualizujte na nejnovější verzi. Zajistěte, aby že vaše aplikace sestavena úspěšně. Po upgradu, pokud nejsou žádné chyby balíčku, provést downgrade balíčku na nejnovější verzi, která nedojde k narušení kódu.

01. Visual Studio 2019 zatím nepodporuje WPF Designer pro .NET Core 3.0

    V současné době je potřeba nechat existující soubor projektu WPF rozhraní .NET Framework, pokud chcete použít Návrhář WPF v sadě Visual Studio.

## <a name="create-a-new-sdk-project"></a>Vytvořte nový projekt sady SDK

Nový projekt .NET Core 3.0, které vytvoříte, musí být v jiném adresáři z rozhraní .NET Framework projektu. Pokud jsou oba ve stejném adresáři, můžete jej spustit do je v konfliktu se soubory, které jsou generovány v **obj** adresáře. V tomto příkladu vytvoříte adresář s názvem **MyWPFAppCore** v **SolutionFolder** adresáře:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

V dalším kroku je potřeba vytvořit **MyWPFCore.csproj** projekt **MyWPFAppCore** adresáře. Můžete tento soubor můžete vytvořit ručně pomocí text editoru. Vložte následující kód XML:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

Pokud nechcete vytvořit soubor projektu ručně, můžete použít ke generování projektu sady Visual Studio nebo .NET Core SDK. Nicméně je nutné odstranit všechny ostatní soubory vygenerovaná šablona projektu s výjimkou souboru projektu. Použití sady SDK, spusťte následující příkaz z **SolutionFolder** adresáře:

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

Po vytvoření **MyWPFCore.csproj**, strukturu by měl vypadat nějak takto:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

Bude potřeba přidat **MyWPFCore.csproj** projekt k **MyApps.sln** sadou Visual Studio nebo rozhraní příkazového řádku .NET Core z **SolutionFolder** adresáře:

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Oprava generování informací o sestavení

Windows Presentation Foundation projekty, které byly vytvořeny pomocí rozhraní .NET Framework zahrnují `AssemblyInfo.cs` soubor, který obsahuje sestavení atributům, jako je verze sestavení, které má být vygenerována. Projekty založenými na sadě SDK automaticky vygenerovat tyto informace vám na základě souboru projektu sadu SDK. Oba typy "informace o sestavení" způsobí konflikt. Tento problém vyřešit tím, že zakážete automatické generování, která vynutí projekt, který používá vaše existující `AssemblyInfo.cs` souboru.

Existují tři nastavení, chcete-li přidat hlavní `<PropertyGroup>` uzlu. 

- **GenerateAssemblyInfo**\
Pokud nastavíte tuto vlastnost na `false`, nevygeneruje atributů sestavení. Tím předejdete konfliktu s existujícím `AssemblyInfo.cs` soubor z rozhraní .NET Framework projektu.

- **AssemblyName**\
Hodnota této vlastnosti je binární výstup vytvořený při kompilaci. Název nemusí rozšíření do ní přidá. Například použití `MyCoreApp` vytváří `MyCoreApp.exe`.

- **RootNamespace**\
Výchozí obor názvů použitou vaším projektem. Ten by měl odpovídat výchozí obor názvů rozhraní .NET Framework projektu.

Přidejte tyto tři prvky, aby `<PropertyGroup>` uzlu `MyWPFCore.csproj` souboru:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>Přidejte zdrojový kód
Právě teď **MyWPFCore.csproj** projekt nebude kompilovat žádný kód. Ve výchozím nastavení projekty .NET Core automaticky zahrnout všechny zdrojového kódu v aktuálním adresáři a všechny podřízené adresáře. Je nutné nakonfigurovat projekt tak, aby zahrnout kód z rozhraní .NET Framework projektu pomocí relativní cesty. Pokud rozhraní .NET Framework projekt používá **RESX** soubory ikon a materiály pro windows a ovládací prvky, budete muset zahrnout ty příliš. 

První `<ItemGroup>` obsahuje uzel, je třeba přidat do projektu **App.xaml** soubor, který představuje spuštění config a prostředky aplikace používá. **App.xaml** soubor má také je v doprovodné **App.xaml.cs** soubor, ale budou automaticky zahrnuty v jiné `<ItemGroup>`.

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

V dalším kroku přidejte následující `<ItemGroup>` uzlu do projektu. Každý výpis obsahuje vzor glob souboru, který obsahuje podadresáře. Obsahuje zdrojový kód pro váš projekt, všechny soubory nastavení a všechny prostředky. **Obj** adresář je explicitně vyloučeny.

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

V dalším kroku obsahovat jiné `<ItemGroup>` uzel, který obsahuje `<Page>` záznam pro každý **xaml** soubor v projektu s výjimkou **App.xaml** souboru. Ty obsahují všechny windows, stránek a prostředky, které jsou v **xaml** formátu. Nelze použít model glob tady a musíte přidat záznam pro každý soubor a označení `<Generator>` použít.

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>Přidání balíčků NuGet

Přidejte každý balíček NuGet rozhraní .NET Framework projektu do projektu .NET Core. 

Pravděpodobně má vaše aplikace rozhraní .NET Framework WPF **souboru packages.config** soubor, který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt. Můžete si prohlédnout tento seznam a určit, které balíčky NuGet pro přidání do projektu .NET Core. Například, pokud rozhraní .NET Framework projekt odkazuje `MahApps.Metro` NuGet balíček, přidejte do projektu pomocí sady Visual Studio. Můžete také přidat odkaz na balíček pomocí rozhraní příkazového řádku .NET Core z **SolutionFolder** adresáře:

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

Předchozí příkaz přidejte následující odkaz NuGet na **MyWPFCore.csproj** projektu:

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Problémy kompilace

Pokud máte problémy sestavování vašich projektů, může pomocí některé API jen pro Windows, které jsou k dispozici v rozhraní .NET Framework, ale není k dispozici v .NET Core. Můžete zkusit přidat [Windows Compatibility Pack] [ compat-pack] do svého projektu balíček NuGet. Tento balíček pouze běží na Windows a přidá přibližně 20 000 rozhraní Windows API pro projekty .NET Core a .NET Standard.

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

Předchozí příkaz přidá následující **MyWPFCore.csproj** projektu:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>návrhář WPF

Jak je uvedeno v tomto článku podporuje Visual Studio 2019 Návrhář WPF pouze v projektech .NET Framework. Tím, že vytvoříte projekt .NET Core vedle sebe, můžete otestovat projekt pomocí .NET Core při použití rozhraní .NET Framework projektu pro návrh formulářů. Soubor řešení obsahuje projekty rozhraní .NET Framework a .NET Core. Přidat a návrh formulářů a ovládacích prvků v rozhraní .NET Framework projektu a na základě na vzory souborů glob jsme přidali do projektů .NET Core, všechny nové nebo změněné soubory se automaticky zahrnou v projektech .NET Core.

Jakmile Visual Studio 2019 podporuje návrháře WPF, můžete zkopírovat a vložit obsah souboru projektu .NET Core do souboru projektu rozhraní .NET Framework. Odstraňte glob vzory souborů, přidá se `<Source>` a `<EmbeddedResource>` položky. Vyřešte cest pro všechny odkazy projektu používají ve vaší aplikaci. To efektivně provede upgrade rozhraní .NET Framework projektu do projektu .NET Core.
 
## <a name="next-steps"></a>Další kroky

* Další informace najdete [Windows Compatibility Pack][compat-pack].
* Sledování [videa na přenos](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) WPF rozhraní .NET Framework projektu .NET Core.

[compat-pack]: windows-compat-pack.md
