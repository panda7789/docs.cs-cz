---
title: ICorDebugProcess::WriteMemory – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599bf310a0b819bc662b90a5a86e87ac27c37b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737017"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="4dcaf-102">ICorDebugProcess::WriteMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="4dcaf-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="4dcaf-103">Zapíše data do oblasti paměti v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dcaf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dcaf-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dcaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4dcaf-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="4dcaf-106">[in] A `CORDB_ADDRESS` zapsat hodnotu, která je základní adresa paměti oblasti, ke kterým datům.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="4dcaf-107">Předtím, než dojde k přenosu dat, systém ověří, zda oblasti paměti o zadané velikosti, začínající na základní adrese přístupné pro zápis.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="4dcaf-108">Pokud není dostupný, metoda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="4dcaf-109">[in] Počet bajtů, které mají být zapsána do oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="4dcaf-110">[in] Vyrovnávací paměť, která obsahuje data, která má být proveden zápis.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="4dcaf-111">[out] Ukazovat na proměnnou, která přijímá počet bajtů zapsaný na oblast paměti v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="4dcaf-112">Pokud `written` má hodnotu NULL, tento parametr je ignorován.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dcaf-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4dcaf-113">Remarks</span></span>  
 <span data-ttu-id="4dcaf-114">Data je zapsána automaticky za všechny zarážky.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="4dcaf-115">V rozhraní .NET Framework verze 2.0 nativní ladicí programy nepoužívejte tuto metodu vkládat zarážky na datový proud instrukcí.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="4dcaf-116">Použití [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="4dcaf-117">`WriteMemory` Metoda by měla sloužit pouze mimo spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="4dcaf-118">Tato metoda můžou poškodit modul runtime, pokud používá nesprávně.</span><span class="sxs-lookup"><span data-stu-id="4dcaf-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dcaf-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4dcaf-119">Requirements</span></span>  
 <span data-ttu-id="4dcaf-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dcaf-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dcaf-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4dcaf-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dcaf-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dcaf-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dcaf-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dcaf-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
