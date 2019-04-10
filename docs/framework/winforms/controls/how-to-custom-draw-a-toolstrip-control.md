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
ms.openlocfilehash: 9b3d6b9391971d4c2d012345b96c2ed64d33a998
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311042"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="acb57-102">Postupy: Vlastní vykreslení ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="acb57-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="acb57-103"><xref:System.Windows.Forms.ToolStrip> Ovládací prvky mají následující související vykreslování třídy (Malování):</span><span class="sxs-lookup"><span data-stu-id="acb57-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> <span data-ttu-id="acb57-104">poskytuje vzhled a styl operačního systému.</span><span class="sxs-lookup"><span data-stu-id="acb57-104">provides the appearance and style of your operating system.</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> <span data-ttu-id="acb57-105">poskytuje vzhled a stylu společnosti Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="acb57-105">provides the appearance and style of Microsoft Office.</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> <span data-ttu-id="acb57-106">je abstraktní základní třída pro jiné třídy dva vykreslování.</span><span class="sxs-lookup"><span data-stu-id="acb57-106">is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="acb57-107">Pro vlastní vykreslování (označované také jako vlastník draw) <xref:System.Windows.Forms.ToolStrip>, můžete přepsat jedné ze tříd nástroj pro vykreslování a změnit aspekt logiku pro vykreslení.</span><span class="sxs-lookup"><span data-stu-id="acb57-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="acb57-108">Následující postupy popisují různé aspekty vlastního vykreslení.</span><span class="sxs-lookup"><span data-stu-id="acb57-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="acb57-109">Přepínat mezi zadaná renderery</span><span class="sxs-lookup"><span data-stu-id="acb57-109">To switch between the provided renderers</span></span>  
  
-   <span data-ttu-id="acb57-110">Nastavte <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost <xref:System.Windows.Forms.ToolStripRenderMode> hodnotu, kterou chcete.</span><span class="sxs-lookup"><span data-stu-id="acb57-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="acb57-111">S <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, statické <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> určuje zobrazovací jednotky pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="acb57-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="acb57-112">Ostatní hodnoty <xref:System.Windows.Forms.ToolStripRenderMode> jsou <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, a <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span><span class="sxs-lookup"><span data-stu-id="acb57-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="acb57-113">Chcete-li změnit Microsoft Office – styl ohraničení přímo</span><span class="sxs-lookup"><span data-stu-id="acb57-113">To change the Microsoft Office–style borders to straight</span></span>  
  
-   <span data-ttu-id="acb57-114">Přepsat <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale Nevolejte základní třídu.</span><span class="sxs-lookup"><span data-stu-id="acb57-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acb57-115">Je dostupná verze této metody pro <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, a <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span><span class="sxs-lookup"><span data-stu-id="acb57-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="acb57-116">Chcete-li změnit professionalcolortable –</span><span class="sxs-lookup"><span data-stu-id="acb57-116">To change the ProfessionalColorTable</span></span>  
  
-   <span data-ttu-id="acb57-117">Přepsat <xref:System.Windows.Forms.ProfessionalColorTable> a změnit barvy chcete.</span><span class="sxs-lookup"><span data-stu-id="acb57-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="acb57-118">Chcete-li změnit vykreslení u všech ovládacích prvcích ToolStrip ve vaší aplikaci</span><span class="sxs-lookup"><span data-stu-id="acb57-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1. <span data-ttu-id="acb57-119">Použití <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> vlastnost na volbu jednoho ze zadané zobrazovací jednotku.</span><span class="sxs-lookup"><span data-stu-id="acb57-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2. <span data-ttu-id="acb57-120">Použití <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> přiřadit vlastní zobrazovací jednotky.</span><span class="sxs-lookup"><span data-stu-id="acb57-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3. <span data-ttu-id="acb57-121">Ujistěte se, že <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> je nastavena na výchozí hodnotu <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="acb57-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="acb57-122">Chcete-li vypnout barvy Microsoft Office pro celou aplikaci</span><span class="sxs-lookup"><span data-stu-id="acb57-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
-   <span data-ttu-id="acb57-123">Nastavte <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> k `false`.</span><span class="sxs-lookup"><span data-stu-id="acb57-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="acb57-124">Chcete-li vypnout barvy Microsoft Office pro jeden ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="acb57-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
-   <span data-ttu-id="acb57-125">Použijte kód podobně jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="acb57-125">Use code similar to the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="acb57-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acb57-126">See also</span></span>

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [<span data-ttu-id="acb57-127">Ovládací prvky s vestavěnou podporou vykreslování vlastníkem</span><span class="sxs-lookup"><span data-stu-id="acb57-127">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="acb57-128">Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="acb57-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [<span data-ttu-id="acb57-129">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="acb57-129">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
