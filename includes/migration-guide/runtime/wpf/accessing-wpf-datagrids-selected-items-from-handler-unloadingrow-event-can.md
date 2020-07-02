---
ms.openlocfilehash: 7ac0cac53ab2fa7657d0ae58f11d9e777631acc9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620089"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Přístup k vybraným položkám ovládacího prvku DataGrid v GRAFICKÉm přístupu z obslužné rutiny události UnloadingRow objektu DataGrid může způsobit NullReferenceException.

#### <a name="details"></a>Podrobnosti

V důsledku chyby v .NET Framework 4,5 může obslužná rutina události pro <xref:System.Windows.Controls.DataGrid> události zahrnující odebrání řádku způsobit <xref:System.NullReferenceException?displayProperty=fullName> vyvolání, pokud přistupuje k <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> vlastnostem nebo.

#### <a name="suggestion"></a>Návrh

Tento problém byl opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
