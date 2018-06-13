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
ms.openlocfilehash: 905e88eb2f43850124414a42bb4e729158f9555a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405382"
---
# <a name="icordebugclass2-interface1"></a><span data-ttu-id="3e5b1-102">ICorDebugClass2 Interface1</span><span class="sxs-lookup"><span data-stu-id="3e5b1-102">ICorDebugClass2 Interface1</span></span>
<span data-ttu-id="3e5b1-103">Představuje obecné třídy nebo typu třídu pomocí parametru metody <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="3e5b1-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="3e5b1-104">Toto rozhraní rozšiřuje [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3e5b1-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e5b1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3e5b1-105">Methods</span></span>  
  
|<span data-ttu-id="3e5b1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3e5b1-106">Method</span></span>|<span data-ttu-id="3e5b1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3e5b1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e5b1-108">GetParameterizedType – metoda</span><span class="sxs-lookup"><span data-stu-id="3e5b1-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="3e5b1-109">Získá deklarace typu pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="3e5b1-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="3e5b1-110">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="3e5b1-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="3e5b1-111">Pro každou metodu této třídy nastaví hodnotu, která určuje, zda je metoda kód definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3e5b1-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e5b1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e5b1-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e5b1-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3e5b1-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e5b1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e5b1-114">Requirements</span></span>  
 <span data-ttu-id="3e5b1-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e5b1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e5b1-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e5b1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e5b1-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e5b1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e5b1-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e5b1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e5b1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e5b1-119">See Also</span></span>  
 [<span data-ttu-id="3e5b1-120">ICorDebugClass – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="3e5b1-120">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 [<span data-ttu-id="3e5b1-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3e5b1-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
