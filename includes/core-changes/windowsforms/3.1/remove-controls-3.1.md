---
ms.openlocfilehash: 06a700a6fcd9c434e5ea8a10031371d13a4d1a4b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721009"
---
### <a name="removed-controls"></a><span data-ttu-id="4c643-101">Odebrané ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="4c643-101">Removed controls</span></span>

<span data-ttu-id="4c643-102">Počínaje rozhraním .NET Core 3,1 Některé ovládací prvky model Windows Forms již nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4c643-102">Starting in .NET Core 3.1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4c643-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="4c643-103">Change description</span></span>

<span data-ttu-id="4c643-104">Počínaje rozhraním .NET Core 3,1 nejsou k dispozici různé ovládací prvky model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4c643-104">Starting with .NET Core 3.1, various Windows Forms controls are no longer available.</span></span> <span data-ttu-id="4c643-105">Náhradní ovládací prvky, které mají lepší návrh a podporu, byly zavedeny v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="4c643-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="4c643-106">Zastaralé ovládací prvky byly předtím odebrány z nástrojů návrháře, ale byly stále k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="4c643-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span>

<span data-ttu-id="4c643-107">Následující typy již nejsou k dispozici:</span><span class="sxs-lookup"><span data-stu-id="4c643-107">The following types are no longer available:</span></span>

- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.Menu.MenuItemCollection>
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.ToolBar>
- <xref:System.Windows.Forms.ToolBarAppearance>
- <xref:System.Windows.Forms.ToolBarButton>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs>
- <xref:System.Windows.Forms.ToolBarButtonStyle>
- <xref:System.Windows.Forms.ToolBarTextAlign>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.DataGridBoolColumn>
- <xref:System.Windows.Forms.DataGridCell>
- <xref:System.Windows.Forms.DataGridColumnStyle>
- <xref:System.Windows.Forms.DataGridLineStyle>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter>
- <xref:System.Windows.Forms.DataGridTableStyle>
- <xref:System.Windows.Forms.DataGridTextBox>
- <xref:System.Windows.Forms.DataGridTextBoxColumn>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.GridTablesFactory>
- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.IDataGridEditingService>
- <xref:System.Windows.Forms.DataGrid.HitTestType>
- <xref:System.Windows.Forms.Design.IMenuEditorService>

#### <a name="version-introduced"></a><span data-ttu-id="4c643-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="4c643-108">Version introduced</span></span>

<span data-ttu-id="4c643-109">3.1</span><span class="sxs-lookup"><span data-stu-id="4c643-109">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4c643-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4c643-110">Recommended action</span></span>

<span data-ttu-id="4c643-111">Každý odebraný ovládací prvek má doporučený ovládací prvek pro nahrazení.</span><span class="sxs-lookup"><span data-stu-id="4c643-111">Each removed control has a recommended replacement control.</span></span> <span data-ttu-id="4c643-112">Podívejte se na následující tabulku:</span><span class="sxs-lookup"><span data-stu-id="4c643-112">Refer to the following table:</span></span>

| <span data-ttu-id="4c643-113">Odebraný ovládací prvek (API)</span><span class="sxs-lookup"><span data-stu-id="4c643-113">Removed control (API)</span></span> | <span data-ttu-id="4c643-114">Doporučená náhrada</span><span class="sxs-lookup"><span data-stu-id="4c643-114">Recommended replacement</span></span> | <span data-ttu-id="4c643-115">Přidružená rozhraní API k odebrání</span><span class="sxs-lookup"><span data-stu-id="4c643-115">Associated APIs that are removed</span></span> |
|-|-|-|
| <span data-ttu-id="4c643-116">DataGrid</span><span class="sxs-lookup"><span data-stu-id="4c643-116">DataGrid</span></span> | <span data-ttu-id="4c643-117">DataGridView</span><span class="sxs-lookup"><span data-stu-id="4c643-117">DataGridView</span></span> | <span data-ttu-id="4c643-118">DataGridCell, hodnota DataGridRow, DataGridTableCollection, DataGridColumnCollection, styl DataGridTableStyle, styl DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, funkce DataGridBoolColumn, DataGridTextBox, kolekce GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span><span class="sxs-lookup"><span data-stu-id="4c643-118">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span></span> |
| <span data-ttu-id="4c643-119">ToolBar</span><span class="sxs-lookup"><span data-stu-id="4c643-119">ToolBar</span></span> | <span data-ttu-id="4c643-120">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4c643-120">ToolStrip</span></span> | <span data-ttu-id="4c643-121">ToolBarAppearance</span><span class="sxs-lookup"><span data-stu-id="4c643-121">ToolBarAppearance</span></span> |
| <span data-ttu-id="4c643-122">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="4c643-122">ToolBarButton</span></span> | <span data-ttu-id="4c643-123">Prvek ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="4c643-123">ToolStripButton</span></span> | <span data-ttu-id="4c643-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="4c643-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span></span>|
| <span data-ttu-id="4c643-125">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4c643-125">ContextMenu</span></span> | <span data-ttu-id="4c643-126">ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="4c643-126">ContextMenuStrip</span></span> | |
| <span data-ttu-id="4c643-127">Nabídka</span><span class="sxs-lookup"><span data-stu-id="4c643-127">Menu</span></span> | <span data-ttu-id="4c643-128">Ovládací prvek ToolStripDropDown, ToolStripDropDownMenu</span><span class="sxs-lookup"><span data-stu-id="4c643-128">ToolStripDropDown, ToolStripDropDownMenu</span></span> | <span data-ttu-id="4c643-129">MenuItemcollection</span><span class="sxs-lookup"><span data-stu-id="4c643-129">MenuItemCollection</span></span> |
| <span data-ttu-id="4c643-130">MainMenu</span><span class="sxs-lookup"><span data-stu-id="4c643-130">MainMenu</span></span> | <span data-ttu-id="4c643-131">MenuStrip</span><span class="sxs-lookup"><span data-stu-id="4c643-131">MenuStrip</span></span> | |
| <span data-ttu-id="4c643-132">MenuItem</span><span class="sxs-lookup"><span data-stu-id="4c643-132">MenuItem</span></span> | <span data-ttu-id="4c643-133">ToolStripMenuItem</span><span class="sxs-lookup"><span data-stu-id="4c643-133">ToolStripMenuItem</span></span> | |

#### <a name="category"></a><span data-ttu-id="4c643-134">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4c643-134">Category</span></span>

<span data-ttu-id="4c643-135">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c643-135">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4c643-136">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4c643-136">Affected APIs</span></span>

- <xref:System.Windows.Forms.Menu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Menu.MenuItemCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MainMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ContextMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MenuItem?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarAppearance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarTextAlign?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridBoolColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridCell?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridColumnStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridLineStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTableStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBox?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBoxColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridColumnStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTablesFactory?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTableStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.IDataGridEditingService?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid.HitTestType?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Design.IMenuEditorService?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:System.Windows.Forms.Menu`
- `T:System.Windows.Forms.Menu.MenuItemCollection`
- `T:System.Windows.Forms.MainMenu`
- `T:System.Windows.Forms.ContextMenu`
- `T:System.Windows.Forms.MenuItem`
- `T:System.Windows.Forms.ToolBar`
- `T:System.Windows.Forms.ToolBarAppearance`
- `T:System.Windows.Forms.ToolBarButton`
- `T:System.Windows.Forms.ToolBar.ToolBarButtonCollection`
- `T:System.Windows.Forms.ToolBarButtonClickEventArgs`
- `T:System.Windows.Forms.ToolBarButtonStyle`
- `T:System.Windows.Forms.ToolBarTextAlign`
- `T:System.Windows.Forms.DataGrid`
- `T:System.Windows.Forms.DataGridBoolColumn`
- `T:System.Windows.Forms.DataGridCell`
- `T:System.Windows.Forms.DataGridColumnStyle`
- `T:System.Windows.Forms.DataGridLineStyle`
- `T:System.Windows.Forms.DataGridParentRowsLabelStyle`
- `T:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter`
- `T:System.Windows.Forms.DataGridTableStyle`
- `T:System.Windows.Forms.DataGridTextBox`
- `T:System.Windows.Forms.DataGridTextBoxColumn`
- `T:System.Windows.Forms.GridColumnStylesCollection`
- `T:System.Windows.Forms.GridTablesFactory`
- `T:System.Windows.Forms.GridTableStylesCollection`
- `T:System.Windows.Forms.IDataGridEditingService`
- `T:System.Windows.Forms.DataGrid.HitTestType`
- `T:System.Windows.Forms.Design.IMenuEditorService`

-->
