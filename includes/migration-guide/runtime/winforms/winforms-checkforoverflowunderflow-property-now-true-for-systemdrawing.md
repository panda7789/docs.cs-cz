---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235283"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>Formuláře Windows na CheckForOverflowUnderflow vlastnost má nyní hodnotu true pro System.Drawing

|   |   |
|---|---|
|Podrobnosti|Vlastnost CheckForOverflowUnderflow System.Drawing.dll sestavení je nastavena na hodnotu true.|
|Doporučení|Dříve v případě, že dojde k přetečení, by výsledkem bylo tiché zkrácení. Nyní <xref:System.OverflowException?displayProperty=name> je vyvolána výjimka.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
