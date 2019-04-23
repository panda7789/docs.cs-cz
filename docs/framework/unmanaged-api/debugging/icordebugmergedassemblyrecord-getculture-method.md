---
title: ICorDebugMergedAssemblyRecord::GetCulture – metoda
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 093b21a439b96c9fe2f971300f314d1b75527f1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207198"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="a6c68-102">ICorDebugMergedAssemblyRecord::GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="a6c68-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="a6c68-103">Získá řetězec názvu jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="a6c68-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6c68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6c68-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6c68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6c68-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="a6c68-106">[in] Počet znaků `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a6c68-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="a6c68-107">[out] Počet aktuálně zapsaných do znaků `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a6c68-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="a6c68-108">[out] Pole znaků, který obsahuje název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="a6c68-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6c68-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6c68-109">Remarks</span></span>  
 <span data-ttu-id="a6c68-110">Název jazykové verze je jedinečný řetězec, který určuje jazykovou verzi, například "en US" (pro jazykové verze Angličtina (Spojené státy)) nebo "neutrální" (pro neutrální jazykovou verzi).</span><span class="sxs-lookup"><span data-stu-id="a6c68-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6c68-111">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a6c68-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6c68-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6c68-112">Requirements</span></span>  
 <span data-ttu-id="a6c68-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6c68-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6c68-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6c68-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6c68-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6c68-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6c68-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6c68-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c68-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6c68-117">See also</span></span>

- [<span data-ttu-id="a6c68-118">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6c68-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="a6c68-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a6c68-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
