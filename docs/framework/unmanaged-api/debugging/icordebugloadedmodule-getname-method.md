---
title: Metoda ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 628f85f3045533ead7ace47b11573a0b1a46df46
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782052"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="943a6-102">Metoda ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="943a6-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="943a6-103">Získá název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="943a6-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="943a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="943a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="943a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="943a6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="943a6-106">pro Počet znaků ve vyrovnávací paměti `szName`.</span><span class="sxs-lookup"><span data-stu-id="943a6-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="943a6-107">mimo Ukazatel na počet znaků skutečně zapsaných do vyrovnávací paměti `szName`.</span><span class="sxs-lookup"><span data-stu-id="943a6-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="943a6-108">mimo Pole znaků, které obsahují název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="943a6-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="943a6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="943a6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="943a6-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="943a6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="943a6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="943a6-111">Requirements</span></span>  
 <span data-ttu-id="943a6-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="943a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="943a6-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="943a6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="943a6-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="943a6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="943a6-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="943a6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943a6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="943a6-116">See also</span></span>

- [<span data-ttu-id="943a6-117">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="943a6-117">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="943a6-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="943a6-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
