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
ms.openlocfilehash: 3a4da6f958407c0b704ffb7372a77b7f022fc824
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379772"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="b0dc7-102">ICorDebugThread::GetCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="b0dc7-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="b0dc7-103">Získá ukazatel rozhraní na objekt ICorDebugValue, který představuje výjimku, která je aktuálně vyvolána spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0dc7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0dc7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0dc7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0dc7-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="b0dc7-106">mimo Ukazatel na adresu `ICorDebugValue` objektu, který představuje výjimku, která je aktuálně vyvolána spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0dc7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0dc7-107">Remarks</span></span>  
 <span data-ttu-id="b0dc7-108">Objekt výjimky bude existovat od okamžiku, kdy je výjimka vyvolána až do konce `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="b0dc7-109">Vyhodnocení funkce, která je prováděna metodami ICorDebugEval, vyčistí objekt výjimky při instalaci a obnoví ho při dokončení.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="b0dc7-110">Výjimky mohou být vnořené (například pokud je vyvolána výjimka ve filtru nebo ve vyhodnocení funkce), takže v jednom vlákně může existovat několik zbývajících výjimek.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="b0dc7-111">`GetCurrentException`Vrátí aktuální výjimku.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="b0dc7-112">Objekt výjimky a typ se mohou změnit po celou dobu životnosti výjimky.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="b0dc7-113">Například po vyjímka typu x může modul CLR (Common Language Runtime) mít nedostatek paměti a propagovat jej na výjimku mimo paměť.</span><span class="sxs-lookup"><span data-stu-id="b0dc7-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0dc7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0dc7-114">Requirements</span></span>  
 <span data-ttu-id="b0dc7-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0dc7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0dc7-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0dc7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0dc7-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b0dc7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0dc7-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0dc7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
