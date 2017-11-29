---
title: "Cílové rozhraní"
description: "Další informace o cílové rozhraní pro aplikace .NET Core a knihovny."
author: richlander
ms.author: mairaw
ms.date: 09/22/2017
ms.topic: article
ms.custom: updateeachrelease
ms.prod: .net
ms.technology: dotnet-standard
ms.openlocfilehash: 20152a951f11b1b923209b56b31663a9a8a81587
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="target-frameworks"></a>Cílové rozhraní

K identifikaci rozhraní v aplikaci nebo knihovna určujete sadu rozhraní API, které chcete zpřístupnit aplikace nebo knihovny. Určete cílové rozhraní v souboru projektu pomocí cílový Framework Monikery (TFMs).

Aplikace nebo knihovny, můžete vybrat verzi [.NET Standard](~/docs/standard/net-standard.md). Verze rozhraní .NET standardní představují standardizované sadu rozhraní API přes všechny implementace rozhraní .NET. Například můžete knihovnu zacílit .NET Standard 1.6 a získat přístup k rozhraní API této funkce v .NET Core a rozhraní .NET Framework pomocí stejné základu kódu.

Aplikace nebo knihovny, můžete také vybrat konkrétní implementace rozhraní .NET k získání přístupu k rozhraní API pro konkrétní implementaci. Například aplikace, která cílí Xamarin.iOS (například `Xamarin.iOS10`) získá přístup k rozhraní API pro zadaný Xamarin iOS obálek pro iOS 10 nebo aplikaci, která cílí na univerzální platformu Windows (UPW, `uap10.0`) má přístup k rozhraní API, která kompilace pro zařízení se systémem Windows 10.

Pro některé cílové rozhraní (například rozhraní .NET Framework) rozhraní API jsou definované sestavení, že rozhraní nainstaluje v systému a může zahrnovat aplikační rozhraní API (například ASP.NET).

Na základě balíčku cílové rozhraní (například .NET Standard a .NET Core) rozhraní API definováno balíčky součástí aplikace nebo knihovny. A *metapackage* je balíčku NuGet, který nemá žádný obsah samostatně, ale je seznam závislosti (dalších balíčků). Na základě balíčku cílové rozhraní NuGet implicitně určuje metapackage, který odkazuje na všechny balíčky, které společně tvoří rozhraní.

## <a name="latest-target-framework-versions"></a>Nejnovější target framework verze

Následující tabulka definuje nejběžnější cílové rozhraní, jak se odkazuje a kterou verzi [.NET Standard](~/docs/standard/net-standard.md) implementace. Tyto target framework verze jsou nejnovější stabilní verze. Předběžných verzí se nezobrazí. Cílový Framework Přezdívka (TFM) je standardizovaná formát tokenu pro zadání cílové rozhraní aplikace .NET nebo knihovny. 

| Cílová architektura      | Nejnovější verzi | Cílový Framework Přezdívka (TFM) | Implementováno <br/> Standardní verze rozhraní .NET |
| :-------------------: | :------------: | :----------------------------: | :-------------------------------------: |
| Standardní rozhraní .NET         | 2.0            | netstandard2.0                 | Není k dispozici                                     |
| Aplikace .NET core | 2.0            | netcoreapp2.0                  | 2.0                                     |
| .NET Framework        | 4.7.1          | net471                         | 2.0                                     |

## <a name="supported-target-framework-versions"></a>Podporované target framework verze

Cílové rozhraní se obvykle odkazuje TFM. V následující tabulce jsou uvedeny cílové rozhraní nepodporuje rozhraní .NET Core SDK a klienta NuGet. Ekvivalenty se zobrazí v závorkách. Například `win81` je ekvivalentní TFM k `netcore451`.

| Cílová architektura           | TFM |
| -------------------------- | --- |
| Standardní rozhraní .NET              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0 |
| .NET Core                  | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0 |
| .NET Framework             | net11<br>net20<br>Net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471 |
| Windows Store              | netcore [netcore45]<br>netcore45 [win] [win8]<br>netcore451 [win81] |
| Malých rozhraní .NET Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | webové části [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Univerzální platforma pro Windows | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Určení cílové rozhraní

Cílové rozhraní jsou určené v souboru projektu. Pokud je zadána jedné cílové rozhraní, použijte **TargetFramework** elementu. Následující soubor projektu aplikace konzoly ukazuje, jak cílí na .NET Core 2.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Pokud zadáte více cílové rozhraní, může podmíněně odkazujete na sestavení pro každé cílové rozhraní. V kódu, můžete podmíněně zkompilovat proti tyto sestavení pomocí preprocesoru symboly s *if potom else* logiku.

Následující soubor projektu knihovny cílem rozhraní API z Standard .NET (`netstandard1.4`) a rozhraní API rozhraní .NET Framework (`net40` a `net45`). Použijte množném čísle **TargetFrameworks** element s více cílové architektury. Poznámka: Jak `Condition` atributy patří balíčky závisí na implementaci při kompilaci knihovny pro dvě TFMs Framework .NET:

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

V rámci knihovny nebo aplikací zápisu podmíněného kód mohl zkompilovat pro každé cílové rozhraní:

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

Systém sestavení si je vědoma preprocesoru symboly představující cílové rozhraní ukazuje [podporované target framework verze](#supported-target-framework-versions) tabulky. Pokud používáte symbol, který představuje .NET Standard nebo .NET Core TFM, nahraďte podtržítkem tečky a změnit malých písmen na velká písmena (například symbol pro `netstandard1.4` je `NETSTANDARD1_4`).

Úplný seznam preprocesoru symboly pro cílové rozhraní .NET Core je:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Nepoužívané cílové rozhraní

Následující cílové architektury jsou zastaralé. Balíčky cílené na tyto cílové rozhraní měli migrovat na uvedené nahrazení.

| Nepoužívané TFM                                                                             | Nahrazení |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| DotNet.<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | monikerů netstandard |
| netcore50                                                                                  | uap10.0     |
| Win                                                                                        | netcore45   |
| win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | uap10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Viz také

[Balíčky, Metapackages a architektury](~/docs/core/packages.md)  
[Vývoj knihovny s křížové nástrojů platformy](~/docs/core/tutorials/libraries.md)  
[Standardní rozhraní .NET](~/docs/standard/net-standard.md)  
[Správa verzí rozhraní .NET core](~/docs/core/versions/index.md)  
[úložiště GitHub DotNet nebo standard](https://github.com/dotnet/standard)  
[Úložiště GitHub nástroje NuGet](https://github.com/joelverhagen/NuGetTools)  
[Profily Framework v rozhraní .NET](http://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
