---
title: "Postupy: Přidávání ovládacích prvků do formulářů Windows"
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
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d9075c93181b68828a307924259a9170c046baa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="cda79-102">Postupy: Přidávání ovládacích prvků do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="cda79-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="cda79-103">Většina formulářů jsou navrženy přidáním ovládacích prvků na povrch ve formátu pro definování uživatelského rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="cda79-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="cda79-104">A *řízení* je komponenta ve formuláři použít k zobrazení informací nebo přijímají vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="cda79-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="cda79-105">Další informace o ovládacích prvcích najdete v tématu [ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="cda79-105">For more information about controls, see [Windows Forms Controls](../../../../docs/framework/winforms/controls/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cda79-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="cda79-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cda79-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="cda79-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cda79-108">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cda79-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="cda79-109">K vykreslení ovládacího prvku ve formuláři</span><span class="sxs-lookup"><span data-stu-id="cda79-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="cda79-110">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="cda79-110">Open the form.</span></span> <span data-ttu-id="cda79-111">Další informace najdete v tématu [postupy: zobrazení Windows Forms v návrháři](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="cda79-111">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="cda79-112">V **sada nástrojů**, klikněte na ovládací prvek, který chcete přidat do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="cda79-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="cda79-113">Ve formuláři klikněte na levý horní roh ovládacího prvku na nalezen a přetáhněte ji na místo, kde pravém dolním rohu ovládacího prvku na nalezen.</span><span class="sxs-lookup"><span data-stu-id="cda79-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="cda79-114">Ovládací prvek je přidán do formuláře s zadané umístění a velikost.</span><span class="sxs-lookup"><span data-stu-id="cda79-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cda79-115">Každý ovládací prvek má výchozí velikost definované.</span><span class="sxs-lookup"><span data-stu-id="cda79-115">Each control has a default size defined.</span></span> <span data-ttu-id="cda79-116">Ovládacího prvku do svého formuláře ovládacího prvku výchozí velikost můžete přidat přetažením z **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="cda79-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="cda79-117">Přetáhněte ovládacího prvku na formulář</span><span class="sxs-lookup"><span data-stu-id="cda79-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="cda79-118">Otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="cda79-118">Open the form.</span></span> <span data-ttu-id="cda79-119">Další informace najdete v tématu [postupy: zobrazení Windows Forms v návrháři](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="cda79-119">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="cda79-120">V **sada nástrojů**, klikněte na ovládací prvek a přetáhněte ji do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="cda79-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="cda79-121">Ovládací prvek je přidán do formuláře v zadaném umístění v jeho výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="cda79-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cda79-122">Poklepáním na ovládací prvek v **sada nástrojů** ho přidejte do levého horního rohu formuláře v jeho výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="cda79-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="cda79-123">Můžete také přidat ovládací prvky dynamicky do formuláře za běhu.</span><span class="sxs-lookup"><span data-stu-id="cda79-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="cda79-124">V následujícím příkladu kódu <xref:System.Windows.Forms.TextBox> ovládací prvek bude přidán do formuláře při <xref:System.Windows.Forms.Button> po kliknutí na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="cda79-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cda79-125">Následující postup vyžaduje existenci formulář s **tlačítko** řízení, `Button1`, již umístěné na něm.</span><span class="sxs-lookup"><span data-stu-id="cda79-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="cda79-126">Přidání ovládacího prvku na formulář prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="cda79-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="cda79-127">V metodě, která zpracovává na tlačítko `Click` události v rámci svého formuláře třídy, vložení kódu podobný následujícímu se přidat odkaz na řídicí proměnná, nastavte ovládacího prvku `Location`a přidejte ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cda79-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
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
    >  <span data-ttu-id="cda79-128">Můžete také přidat kód pro inicializaci jiných vlastností ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cda79-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="cda79-129">Mohou být vystaveny místního počítače k ohrožení zabezpečení přes síť odkazem škodlivý `UserControl`.</span><span class="sxs-lookup"><span data-stu-id="cda79-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="cda79-130">To může být pouze o problém v případě osoba se zlými úmysly vytváření škodlivé vlastního ovládacího prvku, za nímž následuje jste omylem ho přidáte do projektu.</span><span class="sxs-lookup"><span data-stu-id="cda79-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda79-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="cda79-131">See Also</span></span>  
 [<span data-ttu-id="cda79-132">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="cda79-132">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="cda79-133">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cda79-133">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="cda79-134">Postupy: Změna velikosti ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cda79-134">How to: Resize Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [<span data-ttu-id="cda79-135">Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cda79-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="cda79-136">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cda79-136">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
