---
title: ICorDebugGenericValue – rozhraní 1
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
ms.openlocfilehash: ce4c1b73ab806958627bb68bfdcfcae890bc5e67
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709829"
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="83215-102">ICorDebugGenericValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="83215-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="83215-103">Podtřída ICorDebugValue"", která se vztahuje na všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="83215-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="83215-104">Toto rozhraní poskytuje metody Get a Set pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="83215-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="83215-105">Metody</span><span class="sxs-lookup"><span data-stu-id="83215-105">Methods</span></span>  
  
|<span data-ttu-id="83215-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="83215-106">Method</span></span>|<span data-ttu-id="83215-107">Popis</span><span class="sxs-lookup"><span data-stu-id="83215-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="83215-108">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="83215-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="83215-109">Hodnota se zkopíruje do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="83215-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="83215-110">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="83215-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="83215-111">Zkopíruje nové hodnoty ze zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="83215-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83215-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83215-112">Remarks</span></span>  
 <span data-ttu-id="83215-113">`ICorDebugGenericValue` je dílčí rozhraní, protože je bez podpory vzdáleného přístupu.</span><span class="sxs-lookup"><span data-stu-id="83215-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="83215-114">Pro typy odkazů hodnota je odkaz, nikoli obsah odkazu.</span><span class="sxs-lookup"><span data-stu-id="83215-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="83215-115">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="83215-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83215-116">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="83215-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83215-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83215-117">Requirements</span></span>  
 <span data-ttu-id="83215-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83215-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83215-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83215-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83215-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83215-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83215-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83215-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83215-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83215-122">See also</span></span>

- [<span data-ttu-id="83215-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="83215-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
