---
title: Událost Trasování událostí pro Windows výjimky Thrown_V1
description: Zobrazí podrobné informace o ExceptionThrown_V1 události ETW. Data události, jako jsou názvy polí, datové typy a popisy, jsou uvedeny pro vyvolané výjimky.
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: f800a43d0ed2a82bc51a5e3a028b5fa1870df3fb
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309453"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="f2069-104">Událost Trasování událostí pro Windows výjimky Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="f2069-104">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="f2069-105">Tato událost zachycuje informace o vyvolaných výjimkách.</span><span class="sxs-lookup"><span data-stu-id="f2069-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="f2069-106">Následující tabulka ukazuje klíčové slovo, pod kterým je událost vyvolána, a úroveň události.</span><span class="sxs-lookup"><span data-stu-id="f2069-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="f2069-107">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f2069-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f2069-108">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="f2069-108">Keyword for raising the event</span></span>|<span data-ttu-id="f2069-109">Level</span><span class="sxs-lookup"><span data-stu-id="f2069-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f2069-110">`ExceptionKeyword`0x8000</span><span class="sxs-lookup"><span data-stu-id="f2069-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="f2069-111">Upozornění (2)</span><span class="sxs-lookup"><span data-stu-id="f2069-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="f2069-112">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="f2069-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="f2069-113">Událost</span><span class="sxs-lookup"><span data-stu-id="f2069-113">Event</span></span>|<span data-ttu-id="f2069-114">ID události</span><span class="sxs-lookup"><span data-stu-id="f2069-114">Event ID</span></span>|<span data-ttu-id="f2069-115">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="f2069-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="f2069-116">80</span><span class="sxs-lookup"><span data-stu-id="f2069-116">80</span></span>|<span data-ttu-id="f2069-117">Je vyvolána spravovaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="f2069-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="f2069-118">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="f2069-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="f2069-119">Název pole</span><span class="sxs-lookup"><span data-stu-id="f2069-119">Field name</span></span>|<span data-ttu-id="f2069-120">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f2069-120">Data type</span></span>|<span data-ttu-id="f2069-121">Popis</span><span class="sxs-lookup"><span data-stu-id="f2069-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f2069-122">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="f2069-122">Exception Type</span></span>|<span data-ttu-id="f2069-123">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f2069-123">win:UnicodeString</span></span>|<span data-ttu-id="f2069-124">Typ výjimky; například `System.NullReferenceException` .</span><span class="sxs-lookup"><span data-stu-id="f2069-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="f2069-125">Zpráva o výjimce</span><span class="sxs-lookup"><span data-stu-id="f2069-125">Exception Message</span></span>|<span data-ttu-id="f2069-126">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f2069-126">win:UnicodeString</span></span>|<span data-ttu-id="f2069-127">Skutečná zpráva výjimky</span><span class="sxs-lookup"><span data-stu-id="f2069-127">Actual exception message.</span></span>|  
|<span data-ttu-id="f2069-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="f2069-128">EIPCodeThrow</span></span>|<span data-ttu-id="f2069-129">Win: ukazatel</span><span class="sxs-lookup"><span data-stu-id="f2069-129">win:Pointer</span></span>|<span data-ttu-id="f2069-130">Ukazatel na instrukci, kde došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="f2069-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="f2069-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="f2069-131">ExceptionHR</span></span>|<span data-ttu-id="f2069-132">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f2069-132">win:UInt32</span></span>|<span data-ttu-id="f2069-133">Výjimka [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="f2069-133">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="f2069-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="f2069-134">ExceptionFlags</span></span>|<span data-ttu-id="f2069-135">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f2069-135">win:UInt16</span></span>|<span data-ttu-id="f2069-136">0x01: HasInnerException (viz [události CLR ETW](clr-etw-events.md) v dokumentaci k Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f2069-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="f2069-137">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="f2069-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="f2069-138">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="f2069-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="f2069-139">0x08: IsCorruptedStateException (označuje, že stav procesu je poškozen; viz [zpracování výjimek poškozených stavů](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="f2069-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="f2069-140">0x10: IsCLSCompliant (výjimka odvozená z <xref:System.Exception> je kompatibilní se specifikací CLS; v opačném případě není kompatibilní se specifikací CLS).</span><span class="sxs-lookup"><span data-stu-id="f2069-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="f2069-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f2069-141">ClrInstanceID</span></span>|<span data-ttu-id="f2069-142">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f2069-142">win:UInt16</span></span>|<span data-ttu-id="f2069-143">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f2069-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2069-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2069-144">See also</span></span>

- [<span data-ttu-id="f2069-145">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="f2069-145">CLR ETW Events</span></span>](clr-etw-events.md)
