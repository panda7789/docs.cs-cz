---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379522"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>Textové pole WPF vybraný text se zobrazí odlišnou barvou, když do textového pole je neaktivní

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, když je neaktivní ovládacího prvku WPF textového pole (nemá fokus), zobrazí se vybraný text v poli jinou barvou, než když je aktivní ovládací prvek.|
|Doporučení|Může se obnovit předchozí chování (.NET Framework 4.0) tak, že nastavíte <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> vlastnost <code>false</code>.|
|Scope|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
