---
title: ICorDebugMergedAssemblyRecord::Metoda GetCulture
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: ad54a93b16e803170987dd56d8063669f7e67f94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178755"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="a2fd4-102">ICorDebugMergedAssemblyRecord::Metoda GetCulture</span><span class="sxs-lookup"><span data-stu-id="a2fd4-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="a2fd4-103">Získá řetězec název jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2fd4-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2fd4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2fd4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2fd4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2fd4-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="a2fd4-106">[v] Počet znaků ve `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a2fd4-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="a2fd4-107">[out] Počet znaků skutečně zapsaných `szCulture` do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a2fd4-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="a2fd4-108">[out] Pole znaků, které obsahuje název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="a2fd4-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2fd4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2fd4-109">Remarks</span></span>  
 <span data-ttu-id="a2fd4-110">Název jazykové verze je jedinečný řetězec, který identifikuje jazykovou verzi, například "en US" (pro jazykovou verzi angličtiny (Spojené státy) nebo "neutrální" (pro neutrální jazykovou verzi).</span><span class="sxs-lookup"><span data-stu-id="a2fd4-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2fd4-111">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="a2fd4-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2fd4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2fd4-112">Requirements</span></span>  
 <span data-ttu-id="a2fd4-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2fd4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2fd4-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2fd4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2fd4-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2fd4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2fd4-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2fd4-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2fd4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2fd4-117">See also</span></span>

- [<span data-ttu-id="a2fd4-118">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2fd4-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="a2fd4-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2fd4-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
