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
ms.openlocfilehash: 003b29501e8f22ed9010a9f16a4f7ee67bce03a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098946"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="5b227-102">ICorDebugCode::GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="5b227-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="5b227-103">Získá počet založen na jedničce, která identifikuje verzi kódu, který představuje tento "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="5b227-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b227-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b227-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b227-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b227-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="5b227-106">[out] Ukazatel na číslo verze kódu.</span><span class="sxs-lookup"><span data-stu-id="5b227-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b227-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b227-107">Remarks</span></span>  
 <span data-ttu-id="5b227-108">Číslo verze se zvýší pokaždé, když operace edit-and-continue (EnC) je prováděno v kódu.</span><span class="sxs-lookup"><span data-stu-id="5b227-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b227-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b227-109">Requirements</span></span>  
 <span data-ttu-id="5b227-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b227-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b227-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b227-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b227-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b227-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b227-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b227-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b227-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b227-114">See also</span></span>
