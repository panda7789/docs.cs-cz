---
title: 'ICorDebugMutableDataTarget:: Writevirtual – – metoda'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 2b4bd1dc97f37f5a514ab54f9e4d778fe3b91736
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792836"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="95054-102">ICorDebugMutableDataTarget:: Writevirtual – – metoda</span><span class="sxs-lookup"><span data-stu-id="95054-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="95054-103">Zapíše paměť do cílového adresního prostoru procesu.</span><span class="sxs-lookup"><span data-stu-id="95054-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95054-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95054-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95054-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95054-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="95054-106">pro Adresa, na které se má zapisovat obsah `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="95054-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="95054-107">pro Ukazatel na pole bajtů obsahující bajty, které mají být zapsány.</span><span class="sxs-lookup"><span data-stu-id="95054-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="95054-108">pro Počet bajtů v `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="95054-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95054-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="95054-109">Return Value</span></span>  
 <span data-ttu-id="95054-110">`S_OK` při úspěchu nebo jakékoli jiné `HRESULT` při selhání.</span><span class="sxs-lookup"><span data-stu-id="95054-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95054-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95054-111">Remarks</span></span>  
 <span data-ttu-id="95054-112">Pokud nemůžete zapsat libovolné bajty, volání metody se nepovede bez změny jakýchkoli bajtů v cílovém adresním prostoru.</span><span class="sxs-lookup"><span data-stu-id="95054-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="95054-113">(Jinak by byl cíl v nekonzistentním stavu, který umožňuje další ladění nespolehlivě.)</span><span class="sxs-lookup"><span data-stu-id="95054-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95054-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95054-114">Requirements</span></span>  
 <span data-ttu-id="95054-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95054-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95054-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="95054-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95054-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="95054-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95054-118">**Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95054-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95054-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95054-119">See also</span></span>

- [<span data-ttu-id="95054-120">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95054-120">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="95054-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="95054-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
