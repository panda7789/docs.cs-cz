---
ms.openlocfilehash: ab8d801f3cdcfbeb6de20146754b26e3713d7dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702447"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="7edc8-101">Metody WinForms teď vyvolávají ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="7edc8-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="7edc8-102">Některé metody model Windows Forms nyní vyvolávají výjimku <xref:System.ArgumentNullException> pro argumenty null, kde dříve vyvolaly <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="7edc8-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7edc8-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="7edc8-103">Change description</span></span>

<span data-ttu-id="7edc8-104">Dříve některé model Windows Forms metody vyvolaly výjimku <xref:System.NullReferenceException> , pokud předala argument, který měl hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="7edc8-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="7edc8-105">Počínaje rozhraním .NET 5,0 tyto metody nyní vyvolávají <xref:System.ArgumentNullException> místo toho argumenty pro hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="7edc8-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="7edc8-106">Vyvolání <xref:System.ArgumentNullException> vyhovuje chování modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="7edc8-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="7edc8-107">Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, že argument má hodnotu null a který argument je.</span><span class="sxs-lookup"><span data-stu-id="7edc8-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7edc8-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="7edc8-108">Version introduced</span></span>

<span data-ttu-id="7edc8-109">.NET 5,0 Preview 1 </span><span class="sxs-lookup"><span data-stu-id="7edc8-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="7edc8-110">.NET 5,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="7edc8-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7edc8-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="7edc8-111">Recommended action</span></span>

<span data-ttu-id="7edc8-112">Pokud voláte některou z těchto metod a váš kód aktuálně zachytává <xref:System.NullReferenceException> pro argumenty null, Zachyťte <xref:System.ArgumentNullException> místo toho.</span><span class="sxs-lookup"><span data-stu-id="7edc8-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="7edc8-113">Kromě toho zvažte aktualizaci kódu, abyste zabránili předávání argumentů do uvedených metod.</span><span class="sxs-lookup"><span data-stu-id="7edc8-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="7edc8-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="7edc8-114">Category</span></span>

<span data-ttu-id="7edc8-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7edc8-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7edc8-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7edc8-116">Affected APIs</span></span>

<span data-ttu-id="7edc8-117">Počínaje verzí .NET 5,0 Preview 1:</span><span class="sxs-lookup"><span data-stu-id="7edc8-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="7edc8-118">Od verze .NET 5,0 Preview 2:</span><span class="sxs-lookup"><span data-stu-id="7edc8-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="7edc8-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(pouze pro <xref:System.IO.Stream> parametr)</span><span class="sxs-lookup"><span data-stu-id="7edc8-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

<!-- 

#### Affected APIs

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
