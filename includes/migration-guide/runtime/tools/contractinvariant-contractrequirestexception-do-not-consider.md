---
ms.openlocfilehash: 29c66edfeb1690199aac39b9c3076d161b2075d4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621151"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Kontrakt. invariantní nebo kontrakt. vyžaduje, \<TException> aby nebral řetězec. IsNullOrEmpty na hodnotu Pure.

#### <a name="details"></a>Podrobnosti

Pro aplikace, které cílí na .NET Framework 4.6.1, pokud invariantní smlouva pro <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> nebo smlouvu předběžných podmínek pro <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> volání <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody, Rewrite vygeneruje upozornění kompilátoru CC1036: &quot; zjištěno volání metody System. String. IsNullOrWhteSpace (System. String) bez [Pure] v metodě. &quot; Toto je upozornění kompilátoru, nikoli Chyba kompilátoru.

#### <a name="suggestion"></a>Návrh

Toto chování bylo vyřešeno [#339 problému na GitHubu](https://github.com/Microsoft/CodeContracts/issues/339). Chcete-li odstranit toto upozornění, můžete stáhnout a zkompilovat aktualizovanou verzi zdrojového kódu pro nástroj Code Contracts z [GitHubu](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Informace o stažení najdete v dolní části stránky.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6.1|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
