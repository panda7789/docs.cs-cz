---
ms.openlocfilehash: 204fe32ec8b7fbaab89e37d7e761469212091728
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237929"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant nebo Contract.Requires\<TException> nepovažují String.IsNullOrEmpty za čistý

|   |   |
|---|---|
|Podrobnosti|Pro aplikace, které cílí na rozhraní .NET Framework 4.6.1, pokud invariantní kontrakt nebo <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> kontrakt s podmínkou pro <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> volání <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody vydává vypalovač emitátor upozornění kompilátoru CC1036: &quot;Zjištěné volání metody System.String.IsNullOrWhteSpace(System.String)' bez [Pure] v metodě. &quot; Toto je upozornění kompilátoru spíše než chyba kompilátoru.|
|Návrh|Toto chování bylo vyřešeno v [#339 problém GitHub](https://github.com/Microsoft/CodeContracts/issues/339). Chcete-li toto upozornění odstranit, můžete stáhnout a zkompilovat aktualizovanou verzi zdrojového kódu pro nástroj Kontrakty kódu z [GitHubu](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Informace o stažení se nacházejí v dolní části stránky.|
|Rozsah|Vedlejší|
|Version|4.6.1|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
