---
title: 'Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 6bdd561c863a461f43a5a7aac025fead1f971bb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039807"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="85561-102">Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="85561-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="85561-103">Ve výchozím nastavení mohou uživatelé upravovat text a číselná data zobrazená v ovládacím <xref:System.Windows.Forms.DataGridView> prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="85561-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="85561-104">Chcete-li zobrazit data, která nejsou určena k úpravám, je nutné vytvořit sloupce, které obsahují data jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="85561-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="85561-105">Informace o tom, jak nastavit ovládací prvek jen pro čtení, najdete v [tématu How to: Zabraňte přidávání a odstraňování řádků v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="85561-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="85561-106">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="85561-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="85561-107">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="85561-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="85561-108">Zpřístupnění sloupce jen pro čtení pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="85561-108">To make a column read-only by using the designer</span></span>

1. <span data-ttu-id="85561-109">V pravém <xref:System.Windows.Forms.DataGridView> horním rohu ovládacího prvku klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Upravit sloupce**.</span><span class="sxs-lookup"><span data-stu-id="85561-109">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="85561-110">Vyberte sloupec ze seznamu **vybrané sloupce** .</span><span class="sxs-lookup"><span data-stu-id="85561-110">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="85561-111">V mřížce **vlastnosti sloupce** nastavte <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> vlastnost na `true`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="85561-111">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="85561-112">Sloupec můžete také nastavit jen pro čtení, když ho přidáte výběrem zaškrtávacího políčka jen **pro čtení** v dialogovém okně **Přidat sloupec** .</span><span class="sxs-lookup"><span data-stu-id="85561-112">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="85561-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85561-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="85561-114">Postupy: Přidání a odebrání sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="85561-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="85561-115">Postupy: Zabránit přidávání a odstraňování řádků v ovládacím prvku DataGridView model Windows Forms pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="85561-115">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="85561-116">Postupy: Vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="85561-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="85561-117">Postupy: Přidat ovládací prvky do model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="85561-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
