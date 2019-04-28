---
title: LoggingLevelEnum – výčet
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe8e1355382273a681e927897f4a8ff5814b8de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765424"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="b5258-102">LoggingLevelEnum – výčet</span><span class="sxs-lookup"><span data-stu-id="b5258-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="b5258-103">Určuje úroveň závažnosti popisnou zprávou, která jsou zapsána do protokolu událostí při spravovaným vláknem se zaprotokoluje událost.</span><span class="sxs-lookup"><span data-stu-id="b5258-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5258-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5258-104">Syntax</span></span>  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a><span data-ttu-id="b5258-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b5258-105">Members</span></span>  
  
|<span data-ttu-id="b5258-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b5258-106">Member</span></span>|<span data-ttu-id="b5258-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b5258-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="b5258-108">Zpráva je úroveň trasování 0.</span><span class="sxs-lookup"><span data-stu-id="b5258-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="b5258-109">Zpráva je 1 úroveň trasování.</span><span class="sxs-lookup"><span data-stu-id="b5258-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="b5258-110">Zpráva je úroveň trasování 2.</span><span class="sxs-lookup"><span data-stu-id="b5258-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="b5258-111">Úroveň trasování 3 je zpráva.</span><span class="sxs-lookup"><span data-stu-id="b5258-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="b5258-112">Úroveň trasování 4 je zpráva.</span><span class="sxs-lookup"><span data-stu-id="b5258-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="b5258-113">Zpráva je úroveň stav 0.</span><span class="sxs-lookup"><span data-stu-id="b5258-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="b5258-114">Zpráva je stav úrovně 1.</span><span class="sxs-lookup"><span data-stu-id="b5258-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="b5258-115">Zpráva je stav úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="b5258-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="b5258-116">Zpráva je stav úrovně 3.</span><span class="sxs-lookup"><span data-stu-id="b5258-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="b5258-117">Úroveň stavu 4 je zpráva.</span><span class="sxs-lookup"><span data-stu-id="b5258-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="b5258-118">Zpráva je úroveň pro upozornění.</span><span class="sxs-lookup"><span data-stu-id="b5258-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="b5258-119">Zpráva je úrovně chyby.</span><span class="sxs-lookup"><span data-stu-id="b5258-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="b5258-120">Zpráva je tísňový úroveň.</span><span class="sxs-lookup"><span data-stu-id="b5258-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5258-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5258-121">Remarks</span></span>  
 <span data-ttu-id="b5258-122">Common language runtime (CLR) zavolá [icordebugmanagedcallback::logmessage –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) metoda oznámit ladicího programu, že má spravovaným vláknem protokoluje událost.</span><span class="sxs-lookup"><span data-stu-id="b5258-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="b5258-123">Modul CLR předá hodnotu `LoggingLevelEnum` výčet označující úroveň závažnosti zprávy, která spravované vlákno zapsáno do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="b5258-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5258-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5258-124">Requirements</span></span>  
 <span data-ttu-id="b5258-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5258-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5258-126">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5258-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5258-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5258-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5258-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5258-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5258-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5258-129">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="b5258-130">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="b5258-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
