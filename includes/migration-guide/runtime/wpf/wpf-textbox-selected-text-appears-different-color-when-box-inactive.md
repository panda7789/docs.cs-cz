---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803694"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>Textové pole WPF vybraný text se zobrazí odlišnou barvou, když do textového pole je neaktivní

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, když je neaktivní ovládacího prvku WPF textového pole (nemá fokus), zobrazí se vybraný text v poli jinou barvou, než když je aktivní ovládací prvek.|
|Doporučení|Může se obnovit předchozí chování (.NET Framework 4.0) tak, že nastavíte <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> vlastnost <code>false</code>.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
