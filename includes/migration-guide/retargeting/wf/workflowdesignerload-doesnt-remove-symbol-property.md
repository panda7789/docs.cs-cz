---
ms.openlocfilehash: ddc98448101c65003001ad05e67f29d75d99ad44
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616043"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner. Load neodebere vlastnost symbol.

#### <a name="details"></a>Podrobnosti

Při cílení na .NET Framework 4,5 v Návrháři pracovních postupů a načítají se znovu hostovaný pracovní postup 3,5 s <xref:System.Activities.Presentation.WorkflowDesigner.Load> metodou, <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> je při ukládání pracovního postupu vyvolána výjimka.

#### <a name="suggestion"></a>Návrh

Tato chyba se manifestuje pouze v případě, že je v Návrháři pracovních postupů cílen .NET Framework 4,5, takže je možné ji vyřešit nastavením na `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` 4,0 .NET Framework. Alternativně lze problému zabránit pomocí <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metody pro načtení pracovního postupu namísto <xref:System.Activities.Presentation.WorkflowDesigner.Load> .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4.5         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType>
