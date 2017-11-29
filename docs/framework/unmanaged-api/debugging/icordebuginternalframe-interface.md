---
title: "Icordebuginternalframe – Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame
helpviewer_keywords: ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a05ba891e734fbf5a94b2a1f91e29d484e1c788b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuginternalframe-interface1"></a><span data-ttu-id="49910-102">Icordebuginternalframe – Interface1</span><span class="sxs-lookup"><span data-stu-id="49910-102">ICorDebugInternalFrame Interface1</span></span>
<span data-ttu-id="49910-103">Představuje modul runtime interní rámce v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="49910-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="49910-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="49910-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49910-105">Metody</span><span class="sxs-lookup"><span data-stu-id="49910-105">Methods</span></span>  
  
|<span data-ttu-id="49910-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="49910-106">Method</span></span>|<span data-ttu-id="49910-107">Popis</span><span class="sxs-lookup"><span data-stu-id="49910-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49910-108">Getframetype – metoda</span><span class="sxs-lookup"><span data-stu-id="49910-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="49910-109">Získá typ této interní rámce.</span><span class="sxs-lookup"><span data-stu-id="49910-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49910-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49910-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49910-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="49910-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49910-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49910-112">Requirements</span></span>  
 <span data-ttu-id="49910-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49910-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49910-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49910-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49910-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49910-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49910-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49910-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49910-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="49910-117">See Also</span></span>  
 [<span data-ttu-id="49910-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="49910-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
