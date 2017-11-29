---
title: "ICorDebugDataTarget2::GetImageFromPointer – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e56f65aea12c71145c99a9a195b910ef2876aa09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="36b83-102">ICorDebugDataTarget2::GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="36b83-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="36b83-103">Vrátí základní adresa modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="36b83-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36b83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36b83-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36b83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36b83-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="36b83-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje adresu v modulu.</span><span class="sxs-lookup"><span data-stu-id="36b83-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="36b83-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="36b83-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="36b83-108">Ukazatel na velikost modulu.</span><span class="sxs-lookup"><span data-stu-id="36b83-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36b83-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36b83-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36b83-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="36b83-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36b83-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36b83-111">Requirements</span></span>  
 <span data-ttu-id="36b83-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36b83-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36b83-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36b83-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36b83-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36b83-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36b83-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36b83-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b83-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="36b83-116">See Also</span></span>  
 [<span data-ttu-id="36b83-117">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="36b83-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="36b83-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="36b83-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
