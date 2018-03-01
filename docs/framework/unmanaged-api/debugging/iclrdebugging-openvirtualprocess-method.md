---
title: "ICLRDebugging::OpenVirtualProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f1f71f42f10c3d25714998d1697b20a5ee13e055
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="0385b-102">ICLRDebugging::OpenVirtualProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="0385b-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="0385b-103">Získá rozhraní ICorDebugProcess, která odpovídá common language runtime (CLR) modul načíst v procesu.</span><span class="sxs-lookup"><span data-stu-id="0385b-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0385b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0385b-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="0385b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0385b-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="0385b-106">[v] Základní adresa modulu v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="0385b-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="0385b-107">COR_E_NOT_CLR bude vrácen, pokud zadaný modul není modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0385b-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="0385b-108">[v] Abstrakce cílový data, která umožňuje spravované ladicí program ke kontrole stavu procesu.</span><span class="sxs-lookup"><span data-stu-id="0385b-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="0385b-109">Ladicí program musí implementovat [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0385b-109">The debugger must implement the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="0385b-110">Měli byste implementovat [iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) rozhraní podporu scénářů, kde není CLR, který je právě laděn nainstalovaná místně v počítači.</span><span class="sxs-lookup"><span data-stu-id="0385b-110">You should implement the [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="0385b-111">[v] Rozhraní zpětné volání zprostředkovatele knihovny, které lze najít a načíst na vyžádání specifické pro verzi ladění knihoven.</span><span class="sxs-lookup"><span data-stu-id="0385b-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="0385b-112">Tento parametr je vyžadován, pouze pokud `ppProcess` nebo `pFlags` není `null`.</span><span class="sxs-lookup"><span data-stu-id="0385b-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="0385b-113">[v] Nejvyšší verze modulu CLR, který můžete ladit tento ladicí program.</span><span class="sxs-lookup"><span data-stu-id="0385b-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="0385b-114">By měl určit hlavní, vedlejší verzi a vytvářet verze z nejnovější verze CLR, kterou podporuje tento ladicí program a nastavte číslo revize do 65535, aby dokázala pojmout budoucí CLR místní obsluhy verze.</span><span class="sxs-lookup"><span data-stu-id="0385b-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="0385b-115">[v] ID rozhraní ICorDebugProcess k načtení.</span><span class="sxs-lookup"><span data-stu-id="0385b-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="0385b-116">V současné době jsou pouze hodnoty IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 a IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="0385b-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="0385b-117">[out] Ukazatel na rozhraní modelu COM, která je identifikovaná `riidProcess`.</span><span class="sxs-lookup"><span data-stu-id="0385b-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="0385b-118">[ve out] Verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0385b-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="0385b-119">Na vstupu, tato hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="0385b-119">On input, this value can be `null`.</span></span> <span data-ttu-id="0385b-120">Může taky ukazovat na [clr_debugging_version –](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) struktury v takovém případě struktura `wStructVersion` pole musí být inicializován na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="0385b-120">It can also point to a [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="0385b-121">Na výstupu vráceného `CLR_DEBUGGING_VERSION` struktura se uvede informace o verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0385b-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="0385b-122">[out] Informační příznaky o zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0385b-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="0385b-123">Najdete v článku [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) tématu Popis příznaků.</span><span class="sxs-lookup"><span data-stu-id="0385b-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0385b-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0385b-124">Return Value</span></span>  
 <span data-ttu-id="0385b-125">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="0385b-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0385b-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0385b-126">HRESULT</span></span>|<span data-ttu-id="0385b-127">Popis</span><span class="sxs-lookup"><span data-stu-id="0385b-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0385b-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="0385b-128">S_OK</span></span>|<span data-ttu-id="0385b-129">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="0385b-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="0385b-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0385b-130">E_POINTER</span></span>|<span data-ttu-id="0385b-131">`pDataTarget`je `null`.</span><span class="sxs-lookup"><span data-stu-id="0385b-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="0385b-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="0385b-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="0385b-133">[Iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) zpětného volání vrátí chybu nebo neposkytuje platný popisovač.</span><span class="sxs-lookup"><span data-stu-id="0385b-133">The [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="0385b-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="0385b-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="0385b-135">`pDataTarget`neimplementuje rozhraní target požadovaných dat pro tuto verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0385b-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="0385b-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="0385b-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="0385b-137">Modul uvedené není modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0385b-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="0385b-138">Tato HRESULT je také vrácena, pokud modul CLR nelze nalézt, protože byl poškozen paměti, modul není k dispozici nebo CLR verze je novější než verze shim.</span><span class="sxs-lookup"><span data-stu-id="0385b-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="0385b-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="0385b-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="0385b-140">Tato verze modulu runtime nepodporuje tento ladění model.</span><span class="sxs-lookup"><span data-stu-id="0385b-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="0385b-141">V současné době ladění modelu není podporována verze CLR před [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0385b-141">Currently, the debugging model is not supported by CLR versions before the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="0385b-142">`pwszVersion` Výstupní parametr je stále nastavené na správnou hodnotu po této chybě.</span><span class="sxs-lookup"><span data-stu-id="0385b-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="0385b-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="0385b-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="0385b-144">Je větší než verze, kterou tento ladicí program deklarace identity pro podporu verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0385b-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="0385b-145">`pwszVersion` Výstupní parametr je stále nastavené na správnou hodnotu po této chybě.</span><span class="sxs-lookup"><span data-stu-id="0385b-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="0385b-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="0385b-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="0385b-147">`riidProcess` Rozhraní není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0385b-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="0385b-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="0385b-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="0385b-149">`CLR_DEBUGGING_VERSION` Struktura nemá platný hodnotu `wStructVersion`.</span><span class="sxs-lookup"><span data-stu-id="0385b-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="0385b-150">Jediná hodnota přijaté v tuto chvíli je 0.</span><span class="sxs-lookup"><span data-stu-id="0385b-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0385b-151">Výjimky</span><span class="sxs-lookup"><span data-stu-id="0385b-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0385b-152">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0385b-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0385b-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0385b-153">Requirements</span></span>  
 <span data-ttu-id="0385b-154">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0385b-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0385b-155">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0385b-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0385b-156">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0385b-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0385b-157">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0385b-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0385b-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="0385b-158">See Also</span></span>  
 [<span data-ttu-id="0385b-159">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0385b-159">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0385b-160">Ladění</span><span class="sxs-lookup"><span data-stu-id="0385b-160">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
