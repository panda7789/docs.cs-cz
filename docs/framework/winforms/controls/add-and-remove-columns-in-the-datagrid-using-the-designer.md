---
title: 'Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 99fe1b8ffb7ccc2a5bef13ea8fef6ace5d5bdfdc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452804"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="50145-102">Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="50145-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="50145-103">Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek musí obsahovat sloupce, pokud chcete zobrazit data.</span><span class="sxs-lookup"><span data-stu-id="50145-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="50145-104">Pokud budete chtít ručně naplnění ovládacího prvku, je nutné přidat sloupce sami.</span><span class="sxs-lookup"><span data-stu-id="50145-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="50145-105">Případně lze vazbu ovládacího prvku ke zdroji dat, která vytvoří a naplní sloupce automaticky.</span><span class="sxs-lookup"><span data-stu-id="50145-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="50145-106">Pokud zdroj dat obsahuje více sloupců, než které chcete zobrazit, můžete odebrat nežádoucí sloupce.</span><span class="sxs-lookup"><span data-stu-id="50145-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>  
  
 <span data-ttu-id="50145-107">Následující postup vyžaduje **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50145-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="50145-108">Informace o nastavení takový projekt, naleznete v tématu [postupy: vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="50145-108">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50145-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="50145-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="50145-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="50145-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="50145-111">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="50145-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="50145-112">Chcete-li přidat sloupec pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="50145-112">To add a column using the designer</span></span>  
  
1.  <span data-ttu-id="50145-113">Klikněte na inteligentní označit piktogram (![piktogram inteligentní](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> ovládací prvek a potom vyberte **přidat sloupec**.</span><span class="sxs-lookup"><span data-stu-id="50145-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>  
  
2.  <span data-ttu-id="50145-114">V **přidat sloupec** dialogového okna zvolte **sloupec datové vazby** možnost a vyberte sloupec ze zdroje dat nebo zvolte **nepřipojeného sloupce** možnost a definovat sloupec pomocí do příslušných polí.</span><span class="sxs-lookup"><span data-stu-id="50145-114">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>  
  
3.  <span data-ttu-id="50145-115">Klikněte na tlačítko **přidat** tlačítko Přidat sloupec by ji zobrazit v návrháři, pokud existující sloupce již nevyplní oblasti ovládacího prvku zobrazení.</span><span class="sxs-lookup"><span data-stu-id="50145-115">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50145-116">Můžete upravit vlastnosti sloupce v **upravit sloupce** dialogové okno, které se dá dostat z ovládacího prvku inteligentních značek.</span><span class="sxs-lookup"><span data-stu-id="50145-116">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>  
  
### <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="50145-117">Chcete-li odebrat sloupce pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="50145-117">To remove a column using the designer</span></span>  
  
1.  <span data-ttu-id="50145-118">Zvolte **upravit sloupce** z ovládacího prvku inteligentních značek.</span><span class="sxs-lookup"><span data-stu-id="50145-118">Choose **Edit Columns** from the control's smart tag.</span></span>  
  
2.  <span data-ttu-id="50145-119">Vyberte sloupec **vybrané sloupce** seznamu.</span><span class="sxs-lookup"><span data-stu-id="50145-119">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="50145-120">Klikněte na tlačítko **odebrat** tlačítko pro odstranění sloupce by ji zmizí z návrháře.</span><span class="sxs-lookup"><span data-stu-id="50145-120">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50145-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="50145-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="50145-122">Postupy: vytvoření projektu aplikace Windows</span><span class="sxs-lookup"><span data-stu-id="50145-122">How to: Create a Windows Application Project</span></span>](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="50145-123">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50145-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
