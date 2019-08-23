---
title: 'ICorDebugVariableSymbol:: SetValue – metoda'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5436f56d3dcad7de3df2296485b0a36e5b3cfd79
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967969"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="40970-102">ICorDebugVariableSymbol:: SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="40970-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="40970-103">Přiřadí hodnotu bajtového pole proměnné.</span><span class="sxs-lookup"><span data-stu-id="40970-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40970-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40970-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40970-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40970-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="40970-106">pro Počáteční posun v proměnné, při které má být nastavena hodnota.</span><span class="sxs-lookup"><span data-stu-id="40970-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="40970-107">Tento parametr se používá při zápisu do polí členů v objektu.</span><span class="sxs-lookup"><span data-stu-id="40970-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="40970-108">pro Identifikátor vlákna vlákna, jehož kontext musí být aktualizován, aby odrážel novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="40970-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="40970-109">pro Velikost v bajtech kontextu vlákna.</span><span class="sxs-lookup"><span data-stu-id="40970-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="40970-110">pro Kontext vlákna použitý k zápisu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="40970-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="40970-111">pro Velikost `pValue` vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="40970-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="40970-112">pro Vyrovnávací paměť obsahující hodnotu, kterou chcete nastavit.</span><span class="sxs-lookup"><span data-stu-id="40970-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40970-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40970-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40970-114">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="40970-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40970-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40970-115">Requirements</span></span>  
 <span data-ttu-id="40970-116">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40970-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40970-117">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40970-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40970-118">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40970-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40970-119">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40970-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40970-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40970-120">See also</span></span>

- [<span data-ttu-id="40970-121">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40970-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="40970-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="40970-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
