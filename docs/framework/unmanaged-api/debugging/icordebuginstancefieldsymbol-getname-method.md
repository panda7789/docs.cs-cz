---
title: 'ICorDebugInstanceFieldSymbol:: GetName – Metoda'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1b3cc489c504942806b043fa2e3b76d5415d84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936938"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="39034-102">ICorDebugInstanceFieldSymbol:: GetName – Metoda</span><span class="sxs-lookup"><span data-stu-id="39034-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="39034-103">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="39034-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39034-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39034-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39034-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39034-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="39034-106">pro Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="39034-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="39034-107">mimo Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="39034-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="39034-108">mimo Pole znaků, které ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="39034-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39034-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39034-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39034-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="39034-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39034-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39034-111">Requirements</span></span>  
 <span data-ttu-id="39034-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39034-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39034-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="39034-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39034-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39034-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39034-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39034-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39034-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39034-116">See also</span></span>

- [<span data-ttu-id="39034-117">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="39034-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="39034-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="39034-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
