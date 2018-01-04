---
title: "ICorDebugSymbolProvider::GetCodeRange – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0bb2729ee5bc77842f658e38a2afbbb2b24da55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="b7cd5-102">ICorDebugSymbolProvider::GetCodeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="b7cd5-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="b7cd5-103">Získá metoda počáteční adresy a velikost relativní virtuální adresy (RVA) v metodu.</span><span class="sxs-lookup"><span data-stu-id="b7cd5-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7cd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7cd5-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7cd5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7cd5-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="b7cd5-106">[v] Relativní virtuální adresa (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="b7cd5-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="b7cd5-107">[out] Ukazatel na počáteční adresa metody.</span><span class="sxs-lookup"><span data-stu-id="b7cd5-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="b7cd5-108">Ukazatel na velikosti kódu – metoda (počet bajtů metoda kódu).</span><span class="sxs-lookup"><span data-stu-id="b7cd5-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7cd5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7cd5-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7cd5-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="b7cd5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7cd5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7cd5-111">Requirements</span></span>  
 <span data-ttu-id="b7cd5-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7cd5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7cd5-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7cd5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7cd5-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7cd5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7cd5-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7cd5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7cd5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7cd5-116">See Also</span></span>  
 [<span data-ttu-id="b7cd5-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7cd5-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="b7cd5-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b7cd5-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
