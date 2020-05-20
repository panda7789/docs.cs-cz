---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420422"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a>Process. StartInfo vyvolá InvalidOperationException pro procesy, které jste nespustili.

Čtení <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> vlastnosti pro procesy, které nespustil váš kód, vyvolá výjimku <xref:System.InvalidOperationException> .

#### <a name="change-description"></a>Popis změny

V .NET Framework přístup k <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> vlastnosti pro procesy, které nespustil váš kód, vrátí zástupný <xref:System.Diagnostics.ProcessStartInfo> objekt. Zástupný objekt obsahuje výchozí hodnoty pro všechny jeho vlastnosti s výjimkou <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> .

Pokud v .NET Core 1,0 přečtete <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> vlastnost pro proces, který jste nespustili (to znamená voláním <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> ), <xref:System.InvalidOperationException> je vyvolána výjimka.

#### <a name="version-introduced"></a>Představená verze

1.0

#### <a name="recommended-action"></a>Doporučená akce

Nepoužívejte přístup k <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> vlastnosti pro procesy, které nespustily váš kód. Například tuto vlastnost nepřečtete pro procesy, které vrátí <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> .

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
