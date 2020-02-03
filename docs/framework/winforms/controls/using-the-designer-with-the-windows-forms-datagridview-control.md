---
title: Použití návrháře s ovládacím prvkem DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
ms.openlocfilehash: 50e8bddb97c2dfb84cebdbb2ca4d42a6c5743304
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728364"
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="f5b79-102">Používání Návrháře s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f5b79-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f5b79-103">Visual Studio poskytuje podporu návrháře pro ovládací prvek `DataGridView`, který umožňuje provádět mnoho úloh nastavení bez psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="f5b79-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="f5b79-104">Tyto úlohy zahrnují vazbu ovládacího prvku na zdroj dat, úpravu sloupců používaných k zobrazení dat a úpravu vzhledu a základního chování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f5b79-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5b79-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f5b79-105">In This Section</span></span>  
 [<span data-ttu-id="f5b79-106">Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="f5b79-107">Popisuje, jak použít dialogová okna **Přidat sloupce** a **Upravit sloupce** k naplnění a úpravě kolekce sloupců.</span><span class="sxs-lookup"><span data-stu-id="f5b79-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="f5b79-108">Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="f5b79-109">Popisuje způsob použití možnosti **Zvolit zdroj dat** na inteligentní značce ovládacího prvku pro připojení k datům.</span><span class="sxs-lookup"><span data-stu-id="f5b79-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="f5b79-110">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="f5b79-111">Popisuje, jak změnit uspořádání sloupců pomocí dialogového okna **Upravit sloupce** .</span><span class="sxs-lookup"><span data-stu-id="f5b79-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="f5b79-112">Postupy: Změna typu sloupce Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="f5b79-113">Popisuje, jak použít dialogové okno **Upravit sloupce** pro změnu typu sloupce.</span><span class="sxs-lookup"><span data-stu-id="f5b79-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="f5b79-114">Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="f5b79-115">Popisuje, jak používat inteligentní značku ovládacího prvku k tomu, aby uživatelé mohli změnit uspořádání sloupců.</span><span class="sxs-lookup"><span data-stu-id="f5b79-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="f5b79-116">Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="f5b79-117">Popisuje, jak pomocí dialogového okna **Upravit sloupce** zabránit posouvání konkrétních sloupců.</span><span class="sxs-lookup"><span data-stu-id="f5b79-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="f5b79-118">Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="f5b79-119">Popisuje, jak použít dialogové okno **Upravit sloupce** pro skrytí určitých sloupců.</span><span class="sxs-lookup"><span data-stu-id="f5b79-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="f5b79-120">Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="f5b79-121">Popisuje, jak používat dialogové okno **Upravit sloupce** k tomu, aby uživatelé nemohli upravovat hodnoty v konkrétních sloupcích.</span><span class="sxs-lookup"><span data-stu-id="f5b79-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="f5b79-122">Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="f5b79-123">Popisuje, jak používat inteligentní značku ovládacího prvku k zabránění uživatelům v přidávání a odstraňování řádků.</span><span class="sxs-lookup"><span data-stu-id="f5b79-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="f5b79-124">Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="f5b79-125">Popisuje, jak pomocí dialogového okna **Tvůrce CellStyle** vytvořit vzhled v rámci ovládacího prvku v podobě knihy.</span><span class="sxs-lookup"><span data-stu-id="f5b79-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="f5b79-126">Postupy: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f5b79-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](default-cell-styles-datagridview.md)  
 <span data-ttu-id="f5b79-127">Popisuje, jak použít dialogové okno **Tvůrce CellStyle** k nastavení základního vzhledu a formátů zobrazení dat pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f5b79-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f5b79-128">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="f5b79-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="f5b79-129">Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f5b79-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b79-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5b79-130">See also</span></span>

- [<span data-ttu-id="f5b79-131">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="f5b79-131">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
