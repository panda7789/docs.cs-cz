---
title: ICorDebugValue3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: 5fa042223e47961dad0a6799ab8ca999ef76e285
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791082"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="d6877-102">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6877-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="d6877-103">Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" tak, aby poskytovala podporu pro pole, která jsou větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="d6877-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6877-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d6877-104">Methods</span></span>  
  
|<span data-ttu-id="d6877-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d6877-105">Method</span></span>|<span data-ttu-id="d6877-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d6877-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6877-107">GetSize64 – metoda</span><span class="sxs-lookup"><span data-stu-id="d6877-107">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="d6877-108">Získá velikost objektu `ICorDebugValue3` v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d6877-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6877-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6877-109">Remarks</span></span>  
 <span data-ttu-id="d6877-110">Metoda [ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md) vrátí velikost objektu, který je v rozsahu od 0 do 2 147 483 647 bajtů.</span><span class="sxs-lookup"><span data-stu-id="d6877-110">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="d6877-111">V .NET Framework 4,5 může velikost polí překročit 2 GB.</span><span class="sxs-lookup"><span data-stu-id="d6877-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="d6877-112">Rozhraní `ICorDebugValue3` umožňuje určit velikost těchto polí.</span><span class="sxs-lookup"><span data-stu-id="d6877-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6877-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6877-113">Requirements</span></span>  
 <span data-ttu-id="d6877-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6877-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6877-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d6877-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6877-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d6877-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6877-117">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6877-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6877-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6877-118">See also</span></span>

- [<span data-ttu-id="d6877-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d6877-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d6877-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="d6877-120">Debugging</span></span>](index.md)
