---
title: ICLRDebugging::OpenVirtualProcess – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4ed9526dc38d72b01798215bc602fb8298c2bc3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478021"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="0257a-102">ICLRDebugging::OpenVirtualProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="0257a-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="0257a-103">Získá icordebugprocess – rozhraní, která odpovídá common language runtime (CLR) modulu načtené v procesu.</span><span class="sxs-lookup"><span data-stu-id="0257a-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0257a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0257a-104">Syntax</span></span>  
  
```  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0257a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0257a-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="0257a-106">[in] Základní adresa modul v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="0257a-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="0257a-107">COR_E_NOT_CLR bude vrácen, pokud zadaný modul není modul CLR.</span><span class="sxs-lookup"><span data-stu-id="0257a-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="0257a-108">[in] Abstrakce cílové data, která umožňuje spravovanému ladicímu programu na kontrolu stavu procesu.</span><span class="sxs-lookup"><span data-stu-id="0257a-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="0257a-109">Ladicí program musí implementovat [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0257a-109">The debugger must implement the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="0257a-110">Měli byste implementovat [iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) rozhraní pro zajištění podpory scénářů, kde není CLR, který je právě laděna nainstalovaný místně na počítači.</span><span class="sxs-lookup"><span data-stu-id="0257a-110">You should implement the [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="0257a-111">[in] Rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje knihovnám ladění specifickým pro verzi k vyhledání a načtení na požádání.</span><span class="sxs-lookup"><span data-stu-id="0257a-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="0257a-112">Tento parametr je povinný, jenom Pokud `ppProcess` nebo `pFlags` není `null`.</span><span class="sxs-lookup"><span data-stu-id="0257a-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="0257a-113">[in] Nejvyšší verze modulu CLR, který lze ladit tímto ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="0257a-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="0257a-114">By měl určit hlavní, vedlejší verzi a vytvářet verze z nejnovější verze modulu CLR, který podporuje tento ladicí program a nastavit číslo revize 65535 tak, aby vyhovovaly budoucí místní CLR servisní verze.</span><span class="sxs-lookup"><span data-stu-id="0257a-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="0257a-115">[in] Icordebugprocess – rozhraní ID pro načtení.</span><span class="sxs-lookup"><span data-stu-id="0257a-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="0257a-116">V současné době jsou pouze hodnoty IID_CORDEBUGPROCESS3 IID_CORDEBUGPROCESS2 a IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="0257a-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="0257a-117">[out] Ukazatel na rozhraní modelu COM, která je identifikovaná `riidProcess`.</span><span class="sxs-lookup"><span data-stu-id="0257a-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="0257a-118">[out v] Verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0257a-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="0257a-119">Na vstupu, tato hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="0257a-119">On input, this value can be `null`.</span></span> <span data-ttu-id="0257a-120">Můžete také ukázat [clr_debugging_version –](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) struktury, v takovém případě struktura `wStructVersion` pole musí být inicializován na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="0257a-120">It can also point to a [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="0257a-121">Na výstupu vráceného `CLR_DEBUGGING_VERSION` struktura se vyplní informace o verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="0257a-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="0257a-122">[out] Informační příznaky o zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0257a-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="0257a-123">Zobrazit [clr_debugging_process_flags –](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) tématu Popis příznaky.</span><span class="sxs-lookup"><span data-stu-id="0257a-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0257a-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0257a-124">Return Value</span></span>  
 <span data-ttu-id="0257a-125">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="0257a-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0257a-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0257a-126">HRESULT</span></span>|<span data-ttu-id="0257a-127">Popis</span><span class="sxs-lookup"><span data-stu-id="0257a-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0257a-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="0257a-128">S_OK</span></span>|<span data-ttu-id="0257a-129">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="0257a-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="0257a-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0257a-130">E_POINTER</span></span>|<span data-ttu-id="0257a-131">`pDataTarget` je `null`.</span><span class="sxs-lookup"><span data-stu-id="0257a-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="0257a-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="0257a-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="0257a-133">[Iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) zpětného volání vrátí chybu nebo neposkytuje platný popisovač.</span><span class="sxs-lookup"><span data-stu-id="0257a-133">The [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="0257a-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="0257a-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="0257a-135">`pDataTarget` neimplementuje rozhraní target požadovaná data pro tuto verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0257a-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="0257a-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="0257a-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="0257a-137">Zadaný modul není modul CLR.</span><span class="sxs-lookup"><span data-stu-id="0257a-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="0257a-138">Hodnota HRESULT je také vrácen, když modul CLR nelze zjistit, že paměť byla poškozena, modul není k dispozici nebo verze CLR je novější než verze překrytí.</span><span class="sxs-lookup"><span data-stu-id="0257a-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="0257a-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="0257a-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="0257a-140">Tuto verzi modulu runtime nepodporuje model ladění.</span><span class="sxs-lookup"><span data-stu-id="0257a-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="0257a-141">V současné době nepodporuje model ladění CLR verze starší než [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0257a-141">Currently, the debugging model is not supported by CLR versions before the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="0257a-142">`pwszVersion` Výstupní parametr je stále nastaven na správnou hodnotu po této chybě.</span><span class="sxs-lookup"><span data-stu-id="0257a-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="0257a-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="0257a-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="0257a-144">Verzi modulu CLR je vyšší než verze, které se na podporu deklarací identity tímto ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="0257a-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="0257a-145">`pwszVersion` Výstupní parametr je stále nastaven na správnou hodnotu po této chybě.</span><span class="sxs-lookup"><span data-stu-id="0257a-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="0257a-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="0257a-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="0257a-147">`riidProcess` Rozhraní není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0257a-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="0257a-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="0257a-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="0257a-149">`CLR_DEBUGGING_VERSION` Struktura nemá rozpoznaná hodnota pro `wStructVersion`.</span><span class="sxs-lookup"><span data-stu-id="0257a-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="0257a-150">Jediná akceptovaná hodnota v tuto chvíli je 0.</span><span class="sxs-lookup"><span data-stu-id="0257a-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0257a-151">Výjimky</span><span class="sxs-lookup"><span data-stu-id="0257a-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0257a-152">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0257a-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0257a-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0257a-153">Requirements</span></span>  
 <span data-ttu-id="0257a-154">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0257a-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0257a-155">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0257a-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0257a-156">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0257a-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0257a-157">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0257a-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0257a-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0257a-158">See also</span></span>
- [<span data-ttu-id="0257a-159">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0257a-159">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0257a-160">Ladění</span><span class="sxs-lookup"><span data-stu-id="0257a-160">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
