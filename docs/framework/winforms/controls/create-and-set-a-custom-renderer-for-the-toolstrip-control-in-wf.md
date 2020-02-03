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
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="ef143-102">Postupy: Vytvoření a nastavení vlastní zobrazovací jednotky pro ovládací prvek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef143-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="ef143-103">ovládací prvky <xref:System.Windows.Forms.ToolStrip> poskytují snadnou podporu motivů a stylů.</span><span class="sxs-lookup"><span data-stu-id="ef143-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="ef143-104">Zcela vlastní vzhled a chování (vzhled a chování) můžete dosáhnout nastavením vlastnosti <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> nebo vlastnosti <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> na vlastní zobrazovací jednotku.</span><span class="sxs-lookup"><span data-stu-id="ef143-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="ef143-105">Můžete přiřadit zobrazovací jednotky ke každému jednotlivému <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>nebo ovládacímu prvku <xref:System.Windows.Forms.StatusStrip>, nebo můžete použít vlastnost <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> pro ovlivnění všech objektů nastavením vlastnosti <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef143-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef143-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vrátí <xref:System.Windows.Forms.ToolStripRenderMode.Custom> pouze v případě, že hodnota <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> není `null`.</span><span class="sxs-lookup"><span data-stu-id="ef143-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="ef143-107">Vytvoření vlastního zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="ef143-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="ef143-108">Rozšíří třídu <xref:System.Windows.Forms.ToolStripRenderer>.</span><span class="sxs-lookup"><span data-stu-id="ef143-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="ef143-109">Implementujte požadované vlastní vykreslování přepsáním vhodného *na...*</span><span class="sxs-lookup"><span data-stu-id="ef143-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="ef143-110">členy</span><span class="sxs-lookup"><span data-stu-id="ef143-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="ef143-111">Nastavení vlastního zobrazovacího modulu jako aktuálního zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="ef143-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="ef143-112">Chcete-li nastavit vlastní zobrazovací modul pro jednu <xref:System.Windows.Forms.ToolStrip>, nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> na vlastní zobrazovací jednotku.</span><span class="sxs-lookup"><span data-stu-id="ef143-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="ef143-113">Nebo chcete-li nastavit vlastní vykreslovací modul pro všechny třídy <xref:System.Windows.Forms.ToolStrip> obsažené v aplikaci: nastavte vlastnost <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> na vlastní zobrazovací jednotku a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="ef143-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ef143-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef143-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="ef143-115">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ef143-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="ef143-116">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ef143-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="ef143-117">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ef143-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
