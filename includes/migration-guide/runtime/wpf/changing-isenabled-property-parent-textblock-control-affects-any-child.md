---
ms.openlocfilehash: 395463225e3c1f1d168dd019ea75966ad54e5a8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621109"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Změna vlastnosti-Enable nadřazené položky ovládacího prvku TextBlock se projeví u všech podřízených ovládacích prvků.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.6.2 se změna <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> vlastnosti nadřazeného <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> ovládacího prvku projeví u všech podřízených ovládacích prvků (jako jsou hypertextové odkazy a tlačítka) <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> ovládacího prvku. V .NET Framework 4.6.1 a dřívějších verzích ovládací prvky uvnitř <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> neodrážely stav <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> vlastnosti <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> nadřazeného objektu.

#### <a name="suggestion"></a>Návrh

Žádné Tato změna odpovídá očekávanému chování ovládacích prvků uvnitř <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> ovládacího prvku.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
