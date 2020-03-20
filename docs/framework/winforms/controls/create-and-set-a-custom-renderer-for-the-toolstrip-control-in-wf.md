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
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="28bf4-102">Postupy: Vytvoření a nastavení vlastní zobrazovací jednotky pro ovládací prvek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="28bf4-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="28bf4-103"><xref:System.Windows.Forms.ToolStrip>ovládací prvky poskytují snadnou podporu motivům a stylům.</span><span class="sxs-lookup"><span data-stu-id="28bf4-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="28bf4-104">Můžete dosáhnout zcela vlastní vzhled a chování (vzhled <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> a chování) nastavením vlastnost nebo <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> vlastnost vlastní vykreslovač.</span><span class="sxs-lookup"><span data-stu-id="28bf4-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="28bf4-105">Vykreslovače můžete <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.MenuStrip>přiřadit <xref:System.Windows.Forms.ContextMenuStrip>každému <xref:System.Windows.Forms.StatusStrip> jednotlivci , , <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> nebo ovládacímu prvku <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>můžete pomocí vlastnosti ovlivnit všechny objekty nastavením vlastnosti na .</span><span class="sxs-lookup"><span data-stu-id="28bf4-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28bf4-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>vrátí <xref:System.Windows.Forms.ToolStripRenderMode.Custom> pouze v <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> případě, `null`že hodnota není .</span><span class="sxs-lookup"><span data-stu-id="28bf4-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="28bf4-107">Vytvoření vlastního rendereru</span><span class="sxs-lookup"><span data-stu-id="28bf4-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="28bf4-108">Prodlužte třídu. <xref:System.Windows.Forms.ToolStripRenderer></span><span class="sxs-lookup"><span data-stu-id="28bf4-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="28bf4-109">Implementovat požadované vlastní vykreslování přepsáním příslušné *on...*</span><span class="sxs-lookup"><span data-stu-id="28bf4-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="28bf4-110">členy</span><span class="sxs-lookup"><span data-stu-id="28bf4-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="28bf4-111">Nastavení vlastního rendereru na aktuální vykreslovač</span><span class="sxs-lookup"><span data-stu-id="28bf4-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="28bf4-112">Chcete-li nastavit vlastní <xref:System.Windows.Forms.ToolStrip>vykreslovač pro jednoho , nastavte <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost na vlastní vykreslovač.</span><span class="sxs-lookup"><span data-stu-id="28bf4-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="28bf4-113">Nebo chcete-li nastavit vlastní <xref:System.Windows.Forms.ToolStrip> vykreslovač pro <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> všechny třídy obsažené ve <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vaší <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>aplikaci: Nastavte vlastnost na vlastní vykreslovač a nastavte vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="28bf4-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="28bf4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="28bf4-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="28bf4-115">ToolStrip – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="28bf4-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="28bf4-116">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="28bf4-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="28bf4-117">Souhrn technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="28bf4-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
