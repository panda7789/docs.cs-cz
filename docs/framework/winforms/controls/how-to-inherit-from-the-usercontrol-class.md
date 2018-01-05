---
title: "Postupy: Dědění ze třídy UserControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8d04eb3c0f9ad3ef9f316bf156a9cc9568e7f8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="1dd7c-102">Postupy: Dědění ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="1dd7c-102">How to: Inherit from the UserControl Class</span></span>
<span data-ttu-id="1dd7c-103">Chcete-li funkci jeden nebo více ovládacích prvků Windows Forms kombinovat s vlastní kód, můžete vytvořit *uživatelský ovládací prvek*.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="1dd7c-104">Uživatelské ovládací prvky kombinovat vývoj rychlé ovládacího prvku, funkce a všestrannost vlastní vlastnosti a metody ovládací prvek standardní Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="1dd7c-105">Když začnete vytvoření uživatelského ovládacího prvku, máte k ruce viditelné designer, na který můžete umístit standardní ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="1dd7c-106">Tyto ovládací prvky zachovat všechny jejich vyplývajících funkce, jakož i vzhled a chování (vzhled a chování) standardní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="1dd7c-107">Jakmile tyto ovládací prvky jsou součástí uživatelského ovládacího prvku, ale jsou již k dispozici prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="1dd7c-108">Uživatelský ovládací prvek nepodporuje svůj vlastní Malování a také zpracovává všechny základní funkce související s ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1dd7c-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1dd7c-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1dd7c-111">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1dd7c-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-user-control"></a><span data-ttu-id="1dd7c-112">Vytvoření uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="1dd7c-112">To create a user control</span></span>  
  
1.  <span data-ttu-id="1dd7c-113">Vytvořte novou **knihovny ovládacích prvků Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-113">Create a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="1dd7c-114">Nový projekt se vytvoří s prázdnou uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-114">A new project is created with a blank user control.</span></span>  
  
2.  <span data-ttu-id="1dd7c-115">Přetáhněte ovládací prvky z **Windows Forms** kartě **sada nástrojů** do vašeho návrháře.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-115">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>  
  
3.  <span data-ttu-id="1dd7c-116">Tyto ovládací prvky by měl být umístěný a navržená tak, jak chcete, aby se objevily v ovládacím prvku konečného uživatele.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-116">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="1dd7c-117">Pokud chcete povolit uživatelům přístup k základní ovládací prvky, musí deklarovat jako veřejný nebo selektivně vystavení vlastností základních ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-117">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="1dd7c-118">Podrobnosti najdete v tématu [postupy: vystavení vlastností prvku prvky](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1dd7c-118">For details, see [How to: Expose Properties of Constituent Controls](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).</span></span>  
  
4.  <span data-ttu-id="1dd7c-119">Implementujte jakékoliv vlastní metody nebo vlastnosti, které bude obsahovat vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-119">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
5.  <span data-ttu-id="1dd7c-120">Stiskněte klávesu F5, aby se projekt sestavil a spuštění vlastního ovládacího prvku v **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="1dd7c-120">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="1dd7c-121">Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="1dd7c-121">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd7c-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dd7c-122">See Also</span></span>  
 [<span data-ttu-id="1dd7c-123">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="1dd7c-123">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="1dd7c-124">Postupy: Dědění ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="1dd7c-124">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [<span data-ttu-id="1dd7c-125">Postupy: Dědění ze stávajících ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1dd7c-125">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="1dd7c-126">Postupy: Vytváření ovládacích prvků pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1dd7c-126">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="1dd7c-127">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dd7c-127">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="1dd7c-128">Postupy: Otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="1dd7c-128">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
