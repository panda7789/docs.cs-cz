---
title: ICorDebugCode::GetAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
ms.openlocfilehash: df73663f714b0c1c3d3ae5dfb53e8e84196a8f37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125685"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="3229d-102">ICorDebugCode::GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="3229d-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="3229d-103">Získá relativní virtuální adresu (RVA) segmentu kódu, který představuje toto rozhraní "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="3229d-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3229d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3229d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3229d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3229d-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="3229d-106">mimo Ukazatel na adresu RVA segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="3229d-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3229d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3229d-107">Requirements</span></span>  
 <span data-ttu-id="3229d-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3229d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3229d-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3229d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3229d-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3229d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3229d-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3229d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
