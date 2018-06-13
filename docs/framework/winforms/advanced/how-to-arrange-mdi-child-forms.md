---
title: 'Postupy: Uspořádání podřízených formulářů MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: d5c0d24ff8a7188a669c218ce8b0dc66ffa56c47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521024"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="b7de2-102">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="b7de2-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="b7de2-103">Aplikace často, bude mít příkazy nabídky pro akce, například dlaždice Cascade a uspořádat, které řídí rozložení otevřete podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="b7de2-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="b7de2-104">Můžete použít <xref:System.Windows.Forms.Form.LayoutMdi%2A> metoda s jedním z <xref:System.Windows.Forms.MdiLayout> hodnot výčtu ke změně uspořádání podřízených formulářů v MDI nadřazené formuláře.</span><span class="sxs-lookup"><span data-stu-id="b7de2-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="b7de2-105"><xref:System.Windows.Forms.MdiLayout> Hodnot výčtu zobrazení podřízených formulářů jako kaskádových jako vodorovně nebo svisle vedle sebe, nebo jako podřízené formuláře ikony uspořádané podél dolní části formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="b7de2-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="b7de2-106">Tyto hodnoty mají stejný účinek jako příkazy Windows **sebe**, **zobrazit windows vedle sebe**, **zobrazit windows skládaný**, a **zobrazení plochy** , v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b7de2-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="b7de2-107">Tyto metody se často používají jako obslužné rutiny událostí, které jsou volány položku nabídky <xref:System.Windows.Forms.Control.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="b7de2-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="b7de2-108">Tímto způsobem může mít položku nabídky s textem "Cascade Windows" požadované vliv na podřízených oken MDI.</span><span class="sxs-lookup"><span data-stu-id="b7de2-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="b7de2-109">K uspořádání podřízených formulářů</span><span class="sxs-lookup"><span data-stu-id="b7de2-109">To arrange child forms</span></span>  
  
1.  <span data-ttu-id="b7de2-110">Metoda, použijte <xref:System.Windows.Forms.Form.LayoutMdi%2A> metodu a nastavit <xref:System.Windows.Forms.MdiLayout> výčet nadřazeného formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="b7de2-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="b7de2-111">Následující příklad používá <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> hodnota výčtu pro podřízených oken MDI nadřazeného formuláře (`Form1`).</span><span class="sxs-lookup"><span data-stu-id="b7de2-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="b7de2-112">Výčtu se používá v kódu během obslužné rutiny události pro <xref:System.Windows.Forms.Control.Click> události **sebe** položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="b7de2-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b7de2-113">Vám může také dlaždici windows a windows uspořádáním jako ikony změnou <xref:System.Windows.Forms.MdiLayout> použít hodnotu výčtu.</span><span class="sxs-lookup"><span data-stu-id="b7de2-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2.  <span data-ttu-id="b7de2-114">Pokud používáte Visual C#, vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b7de2-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b7de2-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7de2-115">See Also</span></span>  
 [<span data-ttu-id="b7de2-116">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="b7de2-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="b7de2-117">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="b7de2-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="b7de2-118">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="b7de2-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="b7de2-119">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="b7de2-119">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="b7de2-120">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="b7de2-120">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
