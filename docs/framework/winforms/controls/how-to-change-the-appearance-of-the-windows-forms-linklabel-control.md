---
title: 'Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel'
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
ms.openlocfilehash: be2f6e8e10d9f9b23b4f57fa696f1fb88c4726c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105024"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="692e9-102">Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="692e9-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="692e9-103">Můžete změnit text, zobrazený <xref:System.Windows.Forms.LinkLabel> ovládacího prvku tak, aby odpovídala různé účely.</span><span class="sxs-lookup"><span data-stu-id="692e9-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="692e9-104">Například je běžnou praxí do značí, že text dá kliknout nastavením text, který se zobrazí v určité barvy s podtržení.</span><span class="sxs-lookup"><span data-stu-id="692e9-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="692e9-105">Po kliknutí text, barva se změní na jinou barvu.</span><span class="sxs-lookup"><span data-stu-id="692e9-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="692e9-106">A řídit tak toto chování, můžete nastavit různé vlastnosti pět: <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="692e9-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="692e9-107">Chcete-li změnit vzhled ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="692e9-107">To change the appearance of a LinkLabel control</span></span>  
  
1.  <span data-ttu-id="692e9-108">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> a <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> vlastností požadované barvy.</span><span class="sxs-lookup"><span data-stu-id="692e9-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="692e9-109">To lze provést buď programově, nebo v době návrhu v **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="692e9-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
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
  
2.  <span data-ttu-id="692e9-110">Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnosti k odpovídající titulek.</span><span class="sxs-lookup"><span data-stu-id="692e9-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="692e9-111">To lze provést buď programově, nebo v době návrhu v **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="692e9-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  <span data-ttu-id="692e9-112">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> a určí, které části popisek bude uveden jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="692e9-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="692e9-113"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Hodnota je vyjádřena pomocí <xref:System.Windows.Forms.LinkArea> obsahující dvě čísla, počáteční pozici znaku a počet znaků.</span><span class="sxs-lookup"><span data-stu-id="692e9-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="692e9-114">To lze provést buď programově, nebo v době návrhu v **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="692e9-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  <span data-ttu-id="692e9-115">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> vlastnost <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, nebo <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span><span class="sxs-lookup"><span data-stu-id="692e9-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="692e9-116">Pokud je nastavena na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, část titulek určené <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> bude podtržené pouze při umístění ukazatele myši na něj.</span><span class="sxs-lookup"><span data-stu-id="692e9-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5.  <span data-ttu-id="692e9-117">V <xref:System.Windows.Forms.LinkLabel.LinkClicked> nastavena obslužná rutina události, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="692e9-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="692e9-118">Při odkazu po navštívení, je obvyklé, chcete-li změnit její vzhled nějakým způsobem, obvykle pomocí barev.</span><span class="sxs-lookup"><span data-stu-id="692e9-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="692e9-119">Text se změní barva určená <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="692e9-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="692e9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="692e9-120">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [<span data-ttu-id="692e9-121">Přehled ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="692e9-121">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="692e9-122">Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="692e9-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="692e9-123">Ovládací prvek LinkLabel</span><span class="sxs-lookup"><span data-stu-id="692e9-123">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
