---
title: ICorDebugFunction2::SetJMCStatus – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: 758364b2d63343e464b727d5a1c1817533a6acea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137785"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="4b706-102">ICorDebugFunction2::SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="4b706-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="4b706-103">Označuje funkci představovanou tímto ICorDebugFunction2 pro Pouze můj kód krokování.</span><span class="sxs-lookup"><span data-stu-id="4b706-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b706-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b706-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b706-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b706-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="4b706-106">pro Nastavte na `true` pro označení funkce jako uživatelského kódu; v opačném případě nastavte na `false`.</span><span class="sxs-lookup"><span data-stu-id="4b706-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="4b706-107">Návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="4b706-107">Return Values</span></span>  
  
|<span data-ttu-id="4b706-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b706-108">HRESULT</span></span>|<span data-ttu-id="4b706-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4b706-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4b706-110">Funkce byla úspěšně označena.</span><span class="sxs-lookup"><span data-stu-id="4b706-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="4b706-111">Funkci nelze označit jako uživatelský kód, protože nemůže být Laděna.</span><span class="sxs-lookup"><span data-stu-id="4b706-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b706-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b706-112">Remarks</span></span>  
 <span data-ttu-id="4b706-113">Pouze můj kód stepper přeskočí jiný než uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="4b706-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="4b706-114">Uživatelský kód musí být podmnožinou laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="4b706-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b706-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b706-115">Requirements</span></span>  
 <span data-ttu-id="4b706-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b706-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b706-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4b706-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b706-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4b706-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b706-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b706-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
