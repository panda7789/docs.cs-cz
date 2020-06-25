---
ms.openlocfilehash: 00f89e6ae49982917fa7591c3283adec3947eed2
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365638"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="8e2e5-101">Metody WinForms teď vyvolávají ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="8e2e5-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="8e2e5-102">Některé metody model Windows Forms nyní vyvolávají výjimku <xref:System.ArgumentNullException> pro argumenty null, kde dříve vyvolaly <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="8e2e5-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8e2e5-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="8e2e5-103">Change description</span></span>

<span data-ttu-id="8e2e5-104">Dříve některé model Windows Forms metody vyvolaly výjimku <xref:System.NullReferenceException> , pokud předala argument, který měl hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8e2e5-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="8e2e5-105">Počínaje rozhraním .NET 5,0 tyto metody nyní vyvolávají <xref:System.ArgumentNullException> místo toho argumenty pro hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="8e2e5-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="8e2e5-106">Vyvolání <xref:System.ArgumentNullException> vyhovuje chování modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="8e2e5-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="8e2e5-107">Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, že argument má hodnotu null a který argument je.</span><span class="sxs-lookup"><span data-stu-id="8e2e5-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8e2e5-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="8e2e5-108">Version introduced</span></span>

<span data-ttu-id="8e2e5-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8e2e5-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8e2e5-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="8e2e5-110">Recommended action</span></span>

<span data-ttu-id="8e2e5-111">Pokud voláte některou z těchto metod a váš kód aktuálně zachytává <xref:System.NullReferenceException> pro argumenty null, Zachyťte <xref:System.ArgumentNullException> místo toho.</span><span class="sxs-lookup"><span data-stu-id="8e2e5-111">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="8e2e5-112">Kromě toho zvažte aktualizaci kódu, abyste zabránili předávání argumentů do uvedených metod.</span><span class="sxs-lookup"><span data-stu-id="8e2e5-112">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="8e2e5-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="8e2e5-113">Category</span></span>

<span data-ttu-id="8e2e5-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e2e5-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8e2e5-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8e2e5-115">Affected APIs</span></span>

<span data-ttu-id="8e2e5-116">Následující tabulka uvádí ovlivněné metody a parametry:</span><span class="sxs-lookup"><span data-stu-id="8e2e5-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="8e2e5-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="8e2e5-117">Method</span></span> | <span data-ttu-id="8e2e5-118">Název parametru</span><span class="sxs-lookup"><span data-stu-id="8e2e5-118">Parameter name</span></span> | <span data-ttu-id="8e2e5-119">Přidaná verze</span><span class="sxs-lookup"><span data-stu-id="8e2e5-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="8e2e5-120">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8e2e5-120">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="8e2e5-121">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8e2e5-121">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="8e2e5-122">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8e2e5-122">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="8e2e5-123">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8e2e5-123">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="8e2e5-124">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8e2e5-124">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="8e2e5-125">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8e2e5-125">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="8e2e5-126">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8e2e5-126">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="8e2e5-127">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8e2e5-127">5.0 Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="8e2e5-128">5,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="8e2e5-128">5.0 Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="8e2e5-129">5,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="8e2e5-129">5.0 Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="8e2e5-130">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="8e2e5-130">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="8e2e5-131">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="8e2e5-131">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="8e2e5-132">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="8e2e5-132">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="8e2e5-133">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="8e2e5-133">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="8e2e5-134">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="8e2e5-134">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="8e2e5-135">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="8e2e5-135">`owner`, `value`</span></span> | <span data-ttu-id="8e2e5-136">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="8e2e5-136">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="8e2e5-137">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="8e2e5-137">`owner`, `value`</span></span> | <span data-ttu-id="8e2e5-138">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="8e2e5-138">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="8e2e5-139">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="8e2e5-139">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="8e2e5-140">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="8e2e5-140">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="8e2e5-141">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="8e2e5-141">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="8e2e5-142">`destination`č</span><span class="sxs-lookup"><span data-stu-id="8e2e5-142">`destination`q\`</span></span> | <span data-ttu-id="8e2e5-143">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="8e2e5-143">5.0 Preview 6</span></span> |

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
- `M:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)`

-->
