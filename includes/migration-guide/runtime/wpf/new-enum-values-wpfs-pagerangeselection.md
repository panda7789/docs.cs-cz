---
ms.openlocfilehash: bae6d7c0f8843211c721c68ce6f16000b35b4401
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620094"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a>Nové hodnoty výčtu v PageRangeSelection WPF

#### <a name="details"></a>Podrobnosti

Do výčtu byly přidány dva nové členy ( <xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> a <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName> ) <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> .

#### <a name="suggestion"></a>Návrh

Ve většině případů tyto změny nebudou mít vliv na uživatelský kód. Kód, který závisí na konkrétním počtu prvků existujících v <xref:System.Enum.GetNames(System.Type)> nebo <xref:System.Enum.GetValues(System.Type)> volání <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> typu, by měl být změněn, i když.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|
