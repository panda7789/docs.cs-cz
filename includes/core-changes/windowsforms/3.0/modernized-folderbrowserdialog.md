---
ms.openlocfilehash: 645df8080abd21e4db95903a301a36b79a698858
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888108"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernizace FolderBrowserDialog

<xref:System.Windows.Forms.FolderBrowserDialog> Ovládací prvek se změnil v model Windows Forms aplikací pro .NET Core.

#### <a name="change-description"></a>Popis změny

V .NET Framework používá Windows Forms pro <xref:System.Windows.Forms.FolderBrowserDialog> ovládací prvek následující dialog:

![FolderBrowserDialogControl v .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

V rozhraní .NET Core 3,0 model Windows Forms uživatelé novějším ovládacím prvkem založeným na modelu COM, který byl představen v systému Windows Vista:

![FolderBrowserDialogControl v rozhraní .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Dialog se upgraduje automaticky.

Pokud si přejete zachovat původní dialog, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> vlastnost na `false` hodnotu před zobrazením dialogového okna, jak je znázorněno v následujícím fragmentu kódu:

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

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
