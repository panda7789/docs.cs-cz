---
title: Co je nového ve standardní rozhraní .NET
description: Tento článek shrnuje nové funkce a vylepšení v každé nové verze .NET Standard nalezen.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e422e6ff65439d105020a6305b66a8192586a8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591486"
---
# <a name="whats-new-in-the-net-standard"></a>Co je nového ve standardní rozhraní .NET

.NET Standard je formální specifikaci, která definuje sadu rozhraní API, která musí být k dispozici na implementace rozhraní .NET, které jsou v souladu s touto verzí standardní verzí. .NET Standard je cílena na vývojáře knihovny. Knihovna, která cílí na .NET Standard verzi lze použít v rozhraní .NET Framework, .NET Core nebo Xamarin implementace, která podporuje tuto verzi standard.

Nejnovější verze .NET Standard je 2.0. Je zahrnut pomocí .NET SDK 2.0 jádra, a také s Visual Studio 2017 verze 15.3 se zatížením .NET Core nainstalována.

## <a name="supported-net-implementations"></a>Podporované implementace rozhraní .NET

Rozhraní .NET 2.0 standardní podporuje následující implementace rozhraní .NET:

- .NET core 2.0 nebo novější
- Rozhraní .NET framework 4.6.1 nebo novější
- Mono 5.4 nebo novější
- Xamarin.iOS 10.14 nebo novější
- Xamarin.Mac 3.8 nebo novější
- Xamarin.Android 8.0 nebo novější
- Univerzální platformu Windows 10.0.16299 nebo novější

## <a name="whats-new-in-the-net-standard-20"></a>Co je nového v rozhraní .NET 2.0 Standard

Rozhraní .NET 2.0 standardní obsahuje následující nové funkce:

### <a name="a-vastly-expanded-set-of-apis"></a>Významně rozšířená sada rozhraní API

Prostřednictvím verzi 1.6 zahrnuty .NET Standard poměrně malou podmnožinu rozhraní API. Mezi ty vyloučené byly mnoho rozhraní API, které byly často používány v rozhraní .NET Framework nebo Xamarin. To komplikuje vývoj, protože vyžaduje, že vývojáři najít vhodný nahrazení pro známé rozhraní API při vývoji aplikací a knihovny, které cílí více implementace rozhraní .NET. Rozhraní .NET 2.0 standardní řeší toto omezení přidáním přes 20 000 další rozhraní API, než byly k dispozici v rozhraní .NET standardní 1.6, předchozí verzi standard. Seznam rozhraní API, které jsou přidané do standardní rozhraní .NET 2.0, naleznete v části [standardní rozhraní .NET 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Některé doplňky k <xref:System> oboru názvů v rozhraní .NET 2.0 standardní patří:

- Podpora pro <xref:System.AppDomain> třídy.
- Lepší podpory pro práci s poli od další členové <xref:System.Array> třídy.
- Lepší podpory pro práci s atributy z další členové <xref:System.Attribute> třídy.
- Lépe kalendář podpory a další možnosti formátování <xref:System.DateTime> hodnoty.
- Další <xref:System.Decimal> zaokrouhlení funkce.
- Další funkce v <xref:System.Environment> třídy.
- Rozšířené kontrolu nad uvolňování prostřednictvím <xref:System.GC> třídy.
- Rozšířenou podporu pro porovnání řetězců, výčet a normalizaci v <xref:System.String> třídy.
- Podpora pro letní čas úpravy a doby přechodu v <xref:System.TimeZoneInfo.AdjustmentRule> a <xref:System.TimeZoneInfo.TransitionTime> třídy.
- Výrazně rozšířené funkce v <xref:System.Type> třídy.
- Lepší podpory pro deserializaci objektů výjimek přidáním k výjimce konstruktor s <xref:System.Runtime.Serialization.SerializationInfo> a <xref:System.Runtime.Serialization.StreamingContext> parametry.

### <a name="support-for-net-framework-libraries"></a>Podporu pro knihovny rozhraní .NET Framework

Naprostou většinu knihovny cílí rozhraní .NET Framework místo .NET Standard. Většina volání v tyto knihovny jsou však k rozhraním API, které jsou obsažené v rozhraní .NET 2.0 standardní. Od verze rozhraní .NET 2.0 standardní, dostanete knihovny rozhraní .NET Framework z knihovny .NET Standard pomocí [kompatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification). Tuto vrstvu kompatibility je transparentní pro vývojáře; nemusíte dělat nic využívat výhod knihovnách rozhraní .NET Framework.

Jeden požadavek je, že rozhraní API volat knihovna tříd rozhraní .NET Framework musí být součástí standardní rozhraní .NET 2.0.

### <a name="support-for-visual-basic"></a>Podpora jazyka Visual Basic

Nyní můžete vyvíjet .NET standardní knihovny v jazyce Visual Basic. Pro vývojáře jazyka Visual Basic, Visual Studio 2017 verze 15.3 pomocí nebo novější s .NET Core zatížení nainstalované Visual Studio teď obsahuje šablonu standardní knihovna tříd rozhraní .NET. Pro vývojáře jazyka Visual Basic, kteří používají jiné nástroje pro vývoj a prostředí, můžete použít [dotnet nové](../../core/tools/dotnet-new.md) příkaz k vytvoření standardní knihovny .NET projektu. Další informace najdete v tématu [Podpora nástrojů pro rozhraní .NET standardní knihovny](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Podpora nástrojů pro rozhraní .NET standardní knihovny

Verze rozhraní .NET Core 2.0 a .NET standardní 2.0, jak Visual Studio 2017 a [.NET Core rozhraní příkazového řádku (CLI)](../../core/tools/index.md) patří podpora nástrojů pro vytváření .NET standardní knihovny.

Pokud nainstalujete Visual Studio s **vývoj pro různé platformy .NET Core** zatížení, můžete vytvořit projekt knihovny .NET standardní 2.0 pomocí šablony projektu, jak ukazuje následující obrázek:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Přidat nové standardní rozhraní .NET projektu knihovny](./media/std-project-cs.png)

Pokud používáte rozhraní .NET Core příkazového řádku, následující [dotnet nové](../../core/tools/dotnet-new.md) příkaz vytvoří projektu knihovny tříd, která cílí rozhraní .NET 2.0 standardní:

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Přidat nové standardní rozhraní .NET projektu knihovny](./media/std-project-vb.png)

Pokud používáte rozhraní .NET Core příkazového řádku, následující [dotnet nové](../../core/tools/dotnet-new.md) příkaz vytvoří projektu knihovny tříd, která cílí rozhraní .NET 2.0 standardní:

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Viz také

[.NET Standard](../net-standard.md)  
[Představení Standard rozhraní .NET](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
