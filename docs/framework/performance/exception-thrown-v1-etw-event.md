---
title: Událost Trasování událostí pro Windows výjimky Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd322d25d91bb277a4c817594c968c28a6d61d68
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723014"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="5179b-102">Událost Trasování událostí pro Windows výjimky Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="5179b-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="5179b-103">Tato událost zaznamená informace o výjimkách, které jsou vyvolány.</span><span class="sxs-lookup"><span data-stu-id="5179b-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="5179b-104">V následující tabulce jsou uvedeny klíčové slovo, pod kterým se vyvolá událost a úroveň události.</span><span class="sxs-lookup"><span data-stu-id="5179b-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="5179b-105">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="5179b-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="5179b-106">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="5179b-106">Keyword for raising the event</span></span>|<span data-ttu-id="5179b-107">úroveň</span><span class="sxs-lookup"><span data-stu-id="5179b-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5179b-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="5179b-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="5179b-109">Upozornění (2)</span><span class="sxs-lookup"><span data-stu-id="5179b-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="5179b-110">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="5179b-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="5179b-111">Událost</span><span class="sxs-lookup"><span data-stu-id="5179b-111">Event</span></span>|<span data-ttu-id="5179b-112">ID události</span><span class="sxs-lookup"><span data-stu-id="5179b-112">Event ID</span></span>|<span data-ttu-id="5179b-113">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="5179b-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="5179b-114">80</span><span class="sxs-lookup"><span data-stu-id="5179b-114">80</span></span>|<span data-ttu-id="5179b-115">Spravovaná výjimka je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="5179b-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="5179b-116">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="5179b-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="5179b-117">Název pole</span><span class="sxs-lookup"><span data-stu-id="5179b-117">Field name</span></span>|<span data-ttu-id="5179b-118">Datový typ</span><span class="sxs-lookup"><span data-stu-id="5179b-118">Data type</span></span>|<span data-ttu-id="5179b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5179b-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5179b-120">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="5179b-120">Exception Type</span></span>|<span data-ttu-id="5179b-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5179b-121">win:UnicodeString</span></span>|<span data-ttu-id="5179b-122">Typ výjimky; například `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="5179b-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="5179b-123">Zpráva o výjimce</span><span class="sxs-lookup"><span data-stu-id="5179b-123">Exception Message</span></span>|<span data-ttu-id="5179b-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5179b-124">win:UnicodeString</span></span>|<span data-ttu-id="5179b-125">Zpráva o výjimce skutečný.</span><span class="sxs-lookup"><span data-stu-id="5179b-125">Actual exception message.</span></span>|  
|<span data-ttu-id="5179b-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="5179b-126">EIPCodeThrow</span></span>|<span data-ttu-id="5179b-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="5179b-127">win:Pointer</span></span>|<span data-ttu-id="5179b-128">Ukazatele na instrukci kde došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="5179b-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="5179b-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="5179b-129">ExceptionHR</span></span>|<span data-ttu-id="5179b-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5179b-130">win:UInt32</span></span>|<span data-ttu-id="5179b-131">Výjimka [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="5179b-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="5179b-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="5179b-132">ExceptionFlags</span></span>|<span data-ttu-id="5179b-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5179b-133">win:UInt16</span></span>|<span data-ttu-id="5179b-134">0x01: HasInnerException (viz [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) dokumentace jazyka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5179b-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="5179b-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="5179b-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="5179b-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="5179b-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="5179b-137">0x08: IsCorruptedStateException (vyplývá, že stav procesu je poškozen, naleznete v tématu [zpracování výjimek poškozený stav](https://go.microsoft.com/fwlink/?LinkId=179681) na webové stránce MSDN).</span><span class="sxs-lookup"><span data-stu-id="5179b-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="5179b-138">0x10: IsCLSCompliant (výjimku, která je odvozena z <xref:System.Exception> je kompatibilní se Specifikací CLS; v opačném případě není kompatibilní se Specifikací CLS).</span><span class="sxs-lookup"><span data-stu-id="5179b-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="5179b-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5179b-139">ClrInstanceID</span></span>|<span data-ttu-id="5179b-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5179b-140">win:UInt16</span></span>|<span data-ttu-id="5179b-141">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5179b-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5179b-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5179b-142">See also</span></span>

- [<span data-ttu-id="5179b-143">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="5179b-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
