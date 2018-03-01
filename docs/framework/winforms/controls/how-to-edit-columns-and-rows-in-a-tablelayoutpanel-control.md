---
title: "Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bf54a02a409bead598a4e98315d5709e55677f3b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="76208-102">Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="76208-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>
<span data-ttu-id="76208-103">Můžete použít editor kolekce z <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku, s názvem **styly řádku a sloupce** dialogové okno, chcete-li upravit řádků a sloupců pro vaše ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="76208-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76208-104">Pokud chcete ovládacího prvku na více řádcích nebo sloupců, nastavte `RowSpan` a `ColumnSpan` vlastnosti na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="76208-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="76208-105">Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="76208-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="76208-106">Pokud chcete zarovnání ovládacího prvku v buňce nebo pokud chcete roztáhnout buňce ovládacího prvku, pomocí ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="76208-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="76208-107">Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="76208-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="76208-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="76208-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="76208-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="76208-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="76208-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="76208-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-edit-rows-and-columns"></a><span data-ttu-id="76208-111">Chcete-li upravit řádků a sloupců</span><span class="sxs-lookup"><span data-stu-id="76208-111">To edit rows and columns</span></span>  
  
1.  <span data-ttu-id="76208-112">Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="76208-112">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="76208-113">Klikněte na tlačítko <xref:System.Windows.Forms.TableLayoutPanel> glyfy inteligentní značky ovládacího prvku (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a vyberte **úpravy řádků a sloupců** otevřete  **Styly řádku a sloupce** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="76208-113">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="76208-114">Vám může také klikněte pravým tlačítkem na <xref:System.Windows.Forms.TableLayoutPanel> řízení a vyberte **úpravy řádků a sloupců** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="76208-114">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="76208-115">Chcete-li přidat nebo odebrat sloupce, vyberte **sloupce** z **typ člena** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="76208-115">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>  
  
4.  <span data-ttu-id="76208-116">Chcete-li přidat nebo odebrat řádky, vyberte **řádky** z **typ člena** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="76208-116">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>  
  
5.  <span data-ttu-id="76208-117">Klikněte na tlačítko **přidat** tlačítko Přidat sloupce či řádku na konec **člen** seznamu.</span><span class="sxs-lookup"><span data-stu-id="76208-117">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>  
  
6.  <span data-ttu-id="76208-118">Klikněte **vložit** tlačítko Přidat řádku nebo sloupce před aktuálně vybrané položky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="76208-118">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>  
  
7.  <span data-ttu-id="76208-119">Pokud přidáváte sloupce či řádku, vyberte **typ velikosti** pro nový řádek nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="76208-119">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="76208-120">Další informace naleznete v tématu <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="76208-120">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>  
  
8.  <span data-ttu-id="76208-121">Chcete-li odebrat sloupce či řádku, klikněte na tlačítko **odebrat** tlačítko Odstranit aktuálně vybrané položky v **člen** seznamu.</span><span class="sxs-lookup"><span data-stu-id="76208-121">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76208-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="76208-122">See Also</span></span>  
 <xref:System.Windows.Forms.SizeType>  
 [<span data-ttu-id="76208-123">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="76208-123">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
