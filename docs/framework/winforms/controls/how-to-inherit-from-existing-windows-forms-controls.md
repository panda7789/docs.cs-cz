---
title: "Postupy: Dědění ze stávajících ovládacích prvků Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6049e5e0f2d79bab8ad90b6e63e91d4d4fa705ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="e93b9-102">Postupy: Dědění ze stávajících ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e93b9-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="e93b9-103">Pokud chcete rozšířit funkce existujícího ovládacího prvku, můžete vytvořit ovládacího prvku odvozenou z ovládacího prvku existující prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="e93b9-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="e93b9-104">Při dědění z ovládacího prvku existující, dědí všechny funkce a vizuálních vlastností tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e93b9-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="e93b9-105">Například při vytváření ovládacího prvku, který dědí z <xref:System.Windows.Forms.Button>, nový ovládací prvek vypadat a act přesně standardní <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e93b9-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="e93b9-106">Pak můžete rozšířit nebo změnit funkce nový ovládací prvek prostřednictvím implementace vlastních metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="e93b9-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="e93b9-107">V některé ovládací prvky, můžete také změnit vzhled ovládacího prvku zděděné přepsáním jeho <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e93b9-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e93b9-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="e93b9-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e93b9-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="e93b9-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e93b9-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e93b9-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-an-inherited-control"></a><span data-ttu-id="e93b9-111">Vytvoření ovládacího prvku zděděné</span><span class="sxs-lookup"><span data-stu-id="e93b9-111">To create an inherited control</span></span>  
  
1.  <span data-ttu-id="e93b9-112">Vytvořte novou **formulářové aplikace Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="e93b9-112">Create a new **Windows Forms Application** project.</span></span>  
  
2.  <span data-ttu-id="e93b9-113">Z **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="e93b9-113">From the **Project** menu, choose **Add New Item**.</span></span>  
  
     <span data-ttu-id="e93b9-114">**Přidat novou položku** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e93b9-114">The **Add New Item** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="e93b9-115">V **přidat novou položku** dialogové okno, dvakrát klikněte na **vlastní ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="e93b9-115">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>  
  
     <span data-ttu-id="e93b9-116">Nové vlastní ovládací prvek se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="e93b9-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="e93b9-117">Pokud používáte Visual Basic, v horní části **Průzkumníku řešení**, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="e93b9-117">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="e93b9-118">Rozbalte CustomControl1.vb a pak otevřete CustomControl1.Designer.vb v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="e93b9-118">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>  
  
5.  <span data-ttu-id="e93b9-119">Pokud používáte C#, otevřete v editoru kódu CustomControl1.cs.</span><span class="sxs-lookup"><span data-stu-id="e93b9-119">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>  
  
6.  <span data-ttu-id="e93b9-120">Vyhledejte deklaraci třídy, která dědí z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="e93b9-120">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>  
  
7.  <span data-ttu-id="e93b9-121">Změňte základní třídu pro ovládací prvek, který chcete použít dědění z.</span><span class="sxs-lookup"><span data-stu-id="e93b9-121">Change the base class to the control that you want to inherit from.</span></span>  
  
     <span data-ttu-id="e93b9-122">Například, pokud chcete použít dědění z <xref:System.Windows.Forms.Button>, změňte deklaraci třídy na následující:</span><span class="sxs-lookup"><span data-stu-id="e93b9-122">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  <span data-ttu-id="e93b9-123">Pokud používáte Visual Basic, uložte a zavřete CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="e93b9-123">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="e93b9-124">Otevřete CustomControl1.vb v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="e93b9-124">Open CustomControl1.vb in the Code Editor.</span></span>  
  
9. <span data-ttu-id="e93b9-125">Implementujte jakékoliv vlastní metody nebo vlastnosti, které bude obsahovat vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e93b9-125">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
10. <span data-ttu-id="e93b9-126">Pokud chcete upravit grafický vzhled ovládacího prvku, mají přednost před <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e93b9-126">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e93b9-127">Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> nebude možné změnit vzhled všech ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e93b9-127">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="e93b9-128">Kontrolní mechanismy, které mají všechny jejich Malování provádí systému Windows (například <xref:System.Windows.Forms.TextBox>) nikdy volat jejich <xref:System.Windows.Forms.Control.OnPaint%2A> metoda a proto se nikdy použít vlastní kód.</span><span class="sxs-lookup"><span data-stu-id="e93b9-128">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="e93b9-129">V dokumentaci nápovědy pro konkrétní ovládací prvek, kterou chcete upravit a zjistěte, zda <xref:System.Windows.Forms.Control.OnPaint%2A> metoda je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e93b9-129">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="e93b9-130">Seznam všechny požadované ovládací prvky Windows najdete v tématu [ovládací prvky používané ve formulářích Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e93b9-130">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="e93b9-131">Pokud ovládací prvek nemá <xref:System.Windows.Forms.Control.OnPaint%2A> uvedené jako člen metodu, nelze změnit její vzhled přepsáním této metody.</span><span class="sxs-lookup"><span data-stu-id="e93b9-131">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="e93b9-132">Další informace o vlastních Malování najdete v tématu [vlastní ovládací prvek Malování a vykreslování](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="e93b9-132">For more information about custom painting, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
    ```vb  
    Protected Overrides Sub OnPaint(ByVal e As _  
       System.Windows.Forms.PaintEventArgs)  
       MyBase.OnPaint(e)  
       ' Insert code to do custom painting.   
       ' If you want to completely change the appearance of your control,  
       ' do not call MyBase.OnPaint(e).  
    End Sub  
    ```  
  
    ```csharp  
    protected override void OnPaint(PaintEventArgs pe)  
    {  
       base.OnPaint(pe);  
       // Insert code to do custom painting.  
       // If you want to completely change the appearance of your control,  
       // do not call base.OnPaint(pe).  
    }  
    ```  
  
11. <span data-ttu-id="e93b9-133">Uložte a otestování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e93b9-133">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93b9-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e93b9-134">See Also</span></span>  
 [<span data-ttu-id="e93b9-135">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e93b9-135">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="e93b9-136">Postupy: Dědění ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="e93b9-136">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [<span data-ttu-id="e93b9-137">Postupy: Dědění ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="e93b9-137">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="e93b9-138">Postupy: Vytváření ovládacích prvků pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e93b9-138">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="e93b9-139">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e93b9-139">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="e93b9-140">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="e93b9-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="e93b9-141">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="e93b9-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
