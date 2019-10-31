---
title: ICorDebugClass2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: cb2ab28824d209dd1eed627600e30e9ddb0d7c7a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125722"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="333cd-102">ICorDebugClass2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="333cd-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="333cd-103">Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="333cd-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="333cd-104">Toto rozhraní rozšiřuje [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="333cd-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="333cd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="333cd-105">Methods</span></span>  
  
|<span data-ttu-id="333cd-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="333cd-106">Method</span></span>|<span data-ttu-id="333cd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="333cd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="333cd-108">GetParameterizedType – metoda</span><span class="sxs-lookup"><span data-stu-id="333cd-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="333cd-109">Získá deklaraci typu pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="333cd-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="333cd-110">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="333cd-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="333cd-111">Pro každou metodu této třídy nastaví hodnotu, která označuje, zda je metoda uživatelem definovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="333cd-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="333cd-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="333cd-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="333cd-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="333cd-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="333cd-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="333cd-114">Requirements</span></span>  
 <span data-ttu-id="333cd-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="333cd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="333cd-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="333cd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="333cd-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="333cd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="333cd-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="333cd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="333cd-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="333cd-119">See also</span></span>

- [<span data-ttu-id="333cd-120">Rozhraní ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="333cd-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="333cd-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="333cd-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
