---
title: ICorDebugSymbolProvider::GetCodeRange – metoda
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bfaa8ce16a3874d28e06bdb77f1e903548c0a03b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684785"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="80f57-102">ICorDebugSymbolProvider::GetCodeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="80f57-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="80f57-103">Získá počáteční adresa metody a velikost relativní virtuální adresu (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="80f57-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80f57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80f57-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80f57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80f57-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="80f57-106">[in] Relativní virtuální adresu (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="80f57-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="80f57-107">[out] Ukazatel na počáteční adresu metody.</span><span class="sxs-lookup"><span data-stu-id="80f57-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="80f57-108">Ukazatel na velikost kódu metody (počet bajtů kódu metody).</span><span class="sxs-lookup"><span data-stu-id="80f57-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80f57-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80f57-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80f57-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="80f57-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80f57-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80f57-111">Requirements</span></span>  
 <span data-ttu-id="80f57-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80f57-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80f57-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80f57-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80f57-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80f57-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80f57-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80f57-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f57-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80f57-116">See also</span></span>
- [<span data-ttu-id="80f57-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80f57-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="80f57-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="80f57-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
