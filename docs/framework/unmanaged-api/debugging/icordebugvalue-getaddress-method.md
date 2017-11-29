---
title: "ICorDebugValue::GetAddress – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetAddress
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7018dcb41f46d5407549f5c3d3029716781014e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="00cfa-102">ICorDebugValue::GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="00cfa-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="00cfa-103">Získá adresu tohoto objektu "ICorDebugValue", který je právě probíhá ladit.</span><span class="sxs-lookup"><span data-stu-id="00cfa-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00cfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00cfa-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00cfa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00cfa-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="00cfa-106">[out] Ukazatel na `CORDB_ADDRESS` objekt, který určuje adresu tohoto objektu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="00cfa-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00cfa-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00cfa-107">Remarks</span></span>  
 <span data-ttu-id="00cfa-108">Pokud hodnota není k dispozici, je vrácena 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="00cfa-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="00cfa-109">To může nastat, pokud je hodnota aspoň částečně v registrech nebo uložené v popisovač systém uvolňování paměti (`GCHandle`).</span><span class="sxs-lookup"><span data-stu-id="00cfa-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00cfa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00cfa-110">Requirements</span></span>  
 <span data-ttu-id="00cfa-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00cfa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00cfa-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00cfa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00cfa-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00cfa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00cfa-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00cfa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00cfa-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="00cfa-115">See Also</span></span>  
 
