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
ms.openlocfilehash: 788addee7c024577d029626da4aeb86d0ca9076a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941151"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="14d9c-102">Postupy: Dědění ze stávajících ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14d9c-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="14d9c-103">Pokud chcete rozšířit funkce pro existující ovládací prvek, můžete vytvořit ovládací prvek odvozený z existujícího ovládacího prvku prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="14d9c-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="14d9c-104">Při dědění z existujícího ovládacího prvku, zdědí všechny funkce a vlastností ovládacího prvku visual.</span><span class="sxs-lookup"><span data-stu-id="14d9c-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="14d9c-105">Například, pokud vytváříte ovládací prvek, který dědí z <xref:System.Windows.Forms.Button>, by vypadalo nového ovládacího prvku a act stejně jako standardní <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="14d9c-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="14d9c-106">Pak můžete rozšířit nebo upravit funkce nasazovaných nového ovládacího prvku prostřednictvím implementace vlastních metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="14d9c-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="14d9c-107">V některých ovládacích prvků, můžete také změnit vzhled zděděný ovládací prvek tak, že přepíšete její <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="14d9c-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14d9c-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="14d9c-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="14d9c-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="14d9c-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="14d9c-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="14d9c-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-an-inherited-control"></a><span data-ttu-id="14d9c-111">Chcete-li vytvořit zděděný ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="14d9c-111">To create an inherited control</span></span>  
  
1. <span data-ttu-id="14d9c-112">Vytvořte nový **formulářová aplikace Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="14d9c-112">Create a new **Windows Forms Application** project.</span></span>  
  
2. <span data-ttu-id="14d9c-113">Z **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="14d9c-113">From the **Project** menu, choose **Add New Item**.</span></span>  
  
     <span data-ttu-id="14d9c-114">Zobrazí se dialogové okno **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="14d9c-114">The **Add New Item** dialog box appears.</span></span>  
  
3. <span data-ttu-id="14d9c-115">V **přidat novou položku** dialogové okno, klikněte dvakrát na **vlastní ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="14d9c-115">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>  
  
     <span data-ttu-id="14d9c-116">Nový vlastní ovládací prvek se přidá do vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="14d9c-116">A new custom control is added to your project.</span></span>  
  
4. <span data-ttu-id="14d9c-117">Pokud používáte Visual Basic, v horní části **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="14d9c-117">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="14d9c-118">Rozbalte CustomControl1.vb a poté otevřete CustomControl1.Designer.vb v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="14d9c-118">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>  
  
5. <span data-ttu-id="14d9c-119">Pokud používáte C#, otevřete CustomControl1.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="14d9c-119">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>  
  
6. <span data-ttu-id="14d9c-120">Vyhledejte deklaraci třídy, která dědí z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="14d9c-120">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>  
  
7. <span data-ttu-id="14d9c-121">Změňte základní třídu pro ovládací prvek, který se má Zdědit z.</span><span class="sxs-lookup"><span data-stu-id="14d9c-121">Change the base class to the control that you want to inherit from.</span></span>  
  
     <span data-ttu-id="14d9c-122">Například, pokud chcete dědit z <xref:System.Windows.Forms.Button>, změňte deklaraci třídy na následující:</span><span class="sxs-lookup"><span data-stu-id="14d9c-122">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8. <span data-ttu-id="14d9c-123">Pokud používáte Visual Basic, uložte a zavřete CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="14d9c-123">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="14d9c-124">Otevřete CustomControl1.vb v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="14d9c-124">Open CustomControl1.vb in the Code Editor.</span></span>  
  
9. <span data-ttu-id="14d9c-125">Implementujte všechny vlastní metody nebo vlastnosti, které bude obsahovat váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="14d9c-125">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
10. <span data-ttu-id="14d9c-126">Pokud chcete upravit vzhled grafického ovládacího prvku, má přednost před <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="14d9c-126">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="14d9c-127">Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> nebude možné změnit vzhled všech ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="14d9c-127">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="14d9c-128">Tyto ovládací prvky, které mají všechny jejich Malování provádí Windows (například <xref:System.Windows.Forms.TextBox>) nikdy neměl volat jejich <xref:System.Windows.Forms.Control.OnPaint%2A> metoda a proto se nikdy použít vlastní kód.</span><span class="sxs-lookup"><span data-stu-id="14d9c-128">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="14d9c-129">Přečtěte si dokumentaci nápovědy pro konkrétní ovládací prvek, kterou chcete upravit a zjistěte, jestli <xref:System.Windows.Forms.Control.OnPaint%2A> metoda je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="14d9c-129">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="14d9c-130">Seznam všechny ovládací prvky formuláře Windows najdete v tématu [ovládací prvky používané ve formulářích Windows](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="14d9c-130">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="14d9c-131">Pokud ovládací prvek nemá žádné <xref:System.Windows.Forms.Control.OnPaint%2A> uvedená jako člena metody, není možné pozměnit jeho vzhled přepsáním této metody.</span><span class="sxs-lookup"><span data-stu-id="14d9c-131">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="14d9c-132">Další informace o vlastních Malování, naleznete v tématu [vlastní ovládací prvek Malování a vykreslování](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="14d9c-132">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>  
  
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
  
11. <span data-ttu-id="14d9c-133">Uložit a testování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="14d9c-133">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d9c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14d9c-134">See also</span></span>

- [<span data-ttu-id="14d9c-135">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="14d9c-135">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="14d9c-136">Postupy: Dědit ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="14d9c-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="14d9c-137">Postupy: Dědit ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="14d9c-137">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="14d9c-138">Postupy: Autor ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14d9c-138">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="14d9c-139">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="14d9c-139">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="14d9c-140">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="14d9c-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="14d9c-141">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="14d9c-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
