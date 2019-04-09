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
ms.openlocfilehash: 60cba801446d043fa8c0b36d97628e9b0f8df11d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160105"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="376c2-102">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="376c2-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="376c2-103">Aplikace se mají často, příkazy nabídky pro akce, například dlaždice, Cascade a uspořádat, které řídit rozložení otevřít podřízené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="376c2-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="376c2-104">Můžete použít <xref:System.Windows.Forms.Form.LayoutMdi%2A> metody s jedním z <xref:System.Windows.Forms.MdiLayout> hodnot výčtu, chcete-li uspořádat podřízené formuláře MDI na nadřazený formulář.</span><span class="sxs-lookup"><span data-stu-id="376c2-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="376c2-105"><xref:System.Windows.Forms.MdiLayout> Hodnot výčtu zobrazit podřízené formuláře jako CSS, protože vodorovně nebo svisle vedle sebe, nebo jako podřízené formuláře ikony uspořádané podél dolní části formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="376c2-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="376c2-106">Tyto hodnoty mají stejný účinek jako příkazy Windows **sebe**, **zobrazit okna vedle sebe**, **zobrazit okna skládaný**, a **zobrazení plochy** v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="376c2-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="376c2-107">Tyto metody se často používají jako obslužné rutiny událostí, které jsou volány položku nabídky <xref:System.Windows.Forms.Control.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="376c2-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="376c2-108">Tímto způsobem může mít položku nabídky s textem "Cascade Windows" požadovaný účinek na podřízených oken MDI.</span><span class="sxs-lookup"><span data-stu-id="376c2-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="376c2-109">Chcete-li uspořádat podřízené formuláře</span><span class="sxs-lookup"><span data-stu-id="376c2-109">To arrange child forms</span></span>  
  
1.  <span data-ttu-id="376c2-110">V metodě, použijte <xref:System.Windows.Forms.Form.LayoutMdi%2A> metody nastavte <xref:System.Windows.Forms.MdiLayout> výčtu pro nadřazený formulář MDI.</span><span class="sxs-lookup"><span data-stu-id="376c2-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="376c2-111">V následujícím příkladu <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> hodnotu výčtu pro okny podřízenými nadřazený formulář MDI (`Form1`).</span><span class="sxs-lookup"><span data-stu-id="376c2-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="376c2-112">Výčet se používá v kódu během obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost **Cascade Windows** položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="376c2-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
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
    >  <span data-ttu-id="376c2-113">Můžete také uspořádat windows a uspořádáním windows jako ikony tak, že změníte <xref:System.Windows.Forms.MdiLayout> použít hodnotu výčtu.</span><span class="sxs-lookup"><span data-stu-id="376c2-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2.  <span data-ttu-id="376c2-114">Pokud používáte Visual C#, umístěte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="376c2-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="376c2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="376c2-115">See also</span></span>

- [<span data-ttu-id="376c2-116">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="376c2-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="376c2-117">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="376c2-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="376c2-118">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="376c2-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="376c2-119">Postupy: Určení aktivního podřízeného formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="376c2-119">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="376c2-120">Postupy: Odesílání dat do aktivního podřízeného formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="376c2-120">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
