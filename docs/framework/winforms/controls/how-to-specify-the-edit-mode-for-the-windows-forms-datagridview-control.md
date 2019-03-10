---
title: 'Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 00c5bb85eb1b238371e58a631d90b69a41c49140
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725299"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="bf44b-102">Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="bf44b-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bf44b-103">Ve výchozím nastavení, uživatelé mohou upravovat obsah aktuální <xref:System.Windows.Forms.DataGridView> buňka s textem pole zadáním v ní nebo stisknutím klávesy F2.</span><span class="sxs-lookup"><span data-stu-id="bf44b-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="bf44b-104">To umístí buňku v režimu úprav Pokud jsou splněny všechny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="bf44b-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="bf44b-105">Podkladový zdroj dat podporuje úpravy.</span><span class="sxs-lookup"><span data-stu-id="bf44b-105">The underlying data source supports editing.</span></span>  
  
-   <span data-ttu-id="bf44b-106"><xref:System.Windows.Forms.DataGridView> Je ovládací prvek povolený.</span><span class="sxs-lookup"><span data-stu-id="bf44b-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
-   <span data-ttu-id="bf44b-107"><xref:System.Windows.Forms.DataGridView.EditMode%2A> Hodnota vlastnosti není <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span><span class="sxs-lookup"><span data-stu-id="bf44b-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
-   <span data-ttu-id="bf44b-108">`ReadOnly` Vlastnosti buněk, řádků, sloupců a ovládacího prvku jsou nastaveny na `false`.</span><span class="sxs-lookup"><span data-stu-id="bf44b-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="bf44b-109">Uživatel v režimu úprav, můžete změnit hodnotu buňky a stisknutím ENTERU Potvrdit změnu nebo klávesou ESC Operaci vrátit na původní hodnotu buňky.</span><span class="sxs-lookup"><span data-stu-id="bf44b-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="bf44b-110">Můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> tak, aby buňky přejde do režimu úprav co nejdříve bude aktuální buňky.</span><span class="sxs-lookup"><span data-stu-id="bf44b-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="bf44b-111">V tomto případě je beze změny chování klávesy ENTER a ESC, ale zůstane buňku v režimu úprav po hodnotu potvrzené nebo vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="bf44b-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="bf44b-112">Ovládací prvek můžete také nakonfigurovat tak, aby pouze v případě, že uživatelé budou psát v buňce nebo pouze pokud uživatelé stisknutím klávesy F2 přejděte buňky vstoupit do režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="bf44b-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="bf44b-113">Nakonec můžete zabránit buňky přechod do režimu úprav, s výjimkou při volání <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bf44b-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="bf44b-114">Chcete-li změnit režim úprav ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="bf44b-114">To change the edit mode of a DataGridView control</span></span>  
  
-   <span data-ttu-id="bf44b-115">Nastavte <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> vlastnosti na příslušné <xref:System.Windows.Forms.DataGridViewEditMode> výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf44b-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bf44b-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bf44b-116">Compiling the Code</span></span>  
 <span data-ttu-id="bf44b-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="bf44b-117">This example requires:</span></span>  
  
-   <span data-ttu-id="bf44b-118">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="bf44b-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="bf44b-119">Odkazy <xref:System> a <xref:System.Windows.Forms> sestavení.</span><span class="sxs-lookup"><span data-stu-id="bf44b-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf44b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf44b-120">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bf44b-121">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="bf44b-121">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
