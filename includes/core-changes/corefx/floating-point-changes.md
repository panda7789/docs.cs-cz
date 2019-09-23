---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182065"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Změnilo se formátování a chování při analýze s plovoucí desetinnou čárkou.

Chování při analýze a formátování plovoucí desetinné čárky <xref:System.Double> ( <xref:System.Single> podle typu a) nyní dodržuje standard IEEE.

#### <a name="change-description"></a>Změnit popis

V rozhraní .NET Core 2,2 a starších verzích, formátování <xref:System.Double.ToString%2A?displayProperty=nameWithType> pomocí <xref:System.Single.ToString%2A?displayProperty=nameWithType>a a analýzy <xref:System.Single.TryParse%2A?displayProperty=nameWithType> pomocí <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType>, a nejsou kompatibilní se standardem IEEE. V důsledku toho není možné zaručit, že hodnota převedená s jakýmkoli podporovaným standardním nebo vlastním formátovacím řetězcem. U některých vstupů může být pokus o analýzu formátované hodnoty neúspěšný a pro ostatní se analyzovaná hodnota nerovná původní hodnotě.

Počínaje .NET Core 3,0 jsou operace analýzy a formátování kompatibilní se standardem IEEE 754. Tím je zajištěno, že chování typů s plovoucí desetinnou čárkou v rozhraní .NET odpovídá NORMám standardu IEEE, jako je například C#. Další informace najdete v příspěvku na blogu k [analýze a formátování s plovoucí desetinnou čárkou v .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Část "potenciální dopad na stávající kód" v rámci analýzy s plovoucí desetinnou čárkou [a vylepšení formátování na blogu .NET core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) navrhuje změny kódu, pokud zjistíte, že dojde ke změně chování v porovnání s aplikacemi .net Core 2,2 obecně, To zahrnuje použití jiného standardního nebo vlastního řetězce formátu k vykonání požadovaného chování. Některé výsledky nemusí mít alternativní řešení, pokud byly dříve nesprávné.

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
