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
ms.openlocfilehash: 72b5931a79284a93a4e0fdf3cb2cc3b03157f5f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106480"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="40349-102">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40349-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="40349-103">Většinou forem jsou navržené tak, že přidáte ovládací prvky na plochu formuláře k definování uživatelského rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="40349-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="40349-104">A *ovládací prvek* je součást na formulář pro zobrazení informací ani nebude přijímat uživatelský vstup.</span><span class="sxs-lookup"><span data-stu-id="40349-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="40349-105">Další informace o ovládacích prvcích najdete v tématu [ovládacích prvků Windows Forms](index.md).</span><span class="sxs-lookup"><span data-stu-id="40349-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40349-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="40349-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="40349-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="40349-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="40349-108">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="40349-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="40349-109">K nakreslení ovládacího prvku ve formuláři</span><span class="sxs-lookup"><span data-stu-id="40349-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="40349-110">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="40349-110">Open the form.</span></span> <span data-ttu-id="40349-111">Další informace najdete v tématu [jak: Zobrazení formulářů Windows v návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="40349-111">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="40349-112">V **nástrojů**, klepněte na ovládací prvek, který chcete přidat do formuláře.</span><span class="sxs-lookup"><span data-stu-id="40349-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="40349-113">Ve formuláři klikněte na požadované levého horního rohu ovládacího prvku, který má být umístěná a přetáhněte ji na požadované místo pravého dolního rohu ovládacího prvku, který má být umístěná.</span><span class="sxs-lookup"><span data-stu-id="40349-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="40349-114">Ovládací prvek je přidán do formuláře pomocí zadaného umístění a velikost.</span><span class="sxs-lookup"><span data-stu-id="40349-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="40349-115">Každý ovládací prvek má definovaný výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="40349-115">Each control has a default size defined.</span></span> <span data-ttu-id="40349-116">Můžete přidat ovládací prvek do formuláře ve výchozí velikost ovládacího prvku přetažením z **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="40349-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="40349-117">Přetáhněte ovládací prvek do formuláře</span><span class="sxs-lookup"><span data-stu-id="40349-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="40349-118">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="40349-118">Open the form.</span></span> <span data-ttu-id="40349-119">Další informace najdete v tématu [jak: Zobrazení formulářů Windows v návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="40349-119">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="40349-120">V **nástrojů**, klepněte na ovládací prvek a přetáhněte ji do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="40349-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="40349-121">Ovládací prvek je přidán do formuláře v zadaném umístění v její výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="40349-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="40349-122">Dvakrát kliknete na ovládací prvek v **nástrojů** se přidá do levého horního rohu formuláře v její výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="40349-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="40349-123">Můžete také přidat ovládací prvky dynamicky do formuláře v době běhu.</span><span class="sxs-lookup"><span data-stu-id="40349-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="40349-124">V následujícím příkladu kódu <xref:System.Windows.Forms.TextBox> ovládací prvek bude přidán do formuláře při <xref:System.Windows.Forms.Button> dojde ke kliknutí na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="40349-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="40349-125">Následující postup vyžaduje existenci formulář s **tlačítko** ovládacího prvku, `Button1`, již umístěné na něj.</span><span class="sxs-lookup"><span data-stu-id="40349-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="40349-126">Přidání ovládacího prvku na formulář prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="40349-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="40349-127">V metodě, která zpracovává tlačítka `Click` událostí v rámci třídy formuláře, vložit kód podobný následujícímu se přidat odkaz na řídicí proměnná nastavit u tohoto prvku `Location`a přidejte ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="40349-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
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
    >  <span data-ttu-id="40349-128">Můžete také přidat kód pro inicializaci jiné vlastnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="40349-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="40349-129">Místního počítače k ohrožení zabezpečení prostřednictvím sítě může být odkazem škodlivý `UserControl`.</span><span class="sxs-lookup"><span data-stu-id="40349-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="40349-130">To může být pouze v případě nežádoucí osoba vytváření škodlivé vlastního ovládacího prvku, za nímž následuje omylem přidání do projektu žádný problém.</span><span class="sxs-lookup"><span data-stu-id="40349-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40349-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40349-131">See also</span></span>

- [<span data-ttu-id="40349-132">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40349-132">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="40349-133">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40349-133">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="40349-134">Postupy: Změna velikosti ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40349-134">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="40349-135">Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40349-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="40349-136">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40349-136">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
