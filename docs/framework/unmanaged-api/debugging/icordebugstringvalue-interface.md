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
ms.openlocfilehash: 03ae6fba5d880b11baac695866853e0b3a4d8cc7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="2a311-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="2a311-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="2a311-103">Podtřídou třídy icordebugheapvalue –, která platí pro řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2a311-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a311-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2a311-104">Methods</span></span>  
  
|<span data-ttu-id="2a311-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2a311-105">Method</span></span>|<span data-ttu-id="2a311-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2a311-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a311-107">GetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="2a311-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="2a311-108">Získá počet znaků v řetězci odkazuje toto `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="2a311-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="2a311-109">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="2a311-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="2a311-110">Získá řetězec, který odkazuje toto `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="2a311-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a311-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a311-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a311-112">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2a311-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a311-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a311-113">Requirements</span></span>  
 <span data-ttu-id="2a311-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a311-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a311-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a311-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a311-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a311-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a311-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a311-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a311-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a311-118">See Also</span></span>  
 [<span data-ttu-id="2a311-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a311-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
