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
ms.openlocfilehash: d8a85edf8c001b19191fdfd74d1f9ebdf87024ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195485"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="ff2fd-102">Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff2fd-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<xref:System.Windows.Forms.ToolStrip> <span data-ttu-id="ff2fd-103">ovládací prvky umožňují snadno podporu k používání motivů a stylů.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-103">controls give easy support to themes and styles.</span></span> <span data-ttu-id="ff2fd-104">Zcela vlastní vzhled a chování (vzhled a chování) můžete dosáhnout tím, že buď nastavíte <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost nebo <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> vlastnost vlastní zobrazovací jednotky.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="ff2fd-105">Můžete přiřadit renderery jednotlivých <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, nebo <xref:System.Windows.Forms.StatusStrip> ovládacího prvku, nebo můžete použít <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> vlastnost má vliv na všechny objekty tak, že nastavíte <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> <span data-ttu-id="ff2fd-106">Vrátí <xref:System.Windows.Forms.ToolStripRenderMode.Custom> pouze tehdy, pokud hodnota <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> není `null`.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-106">returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="ff2fd-107">Chcete-li vytvořit vlastní zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="ff2fd-107">To create a custom renderer</span></span>  
  
1.  <span data-ttu-id="ff2fd-108">Rozšíření <xref:System.Windows.Forms.ToolStripRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2.  <span data-ttu-id="ff2fd-109">Implementovat požadované vlastní vykreslování tak, že přepíšete odpovídající *na...*</span><span class="sxs-lookup"><span data-stu-id="ff2fd-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="ff2fd-110">členy</span><span class="sxs-lookup"><span data-stu-id="ff2fd-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="ff2fd-111">Nastavení vlastního rendereru bude aktuální zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="ff2fd-111">To set the custom renderer to be the current renderer</span></span>  
  
1.  <span data-ttu-id="ff2fd-112">Nastavení vlastního rendereru pro jeden <xref:System.Windows.Forms.ToolStrip>, nastavte <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost vlastní zobrazovací jednotky.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  <span data-ttu-id="ff2fd-113">Nebo k nastavení vlastní zobrazovací jednotky pro všechny <xref:System.Windows.Forms.ToolStrip> třídy obsažené ve vaší aplikaci: Nastavte <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> do vlastní zobrazovací jednotky a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ff2fd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff2fd-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="ff2fd-115">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ff2fd-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="ff2fd-116">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ff2fd-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="ff2fd-117">Souhrn technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ff2fd-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
