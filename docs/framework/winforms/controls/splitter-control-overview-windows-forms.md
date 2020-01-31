---
title: Přehled ovládacího prvku Splitter
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 3d6da8daf9bb0e8df4f69554a87725a7ddb65acb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742898"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="544e2-102">Přehled ovládacího prvku Rozdělovač (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="544e2-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="544e2-103">I když <xref:System.Windows.Forms.SplitContainer> nahrazuje a přidává funkce pro <xref:System.Windows.Forms.Splitter> kontrolu nad předchozími verzemi, <xref:System.Windows.Forms.Splitter> se zachová pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="544e2-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="544e2-104">Ovládací prvky model Windows Forms <xref:System.Windows.Forms.Splitter> slouží k změně velikosti ukotvených ovládacích prvků za běhu.</span><span class="sxs-lookup"><span data-stu-id="544e2-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="544e2-105"><xref:System.Windows.Forms.Splitter> ovládací prvek se často používá ve formulářích s ovládacími prvky, které mají různou délku dat, jako je Průzkumník Windows, jejichž podokna dat obsahují informace o různých šířkách v různých časech.</span><span class="sxs-lookup"><span data-stu-id="544e2-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="544e2-106">Práce s ovládacím prvkem rozdělovač</span><span class="sxs-lookup"><span data-stu-id="544e2-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="544e2-107">Když uživatel přejde ukazatelem myši na neukotvený okraj ovládacího prvku, jehož velikost může být změněna rozdělovačem, ukazatel změní jeho vzhled, aby označoval, že lze změnit velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="544e2-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="544e2-108">V ovládacím prvku Rozdělovač může uživatel změnit velikost ukotveného ovládacího prvku, který je těsně před ním.</span><span class="sxs-lookup"><span data-stu-id="544e2-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="544e2-109">Proto, aby uživatel mohl změnit velikost ukotveného ovládacího prvku za běhu, ukotvit ovládací prvek pro změnu velikosti na okraji kontejneru a potom ukotvit ovládací prvek rozdělovače na stejnou stranu tohoto kontejneru.</span><span class="sxs-lookup"><span data-stu-id="544e2-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544e2-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="544e2-110">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="544e2-111">Postupy: Vložení ovládacích prvků ve Windows Forms do doku</span><span class="sxs-lookup"><span data-stu-id="544e2-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="544e2-112">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="544e2-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
