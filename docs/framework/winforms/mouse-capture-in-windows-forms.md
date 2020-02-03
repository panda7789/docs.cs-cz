---
title: Zachycení myši
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 10583f074831b16dce3c713b4ac9a76c7005c9f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741016"
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="25ed1-102">Zachycení myši ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25ed1-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="25ed1-103">*Zachycení myši* odkazuje na to, že ovládací prvek provede příkaz pro všechny vstupy myši.</span><span class="sxs-lookup"><span data-stu-id="25ed1-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="25ed1-104">Když ovládací prvek zachytí myš, dostane vstup z myši bez ohledu na to, zda je ukazatel v rámci jeho ohraničení.</span><span class="sxs-lookup"><span data-stu-id="25ed1-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="25ed1-105">Nastavení zachycení myši</span><span class="sxs-lookup"><span data-stu-id="25ed1-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="25ed1-106">V model Windows Forms je myš zachycena ovládacím prvkem, když uživatel stiskne tlačítko myši na ovládacím prvku a myš je uvolněna ovládacím prvkem, když uživatel uvolní tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="25ed1-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="25ed1-107">Vlastnost <xref:System.Windows.Forms.Control.Capture%2A> třídy <xref:System.Windows.Forms.Control> určuje, zda ovládací prvek zachytil myš.</span><span class="sxs-lookup"><span data-stu-id="25ed1-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="25ed1-108">Chcete-li zjistit, kdy ovládací prvek ztratí zachycení myši, zpracujte událost <xref:System.Windows.Forms.Control.MouseCaptureChanged>.</span><span class="sxs-lookup"><span data-stu-id="25ed1-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="25ed1-109">Myš může zachytit pouze okno v popředí.</span><span class="sxs-lookup"><span data-stu-id="25ed1-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="25ed1-110">Když se okno na pozadí pokusí zachytit myš, okno obdrží zprávy pouze pro události myši, ke kterým dojde, když je ukazatel myši v viditelné části okna.</span><span class="sxs-lookup"><span data-stu-id="25ed1-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="25ed1-111">I když je v okně popředí zachycena myš, uživatel může stále kliknout na jiné okno a přemístit ho do popředí.</span><span class="sxs-lookup"><span data-stu-id="25ed1-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="25ed1-112">Když je myš zachycena, klávesové zkratky nefungují.</span><span class="sxs-lookup"><span data-stu-id="25ed1-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ed1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="25ed1-113">See also</span></span>

- [<span data-ttu-id="25ed1-114">Vstup z myši v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25ed1-114">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
