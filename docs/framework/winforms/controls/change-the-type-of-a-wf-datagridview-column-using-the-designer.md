---
title: 'Postupy: Změna typu sloupce Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: b5d395575ac486307625fbdf2f236b6a588cc3ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527012"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="f993d-102">Postupy: Změna typu sloupce Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f993d-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="f993d-103">Někdy budete chtít změnit typ sloupce, který již byl přidán do Windows Forms <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f993d-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f993d-104">Můžete například změnit některé sloupce, které se generují automaticky po vytvoření vazby ovládacího prvku ke zdroji dat typy.</span><span class="sxs-lookup"><span data-stu-id="f993d-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="f993d-105">To je užitečné, když má sloupců obsahujících cizí klíče na řádky v tabulce související tabulky, které můžete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="f993d-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="f993d-106">V takovém případě můžete nahradit sloupce textové pole, které zobrazují tyto cizí klíče s sloupce pole se seznamem, které zobrazují smysluplnější hodnoty z související tabulky.</span><span class="sxs-lookup"><span data-stu-id="f993d-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>  
  
 <span data-ttu-id="f993d-107">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f993d-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f993d-108">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f993d-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f993d-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="f993d-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f993d-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f993d-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f993d-111">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f993d-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="f993d-112">Změna typu sloupce pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="f993d-112">To change the type of a column using the designer</span></span>  
  
1.  <span data-ttu-id="f993d-113">Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> řízení a potom vyberte **upravit sloupce**.</span><span class="sxs-lookup"><span data-stu-id="f993d-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="f993d-114">Vyberte sloupce z **vybrané sloupce** seznamu.</span><span class="sxs-lookup"><span data-stu-id="f993d-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="f993d-115">V **vlastnosti sloupce** mřížky, nastavte `ColumnType` vlastnost na nový typ sloupce.</span><span class="sxs-lookup"><span data-stu-id="f993d-115">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f993d-116">`ColumnType` Je pouze pro návrh vlastnost, která určuje Třída reprezentující typ sloupce.</span><span class="sxs-lookup"><span data-stu-id="f993d-116">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="f993d-117">Nejedná se o skutečný vlastnost definovaný ve třídě sloupec.</span><span class="sxs-lookup"><span data-stu-id="f993d-117">It is not an actual property defined in a column class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f993d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f993d-118">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [<span data-ttu-id="f993d-119">Postupy: vytvoření projektu aplikace Windows</span><span class="sxs-lookup"><span data-stu-id="f993d-119">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="f993d-120">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f993d-120">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
