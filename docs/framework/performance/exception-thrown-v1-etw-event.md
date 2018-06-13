---
title: Událost Trasování událostí pro Windows výjimky Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dafa5846f779276ab81e8e30e7c7a50b9fbff853
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393852"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="1cc12-102">Událost Trasování událostí pro Windows výjimky Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="1cc12-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="1cc12-103">Tato událost zaznamená informace o výjimky, které jsou vydány.</span><span class="sxs-lookup"><span data-stu-id="1cc12-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="1cc12-104">Následující tabulka uvádí klíčové slovo, pod kterým je událost vyvolána a úroveň události.</span><span class="sxs-lookup"><span data-stu-id="1cc12-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="1cc12-105">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="1cc12-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="1cc12-106">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="1cc12-106">Keyword for raising the event</span></span>|<span data-ttu-id="1cc12-107">úroveň</span><span class="sxs-lookup"><span data-stu-id="1cc12-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1cc12-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="1cc12-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="1cc12-109">Upozornění (2)</span><span class="sxs-lookup"><span data-stu-id="1cc12-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="1cc12-110">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="1cc12-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="1cc12-111">Událost</span><span class="sxs-lookup"><span data-stu-id="1cc12-111">Event</span></span>|<span data-ttu-id="1cc12-112">ID události</span><span class="sxs-lookup"><span data-stu-id="1cc12-112">Event ID</span></span>|<span data-ttu-id="1cc12-113">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="1cc12-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="1cc12-114">80</span><span class="sxs-lookup"><span data-stu-id="1cc12-114">80</span></span>|<span data-ttu-id="1cc12-115">Spravované výjimky je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="1cc12-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="1cc12-116">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="1cc12-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="1cc12-117">Název pole</span><span class="sxs-lookup"><span data-stu-id="1cc12-117">Field name</span></span>|<span data-ttu-id="1cc12-118">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1cc12-118">Data type</span></span>|<span data-ttu-id="1cc12-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1cc12-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1cc12-120">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="1cc12-120">Exception Type</span></span>|<span data-ttu-id="1cc12-121">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1cc12-121">win:UnicodeString</span></span>|<span data-ttu-id="1cc12-122">Typ výjimky; například `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="1cc12-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="1cc12-123">Zpráva o výjimce</span><span class="sxs-lookup"><span data-stu-id="1cc12-123">Exception Message</span></span>|<span data-ttu-id="1cc12-124">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1cc12-124">win:UnicodeString</span></span>|<span data-ttu-id="1cc12-125">Zpráva o výjimce skutečný.</span><span class="sxs-lookup"><span data-stu-id="1cc12-125">Actual exception message.</span></span>|  
|<span data-ttu-id="1cc12-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="1cc12-126">EIPCodeThrow</span></span>|<span data-ttu-id="1cc12-127">Win: ukazatele</span><span class="sxs-lookup"><span data-stu-id="1cc12-127">win:Pointer</span></span>|<span data-ttu-id="1cc12-128">Ukazatel instrukce, kde došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="1cc12-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="1cc12-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="1cc12-129">ExceptionHR</span></span>|<span data-ttu-id="1cc12-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="1cc12-130">win:UInt32</span></span>|<span data-ttu-id="1cc12-131">Výjimka [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="1cc12-131">Exception [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="1cc12-132">Příznaky výjimky</span><span class="sxs-lookup"><span data-stu-id="1cc12-132">ExceptionFlags</span></span>|<span data-ttu-id="1cc12-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1cc12-133">win:UInt16</span></span>|<span data-ttu-id="1cc12-134">0x01: HasInnerException (viz [události ETW CLR](../../../docs/framework/performance/clr-etw-events.md) v dokumentaci k jazyka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1cc12-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="1cc12-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="1cc12-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="1cc12-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="1cc12-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="1cc12-137">0x08: IsCorruptedStateException (označuje, že je poškozený stav procesu; viz [zpracování poškozený stav výjimky](http://go.microsoft.com/fwlink/?LinkId=179681) na webu MSDN).</span><span class="sxs-lookup"><span data-stu-id="1cc12-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](http://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="1cc12-138">0x10: IsCLSCompliant (výjimku, která je odvozena z <xref:System.Exception> je kompatibilní se specifikací CLS, jinak hodnota není kompatibilní se specifikací CLS).</span><span class="sxs-lookup"><span data-stu-id="1cc12-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="1cc12-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1cc12-139">ClrInstanceID</span></span>|<span data-ttu-id="1cc12-140">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1cc12-140">win:UInt16</span></span>|<span data-ttu-id="1cc12-141">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="1cc12-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1cc12-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cc12-142">See Also</span></span>  
 [<span data-ttu-id="1cc12-143">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="1cc12-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
