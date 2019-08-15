---
title: 'Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: d88d658b31c87e7ae89bfb4a11fe794bfbb0e848
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040099"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="543f2-102">Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="543f2-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="543f2-103">Aby bylo <xref:System.Windows.Forms.DataGridView> možné zobrazit data, musí mít ovládací prvek model Windows Forms sloupce.</span><span class="sxs-lookup"><span data-stu-id="543f2-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="543f2-104">Pokud plánujete naplnit ovládací prvek ručně, je nutné přidat sloupce sami.</span><span class="sxs-lookup"><span data-stu-id="543f2-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="543f2-105">Alternativně můžete ovládací prvek navazovat na zdroj dat, který vygeneruje a automaticky naplní sloupce.</span><span class="sxs-lookup"><span data-stu-id="543f2-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="543f2-106">Pokud zdroj dat obsahuje více sloupců, než chcete zobrazit, můžete odstranit nežádoucí sloupce.</span><span class="sxs-lookup"><span data-stu-id="543f2-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>

 <span data-ttu-id="543f2-107">Následující postupy vyžadují projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="543f2-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="543f2-108">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="543f2-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="543f2-109">Přidání sloupce pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="543f2-109">To add a column using the designer</span></span>

1. <span data-ttu-id="543f2-110">V pravém <xref:System.Windows.Forms.DataGridView> horním rohu ovládacího prvku klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Přidat sloupec**.</span><span class="sxs-lookup"><span data-stu-id="543f2-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>

2. <span data-ttu-id="543f2-111">V dialogovém okně **Přidat sloupec** zvolte možnost sloupec s **vazbou** a vyberte sloupec ze zdroje dat, nebo zvolte možnost nevázaný **sloupec** a definujte sloupec pomocí zadaných polí.</span><span class="sxs-lookup"><span data-stu-id="543f2-111">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>

3. <span data-ttu-id="543f2-112">Kliknutím na tlačítko **Přidat** přidejte sloupec, což způsobí, že se zobrazí v návrháři, pokud existující sloupce již neplní oblast zobrazení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="543f2-112">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="543f2-113">Vlastnosti sloupce můžete změnit v dialogovém okně **Upravit sloupce** , ke kterému můžete přistupovat z inteligentní značky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="543f2-113">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>

## <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="543f2-114">Odebrání sloupce pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="543f2-114">To remove a column using the designer</span></span>

1. <span data-ttu-id="543f2-115">Vyberte možnost **Upravit sloupce** z inteligentní značky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="543f2-115">Choose **Edit Columns** from the control's smart tag.</span></span>

2. <span data-ttu-id="543f2-116">Vyberte sloupec ze seznamu **vybrané sloupce** .</span><span class="sxs-lookup"><span data-stu-id="543f2-116">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="543f2-117">Chcete-li odstranit sloupec, klikněte na tlačítko **Odebrat** . tím se z návrháře ztratí.</span><span class="sxs-lookup"><span data-stu-id="543f2-117">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="543f2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="543f2-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="543f2-119">Postupy: Vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="543f2-119">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="543f2-120">Postupy: Přidat ovládací prvky do model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="543f2-120">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
