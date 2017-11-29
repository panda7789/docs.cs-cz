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
ms.openlocfilehash: b29904954a593607a7872c0b59265bbf241dce98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="5c961-102">Používání Návrháře s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5c961-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5c961-103">Visual Studio poskytuje návrháře podpora `DataGridView` ovládací prvek, který umožňuje provádět mnoho úloh nastavení bez nutnosti psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="5c961-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="5c961-104">Tyto úlohy patří vazbu ovládacího prvku ke zdroji dat, úprava sloupce, které slouží k zobrazení dat a úpravě vzhled a chování základní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5c961-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c961-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5c961-105">In This Section</span></span>  
 [<span data-ttu-id="5c961-106">Postupy: přidávání a odebírání sloupců v systému Windows Forms DataGridView – ovládací prvek pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5c961-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="5c961-107">Popisuje postup použití **přidat sloupce** a **upravit sloupce** dialogových oken k naplnění a upravit kolekci sloupců.</span><span class="sxs-lookup"><span data-stu-id="5c961-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="5c961-108">Postupy: vytvoření vazby dat do ovládacího prvku Windows Forms DataGridView – ovládací prvek pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5c961-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="5c961-109">Popisuje postup použití **zvolit zdroj dat** možnost na inteligentní značky ovládacího prvku pro připojení k datům.</span><span class="sxs-lookup"><span data-stu-id="5c961-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="5c961-110">Postupy: Změna pořadí sloupců v prvku Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5c961-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="5c961-111">Popisuje postup použití **upravit sloupce** dialogové okno ke změně uspořádání sloupců.</span><span class="sxs-lookup"><span data-stu-id="5c961-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="5c961-112">Postupy: Změna typu sloupce Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5c961-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="5c961-113">Popisuje postup použití **upravit sloupce** dialogové okno Změnit typy sloupců.</span><span class="sxs-lookup"><span data-stu-id="5c961-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="5c961-114">Postupy: povolení změny pořadí sloupců v prvku Windows Forms DataGridView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5c961-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="5c961-115">Popisuje, jak používat inteligentní značky ovládacího prvku k umožnění uživatelům Změna uspořádání sloupců.</span><span class="sxs-lookup"><span data-stu-id="5c961-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="5c961-116">Postupy: zablokování sloupců v systému Windows Forms DataGridView – ovládací prvek pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5c961-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="5c961-117">Popisuje postup použití **upravit sloupce** dialogové okno zabránit posouvání určité sloupce.</span><span class="sxs-lookup"><span data-stu-id="5c961-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="5c961-118">Postupy: skrytí sloupců v systému Windows Forms DataGridView – ovládací prvek pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5c961-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="5c961-119">Popisuje postup použití **upravit sloupce** dialogové okno ke skrytí určité sloupce.</span><span class="sxs-lookup"><span data-stu-id="5c961-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="5c961-120">Postupy: přepnutí sloupců jen pro čtení v systému Windows Forms DataGridView – ovládací prvek pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5c961-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="5c961-121">Popisuje postup použití **upravit sloupce** dialogové okno uživatelům zabránit v úpravách hodnoty v určité sloupce.</span><span class="sxs-lookup"><span data-stu-id="5c961-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="5c961-122">Postupy: zabránění řádek přidání a odstranění ve Windows Forms DataGridView – ovládací prvek pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5c961-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="5c961-123">Popisuje, jak pomocí inteligentních značek ovládacího prvku zabránit uživatelům v přidávání nebo odstraňování řádků.</span><span class="sxs-lookup"><span data-stu-id="5c961-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="5c961-124">Postupy: nastavení střídavých stylů řádků pro Windows Forms DataGridView – ovládací prvek pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="5c961-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="5c961-125">Popisuje postup použití **objektu CellStyle** dialogové okno Vytvořit vzhled účetní knihy v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="5c961-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="5c961-126">Postupy: nastavení výchozích stylů buňky a datových formátů pro ovládací prvek DataGridView pomocí návrháře Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c961-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/default-cell-styles-datagridview.md)  
 <span data-ttu-id="5c961-127">Popisuje postup použití **objektu CellStyle** dialogové okno nastavit základní vzhled a zobrazení datových formátů pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5c961-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5c961-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="5c961-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="5c961-129">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5c961-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c961-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c961-130">See Also</span></span>  
 [<span data-ttu-id="5c961-131">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="5c961-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
