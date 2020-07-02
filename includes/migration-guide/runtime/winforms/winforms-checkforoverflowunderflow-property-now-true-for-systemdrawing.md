---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620090"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>Vlastnost CheckForOverflowUnderflow DataGridView má nyní hodnotu true pro System. Drawing.

#### <a name="details"></a>Podrobnosti

Vlastnost CheckForOverflowUnderflow pro sestavení System.Drawing.dll je nastavena na hodnotu true.

#### <a name="suggestion"></a>Návrh

Dříve v případě, že dojde k přetečení, by výsledkem bylo tiché zkrácení. Nyní <xref:System.OverflowException?displayProperty=fullName> je vyvolána výjimka.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime|
