---
title: 'Postupy: Vlastní vykreslení ovládacího prvku ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
ms.openlocfilehash: 09d9654bf1a2670c77a4a3db2eae2ed7ab6dbfec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532171"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="76f66-102">Postupy: Vlastní vykreslení ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="76f66-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="76f66-103"><xref:System.Windows.Forms.ToolStrip> Ovládacích prvků mají následující přidružené vykreslování třídy (Malování):</span><span class="sxs-lookup"><span data-stu-id="76f66-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
-   <span data-ttu-id="76f66-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> poskytuje vzhled a stylu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="76f66-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
-   <span data-ttu-id="76f66-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> poskytuje vzhled a stylu systému Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="76f66-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
-   <span data-ttu-id="76f66-106"><xref:System.Windows.Forms.ToolStripRenderer> je abstraktní základní třída pro jiné třídy dvě vykreslování.</span><span class="sxs-lookup"><span data-stu-id="76f66-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="76f66-107">Pro vlastní kreslení (také označované jako vlastník kreslení) <xref:System.Windows.Forms.ToolStrip>, můžete přepsat jednu z tříd zobrazovací jednotky a změnit aspekt logiky vykreslování.</span><span class="sxs-lookup"><span data-stu-id="76f66-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="76f66-108">Následující postupy popisují různé aspekty vlastní kreslení.</span><span class="sxs-lookup"><span data-stu-id="76f66-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="76f66-109">Chcete-li přepnout mezi zadaný pro vykreslování</span><span class="sxs-lookup"><span data-stu-id="76f66-109">To switch between the provided renderers</span></span>  
  
-   <span data-ttu-id="76f66-110">Nastavte <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost, která má <xref:System.Windows.Forms.ToolStripRenderMode> hodnotu, kterou chcete.</span><span class="sxs-lookup"><span data-stu-id="76f66-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="76f66-111">S <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, statické <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> určuje zobrazovací jednotky pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="76f66-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="76f66-112">Další hodnoty <xref:System.Windows.Forms.ToolStripRenderMode> jsou <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, a <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span><span class="sxs-lookup"><span data-stu-id="76f66-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="76f66-113">Ke změně přímo Microsoft Office – styl ohraničení</span><span class="sxs-lookup"><span data-stu-id="76f66-113">To change the Microsoft Office–style borders to straight</span></span>  
  
-   <span data-ttu-id="76f66-114">Přepsání <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale nebude volat základní třídy.</span><span class="sxs-lookup"><span data-stu-id="76f66-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76f66-115">Je verze této metody pro <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, a <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span><span class="sxs-lookup"><span data-stu-id="76f66-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="76f66-116">Chcete-li změnit ProfessionalColorTable</span><span class="sxs-lookup"><span data-stu-id="76f66-116">To change the ProfessionalColorTable</span></span>  
  
-   <span data-ttu-id="76f66-117">Přepsání <xref:System.Windows.Forms.ProfessionalColorTable> a barvy chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="76f66-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="76f66-118">Chcete-li změnit vykreslování pro všechny ovládací prvky ToolStrip ve vaší aplikaci</span><span class="sxs-lookup"><span data-stu-id="76f66-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1.  <span data-ttu-id="76f66-119">Použití <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> vlastnost zvolte jeden ze zadané pro vykreslování.</span><span class="sxs-lookup"><span data-stu-id="76f66-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2.  <span data-ttu-id="76f66-120">Použití <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> přiřadit vlastní zobrazovací jednotky.</span><span class="sxs-lookup"><span data-stu-id="76f66-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3.  <span data-ttu-id="76f66-121">Ujistěte se, že <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> nastavena na výchozí hodnotu <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="76f66-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="76f66-122">Chcete-li vypnout barvy Microsoft Office pro celou aplikaci</span><span class="sxs-lookup"><span data-stu-id="76f66-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
-   <span data-ttu-id="76f66-123">Nastavit <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> k `false`.</span><span class="sxs-lookup"><span data-stu-id="76f66-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="76f66-124">Chcete-li vypnout barvy Microsoft Office pro jeden ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="76f66-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
-   <span data-ttu-id="76f66-125">Pomocí kódu podobně jako následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="76f66-125">Use code similar to the following code example.</span></span>  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="76f66-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="76f66-126">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 [<span data-ttu-id="76f66-127">Ovládací prvky s vestavěnou podporou vykreslování vlastníkem</span><span class="sxs-lookup"><span data-stu-id="76f66-127">Controls with Built-In Owner-Drawing Support</span></span>](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [<span data-ttu-id="76f66-128">Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="76f66-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
 [<span data-ttu-id="76f66-129">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="76f66-129">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
