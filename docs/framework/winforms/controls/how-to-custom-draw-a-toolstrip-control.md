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
ms.openlocfilehash: 810a680a1a9d9065e80ed87453a728fe628a953d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935359"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Postupy: Vlastní vykreslení ovládacího prvku ToolStrip
<xref:System.Windows.Forms.ToolStrip> Ovládací prvky mají následující přidružené třídy vykreslování (malování):  
  
- <xref:System.Windows.Forms.ToolStripSystemRenderer>poskytuje vzhled a styl vašeho operačního systému.  
  
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>poskytuje vzhled a styl systém Microsoft Office.  
  
- <xref:System.Windows.Forms.ToolStripRenderer>je abstraktní základní třída pro ostatní dvě třídy vykreslování.  
  
 Pro vlastní vykreslování (označované také jako Draw Draw) <xref:System.Windows.Forms.ToolStrip>a můžete přepsat jednu z tříd Renderer a změnit aspekt logiky vykreslování.  
  
 Následující postupy popisují různé aspekty vlastního vykreslování.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Přepínání mezi poskytnutými zobrazovacími jednotkami  
  
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> Nastavte vlastnost<xref:System.Windows.Forms.ToolStripRenderMode> na hodnotu, kterou chcete.  
  
     Pomocí <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>nástroje statická <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> určuje zobrazovací jednotku pro vaši aplikaci. Ostatní hodnoty <xref:System.Windows.Forms.ToolStripRenderMode> jsou <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>a. <xref:System.Windows.Forms.ToolStripRenderMode.System>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Změna systém Microsoft Office – ohraničení stylu na rovnou  
  
- Přepište <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale Nevolejte základní třídu.  
  
> [!NOTE]
> Existuje verze této metody pro <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>a <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.  
  
### <a name="to-change-the-professionalcolortable"></a>Změna ProfessionalColorTable  
  
- Přepište <xref:System.Windows.Forms.ProfessionalColorTable> a změňte požadované barvy.  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>Změna vykreslování pro všechny ovládací prvky ToolStrip v aplikaci  
  
1. <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> Pomocí vlastnosti vyberte jednu z poskytnutých zobrazovacích objektů.  
  
2. Slouží <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> k přiřazení vlastního zobrazovací jednotky.  
  
3. Ujistěte se <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> , že je nastavená výchozí <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>hodnota.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Vypnutí systém Microsoft Officech barev pro celou aplikaci  
  
- Nastavte <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> na `false`.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Vypnutí systém Microsoft Officech barev pro jeden ovládací prvek ToolStrip  
  
- Použijte kód podobný následujícímu příkladu kódu.  
  
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
- [Postupy: Vytvoření a nastavení vlastního zobrazovací jednotky pro ovládací prvek ToolStrip v model Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
