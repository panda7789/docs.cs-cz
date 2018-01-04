---
title: "ICorDebugDataTarget2::GetImageLocation – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ab24b483eba4950b02efb89949d8c97d24b2774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="126d0-102">ICorDebugDataTarget2::GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="126d0-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="126d0-103">Vrátí cestu modul z modulu základní adresu.</span><span class="sxs-lookup"><span data-stu-id="126d0-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="126d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="126d0-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="126d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="126d0-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="126d0-106">[v] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="126d0-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="126d0-107">[v] Počet znaků ve vyrovnávací paměti, který přijme modul s cestou.</span><span class="sxs-lookup"><span data-stu-id="126d0-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="126d0-108">[out] Ukazatel na počet znaků, které jsou zapsány do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="126d0-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="126d0-109">[out] Cesta k modulu.</span><span class="sxs-lookup"><span data-stu-id="126d0-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="126d0-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="126d0-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="126d0-111">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="126d0-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="126d0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="126d0-112">Requirements</span></span>  
 <span data-ttu-id="126d0-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="126d0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="126d0-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="126d0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="126d0-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="126d0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="126d0-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="126d0-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126d0-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="126d0-117">See Also</span></span>  
 [<span data-ttu-id="126d0-118">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="126d0-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="126d0-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="126d0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
