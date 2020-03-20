---
title: 'Návod: Práce s ovládacím prvkem MaskedTextBox'
ms.date: 03/30/2017
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
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182061"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="c3687-102">Návod: Práce s ovládacím prvkem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c3687-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="c3687-103">Mezi úkoly znázorněné v tomto návodu patří:</span><span class="sxs-lookup"><span data-stu-id="c3687-103">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="c3687-104">Inicializace ovládacího <xref:System.Windows.Forms.MaskedTextBox> prvku</span><span class="sxs-lookup"><span data-stu-id="c3687-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
- <span data-ttu-id="c3687-105">Použití <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> obslužné rutiny události k upozornění uživatele, když znak neodpovídá masce</span><span class="sxs-lookup"><span data-stu-id="c3687-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
- <span data-ttu-id="c3687-106">Přiřazení typu vlastnosti <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> a použití <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> obslužné rutiny události k upozornění uživatele, když hodnota, kterou se pokouší tepotvrzení, není pro daný typ platná.</span><span class="sxs-lookup"><span data-stu-id="c3687-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="c3687-107">Vytvoření projektu a přidání ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c3687-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="c3687-108">Přidání ovládacího prvku MaskedTextBox do formuláře</span><span class="sxs-lookup"><span data-stu-id="c3687-108">To add a MaskedTextBox control to your form</span></span>  
  
1. <span data-ttu-id="c3687-109">Otevřete formulář, na který <xref:System.Windows.Forms.MaskedTextBox> chcete ovládací prvek umístit.</span><span class="sxs-lookup"><span data-stu-id="c3687-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2. <span data-ttu-id="c3687-110">Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> ovládací prvek z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c3687-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3. <span data-ttu-id="c3687-111">Klepněte pravým tlačítkem myši na ovládací prvek a zvolte **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c3687-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="c3687-112">V okně **Vlastnosti** vyberte vlastnost **Maska** a klepněte na tlačítko **...** (tři tečky) vedle názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3687-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4. <span data-ttu-id="c3687-113">V dialogovém okně **Vstupní maska** vyberte masku **Krátké datum** a klepněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3687-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5. <span data-ttu-id="c3687-114">V okně **Vlastnosti** <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> nastavte `true`vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="c3687-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="c3687-115">Tato vlastnost způsobí, že krátké pípnutí zvuk pokaždé, když se uživatel pokusí zadat znak, který porušuje definici masky.</span><span class="sxs-lookup"><span data-stu-id="c3687-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="c3687-116">Souhrn znaků, které podporuje vlastnost Mask, naleznete v <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> části Poznámky vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3687-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="c3687-117">Upozornit uživatele na vstupní chyby</span><span class="sxs-lookup"><span data-stu-id="c3687-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="c3687-118">Přidání tipu pozice pro odmítnutý vstup masky</span><span class="sxs-lookup"><span data-stu-id="c3687-118">Add a balloon tip for rejected mask input</span></span>  
  
1. <span data-ttu-id="c3687-119">Vraťte se do **panelu nástrojů** a přidejte <xref:System.Windows.Forms.ToolTip> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c3687-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2. <span data-ttu-id="c3687-120">Vytvořte obslužnou rutinu <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> události, která vyvolá při výskytu <xref:System.Windows.Forms.ToolTip> vstupní chyby.</span><span class="sxs-lookup"><span data-stu-id="c3687-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="c3687-121">Špička pozice zůstane viditelná po dobu pěti sekund nebo dokud na ni uživatel neklikne.</span><span class="sxs-lookup"><span data-stu-id="c3687-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
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
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="c3687-122">Upozornit uživatele na typ, který není platný</span><span class="sxs-lookup"><span data-stu-id="c3687-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="c3687-123">Přidání tipu pozice pro neplatné datové typy</span><span class="sxs-lookup"><span data-stu-id="c3687-123">Add a balloon tip for invalid data types</span></span>  
  
1. <span data-ttu-id="c3687-124"><xref:System.Windows.Forms.Form.Load> V obslužné rutině <xref:System.Type> události formuláře <xref:System.DateTime> přiřaďte objekt představující typ vlastnosti ovládacího <xref:System.Windows.Forms.MaskedTextBox> <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> prvku:</span><span class="sxs-lookup"><span data-stu-id="c3687-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
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
  
2. <span data-ttu-id="c3687-125">Přidejte obslužnou rutinu <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> události pro událost:</span><span class="sxs-lookup"><span data-stu-id="c3687-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3687-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3687-126">See also</span></span>

- <xref:System.Windows.Forms.MaskedTextBox>
- [<span data-ttu-id="c3687-127">MaskedTextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="c3687-127">MaskedTextBox Control</span></span>](maskedtextbox-control-windows-forms.md)
