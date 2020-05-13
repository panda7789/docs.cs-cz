---
title: ICorDebugMetaDataLocator – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
ms.openlocfilehash: 7b7b7a42edea775d1aaa850ccfc532ef86749991
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210020"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="ede4c-102">ICorDebugMetaDataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ede4c-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="ede4c-103">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="ede4c-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ede4c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ede4c-104">Methods</span></span>  
  
|<span data-ttu-id="ede4c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-105">Method</span></span>|<span data-ttu-id="ede4c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ede4c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ede4c-107">GetMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-107">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="ede4c-108">Požádá ladicí program, aby vrátil úplnou cestu k modulu, jehož metadata jsou potřeba k dokončení operace, kterou ladicí program požaduje.</span><span class="sxs-lookup"><span data-stu-id="ede4c-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ede4c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ede4c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ede4c-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="ede4c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede4c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ede4c-111">Requirements</span></span>  
 <span data-ttu-id="ede4c-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ede4c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede4c-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ede4c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ede4c-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ede4c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ede4c-115">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ede4c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede4c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ede4c-116">See also</span></span>

- [<span data-ttu-id="ede4c-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ede4c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ede4c-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="ede4c-118">Debugging</span></span>](index.md)
