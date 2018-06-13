---
title: ICorDebugMutableDataTarget::WriteVirtual – metoda
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 184ae290b3a7d86a3c0351d4cfb072bce37337d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417411"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="8d510-102">ICorDebugMutableDataTarget::WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="8d510-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="8d510-103">Zapíše paměti do adresního prostoru procesu cíl.</span><span class="sxs-lookup"><span data-stu-id="8d510-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d510-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d510-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d510-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d510-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="8d510-106">[v] Adresa, kam chcete zapisovat obsah `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="8d510-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="8d510-107">[v] Ukazatel na bajtové pole obsahující bajty k zápisu.</span><span class="sxs-lookup"><span data-stu-id="8d510-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="8d510-108">[v] Počet bajtů v `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="8d510-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d510-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8d510-109">Return Value</span></span>  
 <span data-ttu-id="8d510-110">`S_OK` na úspěch nebo jakékoliv `HRESULT` při selhání.</span><span class="sxs-lookup"><span data-stu-id="8d510-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d510-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d510-111">Remarks</span></span>  
 <span data-ttu-id="8d510-112">Pokud žádné bajtů nelze zapsat, aniž byste museli měnit žádné bajtů v adresním prostoru cíl selže volání metody.</span><span class="sxs-lookup"><span data-stu-id="8d510-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="8d510-113">(Jinak, cíl by být v nekonzistentním stavu, který vytvoří další ladění nespolehlivé.)</span><span class="sxs-lookup"><span data-stu-id="8d510-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d510-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d510-114">Requirements</span></span>  
 <span data-ttu-id="8d510-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d510-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d510-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d510-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d510-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d510-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d510-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d510-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d510-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d510-119">See Also</span></span>  
 [<span data-ttu-id="8d510-120">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d510-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="8d510-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8d510-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
