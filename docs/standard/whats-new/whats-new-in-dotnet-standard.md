---
title: Novinky v rozhraní .NET Standard
description: Tento článek shrnuje nové funkce a vylepšení, které najdete v každé nové verzi .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: a90df0360211c3b02f4f2d8697890180099c5807
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921062"
---
# <a name="whats-new-in-the-net-standard"></a>Novinky v rozhraní .NET Standard

.NET Standard je formální specifikace, která definuje sadu rozhraní API s verzí, která musí být dostupná v implementacích .NET, které vyhovují této verzi standardu. .NET Standard je cílena na vývojáře knihovny. Knihovna, která cílí na verzi .NET Standard, se dá použít v jakékoli implementaci .NET Framework, .NET Core nebo Xamarin, která podporuje tuto verzi standardu.

Nejnovější verze .NET Standard je 2,0. Je součástí sady .NET Core 2,0 SDK a také se sadou Visual Studio 2017 verze 15,3 s nainstalovanou úlohou .NET Core.

## <a name="supported-net-implementations"></a>Podporované implementace .NET

.NET Standard 2,0 jsou podporovány následujícími implementacemi rozhraní .NET:

- .NET Core 2,0 nebo novější
- .NET Framework 4.6.1 nebo novější
- Mono 5,4 nebo novější
- Xamarin. iOS 10,14 nebo novější
- Xamarin. Mac 3,8 nebo novější
- Xamarin. Android 8,0 nebo novější
- Univerzální platforma Windows 10.0.16299 nebo novější

## <a name="whats-new-in-the-net-standard-20"></a>Co je nového v .NET Standard 2,0

.NET Standard 2,0 obsahuje následující nové funkce:

### <a name="a-vastly-expanded-set-of-apis"></a>Obrovské rozšířené sady rozhraní API

Až do verze 1,6, .NET Standard zahrnuli relativně malou podmnožinu rozhraní API. Mezi vyloučenými z těchto možností bylo mnoho rozhraní API, které se běžně používalo v .NET Framework nebo Xamarin. To ztěžuje vývoj, protože vyžaduje, aby vývojáři našli vhodné náhrady pro známá rozhraní API při vývoji aplikací a knihoven, které cílí na více implementací rozhraní .NET. .NET Standard 2,0 řeší toto omezení přidáním více než 20 000 více rozhraní API, než je k dispozici v .NET Standard 1,6, předchozí verze standardu. Seznam rozhraní API, která byla přidána do .NET Standard 2,0, najdete v článku [.NET Standard 2,0 vs 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Mezi doplňky <xref:System> oboru názvů v .NET Standard 2,0 patří:

- Podpora pro třídu <xref:System.AppDomain>.
- Lepší podpora pro práci s poli z dalších členů třídy <xref:System.Array>.
- Lepší podpora pro práci s atributy z dalších členů ve třídě <xref:System.Attribute>.
- Lepší podpora kalendáře a další možnosti formátování pro <xref:System.DateTime> hodnoty.
- Další funkce zaokrouhlování <xref:System.Decimal>.
- Další funkce ve třídě <xref:System.Environment>.
- Vylepšená kontrola uvolňování paměti prostřednictvím <xref:System.GC> třídy.
- Rozšířená podpora pro porovnání řetězců, výčet a normalizaci ve třídě <xref:System.String>.
- Podpora pro letní čas a časy přechodu v <xref:System.TimeZoneInfo.AdjustmentRule> a <xref:System.TimeZoneInfo.TransitionTime>ch třídách.
- Výrazně vylepšené funkce třídy <xref:System.Type>.
- Lepší podpora pro deserializaci objektů výjimek přidáním konstruktoru výjimky s parametry <xref:System.Runtime.Serialization.SerializationInfo> a <xref:System.Runtime.Serialization.StreamingContext>.

### <a name="support-for-net-framework-libraries"></a>Podpora pro knihovny .NET Framework

Většina knihoven cílí na .NET Framework místo .NET Standard. Většina volání v těchto knihovnách je však rozhraní API, která jsou součástí .NET Standard 2,0. Počínaje .NET Standard 2,0 můžete k .NET Framework knihoven přistupovat z knihovny .NET Standard pomocí [překrytí kompatibility](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification). Tato vrstva kompatibility je pro vývojáře transparentní; nemusíte nic dělat, abyste mohli využívat .NET Framework knihoven.

Jediným požadavkem je, aby rozhraní API volaná knihovnou tříd .NET Framework měla být zahrnutá do .NET Standard 2,0.

### <a name="support-for-visual-basic"></a>Podpora Visual Basic

Nyní můžete vyvíjet knihovny .NET Standard v Visual Basic. Pro Visual Basic vývojářů, kteří používají Visual Studio 2017 verze 15,3 nebo novější s nainstalovanou úlohou .NET Core, Visual Studio teď obsahuje .NET Standard šablonu knihovny tříd. Pro Visual Basic vývojářů, kteří používají jiné vývojové nástroje a prostředí, můžete pomocí příkazu [dotnet New](../../core/tools/dotnet-new.md) vytvořit projekt knihovny .NET Standard. Další informace najdete v tématu [Podpora nástrojů pro knihovny .NET Standard](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Podpora nástrojů pro knihovny .NET Standard

S vydáním .NET Core 2,0 a .NET Standard 2,0 aplikace Visual Studio 2017 i [.NET Core CLI](../../core/tools/index.md) zahrnují podporu nástrojů pro vytváření knihoven .NET Standard.

Pokud nainstalujete Visual Studio s úlohou **vývoje .NET Core pro různé platformy** , můžete vytvořit projekt knihovny .NET Standard 2,0 pomocí šablony projektu, jak ukazuje následující obrázek:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Přidat nový projekt knihovny .NET Standard](./media/std-project-cs.png)

Pokud používáte .NET Core CLI, následující příkaz [dotnet New](../../core/tools/dotnet-new.md) vytvoří projekt knihovny tříd, který cílí na .NET Standard 2,0:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Přidat nový projekt knihovny .NET Standard](./media/std-project-vb.png)

Pokud používáte .NET Core CLI, následující příkaz [dotnet New](../../core/tools/dotnet-new.md) vytvoří projekt knihovny tříd, který cílí na .NET Standard 2,0:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Viz také:

- [.NET Standard](../net-standard.md)
- [Představujeme .NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
