---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616048"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Obousměrná datová vazba na vlastnost s neveřejnou metodou Setter není podporovaná.

#### <a name="details"></a>Podrobnosti

Při pokusu o vytvoření vazby dat na vlastnost bez veřejné metody setter nebyl nikdy podporován scénář. Počínaje .NET Framework 4.5.1 Tento scénář vyvolá <xref:System.InvalidOperationException?displayProperty=fullName> . Všimněte si, že tato nová výjimka bude vyvolána jenom pro aplikace, které specificky cílí na .NET Framework 4.5.1. Pokud je aplikace cílena na .NET Framework 4,5, volání bude povoleno. Pokud aplikace necílí na konkrétní verzi .NET Framework, vazba bude považována za jednosměrnou.

#### <a name="suggestion"></a>Návrh

Aplikace by se měla aktualizovat tak, aby buď používala jednosměrnou vazbu, nebo veřejně vystavovat metodu setter vlastnosti. Případně cílení na .NET Framework 4,5 způsobí, že aplikace vykazuje původní chování.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>
