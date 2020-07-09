---
title: Přehled .NET Core
description: Seznamte se s charakteristikami a složením .NET Core a porovnejte je s dalšími implementacemi .NET.
ms.date: 03/26/2020
ms.openlocfilehash: d5ef79fe5a8fbb56beae77edd01830fe6561fa51
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100727"
---
# <a name="net-core-overview"></a>Přehled .NET Core

> [!div class="button"]
> [Stáhnout .NET Core](https://dotnet.microsoft.com/download)

.NET Core má následující vlastnosti:

- **Různé platformy:** Spouští se v [operačních systémech](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, MacOS a Linux.
- **Open Source:** Rozhraní .NET Core Framework je [Open Source](https://github.com/dotnet/core)pomocí licencí MIT a Apache 2. .NET Core je projekt [.NET Foundation](https://dotnetfoundation.org/) .
- **Moderní:** Implementuje moderní paradigma, jako je asynchronní programování, vzory bez kopírování pomocí struktur a zásady správného řízení prostředků pro kontejnery.
- **Výkon:**  Poskytuje [vysoký výkon](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/) díky funkcím, jako jsou [vnitřní objekty hardwaru](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/), [vrstvená kompilace](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)a [rozpětí \<T> ](../standard/memory-and-spans/index.md).
- **Konzistentní v různých prostředích:** Spustí váš kód se stejným chováním na více operačních systémech a architekturách, včetně x64, x86 a ARM.
- **Nástroje příkazového řádku:**  Zahrnuje snadno použitelné nástroje příkazového řádku, které je možné použít pro místní vývoj a pro průběžnou integraci.
- **Flexibilní nasazení:** Do své aplikace můžete zahrnout .NET Core nebo je nainstalovat vedle sebe (instalace v uživatelském prostředí nebo v rámci systému). Dá se použít s [kontejnery Docker](docker/introduction.md).

## <a name="languages"></a>Jazyky

Jazyky [C#](../csharp/index.yml), [Visual Basic](../visual-basic/index.yml)a [F #](../fsharp/index.yml) lze použít k psaní aplikací a knihoven pro .NET Core. Tyto jazyky lze použít ve vašem oblíbeném textovém editoru nebo integrovaném vývojovém prostředí (IDE), včetně:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)

Integrace editoru je poskytována jako součást přispěvatelům projektů [OmniSharp](https://www.omnisharp.net/) a [Ionide](https://ionide.io) .

## <a name="apis"></a>Rozhraní API

.NET Core zpřístupňuje architektury pro tvorbu libovolného typu aplikace:

* Cloudové aplikace s [ASP.NET Core](/aspnet/core/)
* Mobilní aplikace s [Xamarin](/xamarin)
* Aplikace IoT se [System. Device. GPIO](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)
* Klientské aplikace pro Windows s [WPF](../desktop-wpf/overview/index.md) a model Windows Forms
* Strojové učení [ml.NET](../machine-learning/index.yml)

K dispozici je mnoho rozhraní API, které vyhovuje běžným potřebám:

- Primitivní typy, například <xref:System.Boolean?displayProperty=nameWithType> a <xref:System.Int32?displayProperty=nameWithType> .
- Kolekce, například <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> .
- Typy nástrojů, například <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> , a <xref:System.IO.FileStream?displayProperty=nameWithType> .
- Datové typy, například <xref:System.Data.DataSet?displayProperty=nameWithType> , a <xref:System.Data.Entity.DbSet?displayProperty=nameWithType> .
- Vysoce výkonné typy, jako jsou například <xref:System.Span%601?displayProperty=nameWithType> , <xref:System.Numerics.Vector?displayProperty=nameWithType> a [kanály](../standard/io/pipelines.md).

.NET Core poskytuje kompatibilitu s rozhraními API .NET Framework a mono implementací specifikace [.NET Standard](../standard/net-standard.md) .

## <a name="composition"></a>Složení

.NET Core se skládá z následujících částí:

- [Modul runtime .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), který poskytuje systém typů, načítání sestavení, systém uvolňování paměti, nativní spolupráci a další základní služby. [Knihovny .NET Core Framework](https://github.com/dotnet/runtime/tree/master/src/libraries) poskytují primitivní datové typy, typy kompozic aplikací a základní nástroje.
- Modul [runtime ASP.NET Core](https://github.com/dotnet/aspnetcore), který poskytuje rozhraní pro vytváření moderních cloudových aplikací připojených k Internetu, jako jsou webové aplikace, aplikace IoT a mobilní back-endy.
- Kompilátory [.NET Core SDK](https://github.com/dotnet/sdk) a jazyka ([Roslyn](https://github.com/dotnet/roslyn) a [F #](https://github.com/microsoft/visualfsharp)), které umožňují prostředí pro vývojáře .NET Core.
- [Příkaz dotnet](./tools/dotnet.md), který se používá ke spouštění aplikací .NET Core a příkazů rozhraní příkazového řádku. Vybírá a hostuje modul runtime, poskytuje zásady načítání sestavení a spouští aplikace a nástroje.

### <a name="open-source"></a>Open source

[.NET Core](about.md) je [Open Source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)vývojová platforma pro obecné účely. Pro procesory x64, x86, ARM32 a ARM64 můžete vytvářet aplikace .NET Core pro Windows, macOS a Linux. K dispozici jsou architektury a rozhraní API pro [Cloud](/aspnet/core/), [IoT](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [klientské uživatelské rozhraní](../desktop-wpf/overview/index.md)a [strojové učení](../machine-learning/index.yml).

## <a name="support"></a>Podpora

.NET Core [podporuje Microsoft](https://dotnet.microsoft.com/platform/support/policy) v systémech Windows, MacOS a Linux. Pravidelně se aktualizuje o zabezpečení a kvalitu (druhé úterý v měsíci).

Cloudové distribuce .NET Core od Microsoftu se sestavují a testují na serverech spravovaných Microsoftem v Azure a sledují postupy Microsoft Engineering a zabezpečení.

[Red Hat podporuje .NET Core](https://developers.redhat.com/topics/dotnet/) na Red Hat Enterprise Linux (RHEL). Red Hat sestaví .NET Core ze zdroje a zpřístupňuje je v [kolekcích softwaru Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat a Microsoft spolupracují, aby se zajistilo, že .NET Core dobře funguje na RHEL.

[Tizen podporuje .NET Core](https://developer.tizen.org/development/training/.net-application) na platformách Tizen.
