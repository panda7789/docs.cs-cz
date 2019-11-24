---
title: Událost Trasování událostí pro Windows výjimky Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f0e968053c87319bf90bf3de0f21d750ec899ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447626"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="6df62-102">Událost Trasování událostí pro Windows výjimky Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="6df62-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="6df62-103">This event captures information about the exceptions that are thrown.</span><span class="sxs-lookup"><span data-stu-id="6df62-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="6df62-104">The following table shows the keyword under which the event is raised, and the level of the event.</span><span class="sxs-lookup"><span data-stu-id="6df62-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="6df62-105">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="6df62-105">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="6df62-106">Keyword for raising the event</span><span class="sxs-lookup"><span data-stu-id="6df62-106">Keyword for raising the event</span></span>|<span data-ttu-id="6df62-107">Level</span><span class="sxs-lookup"><span data-stu-id="6df62-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6df62-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="6df62-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6df62-109">Warning (2)</span><span class="sxs-lookup"><span data-stu-id="6df62-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="6df62-110">The following table shows event information.</span><span class="sxs-lookup"><span data-stu-id="6df62-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="6df62-111">Událost</span><span class="sxs-lookup"><span data-stu-id="6df62-111">Event</span></span>|<span data-ttu-id="6df62-112">Event ID</span><span class="sxs-lookup"><span data-stu-id="6df62-112">Event ID</span></span>|<span data-ttu-id="6df62-113">Raised when</span><span class="sxs-lookup"><span data-stu-id="6df62-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="6df62-114">80</span><span class="sxs-lookup"><span data-stu-id="6df62-114">80</span></span>|<span data-ttu-id="6df62-115">A managed exception is thrown.</span><span class="sxs-lookup"><span data-stu-id="6df62-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="6df62-116">The following table shows event data.</span><span class="sxs-lookup"><span data-stu-id="6df62-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="6df62-117">Field name</span><span class="sxs-lookup"><span data-stu-id="6df62-117">Field name</span></span>|<span data-ttu-id="6df62-118">Datový typ</span><span class="sxs-lookup"><span data-stu-id="6df62-118">Data type</span></span>|<span data-ttu-id="6df62-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6df62-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6df62-120">Exception Type</span><span class="sxs-lookup"><span data-stu-id="6df62-120">Exception Type</span></span>|<span data-ttu-id="6df62-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6df62-121">win:UnicodeString</span></span>|<span data-ttu-id="6df62-122">Type of the exception; for example, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="6df62-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="6df62-123">Exception Message</span><span class="sxs-lookup"><span data-stu-id="6df62-123">Exception Message</span></span>|<span data-ttu-id="6df62-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6df62-124">win:UnicodeString</span></span>|<span data-ttu-id="6df62-125">Actual exception message.</span><span class="sxs-lookup"><span data-stu-id="6df62-125">Actual exception message.</span></span>|  
|<span data-ttu-id="6df62-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="6df62-126">EIPCodeThrow</span></span>|<span data-ttu-id="6df62-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="6df62-127">win:Pointer</span></span>|<span data-ttu-id="6df62-128">Instruction pointer where exception occurred.</span><span class="sxs-lookup"><span data-stu-id="6df62-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="6df62-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="6df62-129">ExceptionHR</span></span>|<span data-ttu-id="6df62-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="6df62-130">win:UInt32</span></span>|<span data-ttu-id="6df62-131">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="6df62-131">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="6df62-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="6df62-132">ExceptionFlags</span></span>|<span data-ttu-id="6df62-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="6df62-133">win:UInt16</span></span>|<span data-ttu-id="6df62-134">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span><span class="sxs-lookup"><span data-stu-id="6df62-134">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="6df62-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="6df62-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="6df62-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="6df62-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="6df62-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="6df62-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="6df62-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span><span class="sxs-lookup"><span data-stu-id="6df62-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="6df62-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6df62-139">ClrInstanceID</span></span>|<span data-ttu-id="6df62-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="6df62-140">win:UInt16</span></span>|<span data-ttu-id="6df62-141">Unique ID for the instance of CLR or CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="6df62-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6df62-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6df62-142">See also</span></span>

- [<span data-ttu-id="6df62-143">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="6df62-143">CLR ETW Events</span></span>](clr-etw-events.md)
