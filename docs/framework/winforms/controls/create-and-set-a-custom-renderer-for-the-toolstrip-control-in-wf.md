---
title: 'Postupy: vytvoření a nastavení vlastního zobrazovacího modulu pro ovládací prvek ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: ad5ced42754fba6a714452220dd824c4f54fb5e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743418"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Postupy: Vytvoření a nastavení vlastní zobrazovací jednotky pro ovládací prvek ToolStrip ve Windows Forms
ovládací prvky <xref:System.Windows.Forms.ToolStrip> poskytují snadnou podporu motivů a stylů. Zcela vlastní vzhled a chování (vzhled a chování) můžete dosáhnout nastavením vlastnosti <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> nebo vlastnosti <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> na vlastní zobrazovací jednotku.  
  
 Můžete přiřadit zobrazovací jednotky ke každému jednotlivému <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>nebo ovládacímu prvku <xref:System.Windows.Forms.StatusStrip>, nebo můžete použít vlastnost <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> pro ovlivnění všech objektů nastavením vlastnosti <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vrátí <xref:System.Windows.Forms.ToolStripRenderMode.Custom> pouze v případě, že hodnota <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> není `null`.  
  
### <a name="to-create-a-custom-renderer"></a>Vytvoření vlastního zobrazovací jednotky  
  
1. Rozšíří třídu <xref:System.Windows.Forms.ToolStripRenderer>.  
  
2. Implementujte požadované vlastní vykreslování přepsáním vhodného *na...* členové  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Nastavení vlastního zobrazovacího modulu jako aktuálního zobrazovací jednotky  
  
1. Chcete-li nastavit vlastní zobrazovací modul pro jednu <xref:System.Windows.Forms.ToolStrip>, nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> na vlastní zobrazovací jednotku.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Nebo chcete-li nastavit vlastní vykreslovací modul pro všechny třídy <xref:System.Windows.Forms.ToolStrip> obsažené v aplikaci: nastavte vlastnost <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> na vlastní zobrazovací jednotku a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Shrnutí technologie ToolStrip](toolstrip-technology-summary.md)
