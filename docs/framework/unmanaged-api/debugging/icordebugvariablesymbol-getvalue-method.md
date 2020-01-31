---
title: 'ICorDebugVariableSymbol:: GetValue – metoda'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 2dc074384d209d0740a1fb0a9a16d96ff355f02b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790882"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="352c2-102">ICorDebugVariableSymbol:: GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="352c2-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="352c2-103">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="352c2-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="352c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="352c2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="352c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="352c2-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="352c2-106">pro Počáteční posun v proměnné, ze které se má číst hodnota</span><span class="sxs-lookup"><span data-stu-id="352c2-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="352c2-107">Tento parametr se používá při čtení polí členů v objektu.</span><span class="sxs-lookup"><span data-stu-id="352c2-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="352c2-108">pro Velikost argumentu `context` v bajtech.</span><span class="sxs-lookup"><span data-stu-id="352c2-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="352c2-109">pro Kontext vlákna použitý ke čtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="352c2-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="352c2-110">pro Velikost `pValue` vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="352c2-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="352c2-111">mimo Počet bajtů, které jsou ve skutečnosti zapsány do vyrovnávací paměti `pValue`.</span><span class="sxs-lookup"><span data-stu-id="352c2-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="352c2-112">mimo Bajtové pole, které obsahuje hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="352c2-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="352c2-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="352c2-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="352c2-114">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="352c2-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="352c2-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="352c2-115">Requirements</span></span>  
 <span data-ttu-id="352c2-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="352c2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="352c2-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="352c2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="352c2-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="352c2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="352c2-119">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="352c2-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352c2-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="352c2-120">See also</span></span>

- [<span data-ttu-id="352c2-121">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="352c2-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="352c2-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="352c2-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
