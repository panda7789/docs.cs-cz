---
title: "Postupy: Uzamykání ovládacích prvků ve formulářích Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f5cd70e71a4a8bc48a3240055117dadc1086a50
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="573ab-102">Postupy: Uzamykání ovládacích prvků ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="573ab-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="573ab-103">Při návrhu uživatelské rozhraní (UI) aplikace systému Windows, je možné po jejich jsou umístěna správně, tak, aby není nechtěně přesunout nebo změnit jejich velikost, při nastavování jiných vlastností ovládacích prvků zamknout.</span><span class="sxs-lookup"><span data-stu-id="573ab-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>  
  
 <span data-ttu-id="573ab-104">Kromě toho můžete zamykání a odemykání všechny ovládací prvky na formuláři najednou, což je užitečné pro formuláře s mnoha ovládací prvky, nebo můžete odemknout jednotlivých ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="573ab-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="573ab-105">Jakmile jste umístili všechny ovládací prvky. požadované místo na formuláři, uzamčení je na místě, aby se zabránilo chybné pohyb.</span><span class="sxs-lookup"><span data-stu-id="573ab-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="573ab-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="573ab-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="573ab-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="573ab-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="573ab-108">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="573ab-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-lock-a-control"></a><span data-ttu-id="573ab-109">K uzamčení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="573ab-109">To lock a control</span></span>  
  
1.  <span data-ttu-id="573ab-110">V **vlastnosti** okně klikněte na tlačítko **uzamčen** vlastnost a vyberte `true`.</span><span class="sxs-lookup"><span data-stu-id="573ab-110">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="573ab-111">(Dvakrát klikněte na název přepne na nastavení vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="573ab-111">(Double-clicking the name toggles the property setting.)</span></span>  
  
     <span data-ttu-id="573ab-112">Nebo klikněte pravým tlačítkem na ovládací prvek a zvolte **ovládací prvky zámku**.</span><span class="sxs-lookup"><span data-stu-id="573ab-112">Alternatively, right-click the control and choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="573ab-113">Uzamykání ovládacích prvků sdělovat tažením nové velikosti nebo umístění na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="573ab-113">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="573ab-114">Však můžete stále změnit velikost nebo umístění ovládacích prvků pomocí **vlastnosti** okno nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="573ab-114">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>  
  
### <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="573ab-115">Chcete-li zamknout všechny ovládací prvky ve formuláři</span><span class="sxs-lookup"><span data-stu-id="573ab-115">To lock all the controls on a form</span></span>  
  
1.  <span data-ttu-id="573ab-116">Z **formátu** nabídce zvolte **ovládací prvky zámku**.</span><span class="sxs-lookup"><span data-stu-id="573ab-116">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="573ab-117">Tento příkaz Zamkne velikost formuláře je také možné, protože formuláře je ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="573ab-117">This command locks the form's size as well, because a form is a control.</span></span>  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="573ab-118">Odemknout uzamčení všechny ovládací prvky ve formuláři</span><span class="sxs-lookup"><span data-stu-id="573ab-118">To unlock all locked controls on a form</span></span>  
  
1.  <span data-ttu-id="573ab-119">Z **formátu** nabídce zvolte **ovládací prvky zámku**.</span><span class="sxs-lookup"><span data-stu-id="573ab-119">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
     <span data-ttu-id="573ab-120">Všechny dříve uzamčeném ovládací prvky na formuláři jsou nyní odemknout.</span><span class="sxs-lookup"><span data-stu-id="573ab-120">All previously locked controls on the form are now unlocked.</span></span>  
  
### <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="573ab-121">Odemknout uzamčení jednotlivě ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="573ab-121">To unlock locked controls individually</span></span>  
  
1.  <span data-ttu-id="573ab-122">V **vlastnosti** okně klikněte na tlačítko **uzamčen** vlastnost a vyberte `false`.</span><span class="sxs-lookup"><span data-stu-id="573ab-122">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="573ab-123">(Dvakrát klikněte na název přepne na nastavení vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="573ab-123">(Double-clicking the name toggles the property setting.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573ab-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="573ab-124">See Also</span></span>  
 [<span data-ttu-id="573ab-125">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="573ab-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="573ab-126">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="573ab-126">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="573ab-127">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="573ab-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="573ab-128">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="573ab-128">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="573ab-129">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="573ab-129">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
