---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568208"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Změněno formátování a analýza s plovoucí desetinnou tázkem.

Chování analýzy a formátování s plovoucí <xref:System.Double> desetinnou tázkem (podle <xref:System.Single> a typů) je nyní kompatibilní s IEEE.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 2.2 a starších <xref:System.Single.ToString%2A?displayProperty=nameWithType>verzích formátování <xref:System.Double.Parse%2A?displayProperty=nameWithType>s <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Double.ToString%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType>a <xref:System.Single.TryParse%2A?displayProperty=nameWithType> , a analýza s , , a nejsou kompatibilní s IEEE. V důsledku toho není možné zaručit, že hodnota bude roundtrip s všechny podporované standardní nebo vlastní formátovací řetězec. U některých vstupů může pokus o analýzu formátované hodnoty selhat a u jiných se analyzovaná hodnota nerovná původní hodnotě.

Počínaje rozhraním .NET Core 3.0 jsou operace analýzy a formátování kompatibilní s rozhraním IEEE 754. Tím je zajištěno, že chování typů s plovoucí desetinnou desetinnou tácek v rozhraní .NET odpovídá chování jazyků kompatibilních s IEEE, jako je například C#. Další informace naleznete v [vylepšení analýzy a formátování s plovoucí desetinnou tácející](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) v příspěvku blogu .NET Core 3.0.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Část "Potenciální dopad na existující kód" vylepšení [analýzy a formátování s plovoucí desetinnou čárkou v](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) příspěvku blogu .NET Core 3.0 navrhuje změny kódu, pokud zaznamenáte změnu chování ve srovnání s aplikacemi .NET Core 2.2 Obecně to zahrnuje použití jiného standardního nebo vlastního formátovacího řetězce k vynucení požadovaného chování. Některé výsledky nemusí mít řešení, pokud byly dříve nesprávné.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
