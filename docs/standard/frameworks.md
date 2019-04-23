---
title: Cílová rozhraní
description: Další informace o cílové rozhraní pro aplikace .NET Core a knihovny.
author: richlander
ms.author: mairaw
ms.date: 04/02/2019
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 1b7be132691218bf4b8283c60f9527decfd5023c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973873"
---
# <a name="target-frameworks"></a>Cílová rozhraní

Pokud je cílem rozhraní v aplikaci nebo knihovny, zadáváte sadu rozhraní API, která chcete zpřístupnit pro aplikaci nebo knihovny. Cílová architektura, která zadáte v souboru projektu pomocí Monikery cílového rozhraní (Tfm).

Aplikace nebo knihovny můžete cílit na verzi [.NET Standard](~/docs/standard/net-standard.md). Verze .NET standard představují standardizované sady rozhraní API přes všechny implementace .NET. Například knihovny můžete cílit na .NET Standard 1.6 a získat přístup k rozhraní API pro tuto funkci v .NET Core a .NET Framework pomocí stejného základu kódu.

Konkrétní implementace rozhraní .NET získat přístup k rozhraní API pro specifický pro implementaci můžete také směrovat aplikace nebo knihovna. Například aplikace, která se zaměřuje Xamarin.iOS (například `Xamarin.iOS10`) získá přístup k rozhraní API pro zadaný Xamarin iOS obálky pro iOS 10 nebo aplikaci, která cílí na univerzální platformu Windows (UPW, `uap10.0`) má přístup k rozhraní API, která kompilovat pro zařízení se systémem Windows 10.

Rozhraní API pro několik cílových rozhraní (například rozhraní .NET Framework) jsou určené sestavení, rozhraní nainstaluje v systému a může zahrnovat Architektura aplikace na rozhraní API (například technologie ASP.NET).

Pro využívající balíčky cílových rozhraní (například .NET Standard a .NET Core) rozhraní API určené balíčky, které jsou zahrnuty v aplikaci nebo knihovny. A *Microsoft.aspnetcore.all* je balíček NuGet, který nemá žádný obsah samostatně, ale je seznam závislostí (ostatní balíčky). Na základě balíčku cílového rozhraní framework NuGet implicitně určuje Microsoft.aspnetcore.all, který odkazuje na všechny balíčky, které společně tvoří rozhraní.

## <a name="latest-target-framework-versions"></a>Nejnovější verze cílového rozhraní framework

Následující tabulka definuje nejběžnější cílové architektury, jak budete odkazovat a kterou verzi [.NET Standard](~/docs/standard/net-standard.md) implementují. Tyto verze cílového rozhraní framework jsou nejnovější stabilní verze. Předběžné verze se nezobrazují. Moniker cílového rozhraní (TFM) je standardizovaný formát tokenu pro zadání cílové rozhraní framework aplikace .NET nebo knihovny.

| Cílová architektura      | Latest (Nejnovější) <br/> Stabilní verze | Moniker cílového rozhraní (TFM) | Implementováno <br/> Standardní verze rozhraní .NET |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET Standard         | 2.0                         | netstandard2.0                 | Není k dispozici                                     |
| .NET Core             | 2.2                         | netcoreapp2.2                  | 2.0                                     |
| .NET Framework        | 4.8                         | net48                          | 2.0                                     |

## <a name="supported-target-framework-versions"></a>Podporované cílové verze rozhraní framework

Rozhraní .NET framework je obvykle odkazuje TFM. V následující tabulce jsou uvedeny cílové architektury, podporuje .NET Core SDK a klienta NuGet. Ekvivalenty jsou uvedeny v závorkách. Například `win81` je ekvivalentní TFM ke `netcore451`.

| Cílová architektura           | TFM |
| -------------------------- | --- |
| .NET Standard              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0 |
| .NET Core                  | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1<br>netcoreapp2.2 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472<br>net48 |
| Windows Store              | netcore [netcore45]<br>netcore45 [Windows] [win8]<br>netcore451 [win81] |
| Micro rozhraní .NET Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | wp [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Univerzální platforma pro Windows | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Určení cílových platforem

Cílové architektury jsou uvedeny v souboru projektu. Pokud je zadána jednu cílovou architekturu, použijte **TargetFramework** elementu. Následující soubor projektu aplikace konzoly ukazuje, jak cílit na .NET Core 2.2:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>
  </PropertyGroup>

</Project>
```

Při zadávání více cílových rozhraní může podmíněně referenční sestavení pro každou cílovou architekturu. Ve vašem kódu, můžete podmíněné kompilaci proti tato sestavení pomocí symboly preprocesoru s *if-then-else* logiku.

Následující soubor Knihovního projektu cílí na rozhraní API z aplikaci .NET Standard (`netstandard1.4`) a rozhraní API rozhraní .NET Framework (`net40` a `net45`). Použít množném čísle **TargetFrameworks** element s větším počtem cílových rozhraní. Poznámka: Jak `Condition` atributy zahrnout balíčky specifický pro implementaci při kompilaci knihovny pro dva Tfm rozhraní .NET Framework:

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

V rámci knihovny nebo aplikace napište kód podmíněné kompilace pro každou cílovou architekturu:

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

Systém sestavení je seznámen symboly preprocesoru představující cílové architektury ukazuje [podporované verze cílového rozhraní framework](#supported-target-framework-versions) tabulky. Při použití symbolu, který představuje .NET Core TFM nebo .NET Standard, nahrazení tečky podtržítkem a změňte malá písmena na velká písmena (například symbol `netstandard1.4` je `NETSTANDARD1_4`).

Úplný seznam symboly preprocesoru pro cílové rozhraní .NET Core je:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Nepoužívané cílových platforem

Následující cílové architektury jsou zastaralé. Balíčky, které cílí na těchto cílových rozhraní byste migrovat na uvedené nahrazení.

| Nepoužívané TFM                                                                             | Nahrazení |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| DotNet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | netstandard |
| netcore50                                                                                  | uap10.0     |
| Windows                                                                                        | netcore45   |
| win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | uap10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Viz také:

- [Balíčky, metabalíčky a architektury](../core/packages.md)
- [Vývoj knihoven pomocí nástrojů pro různé platformy](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [Správa verzí rozhraní .NET core](../core/versions/index.md)
- [úložiště GitHub DotNet/standard](https://github.com/dotnet/standard)
- [Úložiště GitHub nástroje NuGet](https://github.com/joelverhagen/NuGetTools)
- [Profily rozhraní v rozhraní .NET](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)