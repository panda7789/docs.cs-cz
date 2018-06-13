---
title: ICorDebugGenericValue Interface1
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
ms.openlocfilehash: 0081f020da673023e2c35f9599e9682215e2c9d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415061"
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="681c3-102">ICorDebugGenericValue Interface1</span><span class="sxs-lookup"><span data-stu-id="681c3-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="681c3-103">Podtřídou třídy "ICorDebugValue", která se použije pro všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="681c3-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="681c3-104">Toto rozhraní poskytuje metody Get a Set pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="681c3-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="681c3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="681c3-105">Methods</span></span>  
  
|<span data-ttu-id="681c3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="681c3-106">Method</span></span>|<span data-ttu-id="681c3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="681c3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="681c3-108">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="681c3-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="681c3-109">Hodnotu se zkopíruje do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="681c3-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="681c3-110">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="681c3-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="681c3-111">Zkopíruje novou hodnotu ze zadaného vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="681c3-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="681c3-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="681c3-112">Remarks</span></span>  
 <span data-ttu-id="681c3-113">`ICorDebugGenericValue` je dílčí rozhraní, protože je jiný učinit vzdáleným.</span><span class="sxs-lookup"><span data-stu-id="681c3-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="681c3-114">U typů odkazu hodnota je odkaz na spíše než odkaz na obsah.</span><span class="sxs-lookup"><span data-stu-id="681c3-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="681c3-115">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="681c3-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="681c3-116">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="681c3-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="681c3-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="681c3-117">Requirements</span></span>  
 <span data-ttu-id="681c3-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="681c3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="681c3-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="681c3-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="681c3-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="681c3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="681c3-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="681c3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681c3-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="681c3-122">See Also</span></span>  
    
 [<span data-ttu-id="681c3-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="681c3-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
