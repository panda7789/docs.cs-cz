---
title: 'Postupy: Úpravy sloupců a řádků v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 2149cac7fb15052c2602ef20a6684696730aae1b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59294461"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="9863f-102">Postupy: Úpravy sloupců a řádků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="9863f-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>
<span data-ttu-id="9863f-103">Můžete použít editor kolekce <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku, volá se **styly sloupců a řádků** dialogovém okně Upravit řádky a sloupce ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="9863f-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9863f-104">Pokud chcete ovládací prvek na více řádcích nebo sloupcích, nastavte `RowSpan` a `ColumnSpan` vlastnosti na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="9863f-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="9863f-105">Další informace najdete v tématu [názorný postup: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="9863f-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="9863f-106">Pokud chcete ovládací prvek v rámci buňky zarovnat nebo pokud chcete roztáhnout v rámci buňky, pomocí ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9863f-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="9863f-107">Další informace najdete v tématu [názorný postup: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="9863f-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="9863f-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="9863f-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9863f-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="9863f-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9863f-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="9863f-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-edit-rows-and-columns"></a><span data-ttu-id="9863f-111">Chcete-li upravit řádky a sloupce</span><span class="sxs-lookup"><span data-stu-id="9863f-111">To edit rows and columns</span></span>  
  
1. <span data-ttu-id="9863f-112">Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="9863f-112">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2. <span data-ttu-id="9863f-113">Klikněte na tlačítko <xref:System.Windows.Forms.TableLayoutPanel> piktogram inteligentní značky ovládacího prvku (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a vyberte **upravit řádky a sloupce** otevřít  **Styly sloupců a řádků** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="9863f-113">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="9863f-114">Můžete také pravým tlačítkem myši kliknete na <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek a vyberte **upravit řádky a sloupce** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="9863f-114">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>  
  
3. <span data-ttu-id="9863f-115">Chcete-li přidat nebo odebrat sloupce, vyberte **sloupce** z **typ člena** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="9863f-115">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>  
  
4. <span data-ttu-id="9863f-116">Chcete-li přidat nebo odebrat řádky, vyberte **řádky** z **typ člena** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="9863f-116">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>  
  
5. <span data-ttu-id="9863f-117">Klikněte na tlačítko **přidat** a přidejte na konec řádku nebo sloupce **člen** seznamu.</span><span class="sxs-lookup"><span data-stu-id="9863f-117">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>  
  
6. <span data-ttu-id="9863f-118">Klikněte na tlačítko **vložit** tlačítko pro přidání řádku nebo sloupce před aktuálně vybrané položky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="9863f-118">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>  
  
7. <span data-ttu-id="9863f-119">Pokud přidáváte řádku nebo sloupce, vyberte **typ velikosti** pro nový řádek nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="9863f-119">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="9863f-120">Další informace naleznete v tématu <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="9863f-120">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>  
  
8. <span data-ttu-id="9863f-121">K odebrání řádku nebo sloupce, klikněte na tlačítko **odebrat** tlačítko Odstranit aktuálně vybrané položky v **člen** seznamu.</span><span class="sxs-lookup"><span data-stu-id="9863f-121">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9863f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9863f-122">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="9863f-123">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="9863f-123">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
