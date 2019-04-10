---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234674"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load neodebere vlastnost symbol

|   |   |
|---|---|
|Podrobnosti|Při cílení na rozhraní .NET Framework 4.5 v Návrháři pracovních postupů a načítání 3.5 a znovu hostovaných pracovních postupů s <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> je vyvolána při ukládání pracovního postupu.|
|Doporučení|Tato chyba projevuje pouze při cílení na rozhraní .NET Framework 4.5 v Návrháři pracovních postupů, takže je možné pracovat kolem tak, že nastavíte <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> na 4.0 .NET Framework.Alternatively může být problém vyhnout použitím <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metodu načtení pracovního postupu, místo <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Rozsah|Hlavní|
|Version|4.5|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
