---
title: Port, Windows Forms aplikaci .NET Core 3.0
description: Vás naučí, jak přenést aplikaci formulářů Windows rozhraní .NET Framework 3.0 .NET Core pro Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: aebfaa85338e014ca47256b85a1bd6529ad803bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663086"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>Postupy: Port desktopové aplikace Windows Forms až po .NET Core

Tento článek popisuje, jak přenést na základě formulářů Windows desktopové aplikaci z rozhraní .NET Framework do .NET Core 3.0. .NET Core 3.0 SDK obsahuje podporu pro aplikace Windows Forms. Formuláře Windows je stále rozhraní jen pro Windows a pouze běží na Windows. Tento příklad používá rozhraní příkazového řádku .NET Core SDK k vytváření a správě vašeho projektu.

V tomto článku najdete různé názvy umožňují určit typy souborů se používá pro migraci. Při migraci vašeho projektu, soubory budou pojmenované jinak, takže duševně je přizpůsobit uvedené níže:

| Soubor | Popis |
| ---- | ----------- |
| **MyApps.sln** | Název souboru řešení. |
| **MyForms.csproj** | Název projektu formulářů Windows rozhraní .NET Framework na port. |
| **MyFormsCore.csproj** | Název nového projektu .NET Core, který vytvoříte. |
| **MyAppCore.exe** | Spustitelný soubor aplikace modelu Windows Forms .NET Core. |

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pro jakékoli návrháře práce, které chcete provést.

  Instalace následujících úlohách sady Visual Studio:
  - Vývoj desktopových aplikací .NET
  - Vývoj pro různé platformy .NET

- Funkční projektu Windows Forms v řešení, které vytvoří a spustí bez problému.
- Váš projekt musí být zakódované v C#. 
- Nainstalujte nejnovější [.NET Core 3.0](https://aka.ms/netcore3download) ve verzi preview.

>[!NOTE]
>**Visual Studio 2017** nepodporuje projekty .NET Core 3.0. **Visual Studio 2019** podporuje projekty .NET Core 3.0, ale zatím nepodporuje vizuálního návrháře pro projekty .NET Core 3.0 Windows Forms. Do vizuálního návrháře použít, musí mít projekt .NET Windows Forms ve vašem řešení, která sdílí soubory formuláře s projektem .NET Core.

### <a name="consider"></a>Vezměte v úvahu

Při přenesení aplikací rozhraní .NET Framework Windows Forms, existuje několik věcí, které musíte zvážit.

01. Zkontrolujte, že vaše aplikace je vhodným kandidátem pro migraci.

    Použití [.NET Portability Analyzeru](../../standard/analyzers/portability-analyzer.md) chcete ověřit, jestli váš projekt bude migrovat na rozhraní .NET Core 3.0. Pokud váš projekt obsahuje problémy s .NET Core 3.0, analyzátor vám pomůže určit tyto problémy.

01. Používáte jinou verzi Windows Forms.

    Pokud byla vydána .NET Core 3.0 ve verzi Preview 1, Windows Forms k nějaké open source na Githubu. Kód pro .NET Core Windows Forms je základ kódu rozhraní .NET Framework Windows Forms. Je možné, existují určité rozdíly a vaše aplikace nebude portu.

01. [Windows Compatibility Pack] [ compat-pack] můžete migrovat.

    Některá rozhraní API, které jsou k dispozici v rozhraní .NET Framework nejsou k dispozici v rozhraní .NET Core 3.0. [Windows Compatibility Pack] [ compat-pack] přidá mnohé z těchto rozhraní API a může pomoct vaší aplikace Windows Forms, budou kompatibilní s .NET Core.

01. Aktualizujte balíčky NuGet používané vaším projektem.

    Je vždy vhodné použít nejnovější verzi balíčků NuGet před nějaká migrace. Pokud aplikace odkazuje na všechny balíčky NuGet, můžete je aktualizujte na nejnovější verzi. Zajistěte, aby že vaše aplikace sestavena úspěšně. Po upgradu, pokud nejsou žádné chyby balíčku, provést downgrade balíčku na nejnovější verzi, která nedojde k narušení kódu.

01. Visual Studio 2019 zatím nepodporuje Návrháře formulářů pro .NET Core 3.0

    V současné době je potřeba nechat existující soubor formulářů Windows rozhraní .NET Framework projektu, pokud chcete použít Návrhář formulářů ze sady Visual Studio.

## <a name="create-a-new-sdk-project"></a>Vytvořte nový projekt sady SDK

Nový projekt .NET Core 3.0, které vytvoříte, musí být v jiném adresáři z rozhraní .NET Framework projektu. Pokud jsou oba ve stejném adresáři, můžete jej spustit do je v konfliktu se soubory, které jsou generovány v **obj** adresáře. V tomto příkladu vytvoříme adresář s názvem **MyFormsAppCore** v **SolutionFolder** adresáře:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

V dalším kroku je potřeba vytvořit **MyFormsCore.csproj** projekt **MyFormsAppCore** adresáře. Můžete tento soubor můžete vytvořit ručně pomocí text editoru. Vložte následující kód XML:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

Pokud nechcete vytvořit soubor projektu ručně, můžete použít ke generování projektu sady Visual Studio nebo .NET Core SDK. Nicméně je nutné odstranit všechny ostatní soubory vygenerovaná šablona projektu s výjimkou souboru projektu. Použití sady SDK, spusťte následující příkaz z **SolutionFolder** adresáře:

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

Po vytvoření **MyFormsCore.csproj**, strukturu by měl vypadat nějak takto:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

Bude potřeba přidat **MyFormsCore.csproj** projekt k **MyApps.sln** sadou Visual Studio nebo rozhraní příkazového řádku .NET Core z **SolutionFolder** adresáře:

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Oprava generování informací o sestavení

Windows Forms projekty, které byly vytvořeny pomocí rozhraní .NET Framework zahrnují `AssemblyInfo.cs` soubor, který obsahuje sestavení atributům, jako je verze sestavení, které má být vygenerována. Projekty založenými na sadě SDK automaticky vygenerovat tyto informace vám na základě souboru projektu sadu SDK. Oba typy "informace o sestavení" způsobí konflikt. Tento problém vyřešit tím, že zakážete automatické generování, která vynutí projekt, který používá vaše existující `AssemblyInfo.cs` souboru.

Existují tři nastavení, chcete-li přidat hlavní `<PropertyGroup>` uzlu. 

- **GenerateAssemblyInfo**\
Pokud nastavíte tuto vlastnost na `false`, nevygeneruje atributů sestavení. Tím předejdete konfliktu s existujícím `AssemblyInfo.cs` soubor z rozhraní .NET Framework projektu.

- **AssemblyName**\
Hodnota této vlastnosti je binární výstup vytvořený při kompilaci. Název nemusí rozšíření do ní přidá. Například použití `MyCoreApp` vytváří `MyCoreApp.exe`.

- **RootNamespace**\
Výchozí obor názvů použitou vaším projektem. Ten by měl odpovídat výchozí obor názvů rozhraní .NET Framework projektu.

Přidejte tyto tři prvky, aby `<PropertyGroup>` uzlu `MyFormsCore.csproj` souboru:

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

## <a name="add-source-code"></a>Přidejte zdrojový kód

Právě teď **MyFormsCore.csproj** projekt nebude kompilovat žádný kód. Ve výchozím nastavení projekty .NET Core automaticky zahrnout všechny zdrojového kódu v aktuálním adresáři a všechny podřízené adresáře. Je nutné nakonfigurovat projekt tak, aby zahrnout kód z rozhraní .NET Framework projektu pomocí relativní cesty. Pokud rozhraní .NET Framework projekt používá **RESX** soubory ikon a prostředky pro vaše formuláře, budete muset zahrnout ty příliš. 

Přidejte následující `<ItemGroup>` uzlu do projektu. Každý výpis obsahuje vzor glob souboru, který obsahuje podadresáře.

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

Alternativně můžete vytvořit `<Compile>` nebo `<EmbeddedResource>` položku pro každý soubor v projektu rozhraní .NET Framework.

## <a name="add-nuget-packages"></a>Přidání balíčků NuGet

Přidejte každý balíček NuGet rozhraní .NET Framework projektu do projektu .NET Core. 

Pravděpodobně má vaše aplikace rozhraní .NET Framework Windows Forms **souboru packages.config** soubor, který obsahuje seznam všech balíčků NuGet, na které odkazuje váš projekt. Můžete si prohlédnout tento seznam a určit, které balíčky NuGet pro přidání do projektu .NET Core. Například, pokud rozhraní .NET Framework projektu odkazovat `MetroFramework`, `MetroFramework.Design`, a `MetroFramework.Fonts` balíčky NuGet, přidejte je do projektu pomocí sady Visual Studio nebo rozhraní příkazového řádku .NET Core z **SolutionFolder** adresáře :

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

Předchozích příkazů přidejte následující odkazy NuGet **MyFormsCore.csproj** projektu:

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>Port ovládacího prvku knihovny

Pokud máte projekt knihovny ovládacích prvků Windows Forms k portu, pokynů jsou stejné jako portování projektu aplikace rozhraní .NET Framework Windows Forms, s výjimkou několik nastavení. A místo kompilace do spustitelného souboru, kompilaci do knihovny. Rozdíl mezi spustitelný projekt a projekt knihovny, kromě cesty k souboru globy, obsahující zdrojový kód, je minimální.

Použijeme příklad v předchozím kroku, vám umožní rozšířit jaké projekty a soubory spolupracujeme s.

| Soubor | Popis |
| ---- | ----------- |
| **MyApps.sln** | Název souboru řešení. |
| **MyControls.csproj** | Název projektu .NET Framework Windows Forms ovládací prvky na port. |
| **MyControlsCore.csproj** | Název nového projektu knihovny .NET Core, který vytvoříte. |
| **MyCoreControls.dll** | Knihovna ovládacích prvků .NET Core Windows Forms. |

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

Zvažte rozdíly mezi `MyControlsCore.csproj` projektu a dříve vytvořený `MyFormsCore.csproj` projektu.

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

Tady je příklad toho, co by vypadat soubor Knihovního projektu .NET Core Windows Forms ovládací prvky:

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

Jak je vidět, `<OutputType>` byl uzel odebrán, která má výchozí hodnotu kompilátor vytvoří knihovnu místo spustitelný soubor. `<AssemblyName>` a `<RootNamespace>` byly změněny. Konkrétně `<RootNamespace>` by měl odpovídat oboru názvů jsou portování knihovny ovládacích prvků Windows Forms. A nakonec `<Compile>` a `<EmbeddedResource>` uzly byly upraveny tak, aby odkazoval na složku knihovny ovládacích prvků Windows Forms jsou přenos.

Další hlavní .NET Core **MyFormsCore.csproj** projektu přidejte odkaz na knihovnu nového ovládacího prvku Windows Forms .NET Core. Přidání odkazu pomocí sady Visual Studio nebo rozhraní příkazového řádku .NET Core z **SolutionFolder** adresáře:

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

Předchozí příkaz přidá následující **MyFormsCore.csproj** projektu:

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Problémy kompilace

Pokud máte problémy sestavování vašich projektů, může pomocí některé API jen pro Windows, které jsou k dispozici v rozhraní .NET Framework, ale není k dispozici v .NET Core. Můžete zkusit přidat [Windows Compatibility Pack] [ compat-pack] do svého projektu balíček NuGet. Tento balíček pouze běží na Windows a přidá přibližně 20 000 rozhraní Windows API pro projekty .NET Core a .NET Standard.

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

Předchozí příkaz přidá následující **MyFormsCore.csproj** projektu:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Návrhář formulářů Windows

Jak je uvedeno v tomto článku Visual Studio 2019 pouze podporuje Návrhář formulářů v projektech .NET Framework. Tím, že vytvoříte projekt .NET Core vedle sebe, můžete otestovat projekt pomocí .NET Core při použití rozhraní .NET Framework projektu pro návrh formulářů. Soubor řešení obsahuje projekty rozhraní .NET Framework a .NET Core. Přidat a návrh formulářů a ovládacích prvků v rozhraní .NET Framework projektu a na základě na vzory souborů glob jsme přidali do projektů .NET Core, všechny nové nebo změněné soubory se automaticky zahrnou v projektech .NET Core.

Jakmile Visual Studio 2019 podporuje Návrhář formulářů Windows, můžete zkopírovat a vložit obsah souboru projektu .NET Core do souboru projektu rozhraní .NET Framework. Odstraňte glob vzory souborů, přidá se `<Source>` a `<EmbeddedResource>` položky. Vyřešte cest pro všechny odkazy projektu používají ve vaší aplikaci. To efektivně provede upgrade rozhraní .NET Framework projektu do projektu .NET Core.
 
## <a name="next-steps"></a>Další kroky

* Další informace najdete [Windows Compatibility Pack][compat-pack].
* Sledování [videa na přenos](https://www.youtube.com/watch?v=upVQEUc_KwU) formulářů Windows rozhraní .NET Framework projektu .NET Core.

[compat-pack]: windows-compat-pack.md
