---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803719"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>Formuláře Windows na CheckForOverflowUnderflow vlastnost má nyní hodnotu true pro System.Drawing

|   |   |
|---|---|
|Podrobnosti|Vlastnost CheckForOverflowUnderflow System.Drawing.dll sestavení je nastavena na hodnotu true.|
|Doporučení|Dříve v případě, že dojde k přetečení, by výsledkem bylo tiché zkrácení. Nyní <xref:System.OverflowException?displayProperty=name> je vyvolána výjimka.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
