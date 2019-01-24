---
title: ICorDebugCode2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a5c28ec6c447f3fc3305e0faf51aa868d5a4c17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499970"
---
# <a name="icordebugcode2-interface1"></a><span data-ttu-id="a1e83-102">ICorDebugCode2 Interface1</span><span class="sxs-lookup"><span data-stu-id="a1e83-102">ICorDebugCode2 Interface1</span></span>
<span data-ttu-id="a1e83-103">Poskytuje metody, které rozšiřují možnosti "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="a1e83-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1e83-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1e83-104">Methods</span></span>  
  
|<span data-ttu-id="a1e83-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1e83-105">Method</span></span>|<span data-ttu-id="a1e83-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a1e83-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1e83-107">GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="a1e83-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="a1e83-108">Získá bloky kódu, ze kterých je tento objekt kódu sestaven.</span><span class="sxs-lookup"><span data-stu-id="a1e83-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="a1e83-109">GetCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="a1e83-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="a1e83-110">Získá příznaky určující podmínky, za kterých byl tento objekt kódu buď kompilován just-in-time (JIT), nebo generován pomocí generátoru nativních bitových kopií (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="a1e83-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1e83-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1e83-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1e83-112">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="a1e83-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1e83-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1e83-113">Requirements</span></span>  
 <span data-ttu-id="a1e83-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1e83-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1e83-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1e83-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1e83-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1e83-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1e83-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1e83-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e83-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1e83-118">See also</span></span>

- [<span data-ttu-id="a1e83-119">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1e83-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="a1e83-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a1e83-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
