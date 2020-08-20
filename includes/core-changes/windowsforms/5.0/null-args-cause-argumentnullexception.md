---
ms.openlocfilehash: 7d00145bac473bd1799643a723b9e7928a3cd9a2
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281333"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="b5573-101">Metody WinForms teď vyvolávají ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="b5573-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="b5573-102">Některé metody model Windows Forms nyní vyvolávají výjimku <xref:System.ArgumentNullException> pro argumenty null, kde dříve vyvolaly <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="b5573-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b5573-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b5573-103">Change description</span></span>

<span data-ttu-id="b5573-104">Dříve některé model Windows Forms metody vyvolaly výjimku <xref:System.NullReferenceException> , pokud předala argument, který měl hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b5573-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="b5573-105">Počínaje rozhraním .NET 5,0 tyto metody nyní vyvolávají <xref:System.ArgumentNullException> místo toho argumenty pro hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="b5573-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="b5573-106">Vyvolání <xref:System.ArgumentNullException> vyhovuje chování modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="b5573-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="b5573-107">Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, že argument má hodnotu null a který argument je.</span><span class="sxs-lookup"><span data-stu-id="b5573-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b5573-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b5573-108">Version introduced</span></span>

<span data-ttu-id="b5573-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="b5573-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b5573-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b5573-110">Recommended action</span></span>

<span data-ttu-id="b5573-111">Pokud voláte některou z těchto metod a váš kód aktuálně zachytává <xref:System.NullReferenceException> pro argumenty null, Zachyťte <xref:System.ArgumentNullException> místo toho.</span><span class="sxs-lookup"><span data-stu-id="b5573-111">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="b5573-112">Kromě toho zvažte aktualizaci kódu, abyste zabránili předávání argumentů do uvedených metod.</span><span class="sxs-lookup"><span data-stu-id="b5573-112">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="b5573-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b5573-113">Category</span></span>

<span data-ttu-id="b5573-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5573-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b5573-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b5573-115">Affected APIs</span></span>

<span data-ttu-id="b5573-116">Následující tabulka uvádí ovlivněné metody a parametry:</span><span class="sxs-lookup"><span data-stu-id="b5573-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="b5573-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="b5573-117">Method</span></span> | <span data-ttu-id="b5573-118">Název parametru</span><span class="sxs-lookup"><span data-stu-id="b5573-118">Parameter name</span></span> | <span data-ttu-id="b5573-119">Přidaná verze</span><span class="sxs-lookup"><span data-stu-id="b5573-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="b5573-120">Preview 1</span><span class="sxs-lookup"><span data-stu-id="b5573-120">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="b5573-121">Preview 1</span><span class="sxs-lookup"><span data-stu-id="b5573-121">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="b5573-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="b5573-122">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="b5573-123">Preview 1</span><span class="sxs-lookup"><span data-stu-id="b5573-123">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="b5573-124">Preview 1</span><span class="sxs-lookup"><span data-stu-id="b5573-124">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="b5573-125">Preview 1</span><span class="sxs-lookup"><span data-stu-id="b5573-125">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="b5573-126">Preview 1</span><span class="sxs-lookup"><span data-stu-id="b5573-126">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="b5573-127">Preview 1</span><span class="sxs-lookup"><span data-stu-id="b5573-127">Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="b5573-128">Preview 2</span><span class="sxs-lookup"><span data-stu-id="b5573-128">Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="b5573-129">Preview 2</span><span class="sxs-lookup"><span data-stu-id="b5573-129">Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="b5573-130">Preview 5</span><span class="sxs-lookup"><span data-stu-id="b5573-130">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="b5573-131">Preview 5</span><span class="sxs-lookup"><span data-stu-id="b5573-131">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="b5573-132">Preview 5</span><span class="sxs-lookup"><span data-stu-id="b5573-132">Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="b5573-133">Preview 5</span><span class="sxs-lookup"><span data-stu-id="b5573-133">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="b5573-134">Preview 6</span><span class="sxs-lookup"><span data-stu-id="b5573-134">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="b5573-135">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="b5573-135">`owner`, `value`</span></span> | <span data-ttu-id="b5573-136">Preview 6</span><span class="sxs-lookup"><span data-stu-id="b5573-136">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="b5573-137">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="b5573-137">`owner`, `value`</span></span> | <span data-ttu-id="b5573-138">Preview 6</span><span class="sxs-lookup"><span data-stu-id="b5573-138">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="b5573-139">Preview 6</span><span class="sxs-lookup"><span data-stu-id="b5573-139">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="b5573-140">Preview 6</span><span class="sxs-lookup"><span data-stu-id="b5573-140">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="b5573-141">Preview 6</span><span class="sxs-lookup"><span data-stu-id="b5573-141">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="b5573-142">Preview 6</span><span class="sxs-lookup"><span data-stu-id="b5573-142">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListView.SelectedIndexCollection.%23ctor(System.Windows.Forms.ListView)> | `owner` | <span data-ttu-id="b5573-143">Preview 7</span><span class="sxs-lookup"><span data-stu-id="b5573-143">Preview 7</span></span> |
> | <xref:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b5573-144">`key` je `null` nebo prázdné</span><span class="sxs-lookup"><span data-stu-id="b5573-144">`key` is `null` or empty</span></span> | <span data-ttu-id="b5573-145">Preview 8</span><span class="sxs-lookup"><span data-stu-id="b5573-145">Preview 8</span></span> |

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
- `M:System.Windows.Forms.ListView.SelectedIndexCollection.#ctor(System.Windows.Forms.ListView)`
- `M:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)`

-->
