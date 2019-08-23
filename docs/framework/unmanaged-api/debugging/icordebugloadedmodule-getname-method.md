---
title: Metoda ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63341bcd6079688ed1a8e18ec8c422bca1427c72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910083"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="60be8-102">Metoda ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="60be8-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="60be8-103">Získá název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="60be8-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60be8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60be8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60be8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60be8-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="60be8-106">pro Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="60be8-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="60be8-107">mimo Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="60be8-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="60be8-108">mimo Pole znaků, které obsahují název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="60be8-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60be8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60be8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60be8-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="60be8-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60be8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60be8-111">Requirements</span></span>  
 <span data-ttu-id="60be8-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60be8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60be8-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="60be8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60be8-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60be8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60be8-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60be8-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60be8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60be8-116">See also</span></span>

- [<span data-ttu-id="60be8-117">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60be8-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="60be8-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="60be8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
