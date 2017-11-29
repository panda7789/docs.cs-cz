---
title: "Zachycení myši ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8004b05ea25341a142bfcfd9ae812ee3bebd6d5b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="bd974-102">Zachycení myši ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bd974-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="bd974-103">*Zachycení myši* údaj udává, kdy ovládacího prvku trvá příkaz Všechny myši vstup.</span><span class="sxs-lookup"><span data-stu-id="bd974-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="bd974-104">V případě, že zachycení myši ovládacího prvku obdrží vstup z myši, zda je ukazatel je v rámci svých hranic.</span><span class="sxs-lookup"><span data-stu-id="bd974-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="bd974-105">Nastavení zachycení myši</span><span class="sxs-lookup"><span data-stu-id="bd974-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="bd974-106">V systému Windows Forms myši zachyceny ovládacího prvku, když uživatel stiskne tlačítko myši v ovládacím prvku a uvolnění myši v ovládacím prvku když uživatel uvolní tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="bd974-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="bd974-107"><xref:System.Windows.Forms.Control.Capture%2A> Vlastnost <xref:System.Windows.Forms.Control> třída určuje, zda má ovládacího prvku zaznamenány myši.</span><span class="sxs-lookup"><span data-stu-id="bd974-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="bd974-108">Pokud chcete zjistit, kdy ovládací prvek ztratí zachycení myši, zpracování <xref:System.Windows.Forms.Control.MouseCaptureChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="bd974-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="bd974-109">Pouze okno popředí můžete zaznamenat myši.</span><span class="sxs-lookup"><span data-stu-id="bd974-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="bd974-110">Pokud okno pozadí se pokusí zaznamenat myš, okno přijímá zprávy pouze pro události myši, které dojít, když ukazatel myši nachází v viditelné části okna.</span><span class="sxs-lookup"><span data-stu-id="bd974-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="bd974-111">Navíc i v případě zachycení myši okno popředí uživatele stále můžete pomocí tlačítka Další okno, převedení do popředí.</span><span class="sxs-lookup"><span data-stu-id="bd974-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="bd974-112">Při zachytávání myši nefungují klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="bd974-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd974-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd974-113">See Also</span></span>  
 [<span data-ttu-id="bd974-114">Vstup z myši ve Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="bd974-114">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
