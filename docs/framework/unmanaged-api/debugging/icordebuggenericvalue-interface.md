---
title: ICorDebugGenericValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36c2ed5529151a7ea18ccaffc2202ad6c69bcbd9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910234"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="cb382-102">ICorDebugGenericValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb382-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="cb382-103">Podtřída "ICorDebugValue", která se vztahuje na všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cb382-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="cb382-104">Toto rozhraní poskytuje metody Get a Set pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cb382-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb382-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cb382-105">Methods</span></span>  
  
|<span data-ttu-id="cb382-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="cb382-106">Method</span></span>|<span data-ttu-id="cb382-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cb382-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb382-108">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="cb382-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="cb382-109">Zkopíruje hodnotu do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cb382-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="cb382-110">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="cb382-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="cb382-111">Zkopíruje novou hodnotu ze zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cb382-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb382-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb382-112">Remarks</span></span>  
 <span data-ttu-id="cb382-113">`ICorDebugGenericValue`je dílčí rozhraní, protože se nejedná o nevzdáleněu.</span><span class="sxs-lookup"><span data-stu-id="cb382-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="cb382-114">U typů odkazů je hodnota odkaz spíše než obsah odkazu.</span><span class="sxs-lookup"><span data-stu-id="cb382-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="cb382-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="cb382-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb382-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="cb382-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb382-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb382-117">Requirements</span></span>  
 <span data-ttu-id="cb382-118">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb382-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb382-119">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb382-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb382-120">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb382-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb382-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb382-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb382-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb382-122">See also</span></span>

- [<span data-ttu-id="cb382-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cb382-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
