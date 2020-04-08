---
ms.openlocfilehash: 63959c240b2fe16e086b97881a5a1792035bb3f8
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888107"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a><span data-ttu-id="c15bc-101">WinForms API nyní vyvolat ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="c15bc-101">WinForms APIs now throw ArgumentNullException</span></span>

<span data-ttu-id="c15bc-102">Některé metody Windows Forms <xref:System.ArgumentNullException> nyní vyvolat pro argumenty <xref:System.NullReferenceException>null, kde dříve hodil .</span><span class="sxs-lookup"><span data-stu-id="c15bc-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c15bc-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="c15bc-103">Change description</span></span>

<span data-ttu-id="c15bc-104">Dříve některé metody Windows <xref:System.NullReferenceException> Forms hodil if předán argument, který byl null.</span><span class="sxs-lookup"><span data-stu-id="c15bc-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="c15bc-105">Počínaje .NET 5.0, tyto metody <xref:System.ArgumentNullException> nyní vyvolat pro argumenty null místo.</span><span class="sxs-lookup"><span data-stu-id="c15bc-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="c15bc-106">Vyvolání <xref:System.ArgumentNullException> odpovídá chování .NET runtime.</span><span class="sxs-lookup"><span data-stu-id="c15bc-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="c15bc-107">Také zlepšuje ladění prostředí tím, že jasně sdělit, že argument je null a který argument je.</span><span class="sxs-lookup"><span data-stu-id="c15bc-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c15bc-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="c15bc-108">Version introduced</span></span>

<span data-ttu-id="c15bc-109">.NET 5.0 Náhled 1</span><span class="sxs-lookup"><span data-stu-id="c15bc-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="c15bc-110">.NET 5.0 Náhled 2</span><span class="sxs-lookup"><span data-stu-id="c15bc-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c15bc-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="c15bc-111">Recommended action</span></span>

<span data-ttu-id="c15bc-112">Pokud zavoláte některou z těchto metod <xref:System.NullReferenceException> a váš kód aktuálně <xref:System.ArgumentNullException> zachytí pro argumenty null, místo toho zachyťte.</span><span class="sxs-lookup"><span data-stu-id="c15bc-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="c15bc-113">Kromě toho zvažte aktualizaci kódu, abyste zabránili předání argumentů null uvedeným metodám.</span><span class="sxs-lookup"><span data-stu-id="c15bc-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="c15bc-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="c15bc-114">Category</span></span>

<span data-ttu-id="c15bc-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c15bc-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c15bc-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c15bc-116">Affected APIs</span></span>

<span data-ttu-id="c15bc-117">Počínaje rozhraním .NET 5.0 Náhled 1:</span><span class="sxs-lookup"><span data-stu-id="c15bc-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="c15bc-118">Počínaje rozhraním .NET 5.0 Náhled 2:</span><span class="sxs-lookup"><span data-stu-id="c15bc-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="c15bc-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(pouze <xref:System.IO.Stream> pro parametr)</span><span class="sxs-lookup"><span data-stu-id="c15bc-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

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
