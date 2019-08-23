---
title: 'ICorDebugMergedAssemblyRecord:: getculture – metoda'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0f3ecee5a003587771871a178356d6dbfd8a636
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936845"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="7d139-102">ICorDebugMergedAssemblyRecord:: getculture – metoda</span><span class="sxs-lookup"><span data-stu-id="7d139-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="7d139-103">Získá řetězec názvu jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d139-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d139-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d139-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d139-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d139-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="7d139-106">pro Počet znaků ve `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7d139-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="7d139-107">mimo Počet znaků, které jsou `szCulture` ve skutečnosti zapsány do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7d139-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="7d139-108">mimo Pole znaků, které obsahuje název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="7d139-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d139-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d139-109">Remarks</span></span>  
 <span data-ttu-id="7d139-110">Název jazykové verze je jedinečný řetězec, který identifikuje jazykovou verzi, jako je "en-US" (pro anglickou (USA) jazykovou verzi), nebo "neutrální" (pro neutrální jazykovou verzi).</span><span class="sxs-lookup"><span data-stu-id="7d139-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d139-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7d139-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d139-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d139-112">Requirements</span></span>  
 <span data-ttu-id="7d139-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d139-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d139-114">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d139-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d139-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d139-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d139-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d139-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d139-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d139-117">See also</span></span>

- [<span data-ttu-id="7d139-118">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d139-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="7d139-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7d139-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
