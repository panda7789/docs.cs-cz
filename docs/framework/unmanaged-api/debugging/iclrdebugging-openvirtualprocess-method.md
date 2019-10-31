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
ms.openlocfilehash: cd43dce995c2bc9a45a0c8134a91b20cb1dec26e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111431"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="816a1-102">ICLRDebugging::OpenVirtualProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="816a1-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="816a1-103">Získá rozhraní ICorDebugProcess, které odpovídá modulu CLR (Common Language Runtime) načtenému v procesu.</span><span class="sxs-lookup"><span data-stu-id="816a1-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="816a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="816a1-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="816a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="816a1-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="816a1-106">pro Základní adresa modulu v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="816a1-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="816a1-107">COR_E_NOT_CLR se vrátí, pokud zadaný modul není modul CLR.</span><span class="sxs-lookup"><span data-stu-id="816a1-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="816a1-108">pro Abstrakce cíle dat, která umožňuje spravovanému ladicímu programu zkontrolovat stav procesu.</span><span class="sxs-lookup"><span data-stu-id="816a1-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="816a1-109">Ladicí program musí implementovat rozhraní [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="816a1-109">The debugger must implement the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="816a1-110">Rozhraní [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) byste měli implementovat pro podporu scénářů, ve kterých se modul CLR, který právě ladíte, nenainstaluje místně na počítači.</span><span class="sxs-lookup"><span data-stu-id="816a1-110">You should implement the [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="816a1-111">pro Rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje umístění a načtení knihoven ladění specifických pro konkrétní verzi na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="816a1-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="816a1-112">Tento parametr je vyžadován pouze v případě, že `ppProcess` nebo `pFlags` není `null`.</span><span class="sxs-lookup"><span data-stu-id="816a1-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="816a1-113">pro Nejvyšší verze CLR, kterou tento ladicí program může ladit.</span><span class="sxs-lookup"><span data-stu-id="816a1-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="816a1-114">Měli byste zadat hlavní, vedlejší a buildové verze z nejnovější verze CLR, kterou tento ladicí program podporuje, a nastavit číslo revize na 65535 pro budoucí místní verze údržby CLR.</span><span class="sxs-lookup"><span data-stu-id="816a1-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="816a1-115">pro ID rozhraní ICorDebugProcess, které se má načíst</span><span class="sxs-lookup"><span data-stu-id="816a1-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="816a1-116">V současné době jediné přijatelné hodnoty jsou IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 a IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="816a1-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="816a1-117">mimo Ukazatel na rozhraní COM identifikované `riidProcess`.</span><span class="sxs-lookup"><span data-stu-id="816a1-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="816a1-118">[in, out] Verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="816a1-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="816a1-119">U vstupu může být tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="816a1-119">On input, this value can be `null`.</span></span> <span data-ttu-id="816a1-120">Může také ukazovat na strukturu [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) . v takovém případě musí být pole `wStructVersion` struktury inicializováno na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="816a1-120">It can also point to a [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="816a1-121">Ve výstupu se vrácená `CLR_DEBUGGING_VERSION` struktura vyplní informacemi o verzi pro modul CLR.</span><span class="sxs-lookup"><span data-stu-id="816a1-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="816a1-122">mimo Informační příznaky zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="816a1-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="816a1-123">Popis příznaků najdete v tématu [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="816a1-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="816a1-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="816a1-124">Return Value</span></span>  
 <span data-ttu-id="816a1-125">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="816a1-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="816a1-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="816a1-126">HRESULT</span></span>|<span data-ttu-id="816a1-127">Popis</span><span class="sxs-lookup"><span data-stu-id="816a1-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="816a1-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="816a1-128">S_OK</span></span>|<span data-ttu-id="816a1-129">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="816a1-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="816a1-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="816a1-130">E_POINTER</span></span>|<span data-ttu-id="816a1-131">`pDataTarget` je `null`.</span><span class="sxs-lookup"><span data-stu-id="816a1-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="816a1-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="816a1-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="816a1-133">Zpětné volání [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) vrací chybu nebo neposkytuje platný popisovač.</span><span class="sxs-lookup"><span data-stu-id="816a1-133">The [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="816a1-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="816a1-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="816a1-135">`pDataTarget` neimplementuje požadovaná cílová rozhraní dat pro tuto verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="816a1-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="816a1-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="816a1-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="816a1-137">Uvedený modul není modul CLR.</span><span class="sxs-lookup"><span data-stu-id="816a1-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="816a1-138">Tato hodnota HRESULT je vrácena také v případě, že modul CLR nelze zjistit, protože paměť je poškozena, modul není k dispozici nebo je verze CLR novější než verze Shim.</span><span class="sxs-lookup"><span data-stu-id="816a1-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="816a1-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="816a1-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="816a1-140">Tato verze modulu runtime nepodporuje tento ladicí model.</span><span class="sxs-lookup"><span data-stu-id="816a1-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="816a1-141">Model ladění není aktuálně podporován verzemi CLR před .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="816a1-141">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="816a1-142">Výstupní parametr `pwszVersion` je po této chybě stále nastaven na správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="816a1-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="816a1-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="816a1-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="816a1-144">Verze modulu CLR je vyšší než verze, které tento ladicí program vyžaduje pro podporu.</span><span class="sxs-lookup"><span data-stu-id="816a1-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="816a1-145">Výstupní parametr `pwszVersion` je po této chybě stále nastaven na správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="816a1-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="816a1-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="816a1-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="816a1-147">Rozhraní `riidProcess` není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="816a1-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="816a1-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="816a1-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="816a1-149">Struktura `CLR_DEBUGGING_VERSION` nemá rozpoznanou hodnotu pro `wStructVersion`.</span><span class="sxs-lookup"><span data-stu-id="816a1-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="816a1-150">Jediná přijatá hodnota je v tomto okamžiku 0.</span><span class="sxs-lookup"><span data-stu-id="816a1-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="816a1-151">Výjimky</span><span class="sxs-lookup"><span data-stu-id="816a1-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="816a1-152">Poznámky</span><span class="sxs-lookup"><span data-stu-id="816a1-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="816a1-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="816a1-153">Requirements</span></span>  
 <span data-ttu-id="816a1-154">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="816a1-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="816a1-155">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="816a1-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="816a1-156">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="816a1-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="816a1-157">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="816a1-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816a1-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="816a1-158">See also</span></span>

- [<span data-ttu-id="816a1-159">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="816a1-159">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="816a1-160">Ladění</span><span class="sxs-lookup"><span data-stu-id="816a1-160">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
