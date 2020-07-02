---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617234"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>Pole TextBox.Text ve WPF nemusí být synchronizováno s datovou vazbou

#### <a name="details"></a>Podrobnosti

Pokud byla vlastnost <xref:System.Windows.Controls.TextBox.Text> změněna během operace zápisu datové vazby, v některých případech odráží předchozí hodnotu vlastnosti s datovou vazbou.

#### <a name="suggestion"></a>Návrh

To by nemělo mít žádný negativní dopad. Předchozí chování však můžete obnovit nastavením vlastnosti <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> na `false`.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.5         |
|Typ|Změna cílení

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
