---
title: ICorDebugValue::GetAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac550ee7b1d66612557b30d15c275c90cf09b8af
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187325"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="d56e2-102">ICorDebugValue::GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="d56e2-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="d56e2-103">Získá adresu tohoto objektu "ICorDebugValue", který se právě laděn.</span><span class="sxs-lookup"><span data-stu-id="d56e2-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d56e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d56e2-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d56e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d56e2-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="d56e2-106">[out] Ukazatel `CORDB_ADDRESS` objekt, který určuje adresu tohoto objektu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d56e2-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d56e2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d56e2-107">Remarks</span></span>  
 <span data-ttu-id="d56e2-108">Pokud je hodnota není k dispozici, vrátí se 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="d56e2-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="d56e2-109">To může nastat, pokud je hodnota aspoň částečně v registrech do nebo popisovač systému uvolňování paměti (`GCHandle`).</span><span class="sxs-lookup"><span data-stu-id="d56e2-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d56e2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d56e2-110">Requirements</span></span>  
 <span data-ttu-id="d56e2-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d56e2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d56e2-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d56e2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d56e2-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d56e2-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d56e2-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d56e2-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d56e2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d56e2-115">See also</span></span>
