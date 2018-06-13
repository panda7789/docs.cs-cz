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
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Postupy: Vlastní vykreslení ovládacího prvku ToolStrip
<xref:System.Windows.Forms.ToolStrip> Ovládacích prvků mají následující přidružené vykreslování třídy (Malování):  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> poskytuje vzhled a stylu operačního systému.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> poskytuje vzhled a stylu systému Microsoft Office.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> je abstraktní základní třída pro jiné třídy dvě vykreslování.  
  
 Pro vlastní kreslení (také označované jako vlastník kreslení) <xref:System.Windows.Forms.ToolStrip>, můžete přepsat jednu z tříd zobrazovací jednotky a změnit aspekt logiky vykreslování.  
  
 Následující postupy popisují různé aspekty vlastní kreslení.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Chcete-li přepnout mezi zadaný pro vykreslování  
  
-   Nastavte <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost, která má <xref:System.Windows.Forms.ToolStripRenderMode> hodnotu, kterou chcete.  
  
     S <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, statické <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> určuje zobrazovací jednotky pro vaši aplikaci. Další hodnoty <xref:System.Windows.Forms.ToolStripRenderMode> jsou <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, a <xref:System.Windows.Forms.ToolStripRenderMode.System>.  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Ke změně přímo Microsoft Office – styl ohraničení  
  
-   Přepsání <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale nebude volat základní třídy.  
  
> [!NOTE]
>  Je verze této metody pro <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, a <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.  
  
### <a name="to-change-the-professionalcolortable"></a>Chcete-li změnit ProfessionalColorTable  
  
-   Přepsání <xref:System.Windows.Forms.ProfessionalColorTable> a barvy chcete změnit.  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>Chcete-li změnit vykreslování pro všechny ovládací prvky ToolStrip ve vaší aplikaci  
  
1.  Použití <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> vlastnost zvolte jeden ze zadané pro vykreslování.  
  
2.  Použití <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> přiřadit vlastní zobrazovací jednotky.  
  
3.  Ujistěte se, že <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> nastavena na výchozí hodnotu <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Chcete-li vypnout barvy Microsoft Office pro celou aplikaci  
  
-   Nastavit <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> k `false`.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Chcete-li vypnout barvy Microsoft Office pro jeden ovládací prvek ToolStrip  
  
-   Pomocí kódu podobně jako následující příklad kódu.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 [Ovládací prvky s vestavěnou podporou vykreslování vlastníkem](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
