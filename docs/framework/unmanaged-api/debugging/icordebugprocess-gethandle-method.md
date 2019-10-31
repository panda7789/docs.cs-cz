---
title: ICorDebugProcess::GetHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: e4061580d59b0cf2a6e6e481d5242005e9452caf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128876"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="dcdcc-102">ICorDebugProcess::GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="dcdcc-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="dcdcc-103">Získá popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="dcdcc-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcdcc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcdcc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcdcc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcdcc-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="dcdcc-106">mimo Ukazatel na `HPROCESS`, který je popisovačem procesu.</span><span class="sxs-lookup"><span data-stu-id="dcdcc-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcdcc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcdcc-107">Remarks</span></span>  
 <span data-ttu-id="dcdcc-108">Načtený popisovač je vlastněn rozhraním pro ladění.</span><span class="sxs-lookup"><span data-stu-id="dcdcc-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="dcdcc-109">Ladicí program by měl před použitím Duplikovat popisovač.</span><span class="sxs-lookup"><span data-stu-id="dcdcc-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcdcc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcdcc-110">Requirements</span></span>  
 <span data-ttu-id="dcdcc-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcdcc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcdcc-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dcdcc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcdcc-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dcdcc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcdcc-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcdcc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
