---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643961"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="37a4c-101">Modernizace dialogového okna FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="37a4c-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="37a4c-102">Ovládací <xref:System.Windows.Forms.FolderBrowserDialog> prvek byl změněn v aplikacích Windows Forms pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="37a4c-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="37a4c-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="37a4c-103">Change description</span></span>

<span data-ttu-id="37a4c-104">V rozhraní .NET Framework používají formuláře systému Windows pro <xref:System.Windows.Forms.FolderBrowserDialog> ovládací prvek následující dialogové okno:</span><span class="sxs-lookup"><span data-stu-id="37a4c-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![Ovládací prvek FolderBrowserDialogVV frameworku .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="37a4c-106">V rozhraní .NET Core 3.0 uživatelé windows forms novější ovládací prvek založený na modelu COM, který byl zaveden v systému Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="37a4c-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![Ovládací prvek FolderBrowserDialogControl v jádru rozhraní .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="37a4c-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="37a4c-108">Version introduced</span></span>

<span data-ttu-id="37a4c-109">3.0</span><span class="sxs-lookup"><span data-stu-id="37a4c-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="37a4c-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="37a4c-110">Recommended action</span></span>

<span data-ttu-id="37a4c-111">Dialog bude automaticky inovován.</span><span class="sxs-lookup"><span data-stu-id="37a4c-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="37a4c-112">Pokud chcete zachovat původní dialogové okno, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> vlastnost před `false` zobrazením dialogového okna, jak je znázorněno na následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="37a4c-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="37a4c-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="37a4c-113">Category</span></span>

<span data-ttu-id="37a4c-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37a4c-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="37a4c-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="37a4c-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
