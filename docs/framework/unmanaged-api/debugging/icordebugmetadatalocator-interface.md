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
ms.openlocfilehash: dd31bf458dde043a04e24251cedcac585fd385f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793032"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="bec94-102">ICorDebugMetaDataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bec94-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="bec94-103">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="bec94-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bec94-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bec94-104">Methods</span></span>  
  
|<span data-ttu-id="bec94-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bec94-105">Method</span></span>|<span data-ttu-id="bec94-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bec94-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bec94-107">GetMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="bec94-107">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="bec94-108">Požádá ladicí program, aby vrátil úplnou cestu k modulu, jehož metadata jsou potřeba k dokončení operace, kterou ladicí program požaduje.</span><span class="sxs-lookup"><span data-stu-id="bec94-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bec94-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bec94-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bec94-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="bec94-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bec94-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bec94-111">Requirements</span></span>  
 <span data-ttu-id="bec94-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bec94-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bec94-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bec94-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bec94-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bec94-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bec94-115">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bec94-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec94-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bec94-116">See also</span></span>

- [<span data-ttu-id="bec94-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bec94-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bec94-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="bec94-118">Debugging</span></span>](index.md)
