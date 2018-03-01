---
title: "ICorDebugThread::GetCurrentException – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c18e2dfa68d425e5ec23d4573428018bc971f8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="709f8-102">ICorDebugThread::GetCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="709f8-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="709f8-103">Získá ukazatele rozhraní ICorDebugValue objektu, která představuje výjimku, která je aktuálně hlášeny ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="709f8-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="709f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="709f8-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="709f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="709f8-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="709f8-106">[out] Ukazatel na adresu `ICorDebugValue` objekt, který představuje výjimku, která je aktuálně hlášeny ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="709f8-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="709f8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="709f8-107">Remarks</span></span>  
 <span data-ttu-id="709f8-108">Objekt výjimky bude existovat od času se výjimka až do konce `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="709f8-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="709f8-109">Vyhodnocení funkce, která se provádí pomocí metody ICorDebugEval, bude vymažte objekt výjimky na instalační program a obnovte ji po dokončení.</span><span class="sxs-lookup"><span data-stu-id="709f8-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="709f8-110">Výjimky mohou být vnořené (například pokud ve filtru nebo do vyhodnocení funkce je vyvolána výjimka), takže může být několik nezpracovaných výjimek na jedno vlákno.</span><span class="sxs-lookup"><span data-stu-id="709f8-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="709f8-111">`GetCurrentException`Vrátí aktuální výjimku.</span><span class="sxs-lookup"><span data-stu-id="709f8-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="709f8-112">Objekt výjimky a typ mohou změnit po celou dobu životnosti výjimky.</span><span class="sxs-lookup"><span data-stu-id="709f8-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="709f8-113">Například po je vyvolána výjimka typu x, modul CLR (CLR) může mít nedostatek paměti a povyšte ho na výjimku z důvodu nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="709f8-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="709f8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="709f8-114">Requirements</span></span>  
 <span data-ttu-id="709f8-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="709f8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="709f8-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="709f8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="709f8-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="709f8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="709f8-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="709f8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
