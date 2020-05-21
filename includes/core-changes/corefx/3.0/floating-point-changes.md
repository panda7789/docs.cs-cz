---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721448"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Změnilo se formátování a chování při analýze s plovoucí desetinnou čárkou.

Chování při analýze a formátování plovoucí desetinné čárky (podle <xref:System.Double> <xref:System.Single> typu a) nyní dodržuje standard IEEE.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 2,2 a starších verzích, formátování pomocí <xref:System.Double.ToString%2A?displayProperty=nameWithType> a a <xref:System.Single.ToString%2A?displayProperty=nameWithType> analýzy pomocí,, a <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> nejsou kompatibilní se standardem IEEE. V důsledku toho není možné zaručit, že hodnota převedená s jakýmkoli podporovaným standardním nebo vlastním formátovacím řetězcem. U některých vstupů může být pokus o analýzu formátované hodnoty neúspěšný a pro ostatní se analyzovaná hodnota nerovná původní hodnotě.

Počínaje .NET Core 3,0 jsou operace analýzy a formátování kompatibilní se standardem IEEE 754. Tím je zajištěno, že chování typů s plovoucí desetinnou čárkou v rozhraní .NET odpovídá jazyku standardu IEEE, jako je C#. Další informace najdete v příspěvku na blogu k [analýze a formátování s plovoucí desetinnou čárkou v .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Část "potenciální dopad na stávající kód" v rámci analýzy s plovoucí desetinnou čárkou [a vylepšení formátování na blogu .NET core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) navrhuje změny kódu, pokud v porovnání s aplikacemi .net Core 2,2 nastáváte se změnou chování, pokud se obvykle projeví při použití jiného standardního nebo vlastního formátovacího řetězce, který vynutil požadované chování. Některé výsledky nemusí mít alternativní řešení, pokud byly dříve nesprávné.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
