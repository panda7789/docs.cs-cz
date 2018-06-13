---
title: 'Postupy: Dědění ze stávajících ovládacích prvků Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 6f35881bdb7a781d817c9f671962d0445bfd8e27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538738"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="599f0-102">Postupy: Dědění ze stávajících ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="599f0-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="599f0-103">Pokud chcete rozšířit funkce existujícího ovládacího prvku, můžete vytvořit ovládacího prvku odvozenou z ovládacího prvku existující prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="599f0-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="599f0-104">Při dědění z ovládacího prvku existující, dědí všechny funkce a vizuálních vlastností tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="599f0-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="599f0-105">Například při vytváření ovládacího prvku, který dědí z <xref:System.Windows.Forms.Button>, nový ovládací prvek vypadat a act přesně standardní <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="599f0-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="599f0-106">Pak můžete rozšířit nebo změnit funkce nový ovládací prvek prostřednictvím implementace vlastních metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="599f0-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="599f0-107">V některé ovládací prvky, můžete také změnit vzhled ovládacího prvku zděděné přepsáním jeho <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="599f0-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="599f0-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="599f0-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="599f0-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="599f0-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="599f0-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="599f0-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-an-inherited-control"></a><span data-ttu-id="599f0-111">Vytvoření ovládacího prvku zděděné</span><span class="sxs-lookup"><span data-stu-id="599f0-111">To create an inherited control</span></span>  
  
1.  <span data-ttu-id="599f0-112">Vytvořte novou **formulářové aplikace Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="599f0-112">Create a new **Windows Forms Application** project.</span></span>  
  
2.  <span data-ttu-id="599f0-113">Z **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="599f0-113">From the **Project** menu, choose **Add New Item**.</span></span>  
  
     <span data-ttu-id="599f0-114">**Přidat novou položku** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="599f0-114">The **Add New Item** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="599f0-115">V **přidat novou položku** dialogové okno, dvakrát klikněte na **vlastní ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="599f0-115">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>  
  
     <span data-ttu-id="599f0-116">Nové vlastní ovládací prvek se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="599f0-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="599f0-117">Pokud používáte Visual Basic, v horní části **Průzkumníku řešení**, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="599f0-117">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="599f0-118">Rozbalte CustomControl1.vb a pak otevřete CustomControl1.Designer.vb v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="599f0-118">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>  
  
5.  <span data-ttu-id="599f0-119">Pokud používáte C#, otevřete v editoru kódu CustomControl1.cs.</span><span class="sxs-lookup"><span data-stu-id="599f0-119">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>  
  
6.  <span data-ttu-id="599f0-120">Vyhledejte deklaraci třídy, která dědí z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="599f0-120">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>  
  
7.  <span data-ttu-id="599f0-121">Změňte základní třídu pro ovládací prvek, který chcete použít dědění z.</span><span class="sxs-lookup"><span data-stu-id="599f0-121">Change the base class to the control that you want to inherit from.</span></span>  
  
     <span data-ttu-id="599f0-122">Například, pokud chcete použít dědění z <xref:System.Windows.Forms.Button>, změňte deklaraci třídy na následující:</span><span class="sxs-lookup"><span data-stu-id="599f0-122">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  <span data-ttu-id="599f0-123">Pokud používáte Visual Basic, uložte a zavřete CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="599f0-123">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="599f0-124">Otevřete CustomControl1.vb v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="599f0-124">Open CustomControl1.vb in the Code Editor.</span></span>  
  
9. <span data-ttu-id="599f0-125">Implementujte jakékoliv vlastní metody nebo vlastnosti, které bude obsahovat vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="599f0-125">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
10. <span data-ttu-id="599f0-126">Pokud chcete upravit grafický vzhled ovládacího prvku, mají přednost před <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="599f0-126">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="599f0-127">Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> nebude možné změnit vzhled všech ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="599f0-127">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="599f0-128">Kontrolní mechanismy, které mají všechny jejich Malování provádí systému Windows (například <xref:System.Windows.Forms.TextBox>) nikdy volat jejich <xref:System.Windows.Forms.Control.OnPaint%2A> metoda a proto se nikdy použít vlastní kód.</span><span class="sxs-lookup"><span data-stu-id="599f0-128">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="599f0-129">V dokumentaci nápovědy pro konkrétní ovládací prvek, kterou chcete upravit a zjistěte, zda <xref:System.Windows.Forms.Control.OnPaint%2A> metoda je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="599f0-129">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="599f0-130">Seznam všechny požadované ovládací prvky Windows najdete v tématu [ovládací prvky používané ve formulářích Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="599f0-130">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="599f0-131">Pokud ovládací prvek nemá <xref:System.Windows.Forms.Control.OnPaint%2A> uvedené jako člen metodu, nelze změnit její vzhled přepsáním této metody.</span><span class="sxs-lookup"><span data-stu-id="599f0-131">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="599f0-132">Další informace o vlastních Malování najdete v tématu [vlastní ovládací prvek Malování a vykreslování](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="599f0-132">For more information about custom painting, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
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
  
11. <span data-ttu-id="599f0-133">Uložte a otestování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="599f0-133">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599f0-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="599f0-134">See Also</span></span>  
 [<span data-ttu-id="599f0-135">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="599f0-135">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="599f0-136">Postupy: Dědění ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="599f0-136">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [<span data-ttu-id="599f0-137">Postupy: Dědění ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="599f0-137">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="599f0-138">Postupy: Vytváření ovládacích prvků pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="599f0-138">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="599f0-139">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="599f0-139">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="599f0-140">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="599f0-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="599f0-141">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="599f0-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
