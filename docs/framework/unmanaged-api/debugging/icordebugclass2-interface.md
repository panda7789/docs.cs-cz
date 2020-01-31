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
ms.openlocfilehash: 795e9f4862992d95eeef98a986545cca47d828c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784142"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="3ecf5-102">ICorDebugClass2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ecf5-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="3ecf5-103">Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="3ecf5-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="3ecf5-104">Toto rozhraní rozšiřuje [ICorDebugClass](icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3ecf5-104">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ecf5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3ecf5-105">Methods</span></span>  
  
|<span data-ttu-id="3ecf5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3ecf5-106">Method</span></span>|<span data-ttu-id="3ecf5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3ecf5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ecf5-108">GetParameterizedType – metoda</span><span class="sxs-lookup"><span data-stu-id="3ecf5-108">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="3ecf5-109">Získá deklaraci typu pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="3ecf5-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="3ecf5-110">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="3ecf5-110">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="3ecf5-111">Pro každou metodu této třídy nastaví hodnotu, která označuje, zda je metoda uživatelem definovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="3ecf5-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ecf5-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ecf5-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ecf5-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3ecf5-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ecf5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ecf5-114">Requirements</span></span>  
 <span data-ttu-id="3ecf5-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ecf5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ecf5-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ecf5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ecf5-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3ecf5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ecf5-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ecf5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ecf5-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ecf5-119">See also</span></span>

- [<span data-ttu-id="3ecf5-120">Rozhraní ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="3ecf5-120">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="3ecf5-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3ecf5-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
