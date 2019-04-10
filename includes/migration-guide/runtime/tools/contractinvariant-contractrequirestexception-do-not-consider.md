---
ms.openlocfilehash: 3cff9bfbb1adb6004921903276d75f641c7e703c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234152"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant nebo Contract.Requires\<TException > Neberte v úvahu String.IsNullOrEmpty být čistě

|   |   |
|---|---|
|Podrobnosti|Pro aplikace, které cílí .NET Framework 4.6.1, pokud invariantní smlouvu aktivoval pro <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> nebo předběžné podmínky smlouvy pro <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> volání <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody RW generuje kompilátor varování CC1036: &quot;Zjištěno volání metody <xref:System.String.IsNullOrWhiteSpace%2A?displayProperty=nameWithType> bez [prázdná] v metodě.&quot; Toto je kompilátor varování spíše než chybu kompilátoru.|
|Doporučení|Toto chování se zákazníky a vyřešené v [339 # problém Githubu](https://github.com/Microsoft/CodeContracts/issues/339). Chcete-li odstranit toto upozornění, si můžete stáhnout a kompilaci aktualizovanou verzi zdrojového kódu pro nástroj kontrakty kódu z [Githubu](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Stáhněte si informace najdete v dolní části stránky.|
|Rozsah|Vedlejší|
|Version|4.6.1|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
