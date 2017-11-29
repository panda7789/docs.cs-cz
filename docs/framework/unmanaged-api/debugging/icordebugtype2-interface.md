---
title: "ICorDebugType2 rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType2
helpviewer_keywords: ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 658dd1541a1de852c3c001cc7fbb7954f6c7590f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="24f31-102">ICorDebugType2 rozhraní</span><span class="sxs-lookup"><span data-stu-id="24f31-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="24f31-103">Rozšiřuje rozhraní ICorDebugType načíst identifikátor typu základní typ nebo komplexní typ (definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="24f31-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24f31-104">Metody</span><span class="sxs-lookup"><span data-stu-id="24f31-104">Methods</span></span>  
  
|<span data-ttu-id="24f31-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="24f31-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="24f31-106">GetTypeId – metoda</span><span class="sxs-lookup"><span data-stu-id="24f31-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="24f31-107">Získá [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento typ.</span><span class="sxs-lookup"><span data-stu-id="24f31-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24f31-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24f31-108">Remarks</span></span>  
 <span data-ttu-id="24f31-109">Toto rozhraní je logické rozšíření rozhraní ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="24f31-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24f31-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="24f31-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24f31-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="24f31-111">Example</span></span>  
 <span data-ttu-id="24f31-112">Následující fragment kódu ukazuje použití [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="24f31-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="24f31-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24f31-113">Requirements</span></span>  
 <span data-ttu-id="24f31-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24f31-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24f31-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24f31-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24f31-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24f31-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24f31-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24f31-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f31-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="24f31-118">See Also</span></span>  
 [<span data-ttu-id="24f31-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="24f31-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
