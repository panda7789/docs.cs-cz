---
title: Změna vzhledu ovládacího prvku Popisek odkazů
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
ms.openlocfilehash: df66991289373a05fc7c27b7768a96643e3bbae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142127"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="4b697-102">Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="4b697-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="4b697-103">Text zobrazený <xref:System.Windows.Forms.LinkLabel> ovládacím prvkem můžete změnit tak, aby vyhovoval různým účelům.</span><span class="sxs-lookup"><span data-stu-id="4b697-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="4b697-104">Například je běžnou praxí oznamovat uživateli, že na text lze klepnout nastavením textu tak, aby se zobrazoval v určité barvě s podtržením.</span><span class="sxs-lookup"><span data-stu-id="4b697-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="4b697-105">Po kliknutí na text se barva změní na jinou barvu.</span><span class="sxs-lookup"><span data-stu-id="4b697-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="4b697-106">Chcete-li toto chování řídit, můžete <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>nastavit <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>pět <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> různých vlastností: , , a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4b697-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="4b697-107">Změna vzhledu ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="4b697-107">To change the appearance of a LinkLabel control</span></span>  
  
1. <span data-ttu-id="4b697-108">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> vlastnosti a <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> na požadované barvy.</span><span class="sxs-lookup"><span data-stu-id="4b697-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="4b697-109">To lze provést programově nebo v době návrhu v okně **Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="4b697-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
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
  
2. <span data-ttu-id="4b697-110">Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost na příslušný titulek.</span><span class="sxs-lookup"><span data-stu-id="4b697-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="4b697-111">To lze provést programově nebo v době návrhu v okně **Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="4b697-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. <span data-ttu-id="4b697-112">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnost k určení, která část titulku bude označena jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="4b697-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="4b697-113">Hodnota <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> je reprezentována <xref:System.Windows.Forms.LinkArea> obsahující dvě čísla, počáteční pozici znaku a počet znaků.</span><span class="sxs-lookup"><span data-stu-id="4b697-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="4b697-114">To lze provést programově nebo v době návrhu v okně **Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="4b697-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. <span data-ttu-id="4b697-115">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> vlastnost <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>, nebo .</span><span class="sxs-lookup"><span data-stu-id="4b697-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="4b697-116">Pokud je nastavena na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, část <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> titulku určena bude podtržena pouze tehdy, když ukazatel spočívá na něm.</span><span class="sxs-lookup"><span data-stu-id="4b697-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5. <span data-ttu-id="4b697-117">V <xref:System.Windows.Forms.LinkLabel.LinkClicked> obslužné <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> rutině události nastavte vlastnost na `true`.</span><span class="sxs-lookup"><span data-stu-id="4b697-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="4b697-118">Když byl odkaz navštíven, je běžnou praxí změnit jeho vzhled nějakým způsobem, obvykle podle barvy.</span><span class="sxs-lookup"><span data-stu-id="4b697-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="4b697-119">Text se změní na barvu <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> určenou vlastností.</span><span class="sxs-lookup"><span data-stu-id="4b697-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4b697-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b697-120">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [<span data-ttu-id="4b697-121">LinkLabel – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4b697-121">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="4b697-122">Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="4b697-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="4b697-123">Ovládací prvek LinkLabel</span><span class="sxs-lookup"><span data-stu-id="4b697-123">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
