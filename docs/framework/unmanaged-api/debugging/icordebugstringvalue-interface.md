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
ms.openlocfilehash: 2814f6164f383c36bb5b8e20ce8996b30eef0f1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421697"
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="c7d94-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="c7d94-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="c7d94-103">Podtřídou třídy icordebugheapvalue –, která platí pro řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c7d94-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7d94-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c7d94-104">Methods</span></span>  
  
|<span data-ttu-id="c7d94-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7d94-105">Method</span></span>|<span data-ttu-id="c7d94-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c7d94-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7d94-107">GetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="c7d94-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="c7d94-108">Získá počet znaků v řetězci odkazuje toto `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="c7d94-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="c7d94-109">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="c7d94-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="c7d94-110">Získá řetězec, který odkazuje toto `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="c7d94-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7d94-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7d94-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7d94-112">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c7d94-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d94-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7d94-113">Requirements</span></span>  
 <span data-ttu-id="c7d94-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7d94-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7d94-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7d94-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7d94-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7d94-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7d94-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7d94-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d94-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7d94-118">See Also</span></span>  
 [<span data-ttu-id="c7d94-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c7d94-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
