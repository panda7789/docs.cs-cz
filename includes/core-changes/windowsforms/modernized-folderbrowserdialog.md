---
ms.openlocfilehash: a7cf6210e288d3521f1df248927f0e7cfaf45cab
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119322"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="5d46e-101">Modernizace FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="5d46e-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="5d46e-102"><xref:System.Windows.Forms.FolderBrowserDialog> Ovládací prvek se změnil v model Windows Forms aplikací pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d46e-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5d46e-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="5d46e-103">Change description</span></span>

<span data-ttu-id="5d46e-104">V .NET Framework používá Windows Forms pro <xref:System.Windows.Forms.FolderBrowserDialog> ovládací prvek následující dialog:</span><span class="sxs-lookup"><span data-stu-id="5d46e-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![FolderBrowserDialogControl v .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="5d46e-106">V rozhraní .NET Core 3,0 model Windows Forms uživatelé novějším ovládacím prvkem založeným na modelu COM, který byl představen v systému Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="5d46e-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![FolderBrowserDialogControl v rozhraní .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="5d46e-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5d46e-108">Version introduced</span></span>

<span data-ttu-id="5d46e-109">3.0</span><span class="sxs-lookup"><span data-stu-id="5d46e-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5d46e-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5d46e-110">Recommended action</span></span>

<span data-ttu-id="5d46e-111">Dialog se upgraduje automaticky.</span><span class="sxs-lookup"><span data-stu-id="5d46e-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="5d46e-112">Pokud si přejete zachovat původní dialog, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> vlastnost na `false` hodnotu před zobrazením dialogového okna, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="5d46e-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="5d46e-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5d46e-113">Category</span></span>

<span data-ttu-id="5d46e-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d46e-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5d46e-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5d46e-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!-- 

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->