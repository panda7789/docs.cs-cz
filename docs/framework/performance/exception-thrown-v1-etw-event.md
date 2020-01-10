---
title: Událost Trasování událostí pro Windows výjimky Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: 80faf6e607755ee79c7ec17f2d7d3d5bdce822b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716056"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="42ada-102">Událost Trasování událostí pro Windows výjimky Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="42ada-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="42ada-103">Tato událost zachycuje informace o vyvolaných výjimkách.</span><span class="sxs-lookup"><span data-stu-id="42ada-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="42ada-104">Následující tabulka ukazuje klíčové slovo, pod kterým je událost vyvolána, a úroveň události.</span><span class="sxs-lookup"><span data-stu-id="42ada-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="42ada-105">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="42ada-105">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="42ada-106">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="42ada-106">Keyword for raising the event</span></span>|<span data-ttu-id="42ada-107">Úroveň</span><span class="sxs-lookup"><span data-stu-id="42ada-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="42ada-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="42ada-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="42ada-109">Upozornění (2)</span><span class="sxs-lookup"><span data-stu-id="42ada-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="42ada-110">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="42ada-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="42ada-111">Událost</span><span class="sxs-lookup"><span data-stu-id="42ada-111">Event</span></span>|<span data-ttu-id="42ada-112">ID události</span><span class="sxs-lookup"><span data-stu-id="42ada-112">Event ID</span></span>|<span data-ttu-id="42ada-113">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="42ada-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="42ada-114">80</span><span class="sxs-lookup"><span data-stu-id="42ada-114">80</span></span>|<span data-ttu-id="42ada-115">Je vyvolána spravovaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="42ada-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="42ada-116">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="42ada-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="42ada-117">Název pole</span><span class="sxs-lookup"><span data-stu-id="42ada-117">Field name</span></span>|<span data-ttu-id="42ada-118">Datový typ</span><span class="sxs-lookup"><span data-stu-id="42ada-118">Data type</span></span>|<span data-ttu-id="42ada-119">Popis</span><span class="sxs-lookup"><span data-stu-id="42ada-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="42ada-120">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="42ada-120">Exception Type</span></span>|<span data-ttu-id="42ada-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="42ada-121">win:UnicodeString</span></span>|<span data-ttu-id="42ada-122">Typ výjimky; například `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="42ada-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="42ada-123">Zpráva o výjimce</span><span class="sxs-lookup"><span data-stu-id="42ada-123">Exception Message</span></span>|<span data-ttu-id="42ada-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="42ada-124">win:UnicodeString</span></span>|<span data-ttu-id="42ada-125">Skutečná zpráva výjimky</span><span class="sxs-lookup"><span data-stu-id="42ada-125">Actual exception message.</span></span>|  
|<span data-ttu-id="42ada-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="42ada-126">EIPCodeThrow</span></span>|<span data-ttu-id="42ada-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="42ada-127">win:Pointer</span></span>|<span data-ttu-id="42ada-128">Ukazatel na instrukci, kde došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="42ada-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="42ada-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="42ada-129">ExceptionHR</span></span>|<span data-ttu-id="42ada-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="42ada-130">win:UInt32</span></span>|<span data-ttu-id="42ada-131">Výjimka [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="42ada-131">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="42ada-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="42ada-132">ExceptionFlags</span></span>|<span data-ttu-id="42ada-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="42ada-133">win:UInt16</span></span>|<span data-ttu-id="42ada-134">0x01: HasInnerException (viz [události CLR ETW](clr-etw-events.md) v dokumentaci k Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="42ada-134">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="42ada-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="42ada-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="42ada-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="42ada-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="42ada-137">0x08: IsCorruptedStateException (označuje, že stav procesu je poškozen; viz [zpracování výjimek poškozených stavů](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="42ada-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="42ada-138">0x10: IsCLSCompliant (výjimka odvozená od <xref:System.Exception> je kompatibilní se specifikací CLS; v opačném případě není kompatibilní se specifikací CLS).</span><span class="sxs-lookup"><span data-stu-id="42ada-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="42ada-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="42ada-139">ClrInstanceID</span></span>|<span data-ttu-id="42ada-140">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="42ada-140">win:UInt16</span></span>|<span data-ttu-id="42ada-141">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="42ada-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42ada-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42ada-142">See also</span></span>

- [<span data-ttu-id="42ada-143">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="42ada-143">CLR ETW Events</span></span>](clr-etw-events.md)
