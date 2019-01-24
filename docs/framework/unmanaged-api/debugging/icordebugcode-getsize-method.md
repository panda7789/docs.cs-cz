---
title: ICorDebugCode::GetSize – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a9a43735ec80821c2380b824bfced99113cf08f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651094"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="e313e-102">ICorDebugCode::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="e313e-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="e313e-103">Získá velikost v bajtech binárního kódu představovaného podle této "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="e313e-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e313e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e313e-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e313e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e313e-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="e313e-106">[out] Ukazatel na velikost v bajtech binárního souboru kódu, který tato `ICorDebugCode` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="e313e-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e313e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e313e-107">Requirements</span></span>  
 <span data-ttu-id="e313e-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e313e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e313e-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e313e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e313e-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e313e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e313e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e313e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e313e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e313e-112">See also</span></span>

