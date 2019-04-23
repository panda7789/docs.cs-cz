---
title: ICorDebugDataTarget2::GetImageLocation – metoda
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7acf08262c73df00a96cfb5c244cdfc352e51ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080473"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="91604-102">ICorDebugDataTarget2::GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="91604-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="91604-103">Vrátí cestu modulu z modulu Základní adresa.</span><span class="sxs-lookup"><span data-stu-id="91604-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91604-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91604-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91604-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91604-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="91604-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="91604-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="91604-107">[in] Počet znaků ve vyrovnávací paměti, která se zobrazí cesta modulu.</span><span class="sxs-lookup"><span data-stu-id="91604-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="91604-108">[out] Ukazatel na počet znaků, které jsou zapsány do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="91604-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="91604-109">[out] Cesta modulu.</span><span class="sxs-lookup"><span data-stu-id="91604-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91604-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91604-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91604-111">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="91604-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91604-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91604-112">Requirements</span></span>  
 <span data-ttu-id="91604-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91604-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91604-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91604-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91604-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91604-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91604-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91604-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91604-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91604-117">See also</span></span>

- [<span data-ttu-id="91604-118">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91604-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="91604-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="91604-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
