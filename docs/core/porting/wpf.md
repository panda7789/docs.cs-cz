---
title: Portování aplikace WPF na .NET Core 3,0
description: Naučíte se, jak portovat .NET Framework Windows Presentation Foundation aplikace do .NET Core 3,0 pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 1528e578a978de38998b3f3f4b7beb72ff7422d4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117069"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>Postupy: Port desktopové aplikace WPF na .NET Core

Tento článek popisuje, jak přenést vaši desktopovou aplikaci založenou na Windows Presentation Foundation (WPF) z .NET Framework na .NET Core 3,0. Sada .NET Core 3,0 SDK obsahuje podporu pro aplikace WPF. WPF je stále rozhraním jenom pro Windows a běží jenom v systému Windows. V tomto příkladu se k vytvoření a správě projektu používá rozhraní příkazového řádku .NET Core SDK.

V tomto článku se k identifikaci typů souborů používaných k migraci používají různé názvy. Při migraci projektu budou soubory pojmenovány jinak, takže je bude možné navzájem narovnávat na ty, které jsou uvedeny níže:

| Soubor | Popis |
| ---- | ----------- |
| **MyApps.sln** | Název souboru řešení |
| **MyWPF.csproj** | Název .NET Frameworkho projektu WPF na port. |
| **MyWPFCore.csproj** | Název nového projektu .NET Core, který vytvoříte. |
| **MyAppCore.exe** | Spustitelný soubor aplikace WPF .NET Core |

>[!IMPORTANT]
>I když tento článek používá C# jako cílový jazyk, postup je stejný pro VB.NET, s tím rozdílem, že VB.NET používá soubory *. vbproj* a. *VB* namísto souborů *. csproj* a *. cs* v uvedeném pořadí.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro každou práci návrháře, kterou chcete provést.

  Nainstalujte následující úlohy sady Visual Studio:
  - Vývoj desktopových aplikací .NET
  - Vývoj pro různé platformy .NET

- Pracovní projekt WPF v řešení, které sestaví a spouští bez problémů.
- Nainstalujte nejnovější verzi [.NET Core 3,0](https://aka.ms/netcore3download) Preview.

>[!NOTE]
>**Visual Studio 2017** nepodporuje projekty .net Core 3,0. **Visual Studio 2019** podporuje projekty .net Core 3,0, ale má omezené podpory pro vizuální návrháře WPF .NET Core. Chcete-li použít plně podporovaný vizuální Návrhář, musíte mít ve svém řešení .NET Framework projekt WPF, který sdílí své soubory s projektem .NET Core.

### <a name="consider"></a>Byste

Při přenosu .NET Framework aplikace WPF existuje několik věcí, které je třeba vzít v úvahu.

01. Ověřte, že je vaše aplikace vhodným kandidátem na migraci.

    Pomocí [analyzátoru přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) určete, jestli se váš projekt migruje na .net Core 3,0. Pokud má váš projekt problémy s rozhraním .NET Core 3,0, analyzátor vám pomůže tyto problémy identifikovat.

01. Používáte jinou verzi WPF.

    Po vydání .NET Core 3,0 Preview 1 se WPF na GitHubu otevře jako zdroj. Kód pro .NET Core WPF je rozvětvení .NET Framework základu kódu WPF. Je možné, že existují nějaké rozdíly a vaše aplikace nebude portem.

01. [Sada Windows Compatibility Pack][compat-pack] vám může při migraci trvat.

    V rozhraní .NET Core 3,0 nejsou k dispozici některá rozhraní API, která jsou k dispozici v .NET Framework. [Sada Windows Compatibility Pack][compat-pack] přidává mnoho těchto rozhraní API a může pomáhat vaší aplikaci WPF bude kompatibilní s .NET Core.

01. Aktualizujte balíčky NuGet používané vaším projektem.

    Před migrací je vždycky vhodné použít nejnovější verze balíčků NuGet. Pokud vaše aplikace odkazuje na balíčky NuGet, aktualizujte je na nejnovější verzi. Ujistěte se, že vaše aplikace byla úspěšně vytvořena. Pokud při upgradu dojde k chybám balíčku, proveďte downgrade balíčku na nejnovější verzi, která nepřerušila váš kód.

01. Visual Studio 2019 zatím nepodporuje návrháře WPF pro .NET Core 3,0

    V současné době je nutné zachovat existující .NET Framework soubor projektu WPF, pokud chcete použít návrháře WPF ze sady Visual Studio.

## <a name="create-a-new-sdk-project"></a>Vytvořit nový projekt SDK

Nový projekt .NET Core 3,0, který vytvoříte, musí být v jiném adresáři než váš .NET Framework projekt. Pokud oba jsou ve stejném adresáři, můžete spustit v konfliktu se soubory, které jsou generovány v adresáři **obj** . V tomto příkladu vytvoříte v adresáři **SolutionFolder –** adresář s názvem **MyWPFAppCore** :

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

Dále musíte vytvořit projekt **MyWPFCore. csproj** v adresáři **MyWPFAppCore** . Tento soubor můžete vytvořit ručně pomocí textového editoru výběru. Vložte následující kód XML:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

Pokud nechcete vytvořit soubor projektu ručně, můžete použít aplikaci Visual Studio nebo .NET Core SDK k vygenerování projektu. Je však nutné odstranit všechny ostatní soubory vygenerované šablonou projektu s výjimkou souboru projektu. Chcete-li použít sadu SDK, spusťte následující příkaz z adresáře **SolutionFolder –** :

```dotnetcli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

Po vytvoření **MyWPFCore. csproj**by vaše adresářová struktura měla vypadat nějak takto:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

Projekt **MyWPFCore. csproj** budete chtít přidat do aplikace **MyApp. sln** pomocí sady Visual Studio nebo .NET Core CLI z adresáře **SolutionFolder –** :

```dotnetcli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Opravit generování informací o sestavení

Windows Presentation Foundation projekty, které byly vytvořeny pomocí .NET Framework obsahují `AssemblyInfo.cs` soubor, který obsahuje atributy sestavení, jako je například verze sestavení, která má být vygenerována. Projekty ve stylu sady SDK automaticky generují tyto informace na základě souboru projektu sady SDK. Pokud má oba typy "informace o sestavení", dojde ke konfliktu. Tento problém vyřešíte tak, že zakážete automatické generování, což vynutí `AssemblyInfo.cs` , aby projekt používal existující soubor.

Existují tři nastavení, která lze přidat do hlavního `<PropertyGroup>` uzlu. 

- **GenerateAssemblyInfo**\
Pokud nastavíte tuto vlastnost na `false`, nebudou vygenerovány atributy sestavení. Tím se vyhnete konfliktu se stávajícím `AssemblyInfo.cs` souborem z .NET Framework projektu.

- **Doplňk**\
Hodnota této vlastnosti je výstupní binární soubor vytvořený při kompilaci. Název nepotřebuje přidání rozšíření. Například použití `MyCoreApp` služby generuje `MyCoreApp.exe`.

- **RootNamespace**\
Výchozí obor názvů používaný vaším projektem. Tato hodnota by měla odpovídat výchozímu oboru názvů projektu .NET Framework.

Přidejte tyto tři prvky do `<PropertyGroup>` uzlu `MyWPFCore.csproj` v souboru:

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

## <a name="add-source-code"></a>Přidat zdrojový kód
Nyní projekt **MyWPFCore. csproj** nekompiluje žádný kód. Projekty .NET Core standardně do aktuálního adresáře a všech podřízených adresářů automaticky zahrnují veškerý zdrojový kód. Je nutné nakonfigurovat projekt tak, aby zahrnoval kód z .NET Framework projektu pomocí relativní cesty. Pokud váš .NET Framework projekt používal pro ikony a prostředky pro vaše Windows a ovládací prvky soubory **. resx** , budete je muset zahrnout. 

První `<ItemGroup>` uzel, který je třeba přidat do projektu, zahrnuje soubor **App. XAML** , který představuje spouštěcí konfiguraci a prostředky, které vaše aplikace používá. Soubor **App. XAML** má také doprovodný soubor **App.XAML.cs** , ale bude automaticky zahrnut do jiného `<ItemGroup>`.

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

Dále do svého projektu přidejte `<ItemGroup>` následující uzel. Každý příkaz zahrnuje vzor glob souboru, který obsahuje podřízené adresáře. Obsahuje zdrojový kód pro váš projekt, všechny soubory nastavení a všechny prostředky. Adresář **obj** je explicitně vyloučený.

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

Dále zahrňte jiný `<ItemGroup>` uzel, který `<Page>` obsahuje položku pro každý soubor **XAML** v projektu s výjimkou souboru **App. XAML** . Ty obsahují všechny systémy Windows, stránky a prostředky, které jsou ve formátu **XAML** . Zde nemůžete použít vzor glob a musíte přidat položku pro každý soubor a označit `<Generator>` použitou hodnotu.

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>Přidat balíčky NuGet

Přidejte každý balíček NuGet, na který odkazuje .NET Framework projekt, do projektu .NET Core. 

Nejpravděpodobnější .NET Framework aplikace WPF má soubor **Packages. config** , který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt. Můžete se podívat na tento seznam a určit, které balíčky NuGet se mají přidat do projektu .NET Core. Například pokud projekt .NET Framework odkazuje na `MahApps.Metro` balíček NuGet, přidejte ho do projektu pomocí sady Visual Studio. Odkaz na balíček můžete přidat také pomocí .NET Core CLI v adresáři **SolutionFolder –** :

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

Předchozí příkaz přidá následující odkaz NuGet do projektu **MyWPFCore. csproj** :

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Kompilace problémů

Pokud máte problémy s kompilací vašich projektů, můžete používat jenom některá rozhraní API jenom pro Windows, která jsou k dispozici v .NET Framework, ale nejsou dostupná v .NET Core. Do projektu se můžete pokusit přidat balíček NuGet [sady Windows Compatibility Pack][compat-pack] . Tento balíček se spouští jenom ve Windows a přidává asi 20 000 rozhraní API Windows do projektů .NET Core a .NET Standard.

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

Předchozí příkaz přidá následující do projektu **MyWPFCore. csproj** :

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>návrhář WPF

Jak je popsáno v tomto článku, Visual Studio 2019 podporuje pouze návrháře WPF v .NET Frameworkch projektech. Vytvořením souběžného projektu .NET Core můžete testovat projekt pomocí .NET Core při použití projektu .NET Framework k návrhu formulářů. Váš soubor řešení zahrnuje projekty .NET Framework i .NET Core. Přidejte a navrhněte formuláře a ovládací prvky v projektu .NET Framework a na základě vzorů glob souborů, které jsme přidali do projektů .NET Core, budou všechny nové nebo změněné soubory automaticky zahrnuty v projektech .NET Core.

Jakmile aplikace Visual Studio 2019 podporuje návrháře WPF, můžete zkopírovat nebo vložit obsah souboru projektu .NET Core do souboru projektu .NET Framework. Pak odstraňte vzory glob souborů přidané s `<Source>` položkami a. `<EmbeddedResource>` Opravte cesty pro všechny odkazy na projekt, které vaše aplikace používá. Tím se efektivně upgraduje .NET Framework projekt na projekt .NET Core.

## <a name="next-steps"></a>Další kroky

- Přečtěte si další informace o sadě [Windows Compatibility Pack][compat-pack].
- Podívejte se [na video o přenosu](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) .NET Frameworkho projektu WPF do .NET Core.

[compat-pack]: windows-compat-pack.md
