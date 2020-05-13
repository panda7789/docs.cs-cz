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
ms.openlocfilehash: 5537a48fd085ce98de855fa1ec0913e2637e58e0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376197"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="4ab9d-102">ICorDebugStringValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ab9d-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="4ab9d-103">Podtřída ICorDebugHeapValue, která se vztahuje na řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4ab9d-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4ab9d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4ab9d-104">Methods</span></span>  
  
|<span data-ttu-id="4ab9d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4ab9d-105">Method</span></span>|<span data-ttu-id="4ab9d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4ab9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4ab9d-107">GetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="4ab9d-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="4ab9d-108">Vrátí počet znaků v řetězci, na který odkazuje tento `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="4ab9d-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="4ab9d-109">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="4ab9d-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="4ab9d-110">Získá řetězec, na který odkazuje tento `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="4ab9d-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ab9d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ab9d-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ab9d-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4ab9d-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ab9d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ab9d-113">Requirements</span></span>  
 <span data-ttu-id="4ab9d-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ab9d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ab9d-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4ab9d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ab9d-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4ab9d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ab9d-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ab9d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab9d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ab9d-118">See also</span></span>

- [<span data-ttu-id="4ab9d-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ab9d-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
