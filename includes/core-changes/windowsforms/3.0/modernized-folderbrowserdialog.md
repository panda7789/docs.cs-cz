---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643961"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernizace dialogového okna FolderBrowserDialog

Ovládací <xref:System.Windows.Forms.FolderBrowserDialog> prvek byl změněn v aplikacích Windows Forms pro .NET Core.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Framework používají formuláře systému Windows pro <xref:System.Windows.Forms.FolderBrowserDialog> ovládací prvek následující dialogové okno:

![Ovládací prvek FolderBrowserDialogVV frameworku .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

V rozhraní .NET Core 3.0 uživatelé windows forms novější ovládací prvek založený na modelu COM, který byl zaveden v systému Windows Vista:

![Ovládací prvek FolderBrowserDialogControl v jádru rozhraní .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Dialog bude automaticky inovován.

Pokud chcete zachovat původní dialogové okno, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> vlastnost před `false` zobrazením dialogového okna, jak je znázorněno na následujícím fragmentu kódu:

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
