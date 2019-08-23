---
title: 'ICorDebugStaticFieldSymbol:: GetName – Metoda'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2187a205b41388d191ad4f06db6d6caa86971e13
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913419"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="dcdee-102">ICorDebugStaticFieldSymbol:: GetName – Metoda</span><span class="sxs-lookup"><span data-stu-id="dcdee-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="dcdee-103">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="dcdee-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcdee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcdee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcdee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcdee-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="dcdee-106">pro Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="dcdee-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="dcdee-107">mimo Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="dcdee-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="dcdee-108">mimo Pole znaků, které ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="dcdee-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcdee-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcdee-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dcdee-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dcdee-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcdee-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcdee-111">Requirements</span></span>  
 <span data-ttu-id="dcdee-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcdee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcdee-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dcdee-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcdee-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcdee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcdee-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcdee-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcdee-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcdee-116">See also</span></span>

- [<span data-ttu-id="dcdee-117">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcdee-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="dcdee-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dcdee-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
