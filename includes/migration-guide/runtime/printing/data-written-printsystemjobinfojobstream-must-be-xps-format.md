---
ms.openlocfilehash: a007022bf32ffe76861f6f9016a7edace17b0f61
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620044"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>Data zapsaná do PrintSystemJobInfo. tok úloh musí být ve formátu XPS.

#### <a name="details"></a>Podrobnosti

<xref:System.Printing.PrintSystemJobInfo.JobStream>Vlastnost zpřístupňuje datový proud tiskové úlohy. Uživatel může do tohoto datového proudu odeslat nezpracovaná data do základních tiskových součástí operačního systému. Od verze .NET Framework 4,5 ve Windows 8 a novějších verzích operačního systému Windows musí být data zapsaná do tohoto datového proudu ve formátu XPS jako datový proud balíčku.

#### <a name="suggestion"></a>Návrh

Pro výstup tiskového obsahu můžete provést jednu z následujících akcí:<ul><li>Použijte <xref:System.Windows.Xps.XpsDocumentWriter> třídu pro výstup tiskového obsahu. Toto je Doporučená alternativa.</li><li>Zajistěte, aby data odesílaná do datového proudu vráceného <xref:System.Printing.PrintSystemJobInfo.JobStream> vlastností byla ve formátu XPS jako datový proud balíčku.</li></ul>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
