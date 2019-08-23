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
ms.openlocfilehash: 9ac18fae126425126712dafeb80f05663dfc2ebc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966591"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="32e1e-102">Postupy: Dědění ze stávajících ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32e1e-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="32e1e-103">Chcete-li zvětšit funkce stávajícího ovládacího prvku, můžete vytvořit ovládací prvek odvozený z existujícího ovládacího prvku prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="32e1e-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="32e1e-104">Při dědění z existujícího ovládacího prvku zdědíte všechny funkce a vizuální vlastnosti daného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="32e1e-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="32e1e-105">Například pokud jste vytvořili ovládací prvek, který zdědil z <xref:System.Windows.Forms.Button>, váš nový ovládací prvek by vypadal a fungoval přesně jako standardní <xref:System.Windows.Forms.Button> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="32e1e-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="32e1e-106">Můžete následně roztáhnout nebo změnit funkce nového ovládacího prvku prostřednictvím implementace vlastních metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="32e1e-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="32e1e-107">V některých ovládacích prvcích můžete také změnit vizuální vzhled zděděného ovládacího prvku přepsáním jeho <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="32e1e-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="32e1e-108">Vytvoření zděděného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="32e1e-108">To create an inherited control</span></span>

1. <span data-ttu-id="32e1e-109">Vytvořte nový projekt **aplikace model Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="32e1e-109">Create a new **Windows Forms Application** project.</span></span>

2. <span data-ttu-id="32e1e-110">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="32e1e-110">From the **Project** menu, choose **Add New Item**.</span></span>

     <span data-ttu-id="32e1e-111">Zobrazí se dialogové okno **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="32e1e-111">The **Add New Item** dialog box appears.</span></span>

3. <span data-ttu-id="32e1e-112">V dialogovém okně **Přidat novou položku** dvakrát klikněte na možnost **vlastní ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="32e1e-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

     <span data-ttu-id="32e1e-113">Do projektu se přidá nový vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="32e1e-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="32e1e-114">Pokud používáte Visual Basic, klikněte v horní části **Průzkumník řešení**na **Zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="32e1e-114">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="32e1e-115">Rozbalte CustomControl1. vb a potom v editoru kódu otevřete CustomControl1. Designer. vb.</span><span class="sxs-lookup"><span data-stu-id="32e1e-115">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>

5. <span data-ttu-id="32e1e-116">Pokud používáte C#, otevřete CustomControl1.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="32e1e-116">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>

6. <span data-ttu-id="32e1e-117">Vyhledejte deklaraci třídy, ze <xref:System.Windows.Forms.Control>které dědí.</span><span class="sxs-lookup"><span data-stu-id="32e1e-117">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

7. <span data-ttu-id="32e1e-118">Změňte základní třídu na ovládací prvek, ze kterého chcete dědit.</span><span class="sxs-lookup"><span data-stu-id="32e1e-118">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="32e1e-119">Například pokud chcete dědit z <xref:System.Windows.Forms.Button>, změňte deklaraci třídy na následující:</span><span class="sxs-lookup"><span data-stu-id="32e1e-119">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

8. <span data-ttu-id="32e1e-120">Pokud používáte Visual Basic, uložte a zavřete CustomControl1. Designer. vb.</span><span class="sxs-lookup"><span data-stu-id="32e1e-120">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="32e1e-121">Otevřete CustomControl1. vb v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="32e1e-121">Open CustomControl1.vb in the Code Editor.</span></span>

9. <span data-ttu-id="32e1e-122">Implementujte všechny vlastní metody nebo vlastnosti, které bude váš ovládací prvek obsahovat.</span><span class="sxs-lookup"><span data-stu-id="32e1e-122">Implement any custom methods or properties that your control will incorporate.</span></span>

10. <span data-ttu-id="32e1e-123">Chcete-li upravit grafický vzhled ovládacího prvku, přepište <xref:System.Windows.Forms.Control.OnPaint%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="32e1e-123">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="32e1e-124">Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> nebude umožňovat úpravu vzhledu všech ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="32e1e-124">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="32e1e-125">Tyto ovládací prvky, které mají všechny kresby provedené systémem Windows (například <xref:System.Windows.Forms.TextBox>), nikdy nevolají svou <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, a proto nikdy nepoužijí vlastní kód.</span><span class="sxs-lookup"><span data-stu-id="32e1e-125">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="32e1e-126">Chcete-li zjistit, zda <xref:System.Windows.Forms.Control.OnPaint%2A> je metoda k dispozici, přečtěte si dokumentaci k příslušnému ovládacímu prvku, který chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="32e1e-126">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="32e1e-127">Seznam všech ovládacích prvků Windows Form naleznete v tématu [ovládací prvky pro použití v model Windows Forms](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="32e1e-127">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="32e1e-128">Pokud ovládací prvek není <xref:System.Windows.Forms.Control.OnPaint%2A> uveden jako metoda člena, nelze změnit jeho vzhled přepsáním této metody.</span><span class="sxs-lookup"><span data-stu-id="32e1e-128">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="32e1e-129">Další informace o vlastním Malování naleznete v tématu [Malování a vykreslování vlastního ovládacího prvku](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="32e1e-129">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

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

11. <span data-ttu-id="32e1e-130">Uložte a otestujte svůj ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="32e1e-130">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="32e1e-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32e1e-131">See also</span></span>

- [<span data-ttu-id="32e1e-132">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="32e1e-132">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="32e1e-133">Postupy: Zdědit z třídy ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="32e1e-133">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="32e1e-134">Postupy: Zdědit z třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="32e1e-134">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="32e1e-135">Postupy: Vytváření ovládacích prvků pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32e1e-135">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="32e1e-136">Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32e1e-136">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="32e1e-137">Návod: Dědění z ovládacího prvku model Windows Forms s Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32e1e-137">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="32e1e-138">Návod: Dědění z ovládacího prvku model Windows Forms pomocí vizuáluC#</span><span class="sxs-lookup"><span data-stu-id="32e1e-138">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
