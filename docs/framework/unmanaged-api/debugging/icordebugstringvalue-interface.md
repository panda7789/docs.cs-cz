---
title: ICorDebugStringValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6709b14ce8e7bc131f9feb7a277fb41851ee4352
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994263"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="d6dfe-102">ICorDebugStringValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6dfe-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="d6dfe-103">Podtřída ICorDebugHeapValue, které se týkají řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6dfe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d6dfe-104">Methods</span></span>  
  
|<span data-ttu-id="d6dfe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d6dfe-105">Method</span></span>|<span data-ttu-id="d6dfe-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d6dfe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6dfe-107">GetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="d6dfe-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="d6dfe-108">Získá počet znaků v řetězci odkazovaná tímto objektem `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="d6dfe-109">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="d6dfe-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="d6dfe-110">Získá řetězec, který odkazuje tento `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6dfe-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6dfe-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6dfe-112">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="d6dfe-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6dfe-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6dfe-113">Requirements</span></span>  
 <span data-ttu-id="d6dfe-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6dfe-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6dfe-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6dfe-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6dfe-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6dfe-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6dfe-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6dfe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6dfe-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6dfe-118">See also</span></span>

- [<span data-ttu-id="d6dfe-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d6dfe-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
