---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344462"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>Api, která sestavy verze nyní sestavy produktu a není verze souboru

Mnoho rozhraní API, která vracejí verze v rozhraní .NET Core, nyní vrací verzi produktu, nikoli verzi souboru.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 2.2 a <xref:System.Environment.Version?displayProperty=nameWithType>předchozích verzích odrážejí verze souboru metody jako , <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>a dialogové okno vlastností souboru pro sestavení .NET Core. Počínaje rozhraním .NET Core 3.0 odrážejí verzi produktu.

Následující obrázek znázorňuje rozdíl v informacích o verzi pro sestavení *System.Runtime.dll* pro rozhraní .NET Core 2.2 (vlevo) a .NET Core 3.0 (vpravo), jak je zobrazeno v dialogovém okně vlastností souboru **průzkumníka Windows.**

![Rozdíl v informacích o verzi produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Žádné. Tato změna by měla provést detekci verze intuitivní spíše než tupý.

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
