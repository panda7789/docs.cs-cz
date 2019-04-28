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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49ced1b4be888c7550c3927d1b319ab2f0bef086
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763773"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="4b189-102">ICorDebugFunction2::SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="4b189-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="4b189-103">Označí funkci reprezentována tento icordebugfunction2 – pro volbu pouze vlastní kód krokování.</span><span class="sxs-lookup"><span data-stu-id="4b189-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b189-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b189-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b189-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b189-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="4b189-106">[in] Nastavte na `true` označit funkce jako uživatelského kódu; v opačném případě nastavte na `false`.</span><span class="sxs-lookup"><span data-stu-id="4b189-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="4b189-107">Návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="4b189-107">Return Values</span></span>  
  
|<span data-ttu-id="4b189-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b189-108">HRESULT</span></span>|<span data-ttu-id="4b189-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4b189-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4b189-110">Funkci byl úspěšně označen.</span><span class="sxs-lookup"><span data-stu-id="4b189-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="4b189-111">Funkci nelze označit jako uživatelský kód, protože není možné ladit.</span><span class="sxs-lookup"><span data-stu-id="4b189-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b189-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b189-112">Remarks</span></span>  
 <span data-ttu-id="4b189-113">Funkce pouze můj kód krokovač přeskočí neuživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="4b189-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="4b189-114">Kód uživatele musí být podmnožinou laditelný kód.</span><span class="sxs-lookup"><span data-stu-id="4b189-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b189-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b189-115">Requirements</span></span>  
 <span data-ttu-id="4b189-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b189-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b189-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b189-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b189-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b189-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b189-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b189-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
