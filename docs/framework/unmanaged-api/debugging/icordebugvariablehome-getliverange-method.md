---
title: 'IcorDebugVariableHome:: GetLiveRange – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
ms.openlocfilehash: a8b8955d2f4c164031974f0d9021fb766ff2c030
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125118"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="7b559-102">IcorDebugVariableHome:: GetLiveRange – metoda</span><span class="sxs-lookup"><span data-stu-id="7b559-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="7b559-103">Získá nativní rozsah, ve kterém je tato proměnná živá.</span><span class="sxs-lookup"><span data-stu-id="7b559-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b559-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b559-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b559-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b559-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="7b559-106">mimo Logický posun, při kterém je proměnná nejprve aktivní.</span><span class="sxs-lookup"><span data-stu-id="7b559-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="7b559-107">mimo Logický posun bezprostředně za bodem, kde je proměnná naposledy aktivní.</span><span class="sxs-lookup"><span data-stu-id="7b559-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b559-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b559-108">Requirements</span></span>  
 <span data-ttu-id="7b559-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b559-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b559-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7b559-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b559-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7b559-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b559-112">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b559-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b559-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b559-113">See also</span></span>

- [<span data-ttu-id="7b559-114">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b559-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
