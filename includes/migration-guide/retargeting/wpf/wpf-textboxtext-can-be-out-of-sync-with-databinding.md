---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088483"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>Pole TextBox.Text ve WPF nemusí být synchronizováno s datovou vazbou

|   |   |
|---|---|
|Podrobnosti|Pokud byla vlastnost <xref:System.Windows.Controls.TextBox.Text> změněna během operace zápisu datové vazby, v některých případech odráží předchozí hodnotu vlastnosti s datovou vazbou.|
|Doporučení|To by nemělo mít žádný negativní dopad. Předchozí chování však můžete obnovit nastavením vlastnosti <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> na <code>false</code>.|
|Rozsah|Edge|
|Version|4.5|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|
