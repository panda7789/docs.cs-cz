---
title: 'Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 5d9c978f69b2dcfd91c1af6e80391852ed69da12
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466845"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="d0acb-102">Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="d0acb-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="d0acb-103">Ve výchozím nastavení, mohou uživatelé upravovat textu a číselných dat zobrazovat ve formuláři Windows <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0acb-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d0acb-104">Pokud chcete zobrazit data, která není určená pro úpravy, musíte udělat sloupce, které obsahují data jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="d0acb-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="d0acb-105">Informace o tom, jak nastavit ovládací prvek zcela jen pro čtení najdete v tématu [postupy: zabránění přidávání řádků a odstraňování v prvku DataGridView formuláře Windows ovládacího prvku pomocí návrháře](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="d0acb-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
 <span data-ttu-id="d0acb-106">Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d0acb-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d0acb-107">Informace o nastavení takový projekt, naleznete v tématu [postupy: vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d0acb-107">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0acb-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="d0acb-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d0acb-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="d0acb-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d0acb-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d0acb-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="d0acb-111">Chcete-li sloupec jen pro čtení pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="d0acb-111">To make a column read-only by using the designer</span></span>  
  
1.  <span data-ttu-id="d0acb-112">Klikněte na inteligentní označit piktogram (![piktogram inteligentní](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> ovládací prvek a potom vyberte **upravit sloupce**.</span><span class="sxs-lookup"><span data-stu-id="d0acb-112">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="d0acb-113">Vyberte sloupec **vybrané sloupce** seznamu.</span><span class="sxs-lookup"><span data-stu-id="d0acb-113">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="d0acb-114">V **vlastnosti sloupce** mřížky, nastavte <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="d0acb-114">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d0acb-115">Můžete provést také sloupec jen pro čtení při přidání tak, že vyberete **jen pro čtení** zaškrtávací políčko **přidat sloupec** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="d0acb-115">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0acb-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0acb-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d0acb-117">Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="d0acb-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="d0acb-118">Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="d0acb-118">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="d0acb-119">Postupy: vytvoření projektu aplikace Windows</span><span class="sxs-lookup"><span data-stu-id="d0acb-119">How to: Create a Windows Application Project</span></span>](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="d0acb-120">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0acb-120">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
