---
title: ICorDebugInternalFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
ms.openlocfilehash: 332bc99795c0a4c896b60c61941a5a24b3f4accc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209939"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="bc417-102">ICorDebugInternalFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc417-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="bc417-103">Představuje interní rámec modulu runtime v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bc417-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="bc417-104">Toto rozhraní je podtřídou rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="bc417-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc417-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bc417-105">Methods</span></span>  
  
|<span data-ttu-id="bc417-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="bc417-106">Method</span></span>|<span data-ttu-id="bc417-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bc417-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc417-108">GetFrameType – metoda</span><span class="sxs-lookup"><span data-stu-id="bc417-108">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="bc417-109">Získá typ tohoto interního rámce.</span><span class="sxs-lookup"><span data-stu-id="bc417-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc417-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc417-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc417-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="bc417-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc417-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc417-112">Requirements</span></span>  
 <span data-ttu-id="bc417-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc417-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc417-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc417-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc417-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bc417-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc417-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc417-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc417-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc417-117">See also</span></span>

- [<span data-ttu-id="bc417-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc417-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
