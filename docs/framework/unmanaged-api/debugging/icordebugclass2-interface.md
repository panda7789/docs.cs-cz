---
title: ICorDebugClass2 Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb70016560f453caf7a7a3eed3e1aa6b5fc9f0ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557360"
---
# <a name="icordebugclass2-interface1"></a><span data-ttu-id="e2349-102">ICorDebugClass2 Interface1</span><span class="sxs-lookup"><span data-stu-id="e2349-102">ICorDebugClass2 Interface1</span></span>
<span data-ttu-id="e2349-103">Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="e2349-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="e2349-104">Toto rozhraní rozšiřuje [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e2349-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2349-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e2349-105">Methods</span></span>  
  
|<span data-ttu-id="e2349-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2349-106">Method</span></span>|<span data-ttu-id="e2349-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e2349-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2349-108">GetParameterizedType – metoda</span><span class="sxs-lookup"><span data-stu-id="e2349-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="e2349-109">Získá deklarace typu pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="e2349-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="e2349-110">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="e2349-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="e2349-111">Pro jednotlivé metody této třídy nastaví hodnotu určující, zda je metoda uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="e2349-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2349-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2349-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2349-113">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="e2349-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2349-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2349-114">Requirements</span></span>  
 <span data-ttu-id="e2349-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2349-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2349-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2349-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2349-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2349-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2349-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2349-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2349-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2349-119">See also</span></span>
- [<span data-ttu-id="e2349-120">ICorDebugClass – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="e2349-120">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="e2349-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e2349-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
