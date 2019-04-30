---
title: Co je nového v .NET Standard
description: Tento článek shrnuje nové funkce a vylepšení v každé nové verze .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45e67fe1436863da4050342bb224d67894111cc4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61861106"
---
# <a name="whats-new-in-the-net-standard"></a>Co je nového v .NET Standard

.NET Standard je formální specifikaci, který definuje sadu označené verzí rozhraní API, která musí být k dispozici na implementace .NET, které jsou v souladu s touto verzí standardu. .NET Standard je cílena na vývojáře knihovny. Knihovnu, která cílí na .NET Standard verze lze použít v rozhraní .NET Framework a .NET Core, Xamarin implementaci, která podporuje verzi standard.

Překopírujte nejnovější verzi .NET Standard je 2.0. To je součástí s .NET Core 2.0 SDK, stejně jako s Visual Studio 2017 verze 15.3 nainstalovaná úloha .NET Core.

## <a name="supported-net-implementations"></a>Podporovaná implementace .NET

Rozhraní .NET Standard 2.0 podporuje následující implementace .NET:

- .NET core 2.0 nebo novější
- Rozhraní .NET framework 4.6.1 nebo novější
- Mono 5.4 nebo novější
- Xamarin.iOS 10.14 nebo novější
- Rozhraní Xamarin.Mac 3,8 nebo novější
- Xamarin.Android 8.0 nebo novější
- Univerzální platforma Windows 10.0.16299 nebo novější

## <a name="whats-new-in-the-net-standard-20"></a>Co je nového v .NET Standard 2.0

Rozhraní .NET Standard 2.0 obsahuje následující nové funkce:

### <a name="a-vastly-expanded-set-of-apis"></a>Výrazně rozšířené sady rozhraní API

Prostřednictvím verze 1.6 zahrnuté relativně malou podmnožinu rozhraní API .NET Standard. Mezi ty vyloučené byly mnoho rozhraní API, které se běžně používá v rozhraní .NET Framework nebo Xamarin. To komplikuje vývoje, protože vyžaduje, že vývojáři najít vhodné při nahrazování známá rozhraní API při vývoji aplikací a knihoven, které se zaměřují víc implementací rozhraní .NET. Rozhraní .NET Standard 2.0 řeší toto omezení přidáním více než 20 000 další rozhraní API, než byly k dispozici v rozhraní .NET Standard 1.6, předchozí verze standard. Seznam rozhraní API, která byla přidána do .NET Standard 2.0 najdete v tématu [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Některé nové funkce do <xref:System> obor názvů v rozhraní .NET Standard 2.0 patří:

- Podpora <xref:System.AppDomain> třídy.
- Lepší podporu pro práci s poli z další členy v <xref:System.Array> třídy.
- Lepší podporu pro práci s atributy z další členy v <xref:System.Attribute> třídy.
- Kalendář lepší podporu a další možnosti formátování pro <xref:System.DateTime> hodnoty.
- Další <xref:System.Decimal> zaokrouhlení funkce.
- Další funkce v <xref:System.Environment> třídy.
- Vylepšené kontroly nad systému uvolňování paměti prostřednictvím <xref:System.GC> třídy.
- Vylepšená podpora pro porovnání řetězců, výčet a normalizace v <xref:System.String> třídy.
- Podpora pro letní čas úpravy a časů přechodů v <xref:System.TimeZoneInfo.AdjustmentRule> a <xref:System.TimeZoneInfo.TransitionTime> třídy.
- K výraznému rozšíření funkčnosti v <xref:System.Type> třídy.
- Lepší podpora pro deserializaci objektů výjimek tak, že přidáte k výjimce konstruktor s <xref:System.Runtime.Serialization.SerializationInfo> a <xref:System.Runtime.Serialization.StreamingContext> parametry.

### <a name="support-for-net-framework-libraries"></a>Podporu pro knihovny rozhraní .NET Framework

Drtivou většinu knihoven cílit .NET Framework, nikoli .NET Standard. Většina výzev v těchto knihoven jsou však k rozhraním API, které jsou součástí rozhraní .NET Standard 2.0. Počínaje rozhraním .NET Standard 2.0, dostanete knihovny rozhraní .NET Framework z knihovny .NET Standard s využitím [kompatibility](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification). Tato vrstva kompatibility je transparentní pro vývojáře; nemusíte dělat nic výhod knihovny rozhraní .NET Framework.

Jeden požadavkem je, že rozhraní API volané knihovny tříd rozhraní .NET Framework musí být součástí rozhraní .NET Standard 2.0.

### <a name="support-for-visual-basic"></a>Podpora jazyka Visual Basic

Teď můžete vyvíjet knihovny .NET Standard v jazyce Visual Basic. Pro vývojáře v jazyce Visual Basic pomocí Visual Studio 2017 verze 15.3 nebo novější s .NET Core zatížení nainstalované Visual Studio teď obsahuje šablony knihovna tříd rozhraní .NET Standard. Pro vývojáře jazyka Visual Basic, kteří používají další nástroje pro vývoj a prostředí, můžete použít [dotnet nové](../../core/tools/dotnet-new.md) příkaz pro vytvoření projektu knihovny .NET Standard. Další informace najdete v tématu [Podpora nástrojů pro knihovny .NET Standard](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Podpora nástrojů pro knihovny .NET Standard

Ve verzi 2.0 rozhraní .NET Core a .NET Standard 2.0, obě sady Visual Studio 2017 a [.NET Core rozhraní příkazového řádku (CLI)](../../core/tools/index.md) patří podpora nástrojů pro vytváření knihovny .NET Standard.

Při instalaci sady Visual Studio s **vývoj pro různé platformy .NET Core** úlohy, můžete vytvořit projekt knihovny .NET Standard 2.0 pomocí šablony projektu, jak ukazuje následující obrázek:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Přidejte novou .NET Standard projekt knihovny](./media/std-project-cs.png)

Pokud používáte .NET Core CLI, následující [dotnet nové](../../core/tools/dotnet-new.md) příkaz vytvoří projekt knihovny tříd, který cílí na .NET Standard 2.0:

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Přidejte novou .NET Standard projekt knihovny](./media/std-project-vb.png)

Pokud používáte .NET Core CLI, následující [dotnet nové](../../core/tools/dotnet-new.md) příkaz vytvoří projekt knihovny tříd, který cílí na .NET Standard 2.0:

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Viz také:

- [.NET Standard](../net-standard.md)
- [Představujeme .NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
