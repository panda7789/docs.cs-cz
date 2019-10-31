---
title: ICorDebugInternalFrame::GetFrameType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: b7a33fd6e2178e0e9188b81f516b231702fb6460
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122718"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="2eab7-102">ICorDebugInternalFrame::GetFrameType – metoda</span><span class="sxs-lookup"><span data-stu-id="2eab7-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="2eab7-103">Získá typ tohoto interního rámce.</span><span class="sxs-lookup"><span data-stu-id="2eab7-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eab7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2eab7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2eab7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2eab7-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="2eab7-106">mimo Ukazatel na hodnotu výčtu CorDebugInternalFrameType –, která určuje typ vnitřního rámce reprezentovaného tímto objektem `ICorDebugInternalFrame`.</span><span class="sxs-lookup"><span data-stu-id="2eab7-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2eab7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2eab7-107">Remarks</span></span>  
 <span data-ttu-id="2eab7-108">Interní typ rámce nikdy nebude STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="2eab7-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="2eab7-109">Ladicí programy by měly korektně ignorovat nerozpoznané typy vnitřních rámců.</span><span class="sxs-lookup"><span data-stu-id="2eab7-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eab7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2eab7-110">Requirements</span></span>  
 <span data-ttu-id="2eab7-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eab7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eab7-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2eab7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2eab7-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2eab7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2eab7-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eab7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
