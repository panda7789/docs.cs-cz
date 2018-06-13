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
ms.openlocfilehash: e1bb0ecba6fd8ddf66c6debb90ef4dd94641a97e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531483"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a><span data-ttu-id="92e62-102">Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="92e62-102">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="92e62-103">Můžete změnit textu zobrazovaného <xref:System.Windows.Forms.LinkLabel> ovládacího prvku tak, aby vyhovovala různé účely.</span><span class="sxs-lookup"><span data-stu-id="92e62-103">You can change the text displayed by the <xref:System.Windows.Forms.LinkLabel> control to suit a variety of purposes.</span></span> <span data-ttu-id="92e62-104">Například je běžnou praxí informuje tak uživatele, že text sloužící nastavením text, který se zobrazí v konkrétní barvy s podtržení.</span><span class="sxs-lookup"><span data-stu-id="92e62-104">For example, it is common practice to indicate to the user that text can be clicked by setting the text to appear in a specific color with an underline.</span></span> <span data-ttu-id="92e62-105">Po kliknutí na text, barva se změní na jinou barvu.</span><span class="sxs-lookup"><span data-stu-id="92e62-105">After the user clicks the text, the color changes to a different color.</span></span> <span data-ttu-id="92e62-106">Za účelem řízení, můžete nastavit různé vlastnosti pět: <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="92e62-106">To control this behavior, you can set five different properties: the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> properties.</span></span>  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a><span data-ttu-id="92e62-107">Změna vzhledu ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="92e62-107">To change the appearance of a LinkLabel control</span></span>  
  
1.  <span data-ttu-id="92e62-108">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> a <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> vlastnosti pro barev, které chcete.</span><span class="sxs-lookup"><span data-stu-id="92e62-108">Set the <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> and <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> properties to the colors you want.</span></span>  
  
     <span data-ttu-id="92e62-109">To můžete provést buď programově, nebo v době návrhu v **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="92e62-109">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
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
  
2.  <span data-ttu-id="92e62-110">Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost, která má odpovídající titulek.</span><span class="sxs-lookup"><span data-stu-id="92e62-110">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
     <span data-ttu-id="92e62-111">To můžete provést buď programově, nebo v době návrhu v **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="92e62-111">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  <span data-ttu-id="92e62-112">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnosti k určení, které části titulek bude uveden jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="92e62-112">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
     <span data-ttu-id="92e62-113"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Hodnota je reprezentována pomocí <xref:System.Windows.Forms.LinkArea> obsahující dvě čísla, počáteční pozice znaku a počet znaků.</span><span class="sxs-lookup"><span data-stu-id="92e62-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented with a <xref:System.Windows.Forms.LinkArea> containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="92e62-114">To můžete provést buď programově, nebo v době návrhu v **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="92e62-114">This can be done either programmatically or at design time in the **Properties** window.</span></span>  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  <span data-ttu-id="92e62-115">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> vlastnost <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, nebo <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span><span class="sxs-lookup"><span data-stu-id="92e62-115">Set the <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> property to <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, or <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.</span></span>  
  
     <span data-ttu-id="92e62-116">Pokud je nastaven na hodnotu <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, součástí titulek dáno <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> bude podtržené pouze při umístění ukazatele myši na něm.</span><span class="sxs-lookup"><span data-stu-id="92e62-116">If it is set to <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, the part of the caption determined by <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> will only be underlined when the pointer rests on it.</span></span>  
  
5.  <span data-ttu-id="92e62-117">V <xref:System.Windows.Forms.LinkLabel.LinkClicked> nastavit popisovač události <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="92e62-117">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="92e62-118">Při navštívil odkaz je běžnou praxí změnit její vzhled nějakým způsobem, obvykle pomocí barev.</span><span class="sxs-lookup"><span data-stu-id="92e62-118">When a link has been visited, it is common practice to change its appearance in some way, usually by color.</span></span> <span data-ttu-id="92e62-119">Text se změní na barvu určeného <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="92e62-119">The text will change to the color specified by the <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92e62-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="92e62-120">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>  
 [<span data-ttu-id="92e62-121">Přehled ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="92e62-121">LinkLabel Control Overview</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [<span data-ttu-id="92e62-122">Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="92e62-122">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [<span data-ttu-id="92e62-123">Ovládací prvek LinkLabel</span><span class="sxs-lookup"><span data-stu-id="92e62-123">LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
