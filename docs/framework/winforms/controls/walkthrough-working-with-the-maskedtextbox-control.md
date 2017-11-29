---
title: "Návod: Práce s ovládacím prvkem MaskedTextBox"
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
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06b8ffd2bda9597198d94c99a785c59cc7cc052e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="41924-102">Návod: Práce s ovládacím prvkem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="41924-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="41924-103">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="41924-103">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="41924-104">Inicializace <xref:System.Windows.Forms.MaskedTextBox> ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="41924-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
-   <span data-ttu-id="41924-105">Pomocí <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> obslužné rutiny události pro upozornění uživatele, když znak není v souladu s maskou</span><span class="sxs-lookup"><span data-stu-id="41924-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
-   <span data-ttu-id="41924-106">Přiřazení typu k <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> vlastnost a pomocí <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> obslužné rutiny události pro upozornění uživatele, když se pokoušíte potvrdit hodnota není platná pro typ</span><span class="sxs-lookup"><span data-stu-id="41924-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="41924-107">Vytvoření projektu a přidání ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="41924-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="41924-108">Přidání ovládacího prvku MaskedTextBox do svého formuláře</span><span class="sxs-lookup"><span data-stu-id="41924-108">To add a MaskedTextBox control to your form</span></span>  
  
1.  <span data-ttu-id="41924-109">Otevřít formulář, na kterém chcete umístit <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="41924-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2.  <span data-ttu-id="41924-110">Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> řídit z **sada nástrojů** do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="41924-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3.  <span data-ttu-id="41924-111">Klikněte pravým tlačítkem na ovládací prvek a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="41924-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="41924-112">V **vlastnosti** vyberte **maska** vlastnost a klikněte na tlačítko **...**  (tečkami) vedle názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="41924-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4.  <span data-ttu-id="41924-113">V **vstupní maska** dialogové okno, vyberte **krátkého data** masku a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="41924-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5.  <span data-ttu-id="41924-114">V **vlastnosti** sadu okno <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="41924-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="41924-115">Tato vlastnost způsobí, že krátký zvukový signál na zvukových pokaždé, když se uživatel pokusí o vstupní znak, který je v rozporu s definicí masky.</span><span class="sxs-lookup"><span data-stu-id="41924-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="41924-116">Souhrn znaků, které podporuje vlastnost maska, najdete v části poznámky <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="41924-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="41924-117">Upozornění uživatele vstupních chyb</span><span class="sxs-lookup"><span data-stu-id="41924-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="41924-118">Přidat bublinách tip pro vstup odmítnutých maska</span><span class="sxs-lookup"><span data-stu-id="41924-118">Add a balloon tip for rejected mask input</span></span>  
  
1.  <span data-ttu-id="41924-119">Vraťte se do **sada nástrojů** a přidejte <xref:System.Windows.Forms.ToolTip> do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="41924-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2.  <span data-ttu-id="41924-120">Vytvoření obslužné rutiny události pro <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> událost, která se vyvolá <xref:System.Windows.Forms.ToolTip> když dojde k chybě vstupu.</span><span class="sxs-lookup"><span data-stu-id="41924-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="41924-121">Pět sekund, nebo dokud uživatel klikne, zůstává viditelná balloon špičky.</span><span class="sxs-lookup"><span data-stu-id="41924-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="41924-122">Upozornit uživatele na typ, který není platný</span><span class="sxs-lookup"><span data-stu-id="41924-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="41924-123">Přidat bublinách tip pro typy neplatná data.</span><span class="sxs-lookup"><span data-stu-id="41924-123">Add a balloon tip for invalid data types</span></span>  
  
1.  <span data-ttu-id="41924-124">V svého formuláře <xref:System.Windows.Forms.Form.Load> obslužné rutiny události, přiřadit <xref:System.Type> objekt reprezentující <xref:System.DateTime> typ, který má <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> vlastnost:</span><span class="sxs-lookup"><span data-stu-id="41924-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  <span data-ttu-id="41924-125">Přidání obslužné rutiny události pro <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> událostí:</span><span class="sxs-lookup"><span data-stu-id="41924-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="41924-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="41924-126">See Also</span></span>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [<span data-ttu-id="41924-127">MaskedTextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="41924-127">MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)
