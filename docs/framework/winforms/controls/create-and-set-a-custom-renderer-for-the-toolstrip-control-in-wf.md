---
title: "Postupy: Vytvoření a nastavení vlastní zobrazovací jednotky pro ovládací prvek ToolStrip ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f63ff0a7336ae80ce5652cf3e4c6c7dd409882a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="ec1e9-102">Postupy: Vytvoření a nastavení vlastní zobrazovací jednotky pro ovládací prvek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec1e9-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="ec1e9-103"><xref:System.Windows.Forms.ToolStrip>ovládací prvky snadno podporu předáte motivů a stylů.</span><span class="sxs-lookup"><span data-stu-id="ec1e9-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="ec1e9-104">Zcela vlastní vzhled a chování (vzhled a chování) můžete dosáhnout nastavením buď <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost nebo <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> vlastnost, která má vlastní zobrazovací jednotky.</span><span class="sxs-lookup"><span data-stu-id="ec1e9-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="ec1e9-105">Pro každého uživatele můžete přiřadit pro vykreslování <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, nebo <xref:System.Windows.Forms.StatusStrip> ovládací prvek, nebo můžete použít <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> vlastnost, která má vliv na všechny objekty nastavením <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ec1e9-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec1e9-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>Vrátí <xref:System.Windows.Forms.ToolStripRenderMode.Custom> pouze v případě hodnotu <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> není `null`.</span><span class="sxs-lookup"><span data-stu-id="ec1e9-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="ec1e9-107">Chcete-li vytvořit vlastní zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="ec1e9-107">To create a custom renderer</span></span>  
  
1.  <span data-ttu-id="ec1e9-108">Rozšíření <xref:System.Windows.Forms.ToolStripRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="ec1e9-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2.  <span data-ttu-id="ec1e9-109">Implementace potřeby vlastní vykreslení přepsáním odpovídající *na...*</span><span class="sxs-lookup"><span data-stu-id="ec1e9-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="ec1e9-110">členy</span><span class="sxs-lookup"><span data-stu-id="ec1e9-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="ec1e9-111">Chcete-li nastavit vlastní zobrazovací jednotky jako aktuální zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="ec1e9-111">To set the custom renderer to be the current renderer</span></span>  
  
1.  <span data-ttu-id="ec1e9-112">Chcete-li nastavit vlastní zobrazovací jednotky pro jednu <xref:System.Windows.Forms.ToolStrip>, nastavte <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> vlastnost, která má vlastní zobrazovací jednotky.</span><span class="sxs-lookup"><span data-stu-id="ec1e9-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  <span data-ttu-id="ec1e9-113">Nebo nastavit vlastní zobrazovací jednotky pro všechny <xref:System.Windows.Forms.ToolStrip> třídy, které jsou obsažené v aplikaci: nastavte <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> do vlastní zobrazovací jednotky a nastavte vlastnost <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost, která má <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="ec1e9-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ec1e9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec1e9-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>  
 [<span data-ttu-id="ec1e9-115">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ec1e9-115">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="ec1e9-116">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ec1e9-116">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="ec1e9-117">Souhrn technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ec1e9-117">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
