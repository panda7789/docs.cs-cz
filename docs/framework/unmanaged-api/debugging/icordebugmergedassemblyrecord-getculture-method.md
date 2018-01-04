---
title: "ICorDebugMergedAssemblyRecord::GetCulture – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7963d311707d12aa697c606605f9a34b6f65d1eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="326a1-102">ICorDebugMergedAssemblyRecord::GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="326a1-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="326a1-103">Získá řetězec název jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="326a1-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="326a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="326a1-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="326a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="326a1-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="326a1-106">[v] Počet znaků `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="326a1-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="326a1-107">[out] Počet znaků, které jsou ve skutečnosti zapsána do `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="326a1-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="326a1-108">[out] Pole znaků, který obsahuje název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="326a1-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="326a1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="326a1-109">Remarks</span></span>  
 <span data-ttu-id="326a1-110">Název jazykové verze je jedinečný řetězec, který určuje jazykovou verzi, jako je například "en US" (pro jazykovou verzi Czech (Czech Republic)), nebo "neutrální" (pro neutrální jazykovou verzi).</span><span class="sxs-lookup"><span data-stu-id="326a1-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="326a1-111">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="326a1-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="326a1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="326a1-112">Requirements</span></span>  
 <span data-ttu-id="326a1-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="326a1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="326a1-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="326a1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="326a1-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="326a1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="326a1-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="326a1-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="326a1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="326a1-117">See Also</span></span>  
 [<span data-ttu-id="326a1-118">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="326a1-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="326a1-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="326a1-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
