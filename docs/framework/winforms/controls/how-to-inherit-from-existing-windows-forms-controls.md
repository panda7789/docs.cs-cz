---
title: Dědění ze stávajících ovládacích prvků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b0e0053816efde349c7e4d13d03bef5f8801c667
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849377"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="984b3-102">Postupy: Dědění ze stávajících ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="984b3-102">How to: Inherit from Existing Windows Forms Controls</span></span>

<span data-ttu-id="984b3-103">Pokud chcete rozšířit funkce existujícího ovládacího prvku, můžete vytvořit ovládací prvek odvozený z existujícího ovládacího prvku prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="984b3-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="984b3-104">Při dědění z existujícího ovládacího prvku zdědíte všechny funkce a vizuální vlastnosti tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="984b3-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="984b3-105">Například pokud jste vytvářeli ovládací prvek, který zdědil z <xref:System.Windows.Forms.Button>, nový <xref:System.Windows.Forms.Button> ovládací prvek bude vypadat a chovat přesně jako standardní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="984b3-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="984b3-106">Potom můžete rozšířit nebo upravit funkce nového ovládacího prvku prostřednictvím implementace vlastních metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="984b3-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="984b3-107">V některých ovládacích prvcích můžete také změnit vizuální <xref:System.Windows.Forms.Control.OnPaint%2A> vzhled zděděného ovládacího prvku přepsáním jeho metody.</span><span class="sxs-lookup"><span data-stu-id="984b3-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="984b3-108">Vytvoření zděděného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="984b3-108">To create an inherited control</span></span>

1. <span data-ttu-id="984b3-109">V sadě Visual Studio vytvořte nový projekt **aplikace Windows Forms.**</span><span class="sxs-lookup"><span data-stu-id="984b3-109">In Visual Studio, create a new **Windows Forms Application** project.</span></span>

1. <span data-ttu-id="984b3-110">V nabídce **Projekt** zvolte **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="984b3-110">From the **Project** menu, choose **Add New Item**.</span></span>

    <span data-ttu-id="984b3-111">Zobrazí se dialogové okno **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="984b3-111">The **Add New Item** dialog box appears.</span></span>

1. <span data-ttu-id="984b3-112">V dialogovém okně **Přidat novou položku** poklepejte na **položku Vlastní ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="984b3-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

    <span data-ttu-id="984b3-113">Do projektu je přidán nový vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="984b3-113">A new custom control is added to your project.</span></span>

1. <span data-ttu-id="984b3-114">Pokud používáte:</span><span class="sxs-lookup"><span data-stu-id="984b3-114">If you're using:</span></span>

    - <span data-ttu-id="984b3-115">Visual Basic v horní části **Průzkumníka řešení**klikněte na **Zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="984b3-115">Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="984b3-116">Rozbalte soubor CustomControl1.vb a v Editoru kódu otevřete soubor CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="984b3-116">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>
    - <span data-ttu-id="984b3-117">C#, otevřete CustomControl1.cs v Editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="984b3-117">C#, open CustomControl1.cs in the Code Editor.</span></span>

1. <span data-ttu-id="984b3-118">Vyhledejte deklaraci třídy, <xref:System.Windows.Forms.Control>která dědí z .</span><span class="sxs-lookup"><span data-stu-id="984b3-118">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

1. <span data-ttu-id="984b3-119">Změňte základní třídu na ovládací prvek, ze kterého chcete dědit.</span><span class="sxs-lookup"><span data-stu-id="984b3-119">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="984b3-120">Chcete-li například dědit <xref:System.Windows.Forms.Button>z , změňte deklaraci třídy na následující:</span><span class="sxs-lookup"><span data-stu-id="984b3-120">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. <span data-ttu-id="984b3-121">Pokud používáte visual basic, uložte a zavřete CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="984b3-121">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="984b3-122">V Editoru kódu otevřete soubor CustomControl1.vb.</span><span class="sxs-lookup"><span data-stu-id="984b3-122">Open CustomControl1.vb in the Code Editor.</span></span>

1. <span data-ttu-id="984b3-123">Implementujte všechny vlastní metody nebo vlastnosti, které bude váš ovládací prvek zahrnovat.</span><span class="sxs-lookup"><span data-stu-id="984b3-123">Implement any custom methods or properties that your control will incorporate.</span></span>

1. <span data-ttu-id="984b3-124">Pokud chcete změnit grafický vzhled ovládacího prvku, <xref:System.Windows.Forms.Control.OnPaint%2A> přepište metodu.</span><span class="sxs-lookup"><span data-stu-id="984b3-124">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="984b3-125">Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> neumožňuje změnit vzhled všech ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="984b3-125">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="984b3-126">Tyto ovládací prvky, které mají všechny jejich <xref:System.Windows.Forms.TextBox>malování provádí <xref:System.Windows.Forms.Control.OnPaint%2A> systém Windows (například ) nikdy volat jejich metodu, a proto nikdy nebude používat vlastní kód.</span><span class="sxs-lookup"><span data-stu-id="984b3-126">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="984b3-127">Naleznete v dokumentaci nápovědy pro konkrétní ovládací prvek, který chcete upravit, abyste zjistili, <xref:System.Windows.Forms.Control.OnPaint%2A> zda je metoda k dispozici.</span><span class="sxs-lookup"><span data-stu-id="984b3-127">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="984b3-128">Seznam všech ovládacích prvků formuláře systému Windows naleznete v tématu [Ovládací prvky pro použití ve formulářích systému Windows](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="984b3-128">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="984b3-129">Pokud ovládací prvek <xref:System.Windows.Forms.Control.OnPaint%2A> nemá uvedeny jako členské metody, nelze změnit jeho vzhled přepsáním této metody.</span><span class="sxs-lookup"><span data-stu-id="984b3-129">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="984b3-130">Další informace o vlastním malování naleznete v [tématu Vlastní řídicí malba a vykreslování](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="984b3-130">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

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

1. <span data-ttu-id="984b3-131">Uložte a otestujte ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="984b3-131">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="984b3-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="984b3-132">See also</span></span>

- [<span data-ttu-id="984b3-133">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="984b3-133">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="984b3-134">Postupy: Dědění ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="984b3-134">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="984b3-135">Postupy: Dědění ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="984b3-135">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="984b3-136">Postupy: Vytváření ovládacích prvků pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="984b3-136">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="984b3-137">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="984b3-137">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="984b3-138">Návod: Dědění z ovládacího prvku formulářů systému Windows</span><span class="sxs-lookup"><span data-stu-id="984b3-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
