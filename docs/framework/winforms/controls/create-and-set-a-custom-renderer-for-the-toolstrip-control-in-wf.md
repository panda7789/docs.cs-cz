---
title: 'Postup: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip'
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
ms.openlocfilehash: 49db0d785155f19b7220ac64011eaf4253aaa7e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182406"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Postupy: Vytvoření a nastavení vlastní zobrazovací jednotky pro ovládací prvek ToolStrip ve Windows Forms
<xref:System.Windows.Forms.ToolStrip>ovládací prvky poskytují snadnou podporu motivům a stylům. Můžete dosáhnout zcela vlastní vzhled a chování (vzhled <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> a chování) nastavením vlastnost nebo <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> vlastnost vlastní vykreslovač.  
  
 Vykreslovače můžete <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.MenuStrip>přiřadit <xref:System.Windows.Forms.ContextMenuStrip>každému <xref:System.Windows.Forms.StatusStrip> jednotlivci , , <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> nebo ovládacímu prvku <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>můžete pomocí vlastnosti ovlivnit všechny objekty nastavením vlastnosti na .  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>vrátí <xref:System.Windows.Forms.ToolStripRenderMode.Custom> pouze v <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> případě, `null`že hodnota není .  
  
### <a name="to-create-a-custom-renderer"></a>Vytvoření vlastního rendereru  
  
1. Prodlužte třídu. <xref:System.Windows.Forms.ToolStripRenderer>  
  
2. Implementovat požadované vlastní vykreslování přepsáním příslušné *on...* členy  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Nastavení vlastního rendereru na aktuální vykreslovač  
  
1. Chcete-li nastavit vlastní <xref:System.Windows.Forms.ToolStrip>vykreslovač pro jednoho , nastavte <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost na vlastní vykreslovač.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Nebo chcete-li nastavit vlastní <xref:System.Windows.Forms.ToolStrip> vykreslovač pro <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> všechny třídy obsažené ve <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vaší <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>aplikaci: Nastavte vlastnost na vlastní vykreslovač a nastavte vlastnost na .  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [ToolStrip – přehled ovládacího prvku](toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Souhrn technologie ToolStrip](toolstrip-technology-summary.md)
