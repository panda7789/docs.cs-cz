---
title: ICorDebugArrayValue::GetElementType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementType
helpviewer_keywords:
- ICorDebugArrayValue::GetElementType method [.NET Framework debugging]
- GetElementType method [.NET Framework debugging]
ms.assetid: ed71961e-ae9b-4dfc-9554-06637696d697
topic_type:
- apiref
ms.openlocfilehash: d4de3405f84bfc08f7e1519bc7f9604eb1f5a14e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088294"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="1764b-102">ICorDebugArrayValue::GetElementType – metoda</span><span class="sxs-lookup"><span data-stu-id="1764b-102">ICorDebugArrayValue::GetElementType Method</span></span>
<span data-ttu-id="1764b-103">Získá hodnotu, která označuje jednoduchý typ prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="1764b-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1764b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1764b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1764b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1764b-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="1764b-106">mimo Ukazatel na hodnotu výčtu CorElementType –, která určuje typ.</span><span class="sxs-lookup"><span data-stu-id="1764b-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1764b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1764b-107">Requirements</span></span>  
 <span data-ttu-id="1764b-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1764b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1764b-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1764b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1764b-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1764b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1764b-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1764b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
