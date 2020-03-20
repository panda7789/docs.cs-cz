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
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Postupy: Vlastní vykreslení ovládacího prvku ToolStrip
Ovládací <xref:System.Windows.Forms.ToolStrip> prvky mají následující přidružené vykreslování (malování) třídy:  
  
- <xref:System.Windows.Forms.ToolStripSystemRenderer>poskytuje vzhled a styl operačního systému.  
  
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>poskytuje vzhled a styl sady Microsoft Office.  
  
- <xref:System.Windows.Forms.ToolStripRenderer>je abstraktní základní třída pro další dvě třídy vykreslování.  
  
 Chcete-li vlastní kreslení (označované <xref:System.Windows.Forms.ToolStrip>také jako owner draw) a , můžete přepsat jednu z tříd vykreslovače a změnit aspekt logiky vykreslování.  
  
 Následující postupy popisují různé aspekty vlastního výkresu.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Přepínání mezi dodávacími renderery  
  
- Nastavte <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost na <xref:System.Windows.Forms.ToolStripRenderMode> požadovanou hodnotu.  
  
     Pomocí <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>aplikace <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> určuje statický vykreslovací modul pro vaši aplikaci. Ostatní hodnoty <xref:System.Windows.Forms.ToolStripRenderMode> jsou <xref:System.Windows.Forms.ToolStripRenderMode.Custom> <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, <xref:System.Windows.Forms.ToolStripRenderMode.System>a .  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Změna ohraničení stylu Microsoft Office na rovné  
  
- Přepište <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale nevolejte základní třídu.  
  
> [!NOTE]
> Existuje verze této metody <xref:System.Windows.Forms.ToolStripRenderer>pro <xref:System.Windows.Forms.ToolStripSystemRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>a .  
  
### <a name="to-change-the-professionalcolortable"></a>Změna tabulky ProfessionalColorTable  
  
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
  
1. Pomocí <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> vlastnosti vyberte jeden z poskytnutých rendererů.  
  
2. Slouží <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> k přiřazení vlastního vykreslovače.  
  
3. Ujistěte <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> se, že je <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>nastavena na výchozí hodnotu .  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Vypnutí barev sady Microsoft Office pro celou aplikaci  
  
- <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> Nastaveno `false`na .  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Vypnutí ovládacího prvku Microsoft Office pro jeden ovládací prvek ToolStrip  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [Ovládací prvky s vestavěnou podporou vykreslování vlastníkem](controls-with-built-in-owner-drawing-support.md)
- [Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [ToolStrip – přehled ovládacího prvku](toolstrip-control-overview-windows-forms.md)
