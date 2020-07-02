---
ms.openlocfilehash: 063e10b0310880af255793215a80a5529a5db0ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616046"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>DbParameter. Precision a DbParameter. Scale jsou teď veřejné virtuální členy.

#### <a name="details"></a>Podrobnosti

<xref:System.Data.Common.DbParameter.Precision>a <xref:System.Data.Common.DbParameter.Scale> jsou implementovány jako veřejné virtuální vlastnosti. Nahrazují odpovídající explicitní implementace rozhraní <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> a <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale> .

#### <a name="suggestion"></a>Návrh

Při opětovném sestavování poskytovatele databáze ADO.NET budou tyto rozdíly vyžadovat, aby klíčové slovo override bylo použito pro vlastnosti Precision a Scale. To je nutné pouze při opětovném sestavování komponent. existující binární soubory budou fungovat i nadále.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType>
- <xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType>
