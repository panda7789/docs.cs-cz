---
title: "Postupy: Přidání ovládacího prvku do stránky karty pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: 7ee734e1-e31e-4ed0-bbc0-a7e8a1f20fef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30c8a73d23a1a0d27f049c09752d76dd7d2d6ef2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-a-control-to-a-tab-page-using-the-designer"></a><span data-ttu-id="9cdc1-102">Postupy: Přidání ovládacího prvku do stránky karty pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9cdc1-102">How to: Add a Control to a Tab Page Using the Designer</span></span>
<span data-ttu-id="9cdc1-103">Použití modelu Windows Forms <xref:System.Windows.Forms.TabControl> je zobrazíte další ovládací prvky způsobem uspořádány.</span><span class="sxs-lookup"><span data-stu-id="9cdc1-103">The use of the Windows Forms <xref:System.Windows.Forms.TabControl> is to display other controls in an organized fashion.</span></span> <span data-ttu-id="9cdc1-104">Tyto pokyny slouží k zobrazení obrázku na hlavní část stránky karty.</span><span class="sxs-lookup"><span data-stu-id="9cdc1-104">You can use these instructions to display a picture on the main part of a tab page.</span></span> <span data-ttu-id="9cdc1-105">Informace o přidávání ikonu na popisek část stránky karty najdete v tématu [postupy: Změna vzhledu Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span><span class="sxs-lookup"><span data-stu-id="9cdc1-105">For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
 <span data-ttu-id="9cdc1-106">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.TabControl> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9cdc1-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="9cdc1-107">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9cdc1-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cdc1-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="9cdc1-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9cdc1-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="9cdc1-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9cdc1-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="9cdc1-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-control-using-the-designer"></a><span data-ttu-id="9cdc1-111">Přidání ovládacího prvku pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="9cdc1-111">To add a control using the designer</span></span>  
  
1.  <span data-ttu-id="9cdc1-112">Klikněte na příslušnou kartu stránky tak, aby se v horní části.</span><span class="sxs-lookup"><span data-stu-id="9cdc1-112">Click the appropriate tab page so that it appears on top.</span></span>  
  
2.  <span data-ttu-id="9cdc1-113">Vykreslení ovládacího prvku na kartě stránky.</span><span class="sxs-lookup"><span data-stu-id="9cdc1-113">Draw the control on the tab page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdc1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cdc1-114">See Also</span></span>  
 [<span data-ttu-id="9cdc1-115">Ovládací prvek TabControl</span><span class="sxs-lookup"><span data-stu-id="9cdc1-115">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="9cdc1-116">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="9cdc1-116">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="9cdc1-117">Postupy: Změna vzhledu Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="9cdc1-117">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="9cdc1-118">Postupy: Zákaz karet</span><span class="sxs-lookup"><span data-stu-id="9cdc1-118">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="9cdc1-119">Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="9cdc1-119">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
