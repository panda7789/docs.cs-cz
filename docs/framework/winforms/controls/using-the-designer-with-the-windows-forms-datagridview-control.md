---
title: "Používání Návrháře s ovládacím prvkem Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9df10ecabc8f61c3ef984adb6466f195395fd181
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="9305e-102">Používání Návrháře s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9305e-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9305e-103">Visual Studio poskytuje návrháře podpora `DataGridView` ovládací prvek, který umožňuje provádět mnoho úloh nastavení bez nutnosti psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="9305e-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="9305e-104">Tyto úlohy patří vazbu ovládacího prvku ke zdroji dat, úprava sloupce, které slouží k zobrazení dat a úpravě vzhled a chování základní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9305e-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9305e-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9305e-105">In This Section</span></span>  
 [<span data-ttu-id="9305e-106">Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="9305e-107">Popisuje postup použití **přidat sloupce** a **upravit sloupce** dialogových oken k naplnění a upravit kolekci sloupců.</span><span class="sxs-lookup"><span data-stu-id="9305e-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="9305e-108">Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="9305e-109">Popisuje postup použití **zvolit zdroj dat** možnost na inteligentní značky ovládacího prvku pro připojení k datům.</span><span class="sxs-lookup"><span data-stu-id="9305e-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="9305e-110">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="9305e-111">Popisuje postup použití **upravit sloupce** dialogové okno ke změně uspořádání sloupců.</span><span class="sxs-lookup"><span data-stu-id="9305e-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="9305e-112">Postupy: Změna typu sloupce Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="9305e-113">Popisuje postup použití **upravit sloupce** dialogové okno Změnit typy sloupců.</span><span class="sxs-lookup"><span data-stu-id="9305e-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="9305e-114">Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="9305e-115">Popisuje, jak používat inteligentní značky ovládacího prvku k umožnění uživatelům Změna uspořádání sloupců.</span><span class="sxs-lookup"><span data-stu-id="9305e-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="9305e-116">Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="9305e-117">Popisuje postup použití **upravit sloupce** dialogové okno zabránit posouvání určité sloupce.</span><span class="sxs-lookup"><span data-stu-id="9305e-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="9305e-118">Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="9305e-119">Popisuje postup použití **upravit sloupce** dialogové okno ke skrytí určité sloupce.</span><span class="sxs-lookup"><span data-stu-id="9305e-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="9305e-120">Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="9305e-121">Popisuje postup použití **upravit sloupce** dialogové okno uživatelům zabránit v úpravách hodnoty v určité sloupce.</span><span class="sxs-lookup"><span data-stu-id="9305e-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="9305e-122">Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="9305e-123">Popisuje, jak pomocí inteligentních značek ovládacího prvku zabránit uživatelům v přidávání nebo odstraňování řádků.</span><span class="sxs-lookup"><span data-stu-id="9305e-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="9305e-124">Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="9305e-125">Popisuje postup použití **objektu CellStyle** dialogové okno Vytvořit vzhled účetní knihy v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="9305e-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="9305e-126">Postupy: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9305e-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/default-cell-styles-datagridview.md)  
 <span data-ttu-id="9305e-127">Popisuje postup použití **objektu CellStyle** dialogové okno nastavit základní vzhled a zobrazení datových formátů pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="9305e-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9305e-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="9305e-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="9305e-129">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9305e-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9305e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="9305e-130">See Also</span></span>  
 [<span data-ttu-id="9305e-131">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="9305e-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
