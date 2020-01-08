---
ms.openlocfilehash: 7c0930f6606aa96d2863dc740aef8e9cab724b37
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344880"
---
### <a name="change-in-default-value-of-useshellexecute"></a>Změna výchozí hodnoty UseShellExecute objektu Process

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> má výchozí hodnotu `false` v .NET Core. V .NET Framework je výchozí hodnota `true`.

#### <a name="change-description"></a>Popis změny

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> umožňuje spustit aplikaci přímo, například pomocí kódu, jako je například `Process.Start("mspaint.exe")`, který spouští funkci malování. Umožňuje vám také nepřímo spustit přidruženou aplikaci, pokud je <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> nastaveno na `true`. V .NET Framework je výchozí hodnota pro <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true`, což znamená, že kód, jako je například `Process.Start("mytextfile.txt")`, by spouštěl Poznámkový blok, pokud jste přidružil soubory *. txt* pomocí tohoto editoru. Chcete-li zabránit nepřímo spustit aplikaci na .NET Framework, je nutné explicitně nastavit <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> na `false`. V .NET Core je výchozí hodnota pro <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`. To znamená, že ve výchozím nastavení nejsou přidružené aplikace spouštěny při volání `Process.Start`.

Tato změna byla představena v rozhraní .NET Core z důvodů výkonu. Obvykle se <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> používá ke spuštění aplikace přímo. Přímým spouštěním aplikace není nutné zahrnovat prostředí systému Windows a získat související náklady na výkon. Aby byl tento výchozí případ rychlejší, .NET Core změní výchozí hodnotu <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> na `false`. Pokud ho budete potřebovat, můžete se na pomalejší cestu rozhodnout.

#### <a name="version-introduced"></a>Představená verze

2.1

> [!NOTE]
> V dřívějších verzích rozhraní .NET Core `UseShellExecute` nebyl implementován pro systém Windows.

#### <a name="recommended-action"></a>Doporučená akce

Pokud vaše aplikace spoléhá na staré chování, zavolejte <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> s <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> nastavenou na `true` na objektu <xref:System.Diagnostics.ProcessStartInfo>.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
