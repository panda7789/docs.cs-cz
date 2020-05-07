---
title: ICorDebugCode2 – rozhraní
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
ms.openlocfilehash: 39767ea2603018d088aaefc5da32879aaf49fee6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893488"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="0d156-102">ICorDebugCode2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d156-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="0d156-103">Poskytuje metody, které rozšiřuje možnosti "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="0d156-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d156-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0d156-104">Methods</span></span>  
  
|<span data-ttu-id="0d156-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0d156-105">Method</span></span>|<span data-ttu-id="0d156-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0d156-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d156-107">GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="0d156-107">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="0d156-108">Získá bloky kódu, ze kterých je tento objekt kódu sestaven.</span><span class="sxs-lookup"><span data-stu-id="0d156-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="0d156-109">GetCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="0d156-109">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="0d156-110">Získá příznaky určující podmínky, za kterých byl tento objekt kódu buď kompilován just-in-time (JIT), nebo generován pomocí generátoru nativních bitových kopií (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="0d156-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d156-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d156-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d156-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0d156-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d156-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d156-113">Requirements</span></span>  
 <span data-ttu-id="0d156-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d156-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d156-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0d156-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d156-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0d156-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d156-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d156-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d156-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d156-118">See also</span></span>

- [<span data-ttu-id="0d156-119">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d156-119">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="0d156-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d156-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
