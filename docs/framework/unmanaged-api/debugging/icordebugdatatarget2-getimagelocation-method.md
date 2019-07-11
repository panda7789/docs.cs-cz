---
title: ICorDebugDataTarget2::GetImageLocation – metoda
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 348c51507006fecfe756cb17fd0d6242617577d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750220"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="0bd68-102">ICorDebugDataTarget2::GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="0bd68-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="0bd68-103">Vrátí cestu modulu z modulu Základní adresa.</span><span class="sxs-lookup"><span data-stu-id="0bd68-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bd68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bd68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bd68-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="0bd68-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="0bd68-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="0bd68-107">[in] Počet znaků ve vyrovnávací paměti, která se zobrazí cesta modulu.</span><span class="sxs-lookup"><span data-stu-id="0bd68-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0bd68-108">[out] Ukazatel na počet znaků, které jsou zapsány do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0bd68-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="0bd68-109">[out] Cesta modulu.</span><span class="sxs-lookup"><span data-stu-id="0bd68-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bd68-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bd68-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bd68-111">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0bd68-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd68-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bd68-112">Requirements</span></span>  
 <span data-ttu-id="0bd68-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bd68-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd68-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bd68-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bd68-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bd68-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bd68-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bd68-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd68-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bd68-117">See also</span></span>

- [<span data-ttu-id="0bd68-118">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bd68-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="0bd68-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0bd68-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
