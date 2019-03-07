---
title: ICorDebugCode::GetVersionNumber – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e1f67dde8193ff97bff835f4b653a61baa0a2d7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487782"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="b4ca6-102">ICorDebugCode::GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="b4ca6-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="b4ca6-103">Získá počet založen na jedničce, která identifikuje verzi kódu, který představuje tento "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="b4ca6-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4ca6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4ca6-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4ca6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4ca6-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="b4ca6-106">[out] Ukazatel na číslo verze kódu.</span><span class="sxs-lookup"><span data-stu-id="b4ca6-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4ca6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4ca6-107">Remarks</span></span>  
 <span data-ttu-id="b4ca6-108">Číslo verze se zvýší pokaždé, když operace edit-and-continue (EnC) je prováděno v kódu.</span><span class="sxs-lookup"><span data-stu-id="b4ca6-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4ca6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4ca6-109">Requirements</span></span>  
 <span data-ttu-id="b4ca6-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4ca6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4ca6-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4ca6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4ca6-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4ca6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4ca6-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4ca6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ca6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4ca6-114">See also</span></span>

