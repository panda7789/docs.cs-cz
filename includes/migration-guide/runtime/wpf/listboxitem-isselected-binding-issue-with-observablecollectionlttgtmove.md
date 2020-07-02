---
ms.openlocfilehash: f4ff938b2d0e9ead481fdf239aed8a6b918a99b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620093"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ListBoxItem problém vazby s kolekci ObservableCollection &lt; T &gt; . Pøesunout

#### <a name="details"></a>Podrobnosti

Volání <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> nebo <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> na kolekci vázané k <xref:System.Windows.Controls.ListBox?displayProperty=fullName> vybraným položkám může vést k nestabilnímu chování s budoucím výběrem nebo bez výběru <xref:System.Windows.Controls.ListBox?displayProperty=fullName> položek.

#### <a name="suggestion"></a>Návrh

Volání <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> a <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> místo toho <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> bude tento problém obejít. Případně byl tento problém opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
