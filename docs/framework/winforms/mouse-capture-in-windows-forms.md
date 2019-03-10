---
title: Zachycení myši ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: afb58df99ea30f5e7e6ab5b9156af195d273c44d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712705"
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="91921-102">Zachycení myši ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91921-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="91921-103">*Zachycení myši* odkazuje na příkaz všechny vstup myši pořízením ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="91921-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="91921-104">Když ovládací prvek zachytí myš, zda ukazatel je v rámci jeho okrajů přijímá vstup z myši.</span><span class="sxs-lookup"><span data-stu-id="91921-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="91921-105">Zachycení myši nastavení</span><span class="sxs-lookup"><span data-stu-id="91921-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="91921-106">Ve Windows Forms myši nezachytává ovládacího prvku, když uživatel stiskne tlačítko myši v ovládacím prvku a uvolní se ukazatel myši ovládacím prvkem, když uživatel uvolní tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="91921-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="91921-107"><xref:System.Windows.Forms.Control.Capture%2A> Vlastnost <xref:System.Windows.Forms.Control> třída určuje, zda ovládací prvek zachytí myš.</span><span class="sxs-lookup"><span data-stu-id="91921-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="91921-108">Pokud chcete zjistit, kdy ovládací prvek ztratí zachycení myši, zpracovat <xref:System.Windows.Forms.Control.MouseCaptureChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="91921-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="91921-109">Pouze okno v popředí, můžete zachytit ukazatel myši.</span><span class="sxs-lookup"><span data-stu-id="91921-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="91921-110">Když se pokusí oknem v pozadí pro zachycení myši, v okně přijímá zprávy pouze pro události myši, ke kterým dochází, když ukazatel myši nachází v viditelnou část okna.</span><span class="sxs-lookup"><span data-stu-id="91921-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="91921-111">Navíc i v případě, že okno v popředí zachytí myš, stále kliknutí další okno, přináší na popředí.</span><span class="sxs-lookup"><span data-stu-id="91921-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="91921-112">Když ukazatel myši je zachycena, nebude fungovat klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="91921-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91921-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91921-113">See also</span></span>
- [<span data-ttu-id="91921-114">Vstup z myši v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91921-114">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
