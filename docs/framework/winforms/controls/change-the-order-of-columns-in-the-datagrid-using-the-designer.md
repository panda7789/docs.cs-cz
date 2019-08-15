---
title: 'Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: bf77cf3705a470bbe00be383f6a5cb2d28bda34d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039634"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="19d7d-102">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="19d7d-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="19d7d-103">Při navázání ovládacího <xref:System.Windows.Forms.DataGridView> prvku model Windows Forms ke zdroji dat je pořadí zobrazení automaticky generovaných sloupců řízeno zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="19d7d-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="19d7d-104">Pokud toto pořadí nevyhovuje vašim požadavkům, můžete změnit pořadí sloupců pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="19d7d-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="19d7d-105">Do ovládacího prvku můžete také přidat nevázané sloupce a změnit jejich pořadí zobrazení.</span><span class="sxs-lookup"><span data-stu-id="19d7d-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="19d7d-106">Informace o tom, jak změnit pořadí sloupců pomocí kódu programu, [najdete v tématu How to: Změňte pořadí sloupců v ovládacím prvku](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="19d7d-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="19d7d-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="19d7d-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="19d7d-108">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="19d7d-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="19d7d-109">Změna pořadí sloupců pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="19d7d-109">To change the column order using the designer</span></span>

1. <span data-ttu-id="19d7d-110">V pravém <xref:System.Windows.Forms.DataGridView> horním rohu ovládacího prvku klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Upravit sloupce**.</span><span class="sxs-lookup"><span data-stu-id="19d7d-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="19d7d-111">Vyberte sloupec ze seznamu **vybrané sloupce** .</span><span class="sxs-lookup"><span data-stu-id="19d7d-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="19d7d-112">Klikněte na šipku nahoru nebo dolů napravo od seznamu **vybrané sloupce** , dokud není vybraný sloupec v požadované pozici.</span><span class="sxs-lookup"><span data-stu-id="19d7d-112">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="19d7d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19d7d-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="19d7d-114">Postupy: Přidání a odebrání sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="19d7d-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="19d7d-115">Postupy: Vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="19d7d-115">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="19d7d-116">Postupy: Přidat ovládací prvky do model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19d7d-116">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
