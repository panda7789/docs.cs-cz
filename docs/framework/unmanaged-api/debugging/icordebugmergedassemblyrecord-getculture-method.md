---
title: ICorDebugMergedAssemblyRecord::GetCulture – metoda
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0472a52d0893bfd487cd6daa6548ec1ce0c44a9b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762206"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="7fa58-102">ICorDebugMergedAssemblyRecord::GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="7fa58-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="7fa58-103">Získá řetězec názvu jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="7fa58-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fa58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fa58-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fa58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fa58-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="7fa58-106">[in] Počet znaků `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7fa58-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="7fa58-107">[out] Počet aktuálně zapsaných do znaků `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7fa58-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="7fa58-108">[out] Pole znaků, který obsahuje název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="7fa58-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fa58-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fa58-109">Remarks</span></span>  
 <span data-ttu-id="7fa58-110">Název jazykové verze je jedinečný řetězec, který určuje jazykovou verzi, například "en US" (pro jazykové verze Angličtina (Spojené státy)) nebo "neutrální" (pro neutrální jazykovou verzi).</span><span class="sxs-lookup"><span data-stu-id="7fa58-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fa58-111">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7fa58-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fa58-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fa58-112">Requirements</span></span>  
 <span data-ttu-id="7fa58-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fa58-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fa58-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fa58-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fa58-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fa58-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fa58-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fa58-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa58-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fa58-117">See also</span></span>

- [<span data-ttu-id="7fa58-118">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fa58-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="7fa58-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7fa58-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
