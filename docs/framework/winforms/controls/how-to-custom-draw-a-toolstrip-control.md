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
ms.openlocfilehash: a9f603efdb4b4a5f68154da9c6a8bd05b55b8f46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182215"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="f4a87-102">Postupy: Vlastní vykreslení ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f4a87-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="f4a87-103">Ovládací <xref:System.Windows.Forms.ToolStrip> prvky mají následující přidružené vykreslování (malování) třídy:</span><span class="sxs-lookup"><span data-stu-id="f4a87-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
- <span data-ttu-id="f4a87-104"><xref:System.Windows.Forms.ToolStripSystemRenderer>poskytuje vzhled a styl operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f4a87-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
- <span data-ttu-id="f4a87-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer>poskytuje vzhled a styl sady Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="f4a87-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
- <span data-ttu-id="f4a87-106"><xref:System.Windows.Forms.ToolStripRenderer>je abstraktní základní třída pro další dvě třídy vykreslování.</span><span class="sxs-lookup"><span data-stu-id="f4a87-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="f4a87-107">Chcete-li vlastní kreslení (označované <xref:System.Windows.Forms.ToolStrip>také jako owner draw) a , můžete přepsat jednu z tříd vykreslovače a změnit aspekt logiky vykreslování.</span><span class="sxs-lookup"><span data-stu-id="f4a87-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="f4a87-108">Následující postupy popisují různé aspekty vlastního výkresu.</span><span class="sxs-lookup"><span data-stu-id="f4a87-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="f4a87-109">Přepínání mezi dodávacími renderery</span><span class="sxs-lookup"><span data-stu-id="f4a87-109">To switch between the provided renderers</span></span>  
  
- <span data-ttu-id="f4a87-110">Nastavte <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost na <xref:System.Windows.Forms.ToolStripRenderMode> požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f4a87-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="f4a87-111">Pomocí <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>aplikace <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> určuje statický vykreslovací modul pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f4a87-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="f4a87-112">Ostatní hodnoty <xref:System.Windows.Forms.ToolStripRenderMode> jsou <xref:System.Windows.Forms.ToolStripRenderMode.Custom> <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, <xref:System.Windows.Forms.ToolStripRenderMode.System>a .</span><span class="sxs-lookup"><span data-stu-id="f4a87-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="f4a87-113">Změna ohraničení stylu Microsoft Office na rovné</span><span class="sxs-lookup"><span data-stu-id="f4a87-113">To change the Microsoft Office–style borders to straight</span></span>  
  
- <span data-ttu-id="f4a87-114">Přepište <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale nevolejte základní třídu.</span><span class="sxs-lookup"><span data-stu-id="f4a87-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4a87-115">Existuje verze této metody <xref:System.Windows.Forms.ToolStripRenderer>pro <xref:System.Windows.Forms.ToolStripSystemRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>a .</span><span class="sxs-lookup"><span data-stu-id="f4a87-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="f4a87-116">Změna tabulky ProfessionalColorTable</span><span class="sxs-lookup"><span data-stu-id="f4a87-116">To change the ProfessionalColorTable</span></span>  
  
- <span data-ttu-id="f4a87-117">Přepište <xref:System.Windows.Forms.ProfessionalColorTable> a změňte požadované barvy.</span><span class="sxs-lookup"><span data-stu-id="f4a87-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="f4a87-118">Změna vykreslování pro všechny ovládací prvky ToolStrip v aplikaci</span><span class="sxs-lookup"><span data-stu-id="f4a87-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1. <span data-ttu-id="f4a87-119">Pomocí <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> vlastnosti vyberte jeden z poskytnutých rendererů.</span><span class="sxs-lookup"><span data-stu-id="f4a87-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2. <span data-ttu-id="f4a87-120">Slouží <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> k přiřazení vlastního vykreslovače.</span><span class="sxs-lookup"><span data-stu-id="f4a87-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3. <span data-ttu-id="f4a87-121">Ujistěte <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> se, že je <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>nastavena na výchozí hodnotu .</span><span class="sxs-lookup"><span data-stu-id="f4a87-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="f4a87-122">Vypnutí barev sady Microsoft Office pro celou aplikaci</span><span class="sxs-lookup"><span data-stu-id="f4a87-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
- <span data-ttu-id="f4a87-123"><xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> Nastaveno `false`na .</span><span class="sxs-lookup"><span data-stu-id="f4a87-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="f4a87-124">Vypnutí ovládacího prvku Microsoft Office pro jeden ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f4a87-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
- <span data-ttu-id="f4a87-125">Použijte kód podobný následujícímu příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f4a87-125">Use code similar to the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4a87-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4a87-126">See also</span></span>

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [<span data-ttu-id="f4a87-127">Ovládací prvky s vestavěnou podporou vykreslování vlastníkem</span><span class="sxs-lookup"><span data-stu-id="f4a87-127">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="f4a87-128">Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4a87-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [<span data-ttu-id="f4a87-129">ToolStrip – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f4a87-129">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
