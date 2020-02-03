---
title: Určení režimu úprav pro ovládací prvek DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743761"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="bb363-102">Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="bb363-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bb363-103">Ve výchozím nastavení mohou uživatelé upravovat obsah aktuální <xref:System.Windows.Forms.DataGridView> buňky textového pole, a to tak, že je zapíšete nebo stisknete F2.</span><span class="sxs-lookup"><span data-stu-id="bb363-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="bb363-104">Tato akce převede buňku do režimu úprav, pokud jsou splněné všechny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="bb363-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
- <span data-ttu-id="bb363-105">Podkladový zdroj dat podporuje úpravy.</span><span class="sxs-lookup"><span data-stu-id="bb363-105">The underlying data source supports editing.</span></span>  
  
- <span data-ttu-id="bb363-106">Ovládací prvek <xref:System.Windows.Forms.DataGridView> je povolený.</span><span class="sxs-lookup"><span data-stu-id="bb363-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
- <span data-ttu-id="bb363-107">Hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.EditMode%2A> není <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="bb363-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
- <span data-ttu-id="bb363-108">Vlastnosti `ReadOnly` buňky, řádku, sloupce a ovládacího prvku jsou nastaveny na `false`.</span><span class="sxs-lookup"><span data-stu-id="bb363-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="bb363-109">V režimu úprav může uživatel změnit hodnotu buňky a stisknutím klávesy ENTER Potvrdit změnu nebo klávesu ESC obnovit původní hodnotu buňky.</span><span class="sxs-lookup"><span data-stu-id="bb363-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="bb363-110">Můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> ovládací prvek tak, aby buňka vstoupila do režimu úprav, jakmile se stane aktuální buňkou.</span><span class="sxs-lookup"><span data-stu-id="bb363-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="bb363-111">Chování kláves ENTER a ESC není v tomto případě změněno, ale buňka zůstane v režimu úprav poté, co je hodnota potvrzena nebo vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="bb363-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="bb363-112">Můžete také nakonfigurovat ovládací prvek tak, aby buňky jako režim úprav byly zadány pouze v případě, že uživatel zadá tuto buňku, nebo pouze když uživatel stiskne klávesu F2.</span><span class="sxs-lookup"><span data-stu-id="bb363-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="bb363-113">Nakonec můžete zabránit tomu, aby buňky vstoupily do režimu úprav s výjimkou případů, kdy zavoláte metodu <xref:System.Windows.Forms.DataGridView.BeginEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb363-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="bb363-114">Změna režimu úprav ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="bb363-114">To change the edit mode of a DataGridView control</span></span>  
  
- <span data-ttu-id="bb363-115">Vlastnost <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> nastavte na příslušný výčet <xref:System.Windows.Forms.DataGridViewEditMode>.</span><span class="sxs-lookup"><span data-stu-id="bb363-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb363-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bb363-116">Compiling the Code</span></span>  
 <span data-ttu-id="bb363-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="bb363-117">This example requires:</span></span>  
  
- <span data-ttu-id="bb363-118"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="bb363-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="bb363-119">Odkazy na <xref:System> a <xref:System.Windows.Forms> sestavení.</span><span class="sxs-lookup"><span data-stu-id="bb363-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb363-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb363-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bb363-121">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="bb363-121">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
