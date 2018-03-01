---
title: "ICorDebugType2 rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d44514586a2e91dad3486b6dc04c26946148885
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="ee208-102">ICorDebugType2 rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee208-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="ee208-103">Rozšiřuje rozhraní ICorDebugType načíst identifikátor typu základní typ nebo komplexní typ (definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="ee208-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee208-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ee208-104">Methods</span></span>  
  
|<span data-ttu-id="ee208-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee208-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="ee208-106">GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="ee208-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="ee208-107">Získá [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento typ.</span><span class="sxs-lookup"><span data-stu-id="ee208-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee208-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee208-108">Remarks</span></span>  
 <span data-ttu-id="ee208-109">Toto rozhraní je logické rozšíření rozhraní ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="ee208-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee208-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="ee208-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee208-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee208-111">Example</span></span>  
 <span data-ttu-id="ee208-112">Následující fragment kódu ukazuje použití [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="ee208-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="ee208-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee208-113">Requirements</span></span>  
 <span data-ttu-id="ee208-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee208-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee208-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee208-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee208-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee208-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee208-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee208-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee208-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee208-118">See Also</span></span>  
 [<span data-ttu-id="ee208-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ee208-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
