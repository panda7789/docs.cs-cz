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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 015085cff23028814937dfef9aea19af7438b4f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750602"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="88826-102">ICorDebugClass2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88826-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="88826-103">Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="88826-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="88826-104">Toto rozhraní rozšiřuje [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="88826-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88826-105">Metody</span><span class="sxs-lookup"><span data-stu-id="88826-105">Methods</span></span>  
  
|<span data-ttu-id="88826-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="88826-106">Method</span></span>|<span data-ttu-id="88826-107">Popis</span><span class="sxs-lookup"><span data-stu-id="88826-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88826-108">GetParameterizedType – metoda</span><span class="sxs-lookup"><span data-stu-id="88826-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="88826-109">Získá deklarace typu pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="88826-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="88826-110">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="88826-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="88826-111">Pro jednotlivé metody této třídy nastaví hodnotu určující, zda je metoda uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="88826-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88826-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88826-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88826-113">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="88826-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88826-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88826-114">Requirements</span></span>  
 <span data-ttu-id="88826-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88826-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88826-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88826-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88826-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88826-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88826-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88826-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88826-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88826-119">See also</span></span>

- [<span data-ttu-id="88826-120">Icordebugclass – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88826-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="88826-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="88826-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
