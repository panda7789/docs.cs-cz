---
title: Přidání ovládacích prvků
description: Naučte se, jak nakreslit ovládací prvek ve formuláři Windows. Ovládací prvek je komponenta na formuláři, kterou můžete použít k zobrazení informací nebo přijetí vstupu uživatele.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: d9ab0d78fa0153cce20fb17d22f6e9e781229ece
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325883"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="ffbf3-104">Postupy: Přidávání ovládacích prvků do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="ffbf3-104">How to: Add Controls to Windows Forms</span></span>

<span data-ttu-id="ffbf3-105">Většina formulářů je navržena přidáním ovládacích prvků na plochu formuláře k definování uživatelského rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="ffbf3-105">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="ffbf3-106">*Ovládací prvek* je komponenta na formuláři sloužící k zobrazení informací nebo přijetí vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-106">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="ffbf3-107">Další informace o ovládacích prvcích naleznete v tématu [model Windows Forms Controls](index.md).</span><span class="sxs-lookup"><span data-stu-id="ffbf3-107">For more information about controls, see [Windows Forms Controls](index.md).</span></span>

## <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="ffbf3-108">Nakreslení ovládacího prvku na formuláři</span><span class="sxs-lookup"><span data-stu-id="ffbf3-108">To draw a control on a form</span></span>

1. <span data-ttu-id="ffbf3-109">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-109">Open the form.</span></span> <span data-ttu-id="ffbf3-110">Další informace naleznete v tématu [How to: Display model Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ffbf3-110">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="ffbf3-111">V sadě **nástrojů**klikněte na ovládací prvek, který chcete přidat do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-111">In the **Toolbox**, click the control you want to add to your form.</span></span>

3. <span data-ttu-id="ffbf3-112">Ve formuláři klikněte na místo, kde chcete umístit levý horní roh ovládacího prvku, a přetáhněte jej na místo, kde chcete umístit pravý dolní roh ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-112">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>

    <span data-ttu-id="ffbf3-113">Ovládací prvek je přidán do formuláře se zadaným umístěním a velikostí.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-113">The control is added to the form with the specified location and size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ffbf3-114">U každého ovládacího prvku je definována výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-114">Each control has a default size defined.</span></span> <span data-ttu-id="ffbf3-115">Ovládací prvek lze přidat do formuláře ve výchozí velikosti ovládacího prvku přetažením z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-115">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>

## <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="ffbf3-116">Přetažení ovládacího prvku do formuláře</span><span class="sxs-lookup"><span data-stu-id="ffbf3-116">To drag a control to a form</span></span>

1. <span data-ttu-id="ffbf3-117">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-117">Open the form.</span></span> <span data-ttu-id="ffbf3-118">Další informace naleznete v tématu [How to: Display model Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ffbf3-118">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="ffbf3-119">V sadě **nástrojů**klikněte na požadovaný ovládací prvek a přetáhněte ho do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-119">In the **Toolbox**, click the control you want and drag it to your form.</span></span>

    <span data-ttu-id="ffbf3-120">Ovládací prvek je přidán do formuláře v zadaném umístění ve výchozí velikosti.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-120">The control is added to the form at the specified location in its default size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ffbf3-121">Můžete dvakrát kliknout na ovládací prvek v **sadě nástrojů** a přidat ho do levého horního rohu formuláře ve výchozí velikosti.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-121">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>

    <span data-ttu-id="ffbf3-122">Ovládací prvky lze také dynamicky přidávat do formuláře za běhu.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-122">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="ffbf3-123">V následujícím příkladu kódu <xref:System.Windows.Forms.TextBox> bude ovládací prvek přidán do formuláře při <xref:System.Windows.Forms.Button> kliknutí na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-123">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ffbf3-124">Následující postup vyžaduje existenci formuláře s ovládacím prvkem **tlačítko** , `Button1` na kterém je již umístěn.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-124">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>

## <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="ffbf3-125">Postup pro přidání ovládacího prvku do formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="ffbf3-125">To add a control to a form programmatically</span></span>

1. <span data-ttu-id="ffbf3-126">V metodě, která zpracovává `Click` Událost tlačítka v rámci třídy formuláře, vložte kód podobný následujícímu pro přidání odkazu na proměnnou ovládacího prvku, nastavení ovládacího prvku `Location` a přidání ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-126">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>

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
    > <span data-ttu-id="ffbf3-127">Můžete také přidat kód pro inicializaci dalších vlastností ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-127">You can also add code to initialize other properties of the control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ffbf3-128">Místní počítač můžete vystavit bezpečnostnímu riziku prostřednictvím sítě, a to tak, že se na něj odkazuje škodlivá aktivita `UserControl` .</span><span class="sxs-lookup"><span data-stu-id="ffbf3-128">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="ffbf3-129">To by mělo být obavy jenom v případě, že by škodlivá osoba vytvořila škodlivý vlastní ovládací prvek, a pak ji nepřidali do projektu omylem.</span><span class="sxs-lookup"><span data-stu-id="ffbf3-129">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffbf3-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffbf3-130">See also</span></span>

- [<span data-ttu-id="ffbf3-131">Ovládací prvky model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ffbf3-131">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="ffbf3-132">Postupy: Změna velikosti ovládacích prvků ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="ffbf3-132">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="ffbf3-133">Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ffbf3-133">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="ffbf3-134">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ffbf3-134">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
