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
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="364a1-102">Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="364a1-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="364a1-103"><xref:System.Windows.Forms.ToolStrip>ovládací prvky umožňují snadnou podporu motivů a stylů.</span><span class="sxs-lookup"><span data-stu-id="364a1-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="364a1-104">Můžete dosáhnout úplného vlastního vzhledu a chování (vzhled a chování) nastavením <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnosti <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> nebo vlastnosti na vlastní zobrazovací jednotku.</span><span class="sxs-lookup"><span data-stu-id="364a1-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="364a1-105">Můžete přiřadit zobrazovací jednotky každému <xref:System.Windows.Forms.ToolStrip>jednotlivci <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> nebo <xref:System.Windows.Forms.StatusStrip> ovládacímu prvku nebo <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> můžete použít vlastnost pro ovlivnění všech objektů nastavením vlastnosti na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="364a1-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="364a1-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>Vrátí <xref:System.Windows.Forms.ToolStripRenderMode.Custom> pouze v případě, že <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> hodnota `null`není.</span><span class="sxs-lookup"><span data-stu-id="364a1-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="364a1-107">Vytvoření vlastního zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="364a1-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="364a1-108"><xref:System.Windows.Forms.ToolStripRenderer> Zvětšete třídu.</span><span class="sxs-lookup"><span data-stu-id="364a1-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="364a1-109">Implementujte požadované vlastní vykreslování přepsáním vhodného *na...*</span><span class="sxs-lookup"><span data-stu-id="364a1-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="364a1-110">členy</span><span class="sxs-lookup"><span data-stu-id="364a1-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="364a1-111">Nastavení vlastního zobrazovacího modulu jako aktuálního zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="364a1-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="364a1-112">Chcete-li nastavit vlastní vykreslovací modul pro <xref:System.Windows.Forms.ToolStrip>jeden, <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> nastavte vlastnost na vlastní zobrazovací jednotku.</span><span class="sxs-lookup"><span data-stu-id="364a1-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="364a1-113">Nebo chcete-li nastavit vlastní vykreslovací modul pro <xref:System.Windows.Forms.ToolStrip> všechny třídy obsažené v aplikaci: Nastavte vlastnost na vlastní zobrazovací jednotku a <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> nastavte vlastnost na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>hodnotu. <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="364a1-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="364a1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="364a1-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="364a1-115">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="364a1-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="364a1-116">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="364a1-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="364a1-117">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="364a1-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
