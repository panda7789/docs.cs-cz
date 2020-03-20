---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804655"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load neodstraní vlastnost symbolu

|   |   |
|---|---|
|Podrobnosti|Při cílení rozhraní .NET Framework 4.5 v návrháři pracovního postupu a <xref:System.Activities.Presentation.WorkflowDesigner.Load> načítání re-hostované 3.5 workflow s metodou, je vyvolána <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> při ukládání pracovního postupu.|
|Návrh|Tato chyba se projevuje pouze při cílení rozhraní .NET Framework 4.5 v <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> návrháři pracovního postupu, takže ji lze obejít nastavením rozhraní 4.0 .NET Framework.Alternativně se může vyhnout problému pomocí <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metody k načtení pracovního postupu namísto <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
