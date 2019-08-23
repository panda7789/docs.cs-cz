---
title: 'Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms'
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
ms.openlocfilehash: c354ace3a7d3ce43f549dd1295a85fbee004eb22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929731"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms
<xref:System.Windows.Forms.ToolStrip>ovládací prvky umožňují snadnou podporu motivů a stylů. Můžete dosáhnout úplného vlastního vzhledu a chování (vzhled a chování) nastavením <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnosti <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> nebo vlastnosti na vlastní zobrazovací jednotku.  
  
 Můžete přiřadit zobrazovací jednotky každému <xref:System.Windows.Forms.ToolStrip>jednotlivci <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> nebo <xref:System.Windows.Forms.StatusStrip> ovládacímu prvku nebo <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> můžete použít vlastnost pro ovlivnění všech objektů nastavením vlastnosti na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>Vrátí <xref:System.Windows.Forms.ToolStripRenderMode.Custom> pouze v případě, že <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> hodnota `null`není.  
  
### <a name="to-create-a-custom-renderer"></a>Vytvoření vlastního zobrazovací jednotky  
  
1. <xref:System.Windows.Forms.ToolStripRenderer> Zvětšete třídu.  
  
2. Implementujte požadované vlastní vykreslování přepsáním vhodného *na...* členy  
  
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
  
1. Chcete-li nastavit vlastní vykreslovací modul pro <xref:System.Windows.Forms.ToolStrip>jeden, <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> nastavte vlastnost na vlastní zobrazovací jednotku.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Nebo chcete-li nastavit vlastní vykreslovací modul pro <xref:System.Windows.Forms.ToolStrip> všechny třídy obsažené v aplikaci: Nastavte vlastnost na vlastní zobrazovací jednotku a <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> nastavte vlastnost na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>hodnotu. <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>  
  
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
