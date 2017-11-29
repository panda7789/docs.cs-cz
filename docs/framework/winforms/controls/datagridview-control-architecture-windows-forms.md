---
title: "Architektura ovládacího prvku DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb44a32e63fd7a0ff0e480c205d5459da2ce2bd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="496cf-102">Architektura ovládacího prvku DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="496cf-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="496cf-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek a jeho souvisejících tříd jsou navržené jako flexibilní a rozšiřitelný systém pro zobrazení a úpravy tabulková data.</span><span class="sxs-lookup"><span data-stu-id="496cf-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="496cf-104">Tyto třídy jsou obsaženy v <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů a že jsou všechny pojmenované s předponou "DataGridView".</span><span class="sxs-lookup"><span data-stu-id="496cf-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="496cf-105">Architektura elementy</span><span class="sxs-lookup"><span data-stu-id="496cf-105">Architecture Elements</span></span>  
 <span data-ttu-id="496cf-106">Primární <xref:System.Windows.Forms.DataGridView> doprovodné třídy jsou odvozeny od <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="496cf-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="496cf-107">Znázorňuje následující objektový model <xref:System.Windows.Forms.DataGridViewElement> hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="496cf-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="496cf-108">![DataGridViewElement – objektový Model](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement –")</span><span class="sxs-lookup"><span data-stu-id="496cf-108">![DataGridViewElement Object Model](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span></span>  
<span data-ttu-id="496cf-109">DataGridViewElement – objektový model</span><span class="sxs-lookup"><span data-stu-id="496cf-109">DataGridViewElement object model</span></span>  
  
 <span data-ttu-id="496cf-110"><xref:System.Windows.Forms.DataGridViewElement> Třída poskytuje odkaz na nadřazený <xref:System.Windows.Forms.DataGridView> řízení a má <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnosti, která obsahuje hodnotu, která představuje kombinace hodnot z <xref:System.Windows.Forms.DataGridViewElementStates> výčtu.</span><span class="sxs-lookup"><span data-stu-id="496cf-110">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="496cf-111">Následující části popisují <xref:System.Windows.Forms.DataGridView> doprovodné třídy podrobněji.</span><span class="sxs-lookup"><span data-stu-id="496cf-111">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="496cf-112">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="496cf-112">DataGridViewElementStates</span></span>  
 <span data-ttu-id="496cf-113"><xref:System.Windows.Forms.DataGridViewElementStates> Výčet obsahuje následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="496cf-113">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="496cf-114">Hodnoty tento výčet je možné kombinovat s bitové logické operátory, proto <xref:System.Windows.Forms.DataGridViewElement.State%2A> vlastnost express víc než jeden stav najednou.</span><span class="sxs-lookup"><span data-stu-id="496cf-114">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="496cf-115">Například <xref:System.Windows.Forms.DataGridViewElement> může být současně <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, a <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="496cf-115">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="496cf-116">Buňky a pruhy</span><span class="sxs-lookup"><span data-stu-id="496cf-116">Cells and Bands</span></span>  
 <span data-ttu-id="496cf-117"><xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje dva základní typy objektů: buněk a pruhy.</span><span class="sxs-lookup"><span data-stu-id="496cf-117">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="496cf-118">Všechny buňky odvozena od <xref:System.Windows.Forms.DataGridViewCell> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="496cf-118">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="496cf-119">Dva druhy pruhy, <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.DataGridViewRow>, obě jsou odvozeny od <xref:System.Windows.Forms.DataGridViewBand> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="496cf-119">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="496cf-120"><xref:System.Windows.Forms.DataGridView> Řízení spolupracuje s několik tříd, ale jsou nejčastěji došlo k <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, a <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="496cf-120">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="496cf-121">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="496cf-121">DataGridViewCell</span></span>  
 <span data-ttu-id="496cf-122">Buňky je základní jednotkou interakce pro <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="496cf-122">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="496cf-123">Zobrazení se jedná o buněk a vkládání dat se často provádí prostřednictvím buněk.</span><span class="sxs-lookup"><span data-stu-id="496cf-123">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="496cf-124">Máte přístup k buněk pomocí <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> kolekce <xref:System.Windows.Forms.DataGridViewRow> třídy a můžete přistupovat pomocí vybrané buňky <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekce <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="496cf-124">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="496cf-125">Následující objektový model ukazuje toto využití a zobrazuje <xref:System.Windows.Forms.DataGridViewCell> hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="496cf-125">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="496cf-126">![DataGridViewCell – objektový Model](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span><span class="sxs-lookup"><span data-stu-id="496cf-126">![DataGridViewCell Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span></span>  
<span data-ttu-id="496cf-127">DataGridViewCell objektový model</span><span class="sxs-lookup"><span data-stu-id="496cf-127">DataGridViewCell object model</span></span>  
  
 <span data-ttu-id="496cf-128"><xref:System.Windows.Forms.DataGridViewCell> Typ je abstraktní základní třídu, ze které jsou odvozeny všechny typy buňky.</span><span class="sxs-lookup"><span data-stu-id="496cf-128">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="496cf-129"><xref:System.Windows.Forms.DataGridViewCell>a jeho odvozených typů nejsou ovládací prvky Windows Forms, ale některé ovládací prvky Windows Forms hostitele.</span><span class="sxs-lookup"><span data-stu-id="496cf-129"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="496cf-130">Žádné úpravy funkce nepodporuje buňku je obvykle zpracovávány hostované ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="496cf-130">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="496cf-131"><xref:System.Windows.Forms.DataGridViewCell>objekty neurčují vlastní vzhled a funkce Malování stejným způsobem, jak Windows Forms – ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="496cf-131"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="496cf-132">Místo toho <xref:System.Windows.Forms.DataGridView> zodpovídá za vzhled jeho <xref:System.Windows.Forms.DataGridViewCell> objekty.</span><span class="sxs-lookup"><span data-stu-id="496cf-132">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="496cf-133">Vzhled a chování buněk může výrazně ovlivnit interakcí s <xref:System.Windows.Forms.DataGridView> vlastnosti a události ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="496cf-133">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="496cf-134">Pokud máte speciální požadavky pro úpravy, které jsou nad rámec možností <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete implementovat vlastní třídu odvozenou od <xref:System.Windows.Forms.DataGridViewCell> nebo jedna z jejích podřízených tříd.</span><span class="sxs-lookup"><span data-stu-id="496cf-134">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="496cf-135">V následujícím seznamu jsou uvedeny třídy odvozené z <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="496cf-135">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   <span data-ttu-id="496cf-136">Vaše vlastní buňky typy</span><span class="sxs-lookup"><span data-stu-id="496cf-136">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="496cf-137">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="496cf-137">DataGridViewColumn</span></span>  
 <span data-ttu-id="496cf-138">Schéma <xref:System.Windows.Forms.DataGridView> úložiště připojená data ovládacího prvku je vyjádřena v <xref:System.Windows.Forms.DataGridView> sloupce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="496cf-138">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="496cf-139">Dostanete <xref:System.Windows.Forms.DataGridView> sloupce ovládacího prvku pomocí <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="496cf-139">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="496cf-140">Máte přístup k vybrané sloupce pomocí <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="496cf-140">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="496cf-141">Následující objektový model ukazuje toto využití a zobrazuje <xref:System.Windows.Forms.DataGridViewColumn> hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="496cf-141">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="496cf-142">![DataGridViewColumn – objektový Model](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span><span class="sxs-lookup"><span data-stu-id="496cf-142">![DataGridViewColumn Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span></span>  
<span data-ttu-id="496cf-143">DataGridViewColumn objektový model</span><span class="sxs-lookup"><span data-stu-id="496cf-143">DataGridViewColumn object model</span></span>  
  
 <span data-ttu-id="496cf-144">Některé typy klíčů buňky mají odpovídající typy sloupců.</span><span class="sxs-lookup"><span data-stu-id="496cf-144">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="496cf-145">Tyto jsou odvozeny od <xref:System.Windows.Forms.DataGridViewColumn> základní třídy.</span><span class="sxs-lookup"><span data-stu-id="496cf-145">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="496cf-146">V následujícím seznamu jsou uvedeny třídy odvozené z <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="496cf-146">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   <span data-ttu-id="496cf-147">Vaše vlastní sloupec typy</span><span class="sxs-lookup"><span data-stu-id="496cf-147">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="496cf-148">Ovládací prvky úprav DataGridView</span><span class="sxs-lookup"><span data-stu-id="496cf-148">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="496cf-149">Buněk, které obvykle podporu pokročilých funkcí úpravy pomocí hostované ovládací prvek, který je odvozený z ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="496cf-149">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="496cf-150">Tyto ovládací prvky taky implementovat <xref:System.Windows.Forms.IDataGridViewEditingControl> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="496cf-150">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="496cf-151">Následující objektový model ukazuje použití těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="496cf-151">The following object model illustrates the usage of these controls.</span></span>  
  
 <span data-ttu-id="496cf-152">![Úpravy objektový Model ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span><span class="sxs-lookup"><span data-stu-id="496cf-152">![DataGridView Editing Control Object Model](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span></span>  
<span data-ttu-id="496cf-153">Objektový model úpravy ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="496cf-153">DataGridView editing control object model</span></span>  
  
 <span data-ttu-id="496cf-154">Jsou k dispozici následující ovládací prvky pro úpravy s <xref:System.Windows.Forms.DataGridView> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="496cf-154">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="496cf-155">Informace o vytváření vlastních úprav ovládacích prvků najdete v tématu [postup: hostitelské ovládací prvky v systému Windows Forms DataGridView buněk](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="496cf-155">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="496cf-156">Následující tabulka ukazuje vztah mezi buňky typy, typy sloupců a ovládací prvky pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="496cf-156">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="496cf-157">Typ buňky</span><span class="sxs-lookup"><span data-stu-id="496cf-157">Cell type</span></span>|<span data-ttu-id="496cf-158">Hostované ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="496cf-158">Hosted control</span></span>|<span data-ttu-id="496cf-159">Typ sloupce</span><span class="sxs-lookup"><span data-stu-id="496cf-159">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="496cf-160">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="496cf-160">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="496cf-161">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="496cf-161">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="496cf-162">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="496cf-162">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="496cf-163">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="496cf-163">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="496cf-164">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="496cf-164">DataGridViewRow</span></span>  
 <span data-ttu-id="496cf-165"><xref:System.Windows.Forms.DataGridViewRow> Třída zobrazí pole záznam dat z data ukládat do kterého <xref:System.Windows.Forms.DataGridView> ovládací prvek připojen.</span><span class="sxs-lookup"><span data-stu-id="496cf-165">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="496cf-166">Dostanete <xref:System.Windows.Forms.DataGridView> řádek ovládacího prvku pomocí <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="496cf-166">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="496cf-167">Máte přístup k vybrané řádky pomocí <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="496cf-167">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="496cf-168">Následující objektový model ukazuje toto využití a zobrazuje <xref:System.Windows.Forms.DataGridViewRow> hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="496cf-168">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="496cf-169">![Model objektu DataGridViewRow](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span><span class="sxs-lookup"><span data-stu-id="496cf-169">![DataGridViewRow Object Model](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span></span>  
<span data-ttu-id="496cf-170">DataGridViewRow objektový model</span><span class="sxs-lookup"><span data-stu-id="496cf-170">DataGridViewRow object model</span></span>  
  
 <span data-ttu-id="496cf-171">Odvozujete vlastních typů z <xref:System.Windows.Forms.DataGridViewRow> třídy, i když to není obvykle nutné.</span><span class="sxs-lookup"><span data-stu-id="496cf-171">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="496cf-172"><xref:System.Windows.Forms.DataGridView> Ovládací prvek má několik řádků související události a vlastnosti pro přizpůsobení chování jeho <xref:System.Windows.Forms.DataGridViewRow> objekty.</span><span class="sxs-lookup"><span data-stu-id="496cf-172">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="496cf-173">Pokud povolíte <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> vlastnost, zvláštní řádek pro přidání nové řádky se zobrazí jako poslední řádek.</span><span class="sxs-lookup"><span data-stu-id="496cf-173">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="496cf-174">Tento řádek je součástí <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce, ale má zvláštní funkce, které můžou vyžadovat vaši pozornost.</span><span class="sxs-lookup"><span data-stu-id="496cf-174">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="496cf-175">Další informace najdete v tématu [použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="496cf-175">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="496cf-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="496cf-176">See Also</span></span>  
 [<span data-ttu-id="496cf-177">Přehled ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="496cf-177">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [<span data-ttu-id="496cf-178">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="496cf-178">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="496cf-179">Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="496cf-179">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
