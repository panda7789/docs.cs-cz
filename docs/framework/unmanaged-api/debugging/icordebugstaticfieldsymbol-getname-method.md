---
title: 'ICorDebugStaticFieldSymbol:: GetName – Metoda'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: 0e4c52ff1ae6113ee2c3990a9d91682e10141902
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791833"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="44506-102">ICorDebugStaticFieldSymbol:: GetName – Metoda</span><span class="sxs-lookup"><span data-stu-id="44506-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="44506-103">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="44506-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44506-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44506-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44506-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44506-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="44506-106">pro Počet znaků ve vyrovnávací paměti `szName`.</span><span class="sxs-lookup"><span data-stu-id="44506-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="44506-107">mimo Ukazatel na počet znaků skutečně zapsaných do vyrovnávací paměti `szName`.</span><span class="sxs-lookup"><span data-stu-id="44506-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="44506-108">mimo Pole znaků, které ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="44506-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44506-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44506-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44506-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="44506-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44506-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44506-111">Requirements</span></span>  
 <span data-ttu-id="44506-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44506-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44506-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="44506-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44506-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="44506-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44506-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44506-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44506-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44506-116">See also</span></span>

- [<span data-ttu-id="44506-117">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44506-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="44506-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="44506-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
