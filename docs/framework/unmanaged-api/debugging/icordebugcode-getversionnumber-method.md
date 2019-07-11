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
ms.openlocfilehash: 155a8d5465e0fb19c55c9d11b67c6031c2b2c4a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747519"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="ae417-102">ICorDebugCode::GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="ae417-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="ae417-103">Získá počet založen na jedničce, která identifikuje verzi kódu, který představuje tento "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="ae417-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae417-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae417-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae417-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae417-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="ae417-106">[out] Ukazatel na číslo verze kódu.</span><span class="sxs-lookup"><span data-stu-id="ae417-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae417-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae417-107">Remarks</span></span>  
 <span data-ttu-id="ae417-108">Číslo verze se zvýší pokaždé, když operace edit-and-continue (EnC) je prováděno v kódu.</span><span class="sxs-lookup"><span data-stu-id="ae417-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae417-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae417-109">Requirements</span></span>  
 <span data-ttu-id="ae417-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae417-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae417-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae417-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae417-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae417-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae417-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae417-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae417-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae417-114">See also</span></span>
