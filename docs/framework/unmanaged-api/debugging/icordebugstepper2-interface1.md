---
title: ICorDebugStepper2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
ms.openlocfilehash: ef7aa164c43751fa39e49d0ab6486a9f29e23c20
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379477"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="89fe8-102">ICorDebugStepper2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89fe8-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="89fe8-103">Poskytuje podporu pro ladění pouze můj kód (JMC).</span><span class="sxs-lookup"><span data-stu-id="89fe8-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89fe8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="89fe8-104">Methods</span></span>  
  
|<span data-ttu-id="89fe8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="89fe8-105">Method</span></span>|<span data-ttu-id="89fe8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="89fe8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89fe8-107">SetJMC – metoda</span><span class="sxs-lookup"><span data-stu-id="89fe8-107">SetJMC Method</span></span>](icordebugstepper2-setjmc-method.md)|<span data-ttu-id="89fe8-108">Nastaví hodnotu, která určuje, zda jsou tyto ICorDebugStepper kroky pouze prostřednictvím kódu, který je vytvořen vývojářem aplikace.</span><span class="sxs-lookup"><span data-stu-id="89fe8-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89fe8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89fe8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89fe8-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="89fe8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89fe8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89fe8-111">Requirements</span></span>  
 <span data-ttu-id="89fe8-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89fe8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89fe8-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="89fe8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89fe8-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="89fe8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89fe8-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89fe8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89fe8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="89fe8-116">See also</span></span>

- [<span data-ttu-id="89fe8-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89fe8-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
