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
ms.openlocfilehash: 312b8b005998da44feb5ae24ab4a0a17bb948a3f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138573"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="4349a-102">ICorDebugGenericValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4349a-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="4349a-103">Podtřída "ICorDebugValue", která se vztahuje na všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4349a-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="4349a-104">Toto rozhraní poskytuje metody Get a Set pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4349a-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4349a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4349a-105">Methods</span></span>  
  
|<span data-ttu-id="4349a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4349a-106">Method</span></span>|<span data-ttu-id="4349a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4349a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4349a-108">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="4349a-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="4349a-109">Zkopíruje hodnotu do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4349a-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="4349a-110">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="4349a-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="4349a-111">Zkopíruje novou hodnotu ze zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4349a-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4349a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4349a-112">Remarks</span></span>  
 <span data-ttu-id="4349a-113">`ICorDebugGenericValue` je dílčí rozhraní, protože se nejedná o nevzdáleněu.</span><span class="sxs-lookup"><span data-stu-id="4349a-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="4349a-114">U typů odkazů je hodnota odkaz spíše než obsah odkazu.</span><span class="sxs-lookup"><span data-stu-id="4349a-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="4349a-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4349a-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4349a-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4349a-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4349a-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4349a-117">Requirements</span></span>  
 <span data-ttu-id="4349a-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4349a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4349a-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4349a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4349a-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4349a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4349a-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4349a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4349a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4349a-122">See also</span></span>

- [<span data-ttu-id="4349a-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4349a-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
