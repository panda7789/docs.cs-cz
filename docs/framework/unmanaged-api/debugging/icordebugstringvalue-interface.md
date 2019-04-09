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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173989"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="63984-102">ICorDebugStringValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63984-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="63984-103">Podtřída ICorDebugHeapValue, které se týkají řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="63984-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63984-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63984-104">Methods</span></span>  
  
|<span data-ttu-id="63984-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63984-105">Method</span></span>|<span data-ttu-id="63984-106">Popis</span><span class="sxs-lookup"><span data-stu-id="63984-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63984-107">GetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="63984-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="63984-108">Získá počet znaků v řetězci odkazovaná tímto objektem `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="63984-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="63984-109">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="63984-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="63984-110">Získá řetězec, který odkazuje tento `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="63984-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63984-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63984-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63984-112">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="63984-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63984-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63984-113">Requirements</span></span>  
 <span data-ttu-id="63984-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63984-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63984-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63984-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63984-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63984-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="63984-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="63984-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="63984-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63984-118">See also</span></span>

- [<span data-ttu-id="63984-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63984-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
