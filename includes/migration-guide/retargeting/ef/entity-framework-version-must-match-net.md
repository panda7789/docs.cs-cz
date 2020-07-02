---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617195"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Verze Entity Framework musí odpovídat verzi .NET Framework.

#### <a name="details"></a>Podrobnosti

Verze Entity Framework (EF) by měla odpovídat verzi .NET Framework. Pro .NET Framework 4,5 se doporučuje Entity Framework 5. K dispozici jsou některé známé problémy s EF 4. x v projektu .NET Framework 4,5 <xref:System.ComponentModel.DataAnnotations> . V .NET Framework 4,5 byly tyto přesunuty do jiného sestavení, takže dojde k problémům s určením, které poznámky se mají použít.

#### <a name="suggestion"></a>Návrh

Upgrade na Entity Framework 5 pro .NET Framework 4,5

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4.5         |
| Typ    | Změna cílení |
