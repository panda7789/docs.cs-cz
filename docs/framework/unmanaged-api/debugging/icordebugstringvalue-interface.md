---
title: ICorDebugStringValue Interface1
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
ms.openlocfilehash: b9160b9013481de294e6c8dd032cfa2d0ebb405d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596836"
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="a0dd2-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="a0dd2-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="a0dd2-103">Podtřída ICorDebugHeapValue, které se týkají řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a0dd2-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0dd2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a0dd2-104">Methods</span></span>  
  
|<span data-ttu-id="a0dd2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a0dd2-105">Method</span></span>|<span data-ttu-id="a0dd2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a0dd2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0dd2-107">GetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="a0dd2-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="a0dd2-108">Získá počet znaků v řetězci odkazovaná tímto objektem `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="a0dd2-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="a0dd2-109">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="a0dd2-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="a0dd2-110">Získá řetězec, který odkazuje tento `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="a0dd2-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0dd2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0dd2-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0dd2-112">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="a0dd2-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0dd2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0dd2-113">Requirements</span></span>  
 <span data-ttu-id="a0dd2-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0dd2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0dd2-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0dd2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0dd2-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0dd2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0dd2-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0dd2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0dd2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0dd2-118">See also</span></span>
- [<span data-ttu-id="a0dd2-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a0dd2-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
