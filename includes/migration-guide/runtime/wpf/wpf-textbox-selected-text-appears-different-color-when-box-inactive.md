---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620098"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>Textové pole WPF – vybraný text se zobrazí v případě neaktivního textového pole s jinou barvou

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,5, pokud je ovládací prvek textového pole WPF neaktivní (nemá fokus), se vybraný text v poli zobrazí jinou barvou, než je ovládací prvek aktivní.

#### <a name="suggestion"></a>Návrh

Předchozí chování (.NET Framework 4,0) může být obnoveno nastavením <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> vlastnosti na <code>false</code> .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
