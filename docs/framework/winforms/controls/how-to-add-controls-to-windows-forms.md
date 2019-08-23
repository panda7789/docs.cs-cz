---
title: 'Postupy: Přidávání ovládacích prvků do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 7ee603fa5350ef81c6d32d2f22119bbe526295df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912615"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="94a45-102">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94a45-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="94a45-103">Většina formulářů je navržena přidáním ovládacích prvků na plochu formuláře k definování uživatelského rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="94a45-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="94a45-104">*Ovládací prvek* je komponenta na formuláři sloužící k zobrazení informací nebo přijetí vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="94a45-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="94a45-105">Další informace o ovládacích prvcích naleznete v tématu [model Windows Forms Controls](index.md).</span><span class="sxs-lookup"><span data-stu-id="94a45-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>

## <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="94a45-106">Nakreslení ovládacího prvku na formuláři</span><span class="sxs-lookup"><span data-stu-id="94a45-106">To draw a control on a form</span></span>

1. <span data-ttu-id="94a45-107">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="94a45-107">Open the form.</span></span> <span data-ttu-id="94a45-108">Další informace najdete v tématu [jak: Zobrazit model Windows Forms v Návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="94a45-108">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="94a45-109">V sadě **nástrojů**klikněte na ovládací prvek, který chcete přidat do formuláře.</span><span class="sxs-lookup"><span data-stu-id="94a45-109">In the **Toolbox**, click the control you want to add to your form.</span></span>

3. <span data-ttu-id="94a45-110">Ve formuláři klikněte na místo, kde chcete umístit levý horní roh ovládacího prvku, a přetáhněte jej na místo, kde chcete umístit pravý dolní roh ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94a45-110">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>

     <span data-ttu-id="94a45-111">Ovládací prvek je přidán do formuláře se zadaným umístěním a velikostí.</span><span class="sxs-lookup"><span data-stu-id="94a45-111">The control is added to the form with the specified location and size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="94a45-112">U každého ovládacího prvku je definována výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="94a45-112">Each control has a default size defined.</span></span> <span data-ttu-id="94a45-113">Ovládací prvek lze přidat do formuláře ve výchozí velikosti ovládacího prvku přetažením z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="94a45-113">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>

## <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="94a45-114">Přetažení ovládacího prvku do formuláře</span><span class="sxs-lookup"><span data-stu-id="94a45-114">To drag a control to a form</span></span>

1. <span data-ttu-id="94a45-115">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="94a45-115">Open the form.</span></span> <span data-ttu-id="94a45-116">Další informace najdete v tématu [jak: Zobrazit model Windows Forms v Návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="94a45-116">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="94a45-117">V sadě **nástrojů**klikněte na požadovaný ovládací prvek a přetáhněte ho do formuláře.</span><span class="sxs-lookup"><span data-stu-id="94a45-117">In the **Toolbox**, click the control you want and drag it to your form.</span></span>

     <span data-ttu-id="94a45-118">Ovládací prvek je přidán do formuláře v zadaném umístění ve výchozí velikosti.</span><span class="sxs-lookup"><span data-stu-id="94a45-118">The control is added to the form at the specified location in its default size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="94a45-119">Můžete dvakrát kliknout na ovládací prvek v **sadě nástrojů** a přidat ho do levého horního rohu formuláře ve výchozí velikosti.</span><span class="sxs-lookup"><span data-stu-id="94a45-119">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>

     <span data-ttu-id="94a45-120">Ovládací prvky lze také dynamicky přidávat do formuláře za běhu.</span><span class="sxs-lookup"><span data-stu-id="94a45-120">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="94a45-121">V následujícím příkladu <xref:System.Windows.Forms.TextBox> kódu bude ovládací prvek přidán do formuláře <xref:System.Windows.Forms.Button> při kliknutí na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="94a45-121">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>

    > [!NOTE]
    > <span data-ttu-id="94a45-122">Následující postup vyžaduje existenci formuláře s ovládacím prvkem `Button1` **tlačítko** , na kterém je již umístěn.</span><span class="sxs-lookup"><span data-stu-id="94a45-122">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>

## <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="94a45-123">Postup pro přidání ovládacího prvku do formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="94a45-123">To add a control to a form programmatically</span></span>

1. <span data-ttu-id="94a45-124">V metodě, která zpracovává `Click` událost tlačítka v rámci třídy formuláře, vložte kód podobný následujícímu pro přidání odkazu na proměnnou ovládacího prvku, nastavení `Location`ovládacího prvku a přidání ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94a45-124">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>

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
    > <span data-ttu-id="94a45-125">Můžete také přidat kód pro inicializaci dalších vlastností ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94a45-125">You can also add code to initialize other properties of the control.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="94a45-126">Místní počítač můžete vystavit bezpečnostnímu riziku prostřednictvím sítě, a to tak, že `UserControl`se na něj odkazuje škodlivá aktivita.</span><span class="sxs-lookup"><span data-stu-id="94a45-126">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="94a45-127">To by mělo být obavy jenom v případě, že by škodlivá osoba vytvořila škodlivý vlastní ovládací prvek, a pak ji nepřidali do projektu omylem.</span><span class="sxs-lookup"><span data-stu-id="94a45-127">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="94a45-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94a45-128">See also</span></span>

- [<span data-ttu-id="94a45-129">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="94a45-129">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="94a45-130">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94a45-130">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="94a45-131">Postupy: Změnit velikost ovládacích prvků na model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94a45-131">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="94a45-132">Postupy: Nastavení textu zobrazovaného ovládacím prvkem model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94a45-132">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="94a45-133">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94a45-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
