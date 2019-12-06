---
title: Cílová rozhraní v projektech se stylem sady SDK – .NET
description: Přečtěte si o cílových rozhraních pro aplikace a knihovny .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 12/03/2019
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 957671644ae333180b0c1ba4aae6d6e17ae6478b
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838209"
---
# <a name="target-frameworks-in-sdk-style-projects"></a>Cílová rozhraní v projektech ve stylu sady SDK

Když cílíte na architekturu v aplikaci nebo knihovně, zadáváte sadu rozhraní API, které byste chtěli zpřístupnit pro aplikaci nebo knihovnu. Cílovou architekturu zadáte v souboru projektu pomocí monikerů cílového rozhraní (TFM).

Aplikace nebo knihovna může cílit na verzi [.NET Standard](net-standard.md). .NET Standard verze reprezentují standardizované sady rozhraní API napříč všemi implementacemi rozhraní .NET. Knihovna může například cílit .NET Standard 1,6 a získat přístup k rozhraním API, která fungují napříč .NET Core a .NET Framework pomocí stejného základu kódu.

Aplikace nebo knihovna může také cílit na konkrétní implementaci rozhraní .NET, aby získala přístup k rozhraním API specifickým pro implementaci. Například aplikace, která se zaměřuje na Xamarin. iOS (například `Xamarin.iOS10`), získá přístup k obálkám rozhraní API iOS poskytovaným v Xamarin pro iOS 10 nebo aplikace, která cílí na Univerzální platforma Windows (UWP, `uap10.0`), má přístup k rozhraním API, která se zkompiluje pro zařízení s Windows 10.

Pro některé cílové architektury (například .NET Framework) jsou rozhraní API definována sestaveními, která rozhraní nainstalují do systému a mohou zahrnovat rozhraní API rozhraní Application Framework (například ASP.NET).

Pro cílové architektury založené na balíčku (například .NET Standard a .NET Core) jsou rozhraní API definovaná balíčky obsaženými v aplikaci nebo knihovně. *Metapackage* je balíček NuGet, který nemá žádný vlastní obsah, ale je to seznam závislostí (dalších balíčků). Cílová architektura založená na balíčku NuGet implicitně určuje Metapackage, který odkazuje na všechny balíčky, které dohromady tvoří rozhraní.

## <a name="latest-target-framework-versions"></a>Nejnovější cílové verze rozhraní .NET Framework

Následující tabulka definuje nejběžnější cílová rozhraní, jejich odkazování a verzi [.NET Standard](net-standard.md) , kterou implementují. Tyto verze cílových rozhraní jsou nejnovější stabilní verze. Předběžná verze se nezobrazuje. Moniker cílového rozhraní (TFM) je formát standardizovaného tokenu pro určení cílové architektury aplikace nebo knihovny .NET.

| Cílová architektura      | Latest (Nejnovější) <br/> Stabilní verze | Moniker cílového rozhraní (TFM) | Vede <br/> Verze .NET Standard |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET Standard         | 2.1                         | netstandard 2.1                 | NEUŽÍVÁ SE.                                     |
| .NET Core             | 3.1                         | netcoreapp 3.1                  | 2.1                                     |
| .NET Framework        | 4.8                         | net48                          | 2.0                                     |

## <a name="supported-target-framework-versions"></a>Podporované cílové verze rozhraní .NET Framework

Na cílové rozhraní se obvykle odkazuje pomocí TFM. V následující tabulce jsou uvedeny cílové architektury podporované .NET Core SDK a klientem NuGet. Ekvivalenty jsou uvedeny v závorkách. `win81` je například ekvivalentní TFM k `netcore451`.

| Cílová architektura           | TFM |
| -------------------------- | --- |
| .NET Standard              | netstandard 1.0<br>netstandard 1.1<br>netstandard 1.2<br>netstandard 1.3<br>netstandard 1.4<br>netstandard 1.5<br>netstandard 1.6<br>netstandard 2.0<br>netstandard 2.1 |
| .NET Core                  | netcoreapp 1.0<br>netcoreapp 1.1<br>netcoreapp2.0<br>netcoreapp 2.1<br>netcoreapp 2.2<br>netcoreapp 3.0<br>netcoreapp 3.1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472<br>net48 |
| Windows Store              | Netcore [netcore45]<br>netcore45 [Win] [Win8]<br>netcore451 [win81] |
| .NET Micro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | wp [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Univerzální platforma pro Windows | UAP [UAP 10.0]<br>UAP 10.0 [Win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Určení cílových rozhraní Framework

Cílová rozhraní jsou uvedena v souboru projektu. Pokud je určena jedna cílová architektura, použijte element **targetFramework** . Následující soubor projektu konzolové aplikace ukazuje, jak cílit na .NET Core 3,0:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Pokud zadáte více cílových rozhraní, můžete podmíněně odkazovat na sestavení pro každé cílové rozhraní. Ve vašem kódu můžete podmíněně kompilovat proti těmto sestavením pomocí symbolů preprocesoru s logikou *if-then-else* .

Následující soubor projektu knihovny cílí na rozhraní API .NET Standard (`netstandard1.4`) a rozhraní API .NET Framework (`net40` a `net45`). Použijte element plural **targetframeworks** s více cílovými rozhraními. Všimněte si, jak atributy `Condition` zahrnují balíčky specifické pro implementaci při kompilaci knihovny pro dvě .NET Framework TFM:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.0 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net40' ">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.5 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net45' ">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>

</Project>
```

V rámci knihovny nebo aplikace píšete podmíněný kód pro kompilaci pro každé cílové rozhraní:

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Systém sestavení je vědom symbolů preprocesoru, které představují cílové architektury zobrazené v tabulce [podporovaných verzí cílového rozhraní](#supported-target-framework-versions) při použití projektů ve stylu sady SDK. Při použití symbolu, který představuje .NET Standard nebo .NET Core TFM, nahraďte tečku podtržítkem a malými písmeny se změní na velká písmena (například symbol pro `netstandard1.4` je `NETSTANDARD1_4`).

Úplný seznam symbolů preprocesoru pro .NET Core Target Framework je:

[!INCLUDE [Preprocessor symbols](../../includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Zastaralá cílová rozhraní

Následující cílová rozhraní jsou zastaralá. Balíčky, které cílí na tyto cílové platformy, by se měly migrovat na zmíněné náhrady.

| Zastaralé TFM                                                                             | Náhrada |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>DNX<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| dotnet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | netstandard |
| netcore50                                                                                  | UAP 10.0     |
| výher                                                                                        | netcore45   |
| Win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | UAP 10.0     |
| WinRT                                                                                      | netcore45   |

## <a name="see-also"></a>Viz také:

- [Balíčky, metabalíčky a architektury](../core/packages.md)
- [Vývoj knihoven pomocí nástrojů pro různé platformy](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [Verze .NET Core](../core/versions/index.md)
- [dotnet/standardní úložiště GitHubu](https://github.com/dotnet/standard)
- [Úložiště GitHub nástrojů NuGet](https://github.com/joelverhagen/NuGetTools)
- [Profily architektury v .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
