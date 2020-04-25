---
ms.openlocfilehash: 7a6b0b15de4295506ff03b8566c06010b918566c
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158388"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="e9958-101">Metody WinForms teď vyvolávají ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="e9958-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="e9958-102">Některé metody model Windows Forms nyní vyvolávají výjimku <xref:System.ArgumentNullException> pro argumenty null, kde dříve vyvolaly <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="e9958-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e9958-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e9958-103">Change description</span></span>

<span data-ttu-id="e9958-104">Dříve některé model Windows Forms metody vyvolaly <xref:System.NullReferenceException> výjimku, pokud předala argument, který měl hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e9958-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="e9958-105">Počínaje rozhraním .NET 5,0 tyto metody nyní vyvolávají místo <xref:System.ArgumentNullException> toho argumenty pro hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="e9958-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="e9958-106"><xref:System.ArgumentNullException> Vyvolání vyhovuje chování modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="e9958-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="e9958-107">Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, že argument má hodnotu null a který argument je.</span><span class="sxs-lookup"><span data-stu-id="e9958-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e9958-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e9958-108">Version introduced</span></span>

<span data-ttu-id="e9958-109">.NET 5,0 Preview 1 </span><span class="sxs-lookup"><span data-stu-id="e9958-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="e9958-110">.NET 5,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="e9958-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e9958-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e9958-111">Recommended action</span></span>

<span data-ttu-id="e9958-112">Pokud voláte některou z těchto metod a váš kód aktuálně zachytává <xref:System.NullReferenceException> pro argumenty null, Zachyťte <xref:System.ArgumentNullException> místo toho.</span><span class="sxs-lookup"><span data-stu-id="e9958-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="e9958-113">Kromě toho zvažte aktualizaci kódu, abyste zabránili předávání argumentů do uvedených metod.</span><span class="sxs-lookup"><span data-stu-id="e9958-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="e9958-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e9958-114">Category</span></span>

<span data-ttu-id="e9958-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9958-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e9958-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e9958-116">Affected APIs</span></span>

<span data-ttu-id="e9958-117">Počínaje verzí .NET 5,0 Preview 1:</span><span class="sxs-lookup"><span data-stu-id="e9958-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="e9958-118">Od verze .NET 5,0 Preview 2:</span><span class="sxs-lookup"><span data-stu-id="e9958-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="e9958-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(pouze pro <xref:System.IO.Stream> parametr)</span><span class="sxs-lookup"><span data-stu-id="e9958-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`

-->
