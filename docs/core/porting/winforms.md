---
title: Port model Windows Forms aplikace do .NET Core 3,0
description: Naučíte se, jak portovat .NET Framework model Windows Forms aplikace do .NET Core 3,0 pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: 64920f1d226fcc8265d0be252d4751f2ba278cc1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973281"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>Postup při portování model Windows Forms desktopové aplikace do .NET Core

Tento článek popisuje, jak přenést vaši desktopovou aplikaci založenou na model Windows Forms z .NET Framework na .NET Core 3,0. Sada .NET Core 3,0 SDK obsahuje podporu pro model Windows Forms aplikace. Model Windows Forms je prostředí jenom pro Windows a běží jenom v systému Windows. V tomto příkladu se k vytvoření a správě projektu používá rozhraní příkazového řádku .NET Core SDK.

V tomto článku se k identifikaci typů souborů používaných k migraci používají různé názvy. Při migraci projektu budou soubory pojmenovány jinak, takže je bude možné navzájem narovnávat na ty, které jsou uvedeny níže:

| Soubor | Popis |
| ---- | ----------- |
| **MyApp. sln** | Název souboru řešení |
| **MyForms. csproj** | Název projektu .NET Framework model Windows Forms na port. |
| **MyFormsCore. csproj** | Název nového projektu .NET Core, který vytvoříte. |
| **MyAppCore. exe** | Spustitelný soubor aplikace model Windows Forms .NET Core. |

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro každou práci návrháře, kterou chcete provést.

  Nainstalujte následující úlohy sady Visual Studio:
  - Vývoj pro desktopy .NET
  - Vývoj pro různé platformy .NET

- Pracovní model Windows Forms projekt v řešení, které sestaví a spouští bez problémů.
- Projekt musí být kódován v C#. 
- Nainstalujte nejnovější verzi [.NET Core 3,0](https://aka.ms/netcore3download) Preview.

>[!NOTE]
>**Visual Studio 2017** nepodporuje projekty .net Core 3,0. **Visual Studio 2019** podporuje projekty .net Core 3,0, ale ještě nepodporuje Visual Designer pro .net core 3,0 model Windows Forms projekty. Chcete-li používat vizuálního návrháře, musíte mít ve svém řešení projekt .NET model Windows Forms, který sdílí soubory formulářů s projektem .NET Core.

### <a name="consider"></a>Byste

Při přenosu .NET Framework model Windows Forms aplikace existuje několik věcí, které je potřeba vzít v úvahu.

01. Ověřte, že je vaše aplikace vhodným kandidátem na migraci.

    Pomocí [analyzátoru přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) určete, jestli se váš projekt migruje na .net Core 3,0. Pokud má váš projekt problémy s rozhraním .NET Core 3,0, analyzátor vám pomůže tyto problémy identifikovat.

01. Používáte jinou verzi model Windows Forms.

    Po vydání .NET Core 3,0 Preview 1 model Windows Forms otevřít zdroj na GitHubu. Kód pro .NET Core model Windows Forms je rozvětvení .NET Framework model Windows Forms základu kódu. Je možné, že existují nějaké rozdíly a vaše aplikace nebude portem.

01. [Sada Windows Compatibility Pack][compat-pack] vám může při migraci trvat.

    V rozhraní .NET Core 3,0 nejsou k dispozici některá rozhraní API, která jsou k dispozici v .NET Framework. [Sada Windows Compatibility Pack][compat-pack] přidává mnoho z těchto rozhraní API a může pomáhat s tím, že vaše aplikace model Windows Forms bude kompatibilní s .NET Core.

01. Aktualizujte balíčky NuGet používané vaším projektem.

    Před migrací je vždycky vhodné použít nejnovější verze balíčků NuGet. Pokud vaše aplikace odkazuje na balíčky NuGet, aktualizujte je na nejnovější verzi. Ujistěte se, že vaše aplikace byla úspěšně vytvořena. Pokud při upgradu dojde k chybám balíčku, proveďte downgrade balíčku na nejnovější verzi, která nepřerušila váš kód.

01. Visual Studio 2019 zatím nepodporuje Návrháře formulářů pro .NET Core 3,0

    V současné době je nutné zachovat existující soubor projektu .NET Framework model Windows Forms, pokud chcete použít Návrháře formulářů ze sady Visual Studio.

## <a name="create-a-new-sdk-project"></a>Vytvořit nový projekt SDK

Nový projekt .NET Core 3,0, který vytvoříte, musí být v jiném adresáři než váš .NET Framework projekt. Pokud oba jsou ve stejném adresáři, můžete spustit v konfliktu se soubory, které jsou generovány v adresáři **obj** . V tomto příkladu vytvoříme v adresáři **SolutionFolder –** adresář s názvem **MyFormsAppCore** :

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

Dále musíte vytvořit projekt **MyFormsCore. csproj** v adresáři **MyFormsAppCore** . Tento soubor můžete vytvořit ručně pomocí textového editoru výběru. Vložte následující kód XML:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

Pokud nechcete vytvořit soubor projektu ručně, můžete použít aplikaci Visual Studio nebo .NET Core SDK k vygenerování projektu. Je však nutné odstranit všechny ostatní soubory vygenerované šablonou projektu s výjimkou souboru projektu. Chcete-li použít sadu SDK, spusťte následující příkaz z adresáře **SolutionFolder –** :

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

Po vytvoření **MyFormsCore. csproj**by vaše adresářová struktura měla vypadat nějak takto:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

Projekt **MyFormsCore. csproj** budete chtít přidat do aplikace **MyApp. sln** pomocí sady Visual Studio nebo .NET Core CLI z adresáře **SolutionFolder –** :

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Opravit generování informací o sestavení

Model Windows Forms projekty, které byly vytvořeny pomocí .NET Framework obsahují `AssemblyInfo.cs` soubor, který obsahuje atributy sestavení, jako je například verze sestavení, která má být vygenerována. Projekty ve stylu sady SDK automaticky generují tyto informace na základě souboru projektu sady SDK. Pokud má oba typy "informace o sestavení", dojde ke konfliktu. Tento problém vyřešíte tak, že zakážete automatickou generaci, což vynutí, aby projekt používal existující `AssemblyInfo.cs` soubor.

Existují tři nastavení, která lze přidat do hlavního uzlu `<PropertyGroup>`. 

- **GenerateAssemblyInfo**\
Když nastavíte tuto vlastnost na `false`, negenerují se atributy sestavení. Tím se vyhnete konfliktu s existujícím `AssemblyInfo.cs`m souboru z projektu .NET Framework.

- **AssemblyName**\
Hodnota této vlastnosti je výstupní binární soubor vytvořený při kompilaci. Název nepotřebuje přidání rozšíření. Například použití `MyCoreApp` generuje `MyCoreApp.exe`.

- **RootNamespace**\
Výchozí obor názvů používaný vaším projektem. Tato hodnota by měla odpovídat výchozímu oboru názvů projektu .NET Framework.

Přidejte tyto tři prvky do uzlu `<PropertyGroup>` v souboru `MyFormsCore.csproj`:

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

## <a name="add-source-code"></a>Přidat zdrojový kód

Nyní projekt **MyFormsCore. csproj** nekompiluje žádný kód. Projekty .NET Core standardně do aktuálního adresáře a všech podřízených adresářů automaticky zahrnují veškerý zdrojový kód. Je nutné nakonfigurovat projekt tak, aby zahrnoval kód z .NET Framework projektu pomocí relativní cesty. Pokud váš .NET Framework projekt používal soubory **. resx** pro ikony a prostředky pro vaše formuláře, budete je muset zahrnout. 

Do projektu přidejte následující `<ItemGroup>` uzel. Každý příkaz zahrnuje vzor glob souboru, který obsahuje podřízené adresáře.

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

Alternativně můžete vytvořit `<Compile>` nebo `<EmbeddedResource>` záznam pro každý soubor v projektu .NET Framework.

## <a name="add-nuget-packages"></a>Přidat balíčky NuGet

Přidejte každý balíček NuGet, na který odkazuje .NET Framework projekt, do projektu .NET Core. 

Pravděpodobně vaše aplikace .NET Framework model Windows Forms má soubor **Packages. config** , který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt. Můžete se podívat na tento seznam a určit, které balíčky NuGet se mají přidat do projektu .NET Core. Pokud například projekt .NET Framework odkazoval na balíčky NuGet `MetroFramework`, `MetroFramework.Design`a `MetroFramework.Fonts`, přidejte do projektu každý z nich pomocí sady Visual Studio nebo .NET Core CLI z adresáře **SolutionFolder –** :

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

Předchozí příkazy by přidaly následující odkazy NuGet do projektu **MyFormsCore. csproj** :

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>Knihovny ovládacích prvků portů

Pokud máte projekt knihovny ovládacích prvků model Windows Forms pro port, směry jsou stejné jako při přenosu .NET Framework projektu model Windows Forms aplikace s výjimkou několika nastavení. A namísto kompilování do spustitelného souboru, kompilujete do knihovny. Rozdíl mezi spustitelným projektem a projektem knihovny, kromě cest k souboru globy, který obsahuje váš zdrojový kód, je minimální.

Pomocí příkladu předchozího kroku umožníte rozbalení projektů a souborů, se kterými pracujete.

| Soubor | Popis |
| ---- | ----------- |
| **MyApp. sln** | Název souboru řešení |
| **MyControls. csproj** | Název .NET Framework model Windows Forms řídí projekt na port. |
| **MyControlsCore. csproj** | Název nového projektu knihovny .NET Core, který vytvoříte. |
| **MyCoreControls. dll** | Knihovna ovládacích prvků model Windows Forms .NET Core |

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

Zvažte rozdíly mezi `MyControlsCore.csproj` projektu a dříve vytvořeným projektem `MyFormsCore.csproj`.

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

Tady je příklad toho, co by soubor projektu knihovny ovládacích prvků model Windows Forms .NET Core vypadal jako:

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

Jak vidíte, uzel `<OutputType>` byl odebrán, což nastaví výchozí kompilátor k vytvoření knihovny namísto spustitelného souboru. `<AssemblyName>` a `<RootNamespace>` se změnily. Konkrétně `<RootNamespace>` by měl odpovídat oboru názvů knihovny ovládacích prvků model Windows Forms, kterou portuje. A konečně `<Compile>` a `<EmbeddedResource>` uzlů byly upraveny tak, aby odkazovaly na složku v knihovně ovládacích prvků model Windows Forms Controls, kterou předáváte.

Dále v hlavním projektu .NET Core **MyFormsCore. csproj** přidejte odkaz na novou knihovnu ovládacích prvků .net Core model Windows Forms. Přidejte odkaz buď pomocí sady Visual Studio, nebo .NET Core CLI z adresáře **SolutionFolder –** :

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

Předchozí příkaz přidá následující do projektu **MyFormsCore. csproj** :

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Kompilace problémů

Pokud máte problémy s kompilací vašich projektů, můžete používat jenom některá rozhraní API jenom pro Windows, která jsou k dispozici v .NET Framework, ale nejsou dostupná v .NET Core. Do projektu se můžete pokusit přidat balíček NuGet [sady Windows Compatibility Pack][compat-pack] . Tento balíček se spouští jenom ve Windows a přidává asi 20 000 rozhraní API Windows do projektů .NET Core a .NET Standard.

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

Předchozí příkaz přidá následující do projektu **MyFormsCore. csproj** :

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Návrhář formulářů Windows

Jak je popsáno v tomto článku, Visual Studio 2019 podporuje pouze Návrháře formulářů v .NET Frameworkch projektech. Vytvořením souběžného projektu .NET Core můžete testovat projekt pomocí .NET Core při použití projektu .NET Framework k návrhu formulářů. Váš soubor řešení zahrnuje projekty .NET Framework i .NET Core. Přidejte a navrhněte formuláře a ovládací prvky v projektu .NET Framework a na základě vzorů glob souborů, které jsme přidali do projektů .NET Core, budou všechny nové nebo změněné soubory automaticky zahrnuty v projektech .NET Core.

Jakmile aplikace Visual Studio 2019 podporuje Návrhář formulářů, můžete zkopírovat nebo vložit obsah souboru projektu .NET Core do souboru projektu .NET Framework. Pak odstraňte vzory glob souborů přidané pomocí `<Source>` a `<EmbeddedResource>` položky. Opravte cesty pro všechny odkazy na projekt, které vaše aplikace používá. Tím se efektivně upgraduje .NET Framework projekt na projekt .NET Core.
 
## <a name="next-steps"></a>Další kroky

- Přečtěte si další informace o sadě [Windows Compatibility Pack][compat-pack].
- Podívejte se [na video o přenosu](https://www.youtube.com/watch?v=upVQEUc_KwU) .NET Framework model Windows Forms projektu do .NET Core.

[compat-pack]: windows-compat-pack.md
