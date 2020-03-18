---
title: Cílové architektury v projektech ve stylu sady SDK - .NET
description: Další informace o cílových architekturách pro aplikace a knihovny .NET Core.
ms.date: 12/03/2019
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 33beb5606cbf857cc41b739f256482b0298f1fb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400552"
---
# <a name="target-frameworks-in-sdk-style-projects"></a>Cílové architektury v projektech ve stylu Sady SDK

Když cílíte na architekturu v aplikaci nebo knihovně, určujete sadu rozhraní API, která chcete zpřístupnit aplikaci nebo knihovně. Cílovou architekturu zadáte v souboru projektu pomocí názvů názvů target framework (TFM).

Aplikace nebo knihovna může cílit na verzi [rozhraní .NET Standard](net-standard.md). Standardní verze rozhraní .NET představují standardizované sady rozhraní API ve všech implementacích rozhraní .NET. Knihovna může například cílit na standard .NET Standard 1.6 a získat přístup k rozhraním API, která fungují napříč rozhraními .NET Core a .NET Framework pomocí stejného základu kódu.

Aplikace nebo knihovna můžete také cílit na konkrétní implementaci rozhraní .NET získat přístup k rozhraní API specifické pro implementaci. Například aplikace, která cílí na Xamarin.iOS `Xamarin.iOS10`(například) získá přístup k obálkám rozhraní API pro iOS poskytovaným xamarinem pro `uap10.0`iOS 10 nebo aplikace, která cílí na univerzální platformu Windows (UPW, ) má přístup k rozhraním API, která se kompilují pro zařízení se systémem Windows 10.

Pro některé cílové rámce (například rozhraní .NET Framework) jsou rozhraní API definována sestaveními, která rozhraní nainstaluje do systému, a mohou zahrnovat rozhraní API rozhraní API rozhraní api rozhraní aplikace (například ASP.NET).

Pro cílové architektury založené na balíčcích (například .NET Standard a .NET Core) jsou rozhraní API definována balíčky zahrnutými v aplikaci nebo knihovně. *Metabalíček* je balíček NuGet, který nemá žádný vlastní obsah, ale je seznam závislostí (jiné balíčky). A NuGet balíček na cílové rozhraní implicitně určuje metabalíček, který odkazuje na všechny balíčky, které společně tvoří rozhraní.

## <a name="latest-target-framework-versions"></a>Nejnovější verze cílového frameworku

Následující tabulka definuje nejběžnější cílové architektury, způsob jejich odkazu a verzi [standardu .NET,](net-standard.md) kterou implementují. Tyto cílové verze architektury jsou nejnovější stabilní verze. Předběžné verze se nezobrazují. Zástupný název cílového rozhraní (TFM) je standardizovaný formát tokenu pro určení cílového rozhraní aplikace nebo knihovny .NET.

| Cílová architektura      | Latest (Nejnovější) <br/> Stabilní verze | Zástupný název cílového rámce (TFM) | Implementována <br/> Standardní verze rozhraní .NET |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET Standard         | 2.1                         | netstandard2,1                 | Není dostupné.                                     |
| .NET Core             | 3.1                         | netcoreapp3,1                  | 2.1                                     |
| .NET Framework        | 4.8                         | net48                          | 2.0                                     |

## <a name="supported-target-framework-versions"></a>Podporované verze cílového rozhraní

Cílová architektura je obvykle odkazuje TFM. V následující tabulce jsou uvedeny cílové architektury podporované sadou .NET Core SDK a klientem NuGet. Ekvivalenty jsou zobrazeny v závorkách. Například `win81` je ekvivalentní TFM `netcore451`na .

| Cílová architektura           | Tfm |
| -------------------------- | --- |
| .NET Standard              | netstandard1,0<br>netstandard1,1<br>netstandard1,2<br>netstandard1,3<br>netstandard1,4<br>netstandard1,5<br>netstandard1,6<br>netstandard2.0<br>netstandard2,1 |
| .NET Core                  | netcoreapp1,0<br>netcoreapp1,1<br>netcoreapp2.0<br>netcoreapp2,1<br>netcoreapp2,2<br>netcoreapp3,0<br>netcoreapp3,1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472 řekl:<br>net48 |
| Windows Store              | netcore [netcore45]<br>netcore45 [win] [win8]<br>netcore451 [win81] |
| Rozhraní .NET Micro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | wp [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Univerzální platforma Windows | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Jak určit cílové rámce

Cílové architektury jsou určeny v souboru projektu. Pokud je zadán jeden cílový rámec, použijte **targetframework** element. Následující soubor projektu konzoly aplikace ukazuje, jak cílit na rozhraní .NET Core 3.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Když zadáte více cílových rámců, můžete podmíněně odkazovat na sestavení pro každou cílovou architekturu. V kódu můžete podmíněně zkompilovat proti těmto sestavením pomocí preprocesorových symbolů s *logikou if-then-else.*

Následující soubor projektu knihovny cílí na`netstandard1.4`rozhraní API standardu .NET`net40` `net45`( ) a rozhraní API rozhraní .NET Framework ( a ). Použijte plurální **TargetFrameworks** prvek s více cílové architektury. Všimněte `Condition` si, jak atributy zahrnují balíčky specifické pro implementaci, když je knihovna kompilována pro dvě tfmrozhraní rozhraní .NET Framework:

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

V rámci knihovny nebo aplikace napíšete podmíněný kód pro kompilaci pro každý cílový rámec:

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

Systém sestavení si je vědom symbolů preprocesoru představujících cílové architektury zobrazené v tabulce [podporované cílové architektury,](#supported-target-framework-versions) když používáte projekty ve stylu sady SDK. Při použití symbolu, který představuje standard .NET nebo .NET Core TFM, nahraďte tečku podtržítkem a změňte malá písmena na velká písmena (například symbol pro `netstandard1.4` je). `NETSTANDARD1_4`

Úplný seznam symbolů preprocesoru pro cílové rozhraní .NET Core je:

[!INCLUDE [Preprocessor symbols](../../includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Zastaralé cílové rámce

Následující cílové architektury jsou zastaralé. Balíčky zaměřené na tyto cílové rámce by měly migrovat na uvedené náhrady.

| Zastaralé TFM                                                                             | Náhrada |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>Dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| dotnet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 řekl: | netstandard |
| netcore50                                                                                  | uap10,0     |
| Vyhrát                                                                                        | netcore45   |
| win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | uap10,0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Viz také

- [Balíčky, metabalíčky a rámce](../core/packages.md)
- [Vývoj knihoven pomocí nástrojů pro různé platformy](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [Správa verzí jádra rozhraní .NET](../core/versions/index.md)
- [dotnet/standardní úložiště GitHub](https://github.com/dotnet/standard)
- [Úložiště GitHub nástrojů NuGet](https://github.com/joelverhagen/NuGetTools)
- [Profily architektury v rozhraní .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
