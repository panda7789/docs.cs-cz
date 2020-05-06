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
ms.openlocfilehash: 1598130eb097655d3e83689956eb3614103eb573
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860377"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="b8e58-102">ICLRDebugging::OpenVirtualProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="b8e58-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="b8e58-103">Získá rozhraní ICorDebugProcess, které odpovídá modulu CLR (Common Language Runtime) načtenému v procesu.</span><span class="sxs-lookup"><span data-stu-id="b8e58-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8e58-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b8e58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8e58-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="b8e58-106">pro Základní adresa modulu v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="b8e58-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="b8e58-107">Pokud zadaný modul není modul CLR, vrátí se COR_E_NOT_CLR.</span><span class="sxs-lookup"><span data-stu-id="b8e58-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="b8e58-108">pro Abstrakce cíle dat, která umožňuje spravovanému ladicímu programu zkontrolovat stav procesu.</span><span class="sxs-lookup"><span data-stu-id="b8e58-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="b8e58-109">Ladicí program musí implementovat rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b8e58-109">The debugger must implement the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="b8e58-110">Rozhraní [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) byste měli implementovat pro podporu scénářů, ve kterých se modul CLR, který právě ladíte, nenainstaluje místně na počítači.</span><span class="sxs-lookup"><span data-stu-id="b8e58-110">You should implement the [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="b8e58-111">pro Rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje umístění a načtení knihoven ladění specifických pro konkrétní verzi na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="b8e58-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="b8e58-112">Tento parametr je vyžadován pouze v `ppProcess` případě `pFlags` , že `null`není.</span><span class="sxs-lookup"><span data-stu-id="b8e58-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="b8e58-113">pro Nejvyšší verze CLR, kterou tento ladicí program může ladit.</span><span class="sxs-lookup"><span data-stu-id="b8e58-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="b8e58-114">Měli byste zadat hlavní, vedlejší a buildové verze z nejnovější verze CLR, kterou tento ladicí program podporuje, a nastavit číslo revize na 65535 pro budoucí místní verze údržby CLR.</span><span class="sxs-lookup"><span data-stu-id="b8e58-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="b8e58-115">pro ID rozhraní ICorDebugProcess, které se má načíst</span><span class="sxs-lookup"><span data-stu-id="b8e58-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="b8e58-116">V současné době jsou k disIID_CORDEBUGPROCESS3 pouze přijatelné hodnoty, IID_CORDEBUGPROCESS2 a IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="b8e58-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="b8e58-117">mimo Ukazatel na rozhraní modelu COM, které je identifikováno `riidProcess`.</span><span class="sxs-lookup"><span data-stu-id="b8e58-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="b8e58-118">[in, out] Verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b8e58-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="b8e58-119">U vstupu může být `null`tato hodnota.</span><span class="sxs-lookup"><span data-stu-id="b8e58-119">On input, this value can be `null`.</span></span> <span data-ttu-id="b8e58-120">Může také ukazovat na strukturu [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) . v takovém případě musí být `wStructVersion` pole struktury inicializováno na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="b8e58-120">It can also point to a [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="b8e58-121">Ve výstupu se vrácená `CLR_DEBUGGING_VERSION` struktura vyplní informacemi o verzi pro modul CLR.</span><span class="sxs-lookup"><span data-stu-id="b8e58-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="b8e58-122">mimo Informační příznaky zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b8e58-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="b8e58-123">Popis příznaků najdete v tématu věnovaném [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b8e58-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8e58-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b8e58-124">Return Value</span></span>  
 <span data-ttu-id="b8e58-125">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="b8e58-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b8e58-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8e58-126">HRESULT</span></span>|<span data-ttu-id="b8e58-127">Popis</span><span class="sxs-lookup"><span data-stu-id="b8e58-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8e58-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="b8e58-128">S_OK</span></span>|<span data-ttu-id="b8e58-129">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="b8e58-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="b8e58-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b8e58-130">E_POINTER</span></span>|<span data-ttu-id="b8e58-131">`pDataTarget` je `null`.</span><span class="sxs-lookup"><span data-stu-id="b8e58-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="b8e58-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="b8e58-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="b8e58-133">Zpětné volání [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) vrací chybu nebo neposkytuje platný popisovač.</span><span class="sxs-lookup"><span data-stu-id="b8e58-133">The [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="b8e58-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="b8e58-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="b8e58-135">`pDataTarget`neimplementuje požadovaná cílová rozhraní dat pro tuto verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b8e58-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="b8e58-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="b8e58-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="b8e58-137">Uvedený modul není modul CLR.</span><span class="sxs-lookup"><span data-stu-id="b8e58-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="b8e58-138">Tato hodnota HRESULT je vrácena také v případě, že modul CLR nelze zjistit, protože paměť je poškozena, modul není k dispozici nebo je verze CLR novější než verze Shim.</span><span class="sxs-lookup"><span data-stu-id="b8e58-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="b8e58-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="b8e58-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="b8e58-140">Tato verze modulu runtime nepodporuje tento ladicí model.</span><span class="sxs-lookup"><span data-stu-id="b8e58-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="b8e58-141">Model ladění není aktuálně podporován verzemi CLR před .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b8e58-141">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="b8e58-142">Po `pwszVersion` této chybě je výstupní parametr stále nastaven na správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8e58-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="b8e58-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="b8e58-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="b8e58-144">Verze modulu CLR je vyšší než verze, které tento ladicí program vyžaduje pro podporu.</span><span class="sxs-lookup"><span data-stu-id="b8e58-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="b8e58-145">Po `pwszVersion` této chybě je výstupní parametr stále nastaven na správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8e58-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="b8e58-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="b8e58-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="b8e58-147">`riidProcess` Rozhraní není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b8e58-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="b8e58-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="b8e58-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="b8e58-149">`CLR_DEBUGGING_VERSION` Struktura neobsahuje rozpoznanou hodnotu pro `wStructVersion`.</span><span class="sxs-lookup"><span data-stu-id="b8e58-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="b8e58-150">Jediná přijatá hodnota je v tomto okamžiku 0.</span><span class="sxs-lookup"><span data-stu-id="b8e58-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b8e58-151">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b8e58-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8e58-152">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8e58-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8e58-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8e58-153">Requirements</span></span>  
 <span data-ttu-id="b8e58-154">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8e58-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8e58-155">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b8e58-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8e58-156">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b8e58-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8e58-157">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8e58-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e58-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8e58-158">See also</span></span>

- [<span data-ttu-id="b8e58-159">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8e58-159">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b8e58-160">Ladění</span><span class="sxs-lookup"><span data-stu-id="b8e58-160">Debugging</span></span>](index.md)
