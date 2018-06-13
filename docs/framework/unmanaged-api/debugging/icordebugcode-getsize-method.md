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
ms.openlocfilehash: 7c5d42aa7053c1138808775a16d820d5fef3b095
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410816"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="58fd8-102">ICorDebugCode::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="58fd8-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="58fd8-103">Získá velikost v bajtech binární kód reprezentována tento "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="58fd8-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58fd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58fd8-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58fd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58fd8-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="58fd8-106">[out] Ukazatel na velikost v bajtech binárního souboru kódu, který tato `ICorDebugCode` objekt představuje.</span><span class="sxs-lookup"><span data-stu-id="58fd8-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58fd8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58fd8-107">Requirements</span></span>  
 <span data-ttu-id="58fd8-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58fd8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58fd8-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58fd8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58fd8-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58fd8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58fd8-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58fd8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58fd8-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="58fd8-112">See Also</span></span>  
 
