---
title: "Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71b02124dd68299552737df35163e3b766d4df73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="7f489-102">Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="7f489-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="7f489-103">Windows Forms <xref:System.Windows.Forms.DataGridView> řízení musí obsahovat sloupce, aby bylo možné zobrazit data.</span><span class="sxs-lookup"><span data-stu-id="7f489-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="7f489-104">Pokud budete chtít naplnit ovládací prvek ručně, musíte přidat sloupce sami.</span><span class="sxs-lookup"><span data-stu-id="7f489-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="7f489-105">Alternativně můžete vázat ovládacího prvku na zdroj dat, který generuje a automaticky naplní sloupce.</span><span class="sxs-lookup"><span data-stu-id="7f489-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="7f489-106">Pokud zdroj dat obsahuje více sloupců, než se má zobrazit, můžete odebrat nežádoucí sloupce.</span><span class="sxs-lookup"><span data-stu-id="7f489-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>  
  
 <span data-ttu-id="7f489-107">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7f489-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7f489-108">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7f489-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f489-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="7f489-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7f489-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="7f489-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7f489-111">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="7f489-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="7f489-112">Chcete-li přidat sloupec pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="7f489-112">To add a column using the designer</span></span>  
  
1.  <span data-ttu-id="7f489-113">Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> řízení a potom vyberte **přidat sloupec**.</span><span class="sxs-lookup"><span data-stu-id="7f489-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>  
  
2.  <span data-ttu-id="7f489-114">V **přidat sloupec** dialogovém okně vyberte **Vycentrovat sloupec** možnost a vyberte sloupec ze zdroje dat nebo zvolte **nepřipojeného sloupce** možnost a definovat sloupce použití polí zadat.</span><span class="sxs-lookup"><span data-stu-id="7f489-114">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>  
  
3.  <span data-ttu-id="7f489-115">Klikněte **přidat** tlačítko Přidat sloupec, způsobuje se zobrazí v návrháři, pokud existující sloupce již nevyplní oblasti zobrazení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7f489-115">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7f489-116">Můžete upravit vlastnosti sloupce v **upravit sloupce** dialogové okno, které je dostupné z inteligentní značky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7f489-116">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>  
  
### <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="7f489-117">Pokud chcete odebrat sloupec pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="7f489-117">To remove a column using the designer</span></span>  
  
1.  <span data-ttu-id="7f489-118">Zvolte **upravit sloupce** z inteligentní značky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7f489-118">Choose **Edit Columns** from the control's smart tag.</span></span>  
  
2.  <span data-ttu-id="7f489-119">Vyberte sloupce z **vybrané sloupce** seznamu.</span><span class="sxs-lookup"><span data-stu-id="7f489-119">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="7f489-120">Klikněte **odebrat** tlačítko odstranění sloupce, způsobuje její zmizí z návrháře.</span><span class="sxs-lookup"><span data-stu-id="7f489-120">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f489-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f489-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="7f489-122">Postupy: vytvoření projektu aplikace Windows</span><span class="sxs-lookup"><span data-stu-id="7f489-122">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="7f489-123">Postupy: Přidání ovládacích prvků do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="7f489-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
