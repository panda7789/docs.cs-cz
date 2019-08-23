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
ms.openlocfilehash: 7e4d5a80961ae37951251dffa30cb8e75b20be27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955107"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="62c6f-102">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="62c6f-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="62c6f-103">Aplikace budou často obsahovat příkazy nabídky pro akce, jako je například dlaždice, kaskády a uspořádání, které řídí rozložení otevřených podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="62c6f-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="62c6f-104">Můžete použít <xref:System.Windows.Forms.Form.LayoutMdi%2A> metodu s jednou <xref:System.Windows.Forms.MdiLayout> z hodnot výčtu pro změnu uspořádání podřízených formulářů v nadřazeném formuláři MDI.</span><span class="sxs-lookup"><span data-stu-id="62c6f-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="62c6f-105">Hodnoty <xref:System.Windows.Forms.MdiLayout> výčtu zobrazují podřízené formuláře jako kaskádové, jak vodorovně nebo svisle vedle sebe, nebo jako ikony podřízeného formuláře uspořádané podél dolní části formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="62c6f-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="62c6f-106">Tyto hodnoty mají stejný účinek jako příkazy Windows na sebe, zobrazují okna **vedle**sebe, **zobrazují okna skládané**a **zobrazují plochu**, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="62c6f-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="62c6f-107">Tyto metody jsou často používány jako obslužné rutiny událostí volané <xref:System.Windows.Forms.Control.Click> událostmi položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="62c6f-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="62c6f-108">Tímto způsobem může mít položka nabídky s textem "kaskádová okna" v podřízených oknech MDI požadovaný vliv.</span><span class="sxs-lookup"><span data-stu-id="62c6f-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="62c6f-109">Uspořádání podřízených formulářů</span><span class="sxs-lookup"><span data-stu-id="62c6f-109">To arrange child forms</span></span>  
  
1. <span data-ttu-id="62c6f-110">V metodě použijte <xref:System.Windows.Forms.Form.LayoutMdi%2A> metodu k <xref:System.Windows.Forms.MdiLayout> nastavení výčtu nadřazeného formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="62c6f-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="62c6f-111">V následujícím příkladu je použita <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> hodnota výčtu pro podřízená okna nadřazeného formuláře MDI (`Form1`).</span><span class="sxs-lookup"><span data-stu-id="62c6f-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="62c6f-112">Výčet se používá v kódu během obslužné rutiny události pro <xref:System.Windows.Forms.Control.Click> událost položky nabídky oken na **sebe** .</span><span class="sxs-lookup"><span data-stu-id="62c6f-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
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
    > <span data-ttu-id="62c6f-113">Můžete také uspořádat okna a uspořádat okna jako ikony změnou <xref:System.Windows.Forms.MdiLayout> použité hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="62c6f-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2. <span data-ttu-id="62c6f-114">Pokud používáte vizuál C#, vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="62c6f-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="62c6f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62c6f-115">See also</span></span>

- [<span data-ttu-id="62c6f-116">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="62c6f-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="62c6f-117">Postupy: Vytvoření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="62c6f-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="62c6f-118">Postupy: Vytvořit podřízené formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="62c6f-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="62c6f-119">Postupy: Zjistit aktivní podřízenou položku MDI</span><span class="sxs-lookup"><span data-stu-id="62c6f-119">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="62c6f-120">Postupy: Odeslat data do aktivního podřízeného rozhraní MDI</span><span class="sxs-lookup"><span data-stu-id="62c6f-120">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
