---
title: "Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42773e29d7071c5bc5f3d5de3660c9891788b422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="a5ff5-102">Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a5ff5-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a5ff5-103">Ve výchozím nastavení, uživatelé mohou upravovat obsah aktuální <xref:System.Windows.Forms.DataGridView> textového pole buňky zadáním v ní nebo stisknete klávesu F2.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="a5ff5-104">To vloží buňky v režimu úprav Pokud jsou splněny všechny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="a5ff5-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="a5ff5-105">Podkladové zdroje dat, podporuje úpravy.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-105">The underlying data source supports editing.</span></span>  
  
-   <span data-ttu-id="a5ff5-106"><xref:System.Windows.Forms.DataGridView> Řízení je povoleno.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
-   <span data-ttu-id="a5ff5-107"><xref:System.Windows.Forms.DataGridView.EditMode%2A> Hodnota vlastnosti není <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
-   <span data-ttu-id="a5ff5-108">`ReadOnly` Vlastnosti buněk, řádků, sloupce a řízení jsou nastaveny na `false`.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="a5ff5-109">Uživatel v režimu úprav, můžete změnit hodnotu buňky a stiskněte klávesu ENTER k potvrzení změn nebo ESC vrátit zpátky na původní hodnotu buňky.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="a5ff5-110">Můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> řídit tak, aby buňku vstupuje do režimu úprav, jakmile bude aktuální buňky.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="a5ff5-111">V takovém případě se neliší chování ENTER a ESC klíče, ale buňky zůstává v režimu úprav poté, co je hodnota potvrzené nebo vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="a5ff5-112">Ovládací prvek můžete také nakonfigurovat tak, aby pouze v případě, že uživatelé budou psát v buňce nebo pouze když uživatelé stiskněte F2 buněk vstoupit do režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="a5ff5-113">Nakonec můžete zabránit v buňkách přepnutím do režimu úprav kromě při volání <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="a5ff5-114">Chcete-li změnit režimu úprav ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="a5ff5-114">To change the edit mode of a DataGridView control</span></span>  
  
-   <span data-ttu-id="a5ff5-115">Nastavte <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> vlastnost na příslušné <xref:System.Windows.Forms.DataGridViewEditMode> výčtu.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a5ff5-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a5ff5-116">Compiling the Code</span></span>  
 <span data-ttu-id="a5ff5-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a5ff5-117">This example requires:</span></span>  
  
-   <span data-ttu-id="a5ff5-118">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="a5ff5-119">Odkazuje na <xref:System> a <xref:System.Windows.Forms> sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5ff5-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ff5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5ff5-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a5ff5-121">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a5ff5-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
