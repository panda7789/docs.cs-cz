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
ms.openlocfilehash: 62ea982f30a6a73648d9bf36722c0b5a49a68896
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420744"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="ea95f-102">LoggingLevelEnum – výčet</span><span class="sxs-lookup"><span data-stu-id="ea95f-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="ea95f-103">Označuje úroveň závažnosti popisné zprávy, která je zapsána do protokolu událostí, když spravované vlákno zaznamená událost.</span><span class="sxs-lookup"><span data-stu-id="ea95f-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea95f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea95f-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="ea95f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ea95f-105">Members</span></span>  
  
|<span data-ttu-id="ea95f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ea95f-106">Member</span></span>|<span data-ttu-id="ea95f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ea95f-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="ea95f-108">Zpráva je úroveň trasování 0.</span><span class="sxs-lookup"><span data-stu-id="ea95f-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="ea95f-109">Zpráva je úroveň trasování 1.</span><span class="sxs-lookup"><span data-stu-id="ea95f-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="ea95f-110">Zpráva je úroveň trasování 2.</span><span class="sxs-lookup"><span data-stu-id="ea95f-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="ea95f-111">Zpráva je úroveň trasování 3.</span><span class="sxs-lookup"><span data-stu-id="ea95f-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="ea95f-112">Zpráva je úroveň trasování 4.</span><span class="sxs-lookup"><span data-stu-id="ea95f-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="ea95f-113">Zpráva je úroveň stavu 0.</span><span class="sxs-lookup"><span data-stu-id="ea95f-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="ea95f-114">Zpráva je úroveň stavu 1.</span><span class="sxs-lookup"><span data-stu-id="ea95f-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="ea95f-115">Zpráva je úroveň stavu 2.</span><span class="sxs-lookup"><span data-stu-id="ea95f-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="ea95f-116">Zpráva je stavová úroveň 3.</span><span class="sxs-lookup"><span data-stu-id="ea95f-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="ea95f-117">Zpráva je úroveň stavu 4.</span><span class="sxs-lookup"><span data-stu-id="ea95f-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="ea95f-118">Zpráva je úroveň upozornění.</span><span class="sxs-lookup"><span data-stu-id="ea95f-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="ea95f-119">Zpráva je úroveň chyby.</span><span class="sxs-lookup"><span data-stu-id="ea95f-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="ea95f-120">Zpráva je nenouzová úroveň.</span><span class="sxs-lookup"><span data-stu-id="ea95f-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea95f-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea95f-121">Remarks</span></span>  
 <span data-ttu-id="ea95f-122">Modul CLR (Common Language Runtime) volá metodu [ICorDebugManagedCallback:: LogMessage –](icordebugmanagedcallback-logmessage-method.md) , která oznamuje ladicímu programu, že spravované vlákno zaznamenalo událost.</span><span class="sxs-lookup"><span data-stu-id="ea95f-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="ea95f-123">Modul CLR předá hodnotu `LoggingLevelEnum` výčtu, aby označoval úroveň závažnosti zprávy, kterou spravované vlákno zapsalo do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="ea95f-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea95f-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea95f-124">Requirements</span></span>  
 <span data-ttu-id="ea95f-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea95f-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea95f-126">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea95f-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea95f-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ea95f-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea95f-128">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea95f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea95f-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea95f-129">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="ea95f-130">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="ea95f-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
