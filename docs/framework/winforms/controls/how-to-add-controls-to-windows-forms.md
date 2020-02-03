---
title: Přidání ovládacích prvků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 560089a23fbcccb0f0d5683a95ad06dd9c59556d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743965"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="6b1a5-102">Postupy: Přidávání ovládacích prvků do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="6b1a5-102">How to: Add Controls to Windows Forms</span></span>

<span data-ttu-id="6b1a5-103">Většina formulářů je navržena přidáním ovládacích prvků na plochu formuláře k definování uživatelského rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="6b1a5-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="6b1a5-104">*Ovládací prvek* je komponenta na formuláři sloužící k zobrazení informací nebo přijetí vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="6b1a5-105">Další informace o ovládacích prvcích naleznete v tématu [model Windows Forms Controls](index.md).</span><span class="sxs-lookup"><span data-stu-id="6b1a5-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>

## <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="6b1a5-106">Nakreslení ovládacího prvku na formuláři</span><span class="sxs-lookup"><span data-stu-id="6b1a5-106">To draw a control on a form</span></span>

1. <span data-ttu-id="6b1a5-107">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-107">Open the form.</span></span> <span data-ttu-id="6b1a5-108">Další informace naleznete v tématu [How to: Display model Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6b1a5-108">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="6b1a5-109">V sadě **nástrojů**klikněte na ovládací prvek, který chcete přidat do formuláře.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-109">In the **Toolbox**, click the control you want to add to your form.</span></span>

3. <span data-ttu-id="6b1a5-110">Ve formuláři klikněte na místo, kde chcete umístit levý horní roh ovládacího prvku, a přetáhněte jej na místo, kde chcete umístit pravý dolní roh ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-110">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>

    <span data-ttu-id="6b1a5-111">Ovládací prvek je přidán do formuláře se zadaným umístěním a velikostí.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-111">The control is added to the form with the specified location and size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6b1a5-112">U každého ovládacího prvku je definována výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-112">Each control has a default size defined.</span></span> <span data-ttu-id="6b1a5-113">Ovládací prvek lze přidat do formuláře ve výchozí velikosti ovládacího prvku přetažením z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-113">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>

## <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="6b1a5-114">Přetažení ovládacího prvku do formuláře</span><span class="sxs-lookup"><span data-stu-id="6b1a5-114">To drag a control to a form</span></span>

1. <span data-ttu-id="6b1a5-115">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-115">Open the form.</span></span> <span data-ttu-id="6b1a5-116">Další informace naleznete v tématu [How to: Display model Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6b1a5-116">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="6b1a5-117">V sadě **nástrojů**klikněte na požadovaný ovládací prvek a přetáhněte ho do formuláře.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-117">In the **Toolbox**, click the control you want and drag it to your form.</span></span>

    <span data-ttu-id="6b1a5-118">Ovládací prvek je přidán do formuláře v zadaném umístění ve výchozí velikosti.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-118">The control is added to the form at the specified location in its default size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6b1a5-119">Můžete dvakrát kliknout na ovládací prvek v **sadě nástrojů** a přidat ho do levého horního rohu formuláře ve výchozí velikosti.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-119">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>

    <span data-ttu-id="6b1a5-120">Ovládací prvky lze také dynamicky přidávat do formuláře za běhu.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-120">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="6b1a5-121">V následujícím příkladu kódu bude ovládací prvek <xref:System.Windows.Forms.TextBox> přidán do formuláře při kliknutí na ovládací prvek <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-121">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6b1a5-122">Následující postup vyžaduje existenci formuláře s ovládacím prvkem **tlačítko** , `Button1`, již je umístěn.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-122">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>

## <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="6b1a5-123">Postup pro přidání ovládacího prvku do formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="6b1a5-123">To add a control to a form programmatically</span></span>

1. <span data-ttu-id="6b1a5-124">V metodě, která zpracovává událost `Click` tlačítka v rámci třídy formuláře, vložte kód podobný následujícímu pro přidání odkazu na proměnnou ovládacího prvku, nastavte `Location`ovládacího prvku a přidejte ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-124">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>

    ```vb
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim MyText As New TextBox()
       MyText.Location = New Point(25, 25)
       Me.Controls.Add(MyText)
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
       TextBox myText = new TextBox();
       myText.Location = new Point(25,25);
       this.Controls.Add (myText);
    }
    ```

    ```cpp
    private:
      System::Void button1_Click(System::Object ^  sender,
        System::EventArgs ^  e)
      {
        TextBox ^ myText = gcnew TextBox();
        myText->Location = Point(25,25);
        this->Controls->Add(myText);
      }
    ```

    > [!NOTE]
    > <span data-ttu-id="6b1a5-125">Můžete také přidat kód pro inicializaci dalších vlastností ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-125">You can also add code to initialize other properties of the control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="6b1a5-126">Místní počítač můžete vystavit bezpečnostnímu riziku prostřednictvím sítě odkazem na škodlivý `UserControl`.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-126">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="6b1a5-127">To by mělo být obavy jenom v případě, že by škodlivá osoba vytvořila škodlivý vlastní ovládací prvek, a pak ji nepřidali do projektu omylem.</span><span class="sxs-lookup"><span data-stu-id="6b1a5-127">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b1a5-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b1a5-128">See also</span></span>

- [<span data-ttu-id="6b1a5-129">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="6b1a5-129">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="6b1a5-130">Postupy: Změna velikosti ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b1a5-130">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="6b1a5-131">Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b1a5-131">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="6b1a5-132">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b1a5-132">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
