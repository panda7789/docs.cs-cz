---
title: Přehled .NET Core
description: Zjistěte o charakteristikách a složení jádra .NET a porovnejte je s jinými implementacemi rozhraní .NET.
ms.date: 03/26/2020
ms.openlocfilehash: c9a63ddba14cf176be529e9520027c0610cfc087
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391166"
---
# <a name="net-core-overview"></a>Přehled .NET Core

.NET Core má následující charakteristiky:

- **Příčná platforma:** Běží na [operačních systémech](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, macOS a Linux .
- **Open source:** Rozhraní .NET Core framework je [open source](https://github.com/dotnet/core), který používá licence MIT a Apache 2. .NET Core je projekt [.NET Foundation.](https://dotnetfoundation.org/)
- **Moderní:** Implementuje moderní paradigmata, jako je asynchronní programování, no-copy vzory pomocí struktur a zásady správného řízení prostředků pro kontejnery.
- **Výkon:**  Poskytuje [vysoký výkon](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/) s funkcemi, jako jsou vnitřní [prvky hardwaru](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/), [stupňovitá kompilace](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)a [span\<t>](../standard/memory-and-spans/index.md).
- **Konzistentní napříč prostředími:** Spustí váš kód se stejným chováním na více operačních systémech a architekturách, včetně x64, x86 a ARM.
- **Nástroje příkazového řádku:**  Obsahuje snadno použitelné nástroje příkazového řádku, které lze použít pro místní vývoj a pro průběžnou integraci.
- **Flexibilní nasazení:** Do aplikace můžete zahrnout jádro .NET Core nebo jej nainstalovat vedle sebe (instalace v rámci celého uživatele nebo systému). Lze použít s [kontejnery Dockeru](docker/introduction.md).

## <a name="languages"></a>Jazyky

Jazyky [C#](../csharp/index.yml), [Visual Basic](../visual-basic/index.yml)a [F#](../fsharp/index.yml) lze použít k zápisu aplikací a knihoven pro .NET Core. Tyto jazyky lze použít ve vašem oblíbeném textovém editoru nebo integrovaném vývojovém prostředí (IDE), včetně:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Kód visual studia](https://code.visualstudio.com/download)

Editor integrace je poskytována částečně přispěvateli [omnisharp](https://www.omnisharp.net/) a [ionide](http://ionide.io) projektů.

## <a name="apis"></a>Rozhraní API

.NET Core zpřístupňuje architektury pro vytváření jakéhokoli druhu aplikace:

* Cloudové aplikace s [ASP.NET Jádrem](/aspnet/core/)
* Mobilní aplikace s [Xamarinem](/xamarin)
* Aplikace IoT s [system.device.gpio](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)
* Klientské aplikace Windows s [WPF](../desktop-wpf/overview/index.md) a Windows Forms
* [ML.NET](../machine-learning/index.yml) strojového učení

Mnoho api jsou zahrnuty, které splňují běžné potřeby:

- Primitivní typy, <xref:System.Boolean?displayProperty=nameWithType> například a <xref:System.Int32?displayProperty=nameWithType>.
- Kolekce, například <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>a .
- Typy užitkových nástrojů, například <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>, a <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Datové typy, <xref:System.Data.DataSet?displayProperty=nameWithType>například <xref:System.Data.Entity.DbSet?displayProperty=nameWithType>, a .
- Typy s vysokým výkonem, například <xref:System.Span%601?displayProperty=nameWithType>, <xref:System.Numerics.Vector?displayProperty=nameWithType>a [Pipelines](../standard/io/pipelines.md).

Jádro .NET poskytuje kompatibilitu s rozhraními .NET Framework a Mono API implementací specifikace [.NET Standard.](../standard/net-standard.md)

## <a name="composition"></a>Složení

.NET Core se skládá z následujících částí:

- [Zaběhu .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), který poskytuje typ systému, načítání sestavení, uvolňování paměti, nativní interop a další základní služby. [Knihovny rozhraní .NET Core framework](https://github.com/dotnet/runtime/tree/master/src/libraries) poskytují primitivní datové typy, typy složení aplikací a základní nástroje.
- [ASP.NET Core runtime](https://github.com/dotnet/aspnetcore), který poskytuje rámec pro vytváření moderních cloudových aplikací připojených k internetu, jako jsou webové aplikace, aplikace IoT a mobilní back-endy.
- Sada [.NET Core SDK](https://github.com/dotnet/sdk) a kompilátory jazyka ([Roslyn](https://github.com/dotnet/roslyn) a [F#](https://github.com/microsoft/visualfsharp)), které umožňují vývojářské prostředí .NET Core.
- Příkaz dotnet , který se používá ke spuštění aplikací .NET Core a příkazů příkazu příkazu příkazu příkazu příkazu příkazu příkazu.The [dotnet command](./tools/dotnet.md), which is used to launch .NET Core apps and CLI commands. Vybere a hostuje za běhu, poskytuje zásady načítání sestavení a spouští aplikace a nástroje.

### <a name="open-source"></a>Open source

[.NET Core](about.md) je [open-source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)univerzální vývojová platforma. Můžete vytvářet aplikace .NET Core pro procesory Windows, macOS a Linux pro procesory x64, x86, ARM32 a ARM64. Architektury a rozhraní API jsou k dispozici pro [cloud](/aspnet/core/), [IoT](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [klientské ui](../desktop-wpf/overview/index.md)a [strojové učení](../machine-learning/index.yml).

## <a name="support"></a>Podpora

.NET Core je [podporován společností Microsoft](https://dotnet.microsoft.com/platform/support/policy) v systémech Windows, macOS a Linux. Je pravidelně aktualizován z bezpečnostních důvodů (druhé úterý v měsíci).

Binární distribuce .NET Core od Microsoftu jsou sestavené a testované na serverech spravovaných společností Microsoft v Azure a postupujte podle technických a bezpečnostních postupů Microsoftu.

[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat staví .NET Core ze zdroje a zpřístupňuje jej v [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat a Microsoft spolupracují, aby zajistily, že .NET Core funguje dobře na RHEL.

[Tizen podporuje .NET Core](https://developer.tizen.org/development/training/.net-application) na platformách Tizen.
