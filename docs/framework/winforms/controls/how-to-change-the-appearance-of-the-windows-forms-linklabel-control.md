---
title: Změna vzhledu ovládacího prvku LinkLabel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
ms.openlocfilehash: 0b38722fb1647ea215c3bb8978dd3f54b300a0e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746628"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="6ee41-102">Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="6ee41-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="6ee41-103">Text zobrazený ovládacím prvkem <xref:System.Windows.Forms.LinkLabel> můžete změnit tak, aby vyhovoval různým účelům.</span><span class="sxs-lookup"><span data-stu-id="6ee41-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="6ee41-104">Například je běžné, že uživateli označit, že se dá text kliknout, nastavením textu, který se má zobrazit v konkrétní barvě podtržením.</span><span class="sxs-lookup"><span data-stu-id="6ee41-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="6ee41-105">Jakmile uživatel klikne na text, změní se barva na jinou barvu.</span><span class="sxs-lookup"><span data-stu-id="6ee41-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="6ee41-106">Pro řízení tohoto chování můžete nastavit pět různých vlastností: vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>.</span><span class="sxs-lookup"><span data-stu-id="6ee41-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="6ee41-107">Změna vzhledu ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="6ee41-107">To change the appearance of a LinkLabel control</span></span>  
  
1. <span data-ttu-id="6ee41-108">Nastavte vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> a <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> na barvy, které chcete.</span><span class="sxs-lookup"><span data-stu-id="6ee41-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="6ee41-109">To lze provést buď programově, nebo v době návrhu v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="6ee41-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2. <span data-ttu-id="6ee41-110">Vlastnost <xref:System.Windows.Forms.LinkLabel.Text%2A> nastavte na příslušný titulek.</span><span class="sxs-lookup"><span data-stu-id="6ee41-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="6ee41-111">To lze provést buď programově, nebo v době návrhu v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="6ee41-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. <span data-ttu-id="6ee41-112">Nastavením vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> určíte, která část popisku bude označena jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="6ee41-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="6ee41-113">Hodnota <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> je reprezentovaná <xref:System.Windows.Forms.LinkArea>, která obsahuje dvě čísla, počáteční pozici znaku a počet znaků.</span><span class="sxs-lookup"><span data-stu-id="6ee41-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="6ee41-114">To lze provést buď programově, nebo v době návrhu v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="6ee41-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. <span data-ttu-id="6ee41-115">Vlastnost <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> nastavte na <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>nebo <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span><span class="sxs-lookup"><span data-stu-id="6ee41-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="6ee41-116">Pokud je nastavená na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, část titulu určená pomocí <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> bude podtržená jenom v případě, že se ukazatel myši nachází na jeho umístění.</span><span class="sxs-lookup"><span data-stu-id="6ee41-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5. <span data-ttu-id="6ee41-117">V obslužné rutině události <xref:System.Windows.Forms.LinkLabel.LinkClicked> nastavte vlastnost <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="6ee41-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="6ee41-118">V případě, že byl odkaz navštíven, je běžné jeho vzhled snadno měnit, obvykle pomocí barvy.</span><span class="sxs-lookup"><span data-stu-id="6ee41-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="6ee41-119">Text se změní na barvu určenou vlastností <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="6ee41-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6ee41-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ee41-120">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [<span data-ttu-id="6ee41-121">Přehled ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="6ee41-121">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="6ee41-122">Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="6ee41-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="6ee41-123">Ovládací prvek LinkLabel</span><span class="sxs-lookup"><span data-stu-id="6ee41-123">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
