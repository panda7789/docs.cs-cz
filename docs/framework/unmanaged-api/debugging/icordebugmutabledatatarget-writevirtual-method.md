---
title: ICorDebugMutableDataTarget::WriteVirtual – metoda
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fba970de6e5882d3cbe9be17b5b49be5a3e81aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171649"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="0518d-102">ICorDebugMutableDataTarget::WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="0518d-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="0518d-103">Zapíše paměti do adresového prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="0518d-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0518d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0518d-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0518d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0518d-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="0518d-106">[in] Adresa, ve kterém se má zapsat obsah `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="0518d-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="0518d-107">[in] Ukazatel na bajtové pole obsahující bajty k zápisu.</span><span class="sxs-lookup"><span data-stu-id="0518d-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="0518d-108">[in] Počet bajtů v `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="0518d-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0518d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0518d-109">Return Value</span></span>  
 `S_OK` <span data-ttu-id="0518d-110">na úspěch, nebo jakékoli jiné `HRESULT` při selhání.</span><span class="sxs-lookup"><span data-stu-id="0518d-110">on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0518d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0518d-111">Remarks</span></span>  
 <span data-ttu-id="0518d-112">Pokud nelze zapsány všechny bajty, beze změny všechny bajty v adresním prostoru cílového selže volání metody.</span><span class="sxs-lookup"><span data-stu-id="0518d-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="0518d-113">(V opačném případě Cílem by být v nekonzistentním stavu, která provádí další ladění nespolehlivé.)</span><span class="sxs-lookup"><span data-stu-id="0518d-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0518d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0518d-114">Requirements</span></span>  
 <span data-ttu-id="0518d-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0518d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0518d-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0518d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0518d-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0518d-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0518d-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0518d-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0518d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0518d-119">See also</span></span>

- [<span data-ttu-id="0518d-120">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0518d-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="0518d-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0518d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
