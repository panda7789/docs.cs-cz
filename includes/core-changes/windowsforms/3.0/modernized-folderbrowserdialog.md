---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643961"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="fc1ae-101">Modernizace FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="fc1ae-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="fc1ae-102"><xref:System.Windows.Forms.FolderBrowserDialog> ovládací prvek se změnil v model Windows Forms aplikacích pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fc1ae-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fc1ae-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="fc1ae-103">Change description</span></span>

<span data-ttu-id="fc1ae-104">V .NET Framework Windows Forms používá pro ovládací prvek <xref:System.Windows.Forms.FolderBrowserDialog> následující dialog:</span><span class="sxs-lookup"><span data-stu-id="fc1ae-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![FolderBrowserDialogControl v .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="fc1ae-106">V rozhraní .NET Core 3,0 model Windows Forms uživatelé novějším ovládacím prvkem založeným na modelu COM, který byl představen v systému Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="fc1ae-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![FolderBrowserDialogControl v rozhraní .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="fc1ae-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="fc1ae-108">Version introduced</span></span>

<span data-ttu-id="fc1ae-109">3,0</span><span class="sxs-lookup"><span data-stu-id="fc1ae-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fc1ae-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="fc1ae-110">Recommended action</span></span>

<span data-ttu-id="fc1ae-111">Dialog se upgraduje automaticky.</span><span class="sxs-lookup"><span data-stu-id="fc1ae-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="fc1ae-112">Pokud si přejete zachovat původní dialog, nastavte vlastnost <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> na `false` před zobrazením dialogového okna, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="fc1ae-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="fc1ae-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="fc1ae-113">Category</span></span>

<span data-ttu-id="fc1ae-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc1ae-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fc1ae-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="fc1ae-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
