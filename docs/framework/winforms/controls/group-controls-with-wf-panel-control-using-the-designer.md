---
title: "Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c4582a4bcec1d82651c39be179cbefa2dfc34fa2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="d0e2c-102">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="d0e2c-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="d0e2c-103">Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvky slouží k seskupení další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="d0e2c-104">Existují tři důvodů, proč seskupování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-104">There are three reasons to group controls.</span></span> <span data-ttu-id="d0e2c-105">Jedna je visual seskupování elementů související formuláře pro zrušte uživatelské rozhraní; jiné se programový seskupení, přepínačů například; poslední je přesouvání ovládacích prvků jako jednotku v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0e2c-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d0e2c-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d0e2c-108">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="d0e2c-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="d0e2c-109">Chcete-li vytvořit skupinu ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d0e2c-109">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="d0e2c-110">Přetáhněte <xref:System.Windows.Forms.Panel> řídit z **Windows Forms** kartě nástrojů do formuláře.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2.  <span data-ttu-id="d0e2c-111">Přidáte další ovládací prvky panelu Kreslení každý uvnitř panelu.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="d0e2c-112">Pokud máte stávající ovládací prvky, které chcete uzavřete panelu, můžete vybrat všechny ovládací prvky, je vyjmout data do schránky, vyberte <xref:System.Windows.Forms.Panel> řízení a vložte je do panelu.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="d0e2c-113">Můžete také přetáhněte je do panelu.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-113">You can also drag them into the panel.</span></span>  
  
3.  <span data-ttu-id="d0e2c-114">(Volitelné) Pokud chcete přidat k panelu ohraničení, nastavte jeho <xref:System.Windows.Forms.BorderStyle> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="d0e2c-115">Existují tři možnosti: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, a <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="d0e2c-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e2c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0e2c-116">See Also</span></span>  
 [<span data-ttu-id="d0e2c-117">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="d0e2c-117">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="d0e2c-118">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="d0e2c-118">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="d0e2c-119">Postupy: Nastavení pozadí panelu</span><span class="sxs-lookup"><span data-stu-id="d0e2c-119">How to: Set the Background of a Panel</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
