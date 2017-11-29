---
title: "Přehled ovládacího prvku Rozdělovač (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Splitter
helpviewer_keywords: Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e4602796a1a7740adb9a352d0a21fb6c2a58959d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="320e0-102">Přehled ovládacího prvku Rozdělovač (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="320e0-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="320e0-103">I když <xref:System.Windows.Forms.SplitContainer> nahrazuje a přidá funkce <xref:System.Windows.Forms.Splitter> řízení předchozí verze, <xref:System.Windows.Forms.Splitter> se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="320e0-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="320e0-104">Windows Forms <xref:System.Windows.Forms.Splitter> ovládací prvky se používají ke změně velikosti ukotvených ovládacích prvků za běhu.</span><span class="sxs-lookup"><span data-stu-id="320e0-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="320e0-105"><xref:System.Windows.Forms.Splitter> Řízení se často používá ve formulářích s ovládacími prvky, které mají různých délek data k dispozici jako Průzkumník Windows, jejichž data podokna obsahovat informace o různých šířek v různých časech.</span><span class="sxs-lookup"><span data-stu-id="320e0-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="320e0-106">Práce s ovládacím prvkem rozdělovače</span><span class="sxs-lookup"><span data-stu-id="320e0-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="320e0-107">Když uživatel body ukazatel myši na odpojenou okraji ovládacího prvku, který můžete upravit velikost ovládací prvek typu rozdělovač změní její vzhled indikující, že jde změnit ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="320e0-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="320e0-108">Pomocí ovládacího prvku rozdělovač může uživatel změnit velikost ukotveného ovládací prvek, který je bezprostředně před.</span><span class="sxs-lookup"><span data-stu-id="320e0-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="320e0-109">Proto, aby uživatel ke změně velikosti ukotveného ovládacího prvku za běhu, ukotvení na změnu velikosti na hranu kontejneru ovládacího prvku a pak ukotvení – ovládací prvek typu rozdělovač na stejné straně tohoto kontejneru.</span><span class="sxs-lookup"><span data-stu-id="320e0-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320e0-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="320e0-110">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="320e0-111">Postupy: Ukotvování ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="320e0-111">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="320e0-112">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="320e0-112">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
