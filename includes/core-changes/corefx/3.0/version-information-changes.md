---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344462"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>Rozhraní API, která verze sestav nyní hlásí produkt a nikoli verzi souboru

Mnoho rozhraní API, které vrací verze v rozhraní .NET Core, nyní vrátí verzi produktu místo verze souboru.

#### <a name="change-description"></a>Popis změny

V .NET Core 2,2 a předchozích verzích metody jako <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>a dialog vlastností souboru pro sestavení .NET Core odrážejí verzi souboru. Počínaje .NET Core 3,0 se odrážejí verze produktu.

Následující obrázek znázorňuje rozdíl v informacích o verzi pro sestavení *System. Runtime. dll* pro .net Core 2,2 (vlevo) a .net Core 3,0 (na pravé straně), jak je zobrazeno v dialogovém okně Vlastnosti souboru v **Průzkumníkovi Windows** .

![Rozdíl v informacích o verzi produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="recommended-action"></a>Doporučená akce

Žádné Tato změna by měla v případě, že by byla detekce verze intuitivní, spíše než obtuse.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
