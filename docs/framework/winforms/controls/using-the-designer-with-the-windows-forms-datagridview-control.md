---
title: Používání Návrháře s ovládacím prvkem Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
ms.openlocfilehash: 588db8b2f66bbfd58ea6197a7b5a65bb8ecbfd19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644807"
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="c2f92-102">Používání Návrháře s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c2f92-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c2f92-103">Visual Studio podporuje návrháře `DataGridView` ovládací prvek, který umožňuje provádět mnoho úloh její úvodního nastavení bez nutnosti psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="c2f92-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="c2f92-104">Tyto úlohy zahrnují vazby ovládacího prvku na zdroj dat, úprava sloupce, které slouží k zobrazení dat a úprava vzhledu a základní chování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2f92-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2f92-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c2f92-105">In This Section</span></span>  
 [<span data-ttu-id="c2f92-106">Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="c2f92-107">Popisuje způsob použití **přidat sloupce** a **upravit sloupce** dialogových oknech naplnit a upravovat kolekce sloupců.</span><span class="sxs-lookup"><span data-stu-id="c2f92-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="c2f92-108">Postupy: Vytvoření vazby dat na ovládací prvek Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="c2f92-109">Popisuje způsob použití **zvolit zdroj dat** možnost na inteligentní značky ovládacího prvku pro připojení k datům.</span><span class="sxs-lookup"><span data-stu-id="c2f92-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="c2f92-110">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="c2f92-111">Popisuje způsob použití **upravit sloupce** dialogové okno změnit uspořádání sloupců.</span><span class="sxs-lookup"><span data-stu-id="c2f92-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="c2f92-112">Postupy: Změna typu sloupce Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="c2f92-113">Popisuje způsob použití **upravit sloupce** dialogové okno Změnit typ sloupce.</span><span class="sxs-lookup"><span data-stu-id="c2f92-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="c2f92-114">Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="c2f92-115">Popisuje, jak povolit uživatelům změnit uspořádání sloupců pomocí inteligentní značky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2f92-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="c2f92-116">Postupy: Ukotvit sloupce v ovládacím prvku Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="c2f92-117">Popisuje způsob použití **upravit sloupce** dialogové okno zabránit posouvání určité sloupce.</span><span class="sxs-lookup"><span data-stu-id="c2f92-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="c2f92-118">Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="c2f92-119">Popisuje způsob použití **upravit sloupce** dialogové okno skrýt určité sloupce.</span><span class="sxs-lookup"><span data-stu-id="c2f92-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="c2f92-120">Postupy: Nastavení sloupců jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="c2f92-121">Popisuje způsob použití **upravit sloupce** dialogové okno zabránit uživatelům v úpravách hodnoty v určité sloupce.</span><span class="sxs-lookup"><span data-stu-id="c2f92-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="c2f92-122">Postupy: Zabránit řádku přidání a odstranění v ovládacím prvku Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="c2f92-123">Popisuje, jak můžete zabránit uživatelům v přidávání nebo odstraňování řádků inteligentní značky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2f92-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="c2f92-124">Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="c2f92-125">Popisuje způsob použití **sestavení objektu CellStyle** dialogové okno Vytvořit vzhled účetní knihy v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c2f92-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="c2f92-126">Postupy: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="c2f92-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/default-cell-styles-datagridview.md)  
 <span data-ttu-id="c2f92-127">Popisuje způsob použití **sestavení objektu CellStyle** dialogové okno nastavení základního vzhledu a zobrazení datových formátů pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c2f92-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c2f92-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="c2f92-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="c2f92-129">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2f92-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f92-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2f92-130">See also</span></span>
- [<span data-ttu-id="c2f92-131">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="c2f92-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
