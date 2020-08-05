---
ms.openlocfilehash: 74c3d3247912dcd638a9379d54e682967c5e400b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302702"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a>Rozhraní API globalizace používají knihovny ICU ve Windows

.NET 5,0 a novější verze používají [mezinárodní komponenty pro knihovny Unicode (ICU)](http://site.icu-project.org/home) pro funkce globalizace při spuštění ve Windows 10 se dá 2019 Update nebo novějším.

#### <a name="change-description"></a>Popis změny

Dříve knihovny .NET používaly rozhraní API pro [národní jazykovou podporu (NLS)](/windows/win32/intl/national-language-support) pro funkce globalizace. Například funkce NLS byly použity k získání dat jazykové verze, jako jsou například vzory formátu data a času, porovnávání řetězců a provádění řetězcového střeva v příslušné jazykové verzi.

Pokud je aplikace spuštěná ve Windows 10, která se spouští v rozhraní .NET 5,0, 2019 může aktualizace nebo novější knihovna .NET používat rozhraní API globalizace [ICU](http://site.icu-project.org/home) . Windows 10 může 2019 aktualizace a novější verze dodávané s nativní knihovnou ICU. Pokud modul runtime .NET nemůže načíst ICU, místo toho použije NLS.

Tato změna byla představena ze dvou důvodů:

- Aplikace mají stejné chování globalizace napříč platformami, včetně Linux, macOS a Windows.
- Aplikace mohou řídit chování globalizace pomocí vlastních ICU knihoven.

#### <a name="version-introduced"></a>Představená verze

.NET 5,0 Preview 4

#### <a name="recommended-action"></a>Doporučená akce

V rámci vývojáře není vyžadována žádná akce. Nicméně pokud chcete i nadále používat rozhraní API globalizace NLS, můžete nastavit přepínač za [běhu](../../../../docs/core/run-time-config/globalization.md#nls) pro vrácení tohoto chování. Další informace o dostupných přepínačích naleznete v článku [globalizace a ICU v .NET](/dotnet/standard/globalization-localization/globalization-icu) .

#### <a name="category"></a>Kategorie

Globalizace

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- Většina typů v <xref:System.Globalization?displayProperty=fullName> oboru názvů

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
