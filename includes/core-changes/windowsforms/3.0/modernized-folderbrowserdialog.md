---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643961"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernizace FolderBrowserDialog

<xref:System.Windows.Forms.FolderBrowserDialog> ovládací prvek se změnil v model Windows Forms aplikacích pro .NET Core.

#### <a name="change-description"></a>Změnit popis

V .NET Framework Windows Forms používá pro ovládací prvek <xref:System.Windows.Forms.FolderBrowserDialog> následující dialog:

![FolderBrowserDialogControl v .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

V rozhraní .NET Core 3,0 model Windows Forms uživatelé novějším ovládacím prvkem založeným na modelu COM, který byl představen v systému Windows Vista:

![FolderBrowserDialogControl v rozhraní .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="recommended-action"></a>Doporučená akce

Dialog se upgraduje automaticky.

Pokud si přejete zachovat původní dialog, nastavte vlastnost <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> na `false` před zobrazením dialogového okna, jak je znázorněno v následujícím fragmentu kódu:

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
