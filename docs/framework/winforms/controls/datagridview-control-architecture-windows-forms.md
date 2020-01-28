---
title: Architektura ovládacího prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742525"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="30e20-102">Architektura ovládacího prvku DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="30e20-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="30e20-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> a jeho související třídy jsou navržené tak, aby byly flexibilní a rozšiřitelný systém pro zobrazení a úpravy tabulkových dat.</span><span class="sxs-lookup"><span data-stu-id="30e20-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="30e20-104">Tyto třídy jsou obsaženy v oboru názvů <xref:System.Windows.Forms?displayProperty=nameWithType> a jsou všechny pojmenovány s předponou "DataGridView".</span><span class="sxs-lookup"><span data-stu-id="30e20-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="30e20-105">Prvky architektury</span><span class="sxs-lookup"><span data-stu-id="30e20-105">Architecture Elements</span></span>  
 <span data-ttu-id="30e20-106">Primární <xref:System.Windows.Forms.DataGridView> doprovodné třídy jsou odvozeny z <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="30e20-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="30e20-107">Následující objektový model znázorňuje <xref:System.Windows.Forms.DataGridViewElement> hierarchii dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="30e20-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 ![Diagram, který zobrazuje hierarchii objektového modelu DataGridViewElement.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <span data-ttu-id="30e20-109">Třída <xref:System.Windows.Forms.DataGridViewElement> poskytuje odkaz na nadřazený ovládací prvek <xref:System.Windows.Forms.DataGridView> a má vlastnost <xref:System.Windows.Forms.DataGridViewElement.State%2A>, která obsahuje hodnotu, která představuje kombinaci hodnot z výčtu <xref:System.Windows.Forms.DataGridViewElementStates>.</span><span class="sxs-lookup"><span data-stu-id="30e20-109">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="30e20-110">Následující části popisují <xref:System.Windows.Forms.DataGridView> doprovodné třídy podrobněji.</span><span class="sxs-lookup"><span data-stu-id="30e20-110">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="30e20-111">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="30e20-111">DataGridViewElementStates</span></span>  
 <span data-ttu-id="30e20-112"><xref:System.Windows.Forms.DataGridViewElementStates> Výčet obsahuje následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="30e20-112">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="30e20-113">Hodnoty tohoto výčtu lze kombinovat s bitovými logickými operátory, takže vlastnost <xref:System.Windows.Forms.DataGridViewElement.State%2A> může vyjádřit více než jeden stav najednou.</span><span class="sxs-lookup"><span data-stu-id="30e20-113">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="30e20-114"><xref:System.Windows.Forms.DataGridViewElement> může být například současně <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>a <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="30e20-114">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="30e20-115">Buňky a pruhy</span><span class="sxs-lookup"><span data-stu-id="30e20-115">Cells and Bands</span></span>  
 <span data-ttu-id="30e20-116">Ovládací prvek <xref:System.Windows.Forms.DataGridView> obsahuje dva základní druhy objektů: buňky a pásma.</span><span class="sxs-lookup"><span data-stu-id="30e20-116">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="30e20-117">Všechny buňky jsou odvozeny od <xref:System.Windows.Forms.DataGridViewCell> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="30e20-117">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="30e20-118">Dva druhy pásem, <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewRow>, jsou odvozeny ze <xref:System.Windows.Forms.DataGridViewBand> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="30e20-118">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="30e20-119">Ovládací prvek <xref:System.Windows.Forms.DataGridView> spolupracuje s několika třídami, ale nejčastěji zjištěné jsou <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>a <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="30e20-119">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="30e20-120">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="30e20-120">DataGridViewCell</span></span>  
 <span data-ttu-id="30e20-121">Buňka je základní jednotkou interakce pro <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="30e20-121">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="30e20-122">Zobrazení se zacentruje na buňky a zadání dat se často provádí v buňkách.</span><span class="sxs-lookup"><span data-stu-id="30e20-122">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="30e20-123">K buňkám můžete přistupovat pomocí <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> kolekce <xref:System.Windows.Forms.DataGridViewRow> třídy a k vybraným buňkám můžete přistupovat pomocí kolekce <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="30e20-123">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="30e20-124">Následující objektový model znázorňuje toto použití a ukazuje hierarchii dědičnosti <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="30e20-124">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 ![Diagram, který zobrazuje hierarchii objektového modelu DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <span data-ttu-id="30e20-126">Typ <xref:System.Windows.Forms.DataGridViewCell> je abstraktní základní třída, ze které jsou odvozeny všechny typy buněk.</span><span class="sxs-lookup"><span data-stu-id="30e20-126">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="30e20-127"><xref:System.Windows.Forms.DataGridViewCell> a jeho odvozené typy nejsou model Windows Forms ovládací prvky, ale některé ovládací prvky model Windows Forms hostitele.</span><span class="sxs-lookup"><span data-stu-id="30e20-127"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="30e20-128">Všechny funkce úprav, které buňka podporuje, je obvykle zpracovávána hostovaným ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="30e20-128">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="30e20-129"><xref:System.Windows.Forms.DataGridViewCell> objekty neovládají vlastní funkce vzhledu a malování stejným způsobem jako model Windows Forms ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="30e20-129"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="30e20-130">Místo toho je <xref:System.Windows.Forms.DataGridView> zodpovědná za vzhled jeho <xref:System.Windows.Forms.DataGridViewCell>ch objektů.</span><span class="sxs-lookup"><span data-stu-id="30e20-130">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="30e20-131">Při interakci s vlastnostmi a událostmi ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete významně ovlivnit vzhled a chování buněk.</span><span class="sxs-lookup"><span data-stu-id="30e20-131">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="30e20-132">Pokud máte zvláštní požadavky pro přizpůsobení, které jsou nad rámec možností ovládacího prvku <xref:System.Windows.Forms.DataGridView>, můžete implementovat vlastní třídu, která je odvozena z <xref:System.Windows.Forms.DataGridViewCell> nebo některé z jejích podřízených tříd.</span><span class="sxs-lookup"><span data-stu-id="30e20-132">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="30e20-133">Následující seznam obsahuje třídy odvozené od <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="30e20-133">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- <span data-ttu-id="30e20-134">Vlastní typy buněk</span><span class="sxs-lookup"><span data-stu-id="30e20-134">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="30e20-135">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="30e20-135">DataGridViewColumn</span></span>  
 <span data-ttu-id="30e20-136">Schéma připojeného úložiště dat ovládacího prvku <xref:System.Windows.Forms.DataGridView> je vyjádřeno ve sloupcích <xref:System.Windows.Forms.DataGridView>ho ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="30e20-136">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="30e20-137">Ke sloupcům ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přistupovat pomocí kolekce <xref:System.Windows.Forms.DataGridView.Columns%2A>.</span><span class="sxs-lookup"><span data-stu-id="30e20-137">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="30e20-138">K vybraným sloupcům můžete přistupovat pomocí kolekce <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="30e20-138">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="30e20-139">Následující objektový model znázorňuje toto použití a ukazuje hierarchii dědičnosti <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="30e20-139">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 ![Diagram, který znázorňuje hierarchii objektového modelu DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 <span data-ttu-id="30e20-141">Některé typy klíčových buněk mají odpovídající typy sloupců.</span><span class="sxs-lookup"><span data-stu-id="30e20-141">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="30e20-142">Tyto jsou odvozeny od <xref:System.Windows.Forms.DataGridViewColumn> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="30e20-142">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="30e20-143">Následující seznam obsahuje třídy odvozené od <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="30e20-143">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- <span data-ttu-id="30e20-144">Vlastní typy sloupců</span><span class="sxs-lookup"><span data-stu-id="30e20-144">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="30e20-145">Ovládací prvky DataGridView pro úpravy</span><span class="sxs-lookup"><span data-stu-id="30e20-145">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="30e20-146">Buňky, které podporují pokročilé funkce úprav, obvykle používají hostovaný ovládací prvek, který je odvozen od ovládacího prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="30e20-146">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="30e20-147">Tyto ovládací prvky také implementují rozhraní <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="30e20-147">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="30e20-148">Následující objektový model znázorňuje použití těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="30e20-148">The following object model illustrates the usage of these controls.</span></span>  
  
 ![Diagram znázorňující hierarchii modelu objektu ovládacího prvku pro úpravu DataGridView](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <span data-ttu-id="30e20-150">S ovládacím prvkem <xref:System.Windows.Forms.DataGridView> jsou k dispozici následující ovládací prvky pro úpravy:</span><span class="sxs-lookup"><span data-stu-id="30e20-150">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="30e20-151">Informace o vytváření vlastních ovládacích prvků pro úpravy naleznete v tématu [How to: Host Controls in model Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="30e20-151">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="30e20-152">Následující tabulka znázorňuje vztah mezi typy buněk, typy sloupců a ovládacími prvky pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="30e20-152">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="30e20-153">Typ buňky</span><span class="sxs-lookup"><span data-stu-id="30e20-153">Cell type</span></span>|<span data-ttu-id="30e20-154">Hostovaný ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="30e20-154">Hosted control</span></span>|<span data-ttu-id="30e20-155">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="30e20-155">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="30e20-156">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="30e20-156">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="30e20-157">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="30e20-157">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="30e20-158">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="30e20-158">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="30e20-159">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="30e20-159">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="30e20-160">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="30e20-160">DataGridViewRow</span></span>  
 <span data-ttu-id="30e20-161">Třída <xref:System.Windows.Forms.DataGridViewRow> zobrazuje datová pole záznamu z úložiště dat, ke kterému je připojen ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="30e20-161">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="30e20-162">K řádkům ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přistupovat pomocí kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A>.</span><span class="sxs-lookup"><span data-stu-id="30e20-162">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="30e20-163">K vybraným řádkům můžete přistupovat pomocí kolekce <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="30e20-163">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="30e20-164">Následující objektový model znázorňuje toto použití a ukazuje hierarchii dědičnosti <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="30e20-164">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 ![Diagram, který zobrazuje hierarchii objektového modelu DataGridViewRow.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <span data-ttu-id="30e20-166">Z třídy <xref:System.Windows.Forms.DataGridViewRow> můžete odvodit vlastní typy, i když to obvykle nebude nutné.</span><span class="sxs-lookup"><span data-stu-id="30e20-166">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="30e20-167">Ovládací prvek <xref:System.Windows.Forms.DataGridView> má několik událostí souvisejících s řádky a vlastnosti pro přizpůsobení chování jeho objektů <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="30e20-167">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="30e20-168">Pokud povolíte vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> ovládacího prvku <xref:System.Windows.Forms.DataGridView>, zobrazí se speciální řádek pro přidání nových řádků jako poslední řádek.</span><span class="sxs-lookup"><span data-stu-id="30e20-168">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="30e20-169">Tento řádek je součástí kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A>, ale má speciální funkce, které mohou vyžadovat vaši pozornost.</span><span class="sxs-lookup"><span data-stu-id="30e20-169">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="30e20-170">Další informace najdete v tématu [použití řádku pro nové záznamy v ovládacím prvku DataGridView model Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="30e20-170">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e20-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30e20-171">See also</span></span>

- [<span data-ttu-id="30e20-172">Přehled ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="30e20-172">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="30e20-173">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="30e20-173">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="30e20-174">Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="30e20-174">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
