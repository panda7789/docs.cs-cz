---
title: Architektura ovládacího prvku DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 892168ec282fbf168c43515e0718fe5486a345a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011608"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="0470e-102">Architektura ovládacího prvku DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0470e-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="0470e-103"><xref:System.Windows.Forms.DataGridView> Ovládacího prvku a jeho souvisejícími třídami jsou navržené tak flexibilní a rozšiřitelný systém pro zobrazení a úpravy tabulková data.</span><span class="sxs-lookup"><span data-stu-id="0470e-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="0470e-104">Tyto třídy jsou obsaženy v <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů a že jsou všechny pojmenované s předponou "DataGridView".</span><span class="sxs-lookup"><span data-stu-id="0470e-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="0470e-105">Prvky architektury</span><span class="sxs-lookup"><span data-stu-id="0470e-105">Architecture Elements</span></span>  
 <span data-ttu-id="0470e-106">Primární <xref:System.Windows.Forms.DataGridView> doprovodné třídy odvozovat z <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="0470e-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="0470e-107">Následující objektový model ukazuje <xref:System.Windows.Forms.DataGridViewElement> hierarchii dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="0470e-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 ![Diagram znázorňující hierarchii DataGridViewElement – objektový Model.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <span data-ttu-id="0470e-109"><xref:System.Windows.Forms.DataGridViewElement> Třída poskytuje odkaz na nadřazený <xref:System.Windows.Forms.DataGridView> ovládací prvek a má <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnost, která obsahuje hodnotu, která představuje kombinaci hodnot z <xref:System.Windows.Forms.DataGridViewElementStates> výčtu.</span><span class="sxs-lookup"><span data-stu-id="0470e-109">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="0470e-110">V následujících částech <xref:System.Windows.Forms.DataGridView> doprovodné třídy podrobněji.</span><span class="sxs-lookup"><span data-stu-id="0470e-110">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="0470e-111">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="0470e-111">DataGridViewElementStates</span></span>  
 <span data-ttu-id="0470e-112"><xref:System.Windows.Forms.DataGridViewElementStates> Výčet obsahuje následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="0470e-112">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="0470e-113">Hodnoty tento výčet je možné kombinovat s bitové logické operátory, takže <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnost můžete vyjádřit najednou více než jeden stav.</span><span class="sxs-lookup"><span data-stu-id="0470e-113">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="0470e-114">Například <xref:System.Windows.Forms.DataGridViewElement> může být současně <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, a <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="0470e-114">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="0470e-115">Buňky a pruhy</span><span class="sxs-lookup"><span data-stu-id="0470e-115">Cells and Bands</span></span>  
 <span data-ttu-id="0470e-116"><xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje dva základní druhy objektů: buňky a pruhy.</span><span class="sxs-lookup"><span data-stu-id="0470e-116">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="0470e-117">Všechny buňky odvozovat <xref:System.Windows.Forms.DataGridViewCell> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="0470e-117">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="0470e-118">Dva druhy pruhy, <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewRow>, obě jsou odvozeny z <xref:System.Windows.Forms.DataGridViewBand> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="0470e-118">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="0470e-119"><xref:System.Windows.Forms.DataGridView> Ovládací prvek spolupracuje s více třídami, ale jsou nejčastěji vyskytují <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, a <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="0470e-119">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="0470e-120">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="0470e-120">DataGridViewCell</span></span>  
 <span data-ttu-id="0470e-121">Je základní jednotkou interakce pro buňku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="0470e-121">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="0470e-122">U buněk zarovnaný na střed zobrazení a zadávání dat často probíhá prostřednictvím buňky.</span><span class="sxs-lookup"><span data-stu-id="0470e-122">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="0470e-123">Přistupujete buňky pomocí <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> kolekce <xref:System.Windows.Forms.DataGridViewRow> třídy kde můžete přistupovat pomocí vybrané buňky <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekce <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0470e-123">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0470e-124">Následující objektový model ukazuje toto využití a ukazuje, <xref:System.Windows.Forms.DataGridViewCell> hierarchii dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="0470e-124">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 ![Diagram znázorňující hierarchii modelu objektu DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <span data-ttu-id="0470e-126"><xref:System.Windows.Forms.DataGridViewCell> Typ je abstraktní základní třída, ze které jsou odvozeny všechny typy buňky.</span><span class="sxs-lookup"><span data-stu-id="0470e-126">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="0470e-127"><xref:System.Windows.Forms.DataGridViewCell> a jeho odvozených typů nejsou ovládacích prvků Windows Forms, ale některé hostitelské ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0470e-127"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="0470e-128">Žádné funkce pro úpravy podporovaných buňky je obvykle zpracovávána hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0470e-128">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="0470e-129"><xref:System.Windows.Forms.DataGridViewCell> objekty nejsou v ovládacím prvku vlastní vzhled a funkce Malování stejným způsobem jako ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0470e-129"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="0470e-130">Místo toho <xref:System.Windows.Forms.DataGridView> zodpovídá za vzhled jeho <xref:System.Windows.Forms.DataGridViewCell> objekty.</span><span class="sxs-lookup"><span data-stu-id="0470e-130">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="0470e-131">To interakcí se může významně ovlivnit vzhled a chování buněk <xref:System.Windows.Forms.DataGridView> vlastnosti a události ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0470e-131">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="0470e-132">Pokud máte zvláštní požadavky na přizpůsobení, které jsou nad rámec možností <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete implementovat vlastní třídu odvozenou od <xref:System.Windows.Forms.DataGridViewCell> nebo jeden z jejích podřízených tříd.</span><span class="sxs-lookup"><span data-stu-id="0470e-132">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="0470e-133">V následující seznamu jsou uvedeny třídy odvozené od <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="0470e-133">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
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
  
- <span data-ttu-id="0470e-134">Vaše vlastní typy</span><span class="sxs-lookup"><span data-stu-id="0470e-134">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="0470e-135">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="0470e-135">DataGridViewColumn</span></span>  
 <span data-ttu-id="0470e-136">Schéma <xref:System.Windows.Forms.DataGridView> ovládacího prvku připojené datové úložiště je vyjádřen v <xref:System.Windows.Forms.DataGridView> sloupce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0470e-136">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="0470e-137">Můžete přistupovat <xref:System.Windows.Forms.DataGridView> sloupce ovládacího prvku s použitím <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0470e-137">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="0470e-138">Dostanete z vybraných sloupců pomocí <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0470e-138">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="0470e-139">Následující objektový model ukazuje toto využití a ukazuje, <xref:System.Windows.Forms.DataGridViewColumn> hierarchii dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="0470e-139">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 ![Diagram znázorňující hierarchii modelu objektu DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 <span data-ttu-id="0470e-141">Některé typy klíčů buněk mají odpovídající typy sloupců.</span><span class="sxs-lookup"><span data-stu-id="0470e-141">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="0470e-142">Tyto jsou odvozeny z <xref:System.Windows.Forms.DataGridViewColumn> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="0470e-142">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="0470e-143">V následující seznamu jsou uvedeny třídy odvozené od <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="0470e-143">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- <span data-ttu-id="0470e-144">Vaše typy vlastní sloupec</span><span class="sxs-lookup"><span data-stu-id="0470e-144">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="0470e-145">Úpravy ovládacích prvků DataGridView</span><span class="sxs-lookup"><span data-stu-id="0470e-145">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="0470e-146">Buňky, které podporují pokročilé funkce pro úpravy obvykle používají hostovaného ovládacího prvku, který je odvozen z ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0470e-146">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="0470e-147">Tyto ovládací prvky implementovat taky <xref:System.Windows.Forms.IDataGridViewEditingControl> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0470e-147">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="0470e-148">Následující objektový model ukazuje využití těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="0470e-148">The following object model illustrates the usage of these controls.</span></span>  
  
 ![Diagram znázorňující hierarchii Model objektu úpravy ovládacího prvku DataGridView.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <span data-ttu-id="0470e-150">Následující ovládací prvky pro úpravy jsou součástí <xref:System.Windows.Forms.DataGridView> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="0470e-150">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="0470e-151">Informace o vytváření vlastních úprav ovládacích prvků naleznete v tématu [jak: Hostování ovládacích prvků ve Windows Forms DataGridView buňky](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="0470e-151">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="0470e-152">Následující tabulka znázorňuje vztah mezi typy buněk, typy sloupců a ovládací prvky pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="0470e-152">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="0470e-153">Typ buňky</span><span class="sxs-lookup"><span data-stu-id="0470e-153">Cell type</span></span>|<span data-ttu-id="0470e-154">Hostovaného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="0470e-154">Hosted control</span></span>|<span data-ttu-id="0470e-155">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="0470e-155">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="0470e-156">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="0470e-156">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="0470e-157">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="0470e-157">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="0470e-158">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="0470e-158">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="0470e-159">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="0470e-159">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="0470e-160">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="0470e-160">DataGridViewRow</span></span>  
 <span data-ttu-id="0470e-161"><xref:System.Windows.Forms.DataGridViewRow> Třídy zobrazí pole záznamu dat z data ukládat do kterého <xref:System.Windows.Forms.DataGridView> ovládací prvek připojen.</span><span class="sxs-lookup"><span data-stu-id="0470e-161">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="0470e-162">Můžete přistupovat <xref:System.Windows.Forms.DataGridView> řádků ovládacího prvku s použitím <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0470e-162">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="0470e-163">Vybrané řádky přístupné prostřednictvím <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="0470e-163">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="0470e-164">Následující objektový model ukazuje toto využití a ukazuje, <xref:System.Windows.Forms.DataGridViewRow> hierarchii dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="0470e-164">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 ![Diagram znázorňující hierarchii DataGridViewRow objektový Model.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <span data-ttu-id="0470e-166">Můžete odvozovat vlastní typy z <xref:System.Windows.Forms.DataGridViewRow> třídy, i když to není obvykle nutné.</span><span class="sxs-lookup"><span data-stu-id="0470e-166">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="0470e-167"><xref:System.Windows.Forms.DataGridView> Ovládací prvek má několik řádků související události a vlastnosti pro přizpůsobení chování jeho <xref:System.Windows.Forms.DataGridViewRow> objekty.</span><span class="sxs-lookup"><span data-stu-id="0470e-167">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="0470e-168">Pokud povolíte <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> , zvláštní řádek pro přidání nových řádků se zobrazí jako poslední řádek.</span><span class="sxs-lookup"><span data-stu-id="0470e-168">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="0470e-169">Tento řádek je součástí <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce, ale má speciální funkce, které můžou vyžadovat vaši pozornost.</span><span class="sxs-lookup"><span data-stu-id="0470e-169">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="0470e-170">Další informace najdete v tématu [použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="0470e-170">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0470e-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0470e-171">See also</span></span>

- [<span data-ttu-id="0470e-172">Přehled ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="0470e-172">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="0470e-173">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0470e-173">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="0470e-174">Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0470e-174">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
