---
title: 'ICorDebugVariableSymbol:: GetValue – metoda'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b72b9dbeff6aa06a132dc7ec3ddd9477553c4c2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967985"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="14a51-102">ICorDebugVariableSymbol:: GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="14a51-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="14a51-103">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="14a51-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14a51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14a51-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14a51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14a51-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="14a51-106">pro Počáteční posun v proměnné, ze které se má číst hodnota</span><span class="sxs-lookup"><span data-stu-id="14a51-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="14a51-107">Tento parametr se používá při čtení polí členů v objektu.</span><span class="sxs-lookup"><span data-stu-id="14a51-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="14a51-108">pro Velikost `context` argumentu v bajtech</span><span class="sxs-lookup"><span data-stu-id="14a51-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="14a51-109">pro Kontext vlákna použitý ke čtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="14a51-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="14a51-110">pro Velikost `pValue` vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="14a51-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="14a51-111">mimo Počet bajtů, které jsou `pValue` ve skutečnosti zapsány do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="14a51-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="14a51-112">mimo Bajtové pole, které obsahuje hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="14a51-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14a51-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14a51-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14a51-114">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="14a51-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14a51-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14a51-115">Requirements</span></span>  
 <span data-ttu-id="14a51-116">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14a51-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14a51-117">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="14a51-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14a51-118">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14a51-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14a51-119">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14a51-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a51-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14a51-120">See also</span></span>

- [<span data-ttu-id="14a51-121">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14a51-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="14a51-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="14a51-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
