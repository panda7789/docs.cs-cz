---
title: 'ICorDebugMergedAssemblyRecord:: getculture – metoda'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f39a1f17c80d27a38c0f2a8a516405f72c79bbcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131416"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="c7534-102">ICorDebugMergedAssemblyRecord:: getculture – metoda</span><span class="sxs-lookup"><span data-stu-id="c7534-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="c7534-103">Získá řetězec názvu jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7534-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7534-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7534-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7534-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7534-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="c7534-106">pro Počet znaků ve vyrovnávací paměti `szCulture`.</span><span class="sxs-lookup"><span data-stu-id="c7534-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="c7534-107">mimo Počet znaků skutečně zapsaných do vyrovnávací paměti `szCulture`.</span><span class="sxs-lookup"><span data-stu-id="c7534-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="c7534-108">mimo Pole znaků, které obsahuje název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="c7534-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7534-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7534-109">Remarks</span></span>  
 <span data-ttu-id="c7534-110">Název jazykové verze je jedinečný řetězec, který identifikuje jazykovou verzi, jako je "en-US" (pro anglickou (USA) jazykovou verzi), nebo "neutrální" (pro neutrální jazykovou verzi).</span><span class="sxs-lookup"><span data-stu-id="c7534-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7534-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c7534-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7534-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7534-112">Requirements</span></span>  
 <span data-ttu-id="c7534-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7534-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7534-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c7534-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7534-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c7534-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7534-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7534-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7534-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7534-117">See also</span></span>

- [<span data-ttu-id="c7534-118">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7534-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="c7534-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c7534-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
