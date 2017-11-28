---
title: "Postupy: Dědění ze třídy Control"
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
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 75b9c56d2d9df80745cec2b811c39f5e438d07c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="5c0ed-102">Postupy: Dědění ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="5c0ed-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="5c0ed-103">Pokud chcete vytvořit zcela vlastního ovládacího prvku na formuláři Windows používat, musí dědit z <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="5c0ed-104">Při dědění z <xref:System.Windows.Forms.Control> třída vyžaduje provést další plánování a implementace, můžete ho vám rovněž poskytne největší škálu možností.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="5c0ed-105">Když je zděděný z <xref:System.Windows.Forms.Control>, dědí velmi základní funkce, která umožňuje ovládací prvky fungovat.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="5c0ed-106">Funkci vyplývajících z <xref:System.Windows.Forms.Control> třída zpracovává vstupu uživatele prostřednictvím klávesnici a myš, definuje rozsah a velikost ovládacího prvku, poskytuje popisovačů systému windows a poskytuje zpracování zpráv a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="5c0ed-107">Ho nebere v úvahu žádné Malování, který v tomto případě je skutečný vykreslování grafické rozhraní ovládacího prvku, ani nebude obsahovat žádné funkce interakce konkrétního uživatele.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="5c0ed-108">Je nutné zadat všechny tyto aspekty prostřednictvím vlastní kód.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-108">You must provide all of these aspects through custom code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c0ed-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5c0ed-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5c0ed-111">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5c0ed-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-custom-control"></a><span data-ttu-id="5c0ed-112">Chcete-li vytvořit vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="5c0ed-112">To create a custom control</span></span>  
  
1.  <span data-ttu-id="5c0ed-113">Vytvořte novou **aplikace Windows** nebo **knihovny ovládacích prvků Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-113">Create a new **Windows Application** or **Windows Control Library** project.</span></span>  
  
2.  <span data-ttu-id="5c0ed-114">Z **projektu** nabídce zvolte **přidat třídu**.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-114">From the **Project** menu, choose **Add Class**.</span></span>  
  
3.  <span data-ttu-id="5c0ed-115">V **přidat novou položku** dialogové okno, klikněte na tlačítko **vlastní ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-115">In the **Add New Item** dialog box, click **Custom Control**.</span></span>  
  
     <span data-ttu-id="5c0ed-116">Nové vlastní ovládací prvek se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="5c0ed-117">Stisknutím klávesy F7 otevřete **Editor kódu** pro váš vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-117">Press F7 to open the **Code Editor** for your custom control.</span></span>  
  
5.  <span data-ttu-id="5c0ed-118">Vyhledejte <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, která bude prázdný, s výjimkou volání <xref:System.Windows.Forms.Control.OnPaint%2A> metoda základní třídy.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-118">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
6.  <span data-ttu-id="5c0ed-119">Upravte kód, abyste zapracovali všechny vlastní Malování, které chcete použít pro vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-119">Modify the code to incorporate any custom painting you want for your control.</span></span>  
  
     <span data-ttu-id="5c0ed-120">Informace o psaní kódu pro vykreslení grafiky pro ovládací prvky najdete v tématu [vlastní ovládací prvek Malování a vykreslování](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="5c0ed-120">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
7.  <span data-ttu-id="5c0ed-121">Implementujte všech vlastních metod, vlastností nebo událostí, které bude obsahovat vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-121">Implement any custom methods, properties, or events that your control will incorporate.</span></span>  
  
8.  <span data-ttu-id="5c0ed-122">Uložte a otestování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5c0ed-122">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c0ed-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c0ed-123">See Also</span></span>  
 [<span data-ttu-id="5c0ed-124">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="5c0ed-124">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="5c0ed-125">Postupy: dědění ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="5c0ed-125">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="5c0ed-126">Postupy: dědění ze stávajícího systému Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="5c0ed-126">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="5c0ed-127">Postupy: vytváření ovládacích prvků pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c0ed-127">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="5c0ed-128">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c0ed-128">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="5c0ed-129">Vývoj Windows Forms – ovládací prvky v době návrhu</span><span class="sxs-lookup"><span data-stu-id="5c0ed-129">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
