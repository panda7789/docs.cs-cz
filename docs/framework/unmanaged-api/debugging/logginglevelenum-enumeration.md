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
ms.openlocfilehash: 331065d4aae82c66b9ebd82e99427501c3ba8a98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435952"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="264ed-102">LoggingLevelEnum – výčet</span><span class="sxs-lookup"><span data-stu-id="264ed-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="264ed-103">Určuje úroveň závažnosti popisný zprávu, která se zapíšou do protokolu událostí, když spravované vlákno protokoluje nějakou událost.</span><span class="sxs-lookup"><span data-stu-id="264ed-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="264ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="264ed-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="264ed-105">Členové</span><span class="sxs-lookup"><span data-stu-id="264ed-105">Members</span></span>  
  
|<span data-ttu-id="264ed-106">Člen</span><span class="sxs-lookup"><span data-stu-id="264ed-106">Member</span></span>|<span data-ttu-id="264ed-107">Popis</span><span class="sxs-lookup"><span data-stu-id="264ed-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="264ed-108">Zpráva je úroveň trasování 0.</span><span class="sxs-lookup"><span data-stu-id="264ed-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="264ed-109">Zpráva je úroveň trasování 1.</span><span class="sxs-lookup"><span data-stu-id="264ed-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="264ed-110">Zpráva je úroveň trasování 2.</span><span class="sxs-lookup"><span data-stu-id="264ed-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="264ed-111">Zpráva je úroveň trasování 3.</span><span class="sxs-lookup"><span data-stu-id="264ed-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="264ed-112">Zpráva je úroveň trasování 4.</span><span class="sxs-lookup"><span data-stu-id="264ed-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="264ed-113">Zpráva je úroveň stav 0.</span><span class="sxs-lookup"><span data-stu-id="264ed-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="264ed-114">Zpráva je stav úrovně 1.</span><span class="sxs-lookup"><span data-stu-id="264ed-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="264ed-115">Zpráva je stav úroveň 2.</span><span class="sxs-lookup"><span data-stu-id="264ed-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="264ed-116">Zpráva je stav úroveň 3.</span><span class="sxs-lookup"><span data-stu-id="264ed-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="264ed-117">Zpráva je stav úroveň 4.</span><span class="sxs-lookup"><span data-stu-id="264ed-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="264ed-118">Zpráva je úroveň pro upozornění.</span><span class="sxs-lookup"><span data-stu-id="264ed-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="264ed-119">Zpráva je úroveň chyby.</span><span class="sxs-lookup"><span data-stu-id="264ed-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="264ed-120">Zpráva je tísňový úroveň.</span><span class="sxs-lookup"><span data-stu-id="264ed-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="264ed-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="264ed-121">Remarks</span></span>  
 <span data-ttu-id="264ed-122">Modul CLR (CLR) volání [icordebugmanagedcallback::logmessage –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) metoda ladicího programu oznámit, že spravované vlákno se přihlásil událost.</span><span class="sxs-lookup"><span data-stu-id="264ed-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="264ed-123">Modul CLR předá hodnotu `LoggingLevelEnum` výčtu označíte, úroveň závažnosti zprávu, která spravované vlákno napsali do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="264ed-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="264ed-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="264ed-124">Requirements</span></span>  
 <span data-ttu-id="264ed-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="264ed-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="264ed-126">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="264ed-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="264ed-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="264ed-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="264ed-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="264ed-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="264ed-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="264ed-129">See Also</span></span>  
 <xref:System.Diagnostics.EventLog>  
 [<span data-ttu-id="264ed-130">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="264ed-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
