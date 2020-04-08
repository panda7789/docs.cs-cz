---
ms.openlocfilehash: 645df8080abd21e4db95903a301a36b79a698858
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888108"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="2bc4d-101">Modernizace dialogového okna FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="2bc4d-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="2bc4d-102">Ovládací <xref:System.Windows.Forms.FolderBrowserDialog> prvek byl změněn v aplikacích Windows Forms pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bc4d-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2bc4d-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="2bc4d-103">Change description</span></span>

<span data-ttu-id="2bc4d-104">V rozhraní .NET Framework používají formuláře systému Windows pro <xref:System.Windows.Forms.FolderBrowserDialog> ovládací prvek následující dialogové okno:</span><span class="sxs-lookup"><span data-stu-id="2bc4d-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![Ovládací prvek FolderBrowserDialogVV frameworku .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="2bc4d-106">V rozhraní .NET Core 3.0 uživatelé windows forms novější ovládací prvek založený na modelu COM, který byl zaveden v systému Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="2bc4d-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![Ovládací prvek FolderBrowserDialogControl v jádru rozhraní .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="2bc4d-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="2bc4d-108">Version introduced</span></span>

<span data-ttu-id="2bc4d-109">3.0</span><span class="sxs-lookup"><span data-stu-id="2bc4d-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2bc4d-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2bc4d-110">Recommended action</span></span>

<span data-ttu-id="2bc4d-111">Dialog bude automaticky inovován.</span><span class="sxs-lookup"><span data-stu-id="2bc4d-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="2bc4d-112">Pokud chcete zachovat původní dialogové okno, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> vlastnost před `false` zobrazením dialogového okna, jak je znázorněno na následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="2bc4d-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="2bc4d-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2bc4d-113">Category</span></span>

<span data-ttu-id="2bc4d-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bc4d-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2bc4d-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2bc4d-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
