---
title: Novinky v rozhraní .NET Standard
description: Tento článek shrnuje nové funkce a vylepšení, které se nacházejí v každé nové verzi standardu .NET.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: a90df0360211c3b02f4f2d8697890180099c5807
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921062"
---
# <a name="whats-new-in-the-net-standard"></a>Novinky v rozhraní .NET Standard

Standard .NET Je formální specifikace, která definuje sadu rozhraní API s verzí, která musí být k dispozici na implementacích .NET, které jsou v souladu s touto verzí standardu. Standard .NET je určen pro vývojáře knihoven. Knihovnu, která cílí na verzi .NET Standard, lze použít v libovolné implementaci rozhraní .NET Framework, .NET Core nebo Xamarin, která tuto verzi standardu podporuje.

Nejnovější verze standardu .NET je 2.0. Je součástí sady .NET Core 2.0 SDK a také s visual studio 2017 verze 15.3 s nainstalovanou úlohou .NET Core.

## <a name="supported-net-implementations"></a>Podporované implementace rozhraní .NET

Standard .NET 2.0 je podporován následujícími implementacemi rozhraní .NET:

- .NET Core 2.0 nebo novější
- Rozhraní .NET Framework 4.6.1 nebo novější
- Mono 5.4 nebo novější
- Xamarin.iOS 10.14 nebo novější
- Xamarin.Mac 3.8 nebo novější
- Xamarin.Android 8.0 nebo novější
- Univerzální platforma Windows 10.0.16299 nebo novější

## <a name="whats-new-in-the-net-standard-20"></a>Co je nového ve standardu .NET Standard 2.0

Standard .NET 2.0 obsahuje následující nové funkce:

### <a name="a-vastly-expanded-set-of-apis"></a>Výrazně rozšířená sada api

Prostřednictvím verze 1.6 standard .NET zahrnoval poměrně malou podmnožinu rozhraní API. Mezi vyloučenými bylo mnoho rozhraní API, které se běžně používaly v rozhraní .NET Framework nebo Xamarin. To komplikuje vývoj, protože vyžaduje, aby vývojáři najít vhodné náhrady za známé rozhraní API při vývoji aplikací a knihoven, které se zaměřují na více implementací .NET. Standard .NET 2.0 řeší toto omezení přidáním více než 20 000 více rozhraní API, než bylo k dispozici v rozhraní .NET Standard 1.6, předchozí verze standardu. Seznam rozhraní API, které byly přidány do standardu .NET Standard 2.0, naleznete v tématu [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Některé dodatky k <xref:System> oboru názvů v rozhraní .NET Standard 2.0 zahrnují:

- Podpora pro <xref:System.AppDomain> třídu.
- Lepší podpora pro práci s poli <xref:System.Array> z dalších členů ve třídě.
- Lepší podpora pro práci s atributy <xref:System.Attribute> z dalších členů ve třídě.
- Lepší podpora kalendáře a další <xref:System.DateTime> možnosti formátování hodnot.
- Další <xref:System.Decimal> funkce zaokrouhlení.
- Další funkce ve <xref:System.Environment> třídě.
- Rozšířená kontrola nad uvolňování <xref:System.GC> prostřednictvím třídy.
- Rozšířená podpora pro porovnání řetězců, výčt u <xref:System.String> a normalizaci ve třídě.
- Podpora pro úpravy letního času <xref:System.TimeZoneInfo.AdjustmentRule> <xref:System.TimeZoneInfo.TransitionTime> a doby přechodu ve třídách a.
- Výrazně vylepšená funkčnost <xref:System.Type> ve třídě.
- Lepší podpora pro deserializaci objektů výjimek přidáním konstruktoru výjimky s <xref:System.Runtime.Serialization.SerializationInfo> parametry a <xref:System.Runtime.Serialization.StreamingContext> parametry.

### <a name="support-for-net-framework-libraries"></a>Podpora knihoven rozhraní .NET Framework

Drtivá většina knihoven cílí na rozhraní .NET Framework místo na standard .NET. Většina volání v těchto knihovnách jsou však rozhraní API, které jsou zahrnuty v .NET Standard 2.0. Počínaje rozhraním .NET Standard 2.0 můžete přistupovat ke knihovnám rozhraní .NET Framework z knihovny .NET Standard pomocí [překrytí kompatibility](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification). Tato vrstva kompatibility je pro vývojáře průhledná. nemusíte dělat nic, abyste mohli využít výhod knihoven rozhraní .NET Framework.

Jediným požadavkem je, že rozhraní API volaná knihovnou tříd rozhraní .NET Framework musí být zahrnuta do standardu .NET Standard 2.0.

### <a name="support-for-visual-basic"></a>Podpora jazyka Visual Basic

Nyní můžete vyvíjet knihovny .NET Standard v jazyce Visual Basic. Pro vývojáře jazyka Visual Basic, kteří používají Visual Studio 2017 verze 15.3 nebo novější s nainstalovaným zatížením jádra .NET, visual studio nyní obsahuje šablonu knihovny tříd .NET Standard. Pro vývojáře jazyka, kteří používají jiné vývojové nástroje a prostředí, můžete použít [dotnet new](../../core/tools/dotnet-new.md) příkaz k vytvoření projektu knihovny .NET Standard. Další informace naleznete v [části Podpora nástrojů pro knihovny .NET Standard](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Podpora nástrojů pro knihovny .NET Standard

S vydáním .NET Core 2.0 a .NET Standard 2.0, Visual Studio 2017 a [.NET Core CLI](../../core/tools/index.md) zahrnují podporu nástrojů pro vytváření knihoven .NET Standard.

Pokud instalujete Visual Studio s **úlohou vývoje napříč platformami .NET Core,** můžete vytvořit projekt knihovny .NET Standard 2.0 pomocí šablony projektu, jak ukazuje následující obrázek:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

![Přidat nový projekt knihovny .NET Standard](./media/std-project-cs.png)

Pokud používáte rozhraní PŘÍKAZOVÉHO PŘÍKAZU Jádra .NET, následující [dotnet new](../../core/tools/dotnet-new.md) příkaz vytvoří projekt knihovny tříd, který cílí na rozhraní .NET Standard 2.0:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![Přidat nový projekt knihovny .NET Standard](./media/std-project-vb.png)

Pokud používáte rozhraní PŘÍKAZOVÉHO PŘÍKAZU Jádra .NET, následující [dotnet new](../../core/tools/dotnet-new.md) příkaz vytvoří projekt knihovny tříd, který cílí na rozhraní .NET Standard 2.0:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Viz také

- [.NET Standard](../net-standard.md)
- [Představujeme standard .NET](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
