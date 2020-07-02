---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620102"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>Výchozím textovým polem WPF je omezení vrácení 100

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,5 je výchozí limit vrácení pro textové pole WPF (WPF) 100 (na rozdíl od neomezených .NET Framework 4,0).

#### <a name="suggestion"></a>Návrh

Pokud je limit vrácení 100 příliš nízký, lze limit nastavit explicitně na<xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
