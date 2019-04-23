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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311042"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Postupy: Vlastní vykreslení ovládacího prvku ToolStrip
<xref:System.Windows.Forms.ToolStrip> Ovládací prvky mají následující související vykreslování třídy (Malování):  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> poskytuje vzhled a styl operačního systému.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> poskytuje vzhled a stylu společnosti Microsoft Office.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> je abstraktní základní třída pro jiné třídy dva vykreslování.  
  
 Pro vlastní vykreslování (označované také jako vlastník draw) <xref:System.Windows.Forms.ToolStrip>, můžete přepsat jedné ze tříd nástroj pro vykreslování a změnit aspekt logiku pro vykreslení.  
  
 Následující postupy popisují různé aspekty vlastního vykreslení.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Přepínat mezi zadaná renderery  
  
-   Nastavte <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost <xref:System.Windows.Forms.ToolStripRenderMode> hodnotu, kterou chcete.  
  
     S <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, statické <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> určuje zobrazovací jednotky pro vaši aplikaci. Ostatní hodnoty <xref:System.Windows.Forms.ToolStripRenderMode> jsou <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, a <xref:System.Windows.Forms.ToolStripRenderMode.System>.  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Chcete-li změnit Microsoft Office – styl ohraničení přímo  
  
-   Přepsat <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale Nevolejte základní třídu.  
  
> [!NOTE]
>  Je dostupná verze této metody pro <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, a <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.  
  
### <a name="to-change-the-professionalcolortable"></a>Chcete-li změnit professionalcolortable –  
  
-   Přepsat <xref:System.Windows.Forms.ProfessionalColorTable> a změnit barvy chcete.  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>Chcete-li změnit vykreslení u všech ovládacích prvcích ToolStrip ve vaší aplikaci  
  
1. Použití <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> vlastnost na volbu jednoho ze zadané zobrazovací jednotku.  
  
2. Použití <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> přiřadit vlastní zobrazovací jednotky.  
  
3. Ujistěte se, že <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> je nastavena na výchozí hodnotu <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Chcete-li vypnout barvy Microsoft Office pro celou aplikaci  
  
-   Nastavte <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> k `false`.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Chcete-li vypnout barvy Microsoft Office pro jeden ovládací prvek ToolStrip  
  
-   Použijte kód podobně jako v následujícím příkladu kódu.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [Ovládací prvky s vestavěnou podporou vykreslování vlastníkem](controls-with-built-in-owner-drawing-support.md)
- [Postupy: Vytvoření a nastavení vlastního Rendereru pro ovládací prvek ToolStrip ve Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
