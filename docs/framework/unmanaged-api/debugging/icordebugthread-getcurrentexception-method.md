---
title: ICorDebugThread::GetCurrentException – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4baa4eb4da48b923ab0137ca25d9d819c94e33d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487340"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="4102a-102">ICorDebugThread::GetCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="4102a-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="4102a-103">Získá ukazatel rozhraní na ICorDebugValue objekt, který představuje výjimku, která je právě vyvolané spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="4102a-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4102a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4102a-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4102a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4102a-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="4102a-106">[out] Ukazatel na adresu `ICorDebugValue` objekt, který představuje výjimku, která je aktuálně vyvolané ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="4102a-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4102a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4102a-107">Remarks</span></span>  
 <span data-ttu-id="4102a-108">Objekt výjimky budou existovat od doby, kdy je vyvolána výjimka až do konce `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="4102a-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="4102a-109">Vyhodnocení funkce, které se provádí pomocí metody ICorDebugEval, bude vymažte objekt výjimky, instalace a obnovení při dokončení.</span><span class="sxs-lookup"><span data-stu-id="4102a-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="4102a-110">Výjimky mohou být vnořené (například pokud je vyvolána výjimka ve filtru nebo vyhodnocení funkce), takže může být více nezpracovaných výjimek v jednom vlákně.</span><span class="sxs-lookup"><span data-stu-id="4102a-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="4102a-111">`GetCurrentException` Vrátí aktuální výjimky.</span><span class="sxs-lookup"><span data-stu-id="4102a-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="4102a-112">Objekt výjimky a typ může změnit během životnosti výjimku.</span><span class="sxs-lookup"><span data-stu-id="4102a-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="4102a-113">Například po je vyvolána výjimka typu x, common language runtime (CLR) může mít nedostatek paměti a povýšit na výjimku mimo z důvodu nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="4102a-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4102a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4102a-114">Requirements</span></span>  
 <span data-ttu-id="4102a-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4102a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4102a-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4102a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4102a-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4102a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4102a-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4102a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
