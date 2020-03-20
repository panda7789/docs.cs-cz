---
title: ICorDebugSymbolProvider::Metoda GetCodeRange
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: 81babade2ba499ce9326c664e83fa582abbd216f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178471"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="12c28-102">ICorDebugSymbolProvider::Metoda GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="12c28-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="12c28-103">Získá metodu počáteční adresu a velikost dané relativní virtuální adresu (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="12c28-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12c28-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12c28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12c28-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="12c28-106">[v] Relativní virtuální adresa (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="12c28-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="12c28-107">[out] Ukazatel na počáteční adresu metody.</span><span class="sxs-lookup"><span data-stu-id="12c28-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="12c28-108">Ukazatel na velikost kódu metody (počet bajtů kódu metody).</span><span class="sxs-lookup"><span data-stu-id="12c28-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12c28-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12c28-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12c28-110">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="12c28-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12c28-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12c28-111">Requirements</span></span>  
 <span data-ttu-id="12c28-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12c28-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12c28-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12c28-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12c28-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12c28-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12c28-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12c28-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c28-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="12c28-116">See also</span></span>

- [<span data-ttu-id="12c28-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12c28-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="12c28-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12c28-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
