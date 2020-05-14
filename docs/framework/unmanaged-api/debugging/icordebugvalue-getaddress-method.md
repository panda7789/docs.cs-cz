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
ms.openlocfilehash: 467ba53f90081f0c3499fb22acab96b5e380a3f4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395834"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="6c39f-102">ICorDebugValue::GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="6c39f-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="6c39f-103">Získá adresu tohoto objektu "ICorDebugValue", který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="6c39f-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c39f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c39f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c39f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c39f-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="6c39f-106">mimo Ukazatel na `CORDB_ADDRESS` objekt, který určuje adresu tohoto objektu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6c39f-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c39f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c39f-107">Remarks</span></span>  
 <span data-ttu-id="6c39f-108">Pokud je hodnota nedostupná, vrátí se 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="6c39f-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="6c39f-109">K tomu může dojít, pokud je hodnota nejméně částečně v registrech nebo uložená v popisovači systému uvolňování paměti ( `GCHandle` ).</span><span class="sxs-lookup"><span data-stu-id="6c39f-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c39f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c39f-110">Requirements</span></span>  
 <span data-ttu-id="6c39f-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c39f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c39f-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6c39f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c39f-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6c39f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c39f-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c39f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c39f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c39f-115">See also</span></span>
