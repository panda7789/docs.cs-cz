---
title: ICorDebugAssemblyEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum
helpviewer_keywords:
- ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: 891ceb43-5161-421e-a0bf-299962fd7efd
topic_type:
- apiref
ms.openlocfilehash: 988637956b1176235618bf8f4aee7ecec9ce1187
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894838"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="5ed32-102">ICorDebugAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5ed32-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="5ed32-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="5ed32-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ed32-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5ed32-104">Methods</span></span>  
  
|<span data-ttu-id="5ed32-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5ed32-105">Method</span></span>|<span data-ttu-id="5ed32-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5ed32-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ed32-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="5ed32-107">Next Method</span></span>](icordebugassemblyenum-next-method.md)|<span data-ttu-id="5ed32-108">Získá zadaný počet `ICorDebugAssembly` instancí ve výčtu, počínaje od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="5ed32-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ed32-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ed32-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ed32-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="5ed32-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed32-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ed32-111">Requirements</span></span>  
 <span data-ttu-id="5ed32-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ed32-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed32-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5ed32-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ed32-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5ed32-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ed32-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed32-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed32-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ed32-116">See also</span></span>

- [<span data-ttu-id="5ed32-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5ed32-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
