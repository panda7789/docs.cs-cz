---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021789"
---
### <a name="change-in-default-value-of-useshellexecute"></a>Změna výchozí hodnoty useShellExecute

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>má výchozí hodnotu `false` na .NET Core. V rozhraní .NET Framework `true`je jeho výchozí hodnota .

#### <a name="change-description"></a>Popis změny

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>umožňuje spustit aplikaci přímo, například s `Process.Start("mspaint.exe")` kódem, jako je například spuštění programu Malování. Umožňuje také nepřímo spustit přidruženou aplikaci, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true`pokud je nastavena na . V rozhraní .NET Framework <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> je `true`výchozí hodnota pro `Process.Start("mytextfile.txt")` , což znamená, že kód, jako je spuštění programu Poznámkový blok, pokud jste k tomuto editoru přidružili soubory *TXT.* Chcete-li zabránit nepřímému spuštění aplikace v <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> rozhraní `false`.NET Framework, musíte explicitně nastavit . Na .NET Core je <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`výchozí hodnota pro . To znamená, že ve výchozím nastavení nejsou `Process.Start`přidružené aplikace spuštěny při volání .

Tato změna byla zavedena v .NET Core z důvodů výkonu. Obvykle se <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> používá ke spuštění aplikace přímo. Spuštění aplikace přímo nemusí zahrnovat prostředí Windows a vznikají související náklady na výkon. Chcete-li tento výchozí případ urychlit, změní <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> jádro `false`.NET výchozí hodnotu na . Můžete se přihlásit do pomalejší cesty, pokud ji potřebujete.

#### <a name="version-introduced"></a>Zavedená verze

2.1

> [!NOTE]
> V dřívějších verzích rozhraní `UseShellExecute` .NET Core nebyla implementována pro systém Windows.

#### <a name="recommended-action"></a>Doporučená akce

Pokud vaše aplikace závisí na staré <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> chování, `true` volání <xref:System.Diagnostics.ProcessStartInfo> s nastavenou na objekt.

#### <a name="category"></a>Kategorie

Základní knihovny .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
