---
title: "Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 029eb160545164535b8b5ae058cdc7ad85d69ab9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="67ec5-102">Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="67ec5-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="67ec5-103">Někdy budete chtít zabránit uživatelům ve zadáním nové řádky dat nebo odstranění existující řádků ve vaší <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="67ec5-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="67ec5-104">Nové řádky jsou zadány v speciální řádku pro nové záznamy v dolní části ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="67ec5-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="67ec5-105">Když zakážete přidání řádku, řádku pro nové záznamy se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="67ec5-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="67ec5-106">Poté provedete ovládacího prvku zcela jen pro čtení zakázáním odstranění řádku a buňky úpravy.</span><span class="sxs-lookup"><span data-stu-id="67ec5-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>  
  
 <span data-ttu-id="67ec5-107">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="67ec5-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="67ec5-108">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="67ec5-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67ec5-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="67ec5-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="67ec5-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="67ec5-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="67ec5-111">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="67ec5-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="67ec5-112">Aby se zabránilo řádek přidání a odstranění.</span><span class="sxs-lookup"><span data-stu-id="67ec5-112">To prevent row addition and deletion</span></span>  
  
-   <span data-ttu-id="67ec5-113">Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> řízení a zrušte zaškrtnutí políčka **povolit přidání** a **Povolit odstraňování** zaškrtávací políčka.</span><span class="sxs-lookup"><span data-stu-id="67ec5-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="67ec5-114">Chcete-li ovládací prvek zcela jen pro čtení, zrušte **povolit úpravy** také políčko.</span><span class="sxs-lookup"><span data-stu-id="67ec5-114">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ec5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="67ec5-115">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="67ec5-116">Postupy: vytvoření projektu aplikace Windows</span><span class="sxs-lookup"><span data-stu-id="67ec5-116">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="67ec5-117">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ec5-117">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
