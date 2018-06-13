---
title: 'Postupy: Vytvoření a nastavení vlastní zobrazovací jednotky pro ovládací prvek ToolStrip ve Windows Forms'
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
ms.openlocfilehash: 0b7a77a4a923065cba8c7ea366826f7b04126f11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527171"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Postupy: Vytvoření a nastavení vlastní zobrazovací jednotky pro ovládací prvek ToolStrip ve Windows Forms
<xref:System.Windows.Forms.ToolStrip> ovládací prvky snadno podporu předáte motivů a stylů. Zcela vlastní vzhled a chování (vzhled a chování) můžete dosáhnout nastavením buď <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost nebo <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> vlastnost, která má vlastní zobrazovací jednotky.  
  
 Pro každého uživatele můžete přiřadit pro vykreslování <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, nebo <xref:System.Windows.Forms.StatusStrip> ovládací prvek, nebo můžete použít <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> vlastnost, která má vliv na všechny objekty nastavením <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> Vrátí <xref:System.Windows.Forms.ToolStripRenderMode.Custom> pouze v případě hodnotu <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> není `null`.  
  
### <a name="to-create-a-custom-renderer"></a>Chcete-li vytvořit vlastní zobrazovací jednotky  
  
1.  Rozšíření <xref:System.Windows.Forms.ToolStripRenderer> třídy.  
  
2.  Implementace potřeby vlastní vykreslení přepsáním odpovídající *na...* členové  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Chcete-li nastavit vlastní zobrazovací jednotky jako aktuální zobrazovací jednotky  
  
1.  Chcete-li nastavit vlastní zobrazovací jednotky pro jednu <xref:System.Windows.Forms.ToolStrip>, nastavte <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost, která má vlastní zobrazovací jednotky.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  Nebo nastavit vlastní zobrazovací jednotky pro všechny <xref:System.Windows.Forms.ToolStrip> třídy, které jsou obsažené v aplikaci: nastavte <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> do vlastní zobrazovací jednotky a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost, která má <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Shrnutí technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
