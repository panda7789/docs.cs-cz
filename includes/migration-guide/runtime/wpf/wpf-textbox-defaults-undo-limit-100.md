---
ms.openlocfilehash: de79182e326082786c1e0691f8888e30cd410f5d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235220"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>Výchozí hodnota je textové pole WPF zrušit limit 100

|   |   |
|---|---|
|Podrobnosti|Výchozí limit vrácení zpět pro textové pole s WPF v rozhraní .NET Framework 4.5, je 100 (na rozdíl od vrácení neomezený počet v rozhraní .NET Framework 4.0)|
|Doporučení|Pokud zpět maximálně 100 je příliš nízké, limit lze nastavit explicitně pomocí <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
