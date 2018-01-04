---
title: ICorDebugStringValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStringValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStringValue
helpviewer_keywords: ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9958e6f5ad73658b278d83c78e58cf4166d5642
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="8b528-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="8b528-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="8b528-103">Podtřídou třídy icordebugheapvalue –, která platí pro řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8b528-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b528-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8b528-104">Methods</span></span>  
  
|<span data-ttu-id="8b528-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b528-105">Method</span></span>|<span data-ttu-id="8b528-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8b528-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b528-107">GetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="8b528-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="8b528-108">Získá počet znaků v řetězci odkazuje toto `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="8b528-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="8b528-109">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="8b528-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="8b528-110">Získá řetězec, který odkazuje toto `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="8b528-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b528-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b528-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b528-112">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="8b528-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b528-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b528-113">Requirements</span></span>  
 <span data-ttu-id="8b528-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b528-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b528-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b528-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b528-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b528-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b528-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b528-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b528-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b528-118">See Also</span></span>  
 [<span data-ttu-id="8b528-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8b528-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
