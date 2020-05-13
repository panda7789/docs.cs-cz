---
title: 'ICorDebugMergedAssemblyRecord:: getculture – metoda'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f73aac169cc048a87aca3bfc325cf8c6243012e9
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207859"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="f0040-102">ICorDebugMergedAssemblyRecord:: getculture – metoda</span><span class="sxs-lookup"><span data-stu-id="f0040-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="f0040-103">Získá řetězec názvu jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0040-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0040-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0040-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0040-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0040-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="f0040-106">pro Počet znaků ve `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f0040-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="f0040-107">mimo Počet znaků, které jsou ve skutečnosti zapsány do `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f0040-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="f0040-108">mimo Pole znaků, které obsahuje název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="f0040-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0040-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0040-109">Remarks</span></span>  
 <span data-ttu-id="f0040-110">Název jazykové verze je jedinečný řetězec, který identifikuje jazykovou verzi, jako je "en-US" (pro anglickou (USA) jazykovou verzi), nebo "neutrální" (pro neutrální jazykovou verzi).</span><span class="sxs-lookup"><span data-stu-id="f0040-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0040-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f0040-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0040-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0040-112">Requirements</span></span>  
 <span data-ttu-id="f0040-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0040-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0040-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f0040-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0040-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f0040-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0040-116">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0040-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0040-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0040-117">See also</span></span>

- [<span data-ttu-id="f0040-118">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f0040-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="f0040-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f0040-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
