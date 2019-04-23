---
title: ICorDebugSymbolProvider::GetCodeRange – metoda
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52fd0e9dac1d255197909d153099d9c6f2bd8ff7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212931"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="b203b-102">ICorDebugSymbolProvider::GetCodeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="b203b-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="b203b-103">Získá počáteční adresa metody a velikost relativní virtuální adresu (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="b203b-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b203b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b203b-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b203b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b203b-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="b203b-106">[in] Relativní virtuální adresu (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="b203b-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="b203b-107">[out] Ukazatel na počáteční adresu metody.</span><span class="sxs-lookup"><span data-stu-id="b203b-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="b203b-108">Ukazatel na velikost kódu metody (počet bajtů kódu metody).</span><span class="sxs-lookup"><span data-stu-id="b203b-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b203b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b203b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b203b-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b203b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b203b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b203b-111">Requirements</span></span>  
 <span data-ttu-id="b203b-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b203b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b203b-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b203b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b203b-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b203b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b203b-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b203b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b203b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b203b-116">See also</span></span>

- [<span data-ttu-id="b203b-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b203b-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b203b-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b203b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
