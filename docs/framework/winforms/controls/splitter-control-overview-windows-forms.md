---
title: Přehled ovládacího prvku Rozdělovač (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 934efd707f2a52da5ba604139c8e4510aad4606b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964461"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="08806-102">Přehled ovládacího prvku Rozdělovač (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="08806-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="08806-103">I <xref:System.Windows.Forms.SplitContainer> když nahrazuje a přidává funkce <xref:System.Windows.Forms.Splitter> do kontroly nad předchozími verzemi <xref:System.Windows.Forms.Splitter> , je uchována pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="08806-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="08806-104">Ovládací <xref:System.Windows.Forms.Splitter> prvky model Windows Forms slouží k změně velikosti ukotvených ovládacích prvků za běhu.</span><span class="sxs-lookup"><span data-stu-id="08806-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="08806-105">Tento <xref:System.Windows.Forms.Splitter> ovládací prvek se často používá ve formulářích s ovládacími prvky, které mají různou délku dat, jako je Průzkumník Windows, jejichž podokna dat obsahují informace o různých šířkách v různých časech.</span><span class="sxs-lookup"><span data-stu-id="08806-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="08806-106">Práce s ovládacím prvkem rozdělovač</span><span class="sxs-lookup"><span data-stu-id="08806-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="08806-107">Když uživatel přejde ukazatelem myši na neukotvený okraj ovládacího prvku, jehož velikost může být změněna rozdělovačem, ukazatel změní jeho vzhled, aby označoval, že lze změnit velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="08806-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="08806-108">V ovládacím prvku Rozdělovač může uživatel změnit velikost ukotveného ovládacího prvku, který je těsně před ním.</span><span class="sxs-lookup"><span data-stu-id="08806-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="08806-109">Proto, aby uživatel mohl změnit velikost ukotveného ovládacího prvku za běhu, ukotvit ovládací prvek pro změnu velikosti na okraji kontejneru a potom ukotvit ovládací prvek rozdělovače na stejnou stranu tohoto kontejneru.</span><span class="sxs-lookup"><span data-stu-id="08806-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08806-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08806-110">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="08806-111">Postupy: Ukotvit ovládací prvky na model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08806-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="08806-112">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08806-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
